# k6-new-example

> Example repository to demonstrate the use of the k6 DevContainer feature

This repository contains a k6 example script created by the `k6 new` command.

```bash
k6 run script.js
```

<details><summary>script.js</summary>

```js file=script.js
import http from 'k6/http';
import { sleep } from 'k6';

export const options = {
  // A number specifying the number of VUs to run concurrently.
  vus: 10,
  // A string specifying the total duration of the test run.
  duration: '30s',

  // The following section contains configuration options for execution of this
  // test script in Grafana Cloud.
  //
  // See https://grafana.com/docs/grafana-cloud/k6/get-started/run-cloud-tests-from-the-cli/
  // to learn about authoring and running k6 test scripts in Grafana k6 Cloud.
  //
  // cloud: {
  //   // The ID of the project to which the test is assigned in the k6 Cloud UI.
  //   // By default tests are executed in default project.
  //   projectID: "",
  //   // The name of the test in the k6 Cloud UI.
  //   // Test runs with the same name will be grouped.
  //   name: "script.js"
  // },

  // Uncomment this section to enable the use of Browser API in your tests.
  //
  // See https://grafana.com/docs/k6/latest/using-k6-browser/running-browser-tests/ to learn more
  // about using Browser API in your test scripts.
  //
  // scenarios: {
  //   // The scenario name appears in the result summary, tags, and so on.
  //   // You can give the scenario any name, as long as each name in the script is unique.
  //   ui: {
  //     // Executor is a mandatory parameter for browser-based tests.
  //     // Shared iterations in this case tells k6 to reuse VUs to execute iterations.
  //     //
  //     // See https://grafana.com/docs/k6/latest/using-k6/scenarios/executors/ for other executor types.
  //     executor: 'shared-iterations',
  //     options: {
  //       browser: {
  //         // This is a mandatory parameter that instructs k6 to launch and
  //         // connect to a chromium-based browser, and use it to run UI-based
  //         // tests.
  //         type: 'chromium',
  //       },
  //     },
  //   },
  // }
};

// The function that defines VU logic.
//
// See https://grafana.com/docs/k6/latest/examples/get-started-with-k6/ to learn more
// about authoring k6 scripts.
//
export default function() {
  http.get('https://test.k6.io');
  sleep(1);
}
```

</details>

## Usage

The repository contains a [Development Container](https://containers.dev/) configuration, which means that k6 tests can be run immediately, without installing k6, in any [environment that supports Dev Containers](https://containers.dev/supporting) (GitHub Codespaces, JetBrains IDEs, Visual Studio Code, DevPods, CodeSandbox, etc)

<details>
<summary>devcontainer.json</summary>

```json file=.devcontainer/devcontainer.json
{
  "name": "k6-new-example",
  "image": "mcr.microsoft.com/devcontainers/base:1-bookworm",
  "features": {
    "ghcr.io/grafana/devcontainer-features/k6:1": {}
  }
}
```
</details>

**Without installing software**

You can *run k6 test without installing k6* using [GitHub Codespaces](https://docs.github.com/en/codespaces). After forking the repository, [create a codespace for your repository](https://docs.github.com/en/codespaces/developing-in-a-codespace/creating-a-codespace-for-a-repository).

**Using an IDE**

You can *run k6 test without installing k6* using [Visual Studio Code](https://code.visualstudio.com/) if the [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension is installed. After forking the repository, clone your repository and open the folder with Visual Studio Code. It will automatically detect that the folder contains a Dev Container configuration and ask you whether to open the folder in a container. Choose **"Reopen in Container"**.

