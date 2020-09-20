# My bare setup

## Sources

- Github Docs - <https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site>.
- Create React App Docs - <https://create-react-app.dev/docs/deployment/#github-pages>.

### gh-pages npm package

- With script, "deploy": "gh-pages -d build", we can push **build** to **`gh-pages`** branch of the repository.
- With script, "deploy": "gh-pages -b master -d build", we can push **build** to **`master`** branch of the repository. 

## My github pages were deployed to -> sahilrajput03.github.io/my-app -> in `gh-pages` branch.

***

## INFO: I have two scripts in my package.json file as

  "predeploy": "react-scripts build", //This is important.
  "deploy": "gh-pages -d build", //This is equally important.

1. Actually, the `npm run deploy` command will implicitly executes the `predeploy` script, so we just care about running `npm run deploy` only.
2. gh-pages -d build will just post the code of build folder in current directory to `gh-pages` branch to the github repo. NO OTHER SETUP REQUIRED.

## Github side settings

1. Add a CNAME file to `public` folder in cra (with content as -> reactapptest.ml), and when we run `npm run deploy` it implicitly runs `npm run predeploy` which is nothing but `react-scripts build` and that actually copies `CNAME` file along with the build code for site to `public` folder. And gets published to github automatically.

## Scripts settings revisited

1. Defining script "predeploy" script as "react-scripts build" in package.json file, will make our work easy, as we no longer would need to execute the `npm run build` explicitly, but since we have defined `predeploy` script, our script "npm run deploy" which is configure to "gh-pages -d build" would execute the predeploy script implicitly(automatically). Yikes!! LEARN: Anytime, we'd need to deploy to github pages, JUST USE COMMAND `npm run deploy`(I can use `nr deploy` too :D ).{no need to do `npm run build` or `npm run predeploy`}.
