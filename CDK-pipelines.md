While doing this CDK pipeline workshop below I ran into a bunch of issues. Here are my troubleshooting notes. 

https://cdkworkshop.com/20-typescript/70-advanced-topics/200-pipelines




#### Issue 1: This CDK CLI is not compatible with the CDK library used by your application. Please upgrade the CLI to the latest version. (Cloud assembly schema version mismatch: Maximum schema version supported is 8.0.0, but found 9.0.0)



Uninstall the CDK version:

`npm uninstall -g aws-cdk`

Install specfic version which your application is using. For ex: CDK 1.158.0

`npm install -g aws-cdk@1.158.0`

Reference: https://stackoverflow.com/questions/66565550/how-to-solve-cdk-cli-version-mismatch


---

#### Issue 2: When trying to push code to codecommit you get this error `error: src refspec main does not match any `

Check the local branch name. If you're trying to push to the `main` remote branch and your local branch is `master` you'll run in to this error. Fix this by renaming the local branch to `main` and push to remote after that. 

`git master -m main`
`git push` 

---

#### Issue 3: `TS2304: Cannot find blob`

add the dom entry to the lib in  tsconfig.json. Your  tsconfig file should look like this 
```
{
  "compilerOptions": {
    "target":"ES2020",
    "module": "commonjs",
    "lib": ["es2020", "dom"],
    "outDir": "dist",
    "resolveJsonModule": true,
  },
  "exclude": [
    "coverage",
    "node_modules",
    "dist",
    "tests"
  ]
}
```

Reference: https://stackoverflow.com/a/66275649







