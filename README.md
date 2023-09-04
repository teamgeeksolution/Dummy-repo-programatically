# Dummy-repo-programatically
This is your first repository created on the 

```js
import { Octokit } from "https://esm.sh/octokit?dts";
// or npm i octokit (requires node >= 18)
// https://www.npmjs.com/package/octokit

async function createRepo() {
  const octokit = new Octokit({
    auth: "YOUR_GITHUB_TOKEN_HERE"
  });
  try {
    const response = await octokit.request("POST /orgs/teamgeeksolution/repos", {
      org: "teamgeeksolution",
      name: "Dummy-repo-programatically",
      description: "This is your first repository created on the fly",
      homepage: "https://github.com",
      private: false,
      has_issues: true,
      has_projects: false,
      has_wiki: false,
      headers: {
        "X-GitHub-Api-Version": "2022-11-28"
      },
      auto_init: true
    });
    console.log({ response });
  } catch (error) {
    console.log("Error occured while creating the repo", error);
  }
}

async function createOrUpdateFile() {
  const octokit = new Octokit({
    auth: "YOUR_GITHUB_TOKEN_HERE"
  });

  // FOR FOLDER
  // PUT /repos/teamgeeksolution/Dummy-repo-programatically/contents/folder/demo.md"
  try {
    const response = await octokit.request(
      "PUT /repos/teamgeeksolution/Dummy-repo-programatically/contents/demo.md",
      {
        owner: "teamgeeksolution",
        repo: "Dummy-repo-programatically",
        path: "demo.md",
        message: "creating a demo file programatically",
        committer: {
          name: "Ankur Chunekar",
          email: "ankur@thegeeksquad.tech"
        },
        content: btoa("Just dummy context to start with"), // REQUIRES A BASE64
        headers: {
          "X-GitHub-Api-Version": "2022-11-28"
        }
      }
    );
    console.log({ response });
  } catch (error) {
    console.log("Error occured while creating the FILE", error);
  }
}

// createRepo("");
// createOrUpdateFile();
```
