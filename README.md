![Ziggy using the ziti-sdk-nodejs](https://raw.githubusercontent.com/openziti/branding/main/images/banners/Node.jpg)

<p align="center" width="100%">
OpenZiti is a free and open source project focused on bringing zero trust to any application.
     <br>
The project provides all the pieces required to implement or integrate zero trust into your solutions.
<br/>
<br/>
Please star us.
<br/>
<a href="https://github.com/openziti/ziti/stargazers"><img src="https://img.shields.io/github/stars/openziti/ziti?style=flat" ></a>
<br/>
     <br>
</p>

<p align="center" width="100%">
<a href="https://openziti.io"><img src="ziti.png" width="100"></a>
</p>

<p align="center">
    <b>
    <a>@openziti/ziti-console</a>
    <br>
    <br>
    <b>
    This repo hosts the Ziti Admin Console, and is designed to provide a user interface to help you administrate an <a href="https://openziti.io">OpenZiti Network</a> via the <a href="https://openziti.io/docs/reference/developer/api/">Ziti Edge API</a>
    <br>
    <br>
    <b>Part of the <a href="https://openziti.io/about">OpenZiti</a> ecosystem</b>
</p>

<p align="center">
    <br>
    <b>Are you interested in knowing how to easily embed programmable, high performance, zero trust networking into your application without VPNs?
    <br>
    Learn more about our <a href="https://openziti.io/about">OpenZiti</a> project.</b>
    <br>
    </p>

---
[![Build Status](https://github.com/openziti/ziti-console/workflows/Build/badge.svg?branch=main)]()
[![Issues](https://img.shields.io/github/issues-raw/openziti/ziti-console)]()
[![npm version](https://badge.fury.io/js/@openziti%2Fziti-console.svg)](https://badge.fury.io/js/@openziti%2Fziti-sdk-nodejs.svg)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![LOC](https://img.shields.io/tokei/lines/github/openziti/ziti-console)]()
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=rounded)](CONTRIBUTING.md)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-v2.0%20adopted-ff69b4.svg)](CODE_OF_CONDUCT.md)

---


# OpenZiti Console

The OpenZiti Console is an administrative web interface for an OpenZiti network.

## Deployments

Read the production deployment guides for the console as well as the controller, router, etc.

[Link to deployment guides](https://openziti.io/docs/category/deployments/)

## Requirements

To build and run the application from source, you'll also need to make sure you have the following developer tools installed and available on your command line.

| Tool        |      Version |
| :---:       | :---:        |
| Node.js     |  =18         |
| npm         | >=8.1        |
| ng          |  =16         |

### Install Angular CLI

This provides the `ng` command.

```bash
npm install -g @angular/cli@16
```

## Projects

This repository houses two projects.

1. [ziti-console-lib](./projects/ziti-console-lib) - Angular library used by the console UI.
1. [app-ziti-console](./projects/app-ziti-console) - console UI with two deployment modes.
  1. Single page application mode (recommended) 
  1. Node.js server mode (`server.js`, deprecated)

## Build

From the project root:

1. Install the projects' dependencies.

    ```bash
    npm install
    ```

1. Build the library project with Angular.

    ```bash
    ng build ziti-console-lib
    ```
### Build the Single Page Application

This is the recommended approach.

1. Build the console project with Angular.

    ```bash
    ng build ziti-console
    ```

1. You must host the static files with a web server. 
   See [the deployment guide](https://openziti.io/docs/guides/deployments/linux/console) for details on configuring the controller to host these files.
   
1. Access the console at the controller's address: https://localhost:1280/zac/

        
### Build the Standalone Node Server

This deployment mode is deprecated by the SPA mode.

1. Build the console project with Angular.

    ```bash
    ng build ziti-console-node
    ```

1. If developing the standalone Node server, run it.

    ```bash
    node server.js
    ```

1. Access the console at http://localhost:1408
1. Configure the server with the URL of the controller's edge-management API, e.g. https://localhost:1280

## Developing with Angular

There are two elements to the Angular app.

From project Root:

1. Install dependencies

    ```bash
    npm install
    ```

1. Run & watch changes in the core library in **ziti-console-lib** by running the npm script **watch:lib**

    ```bash
    ng build ziti-console-lib --watch
    ```

    * Note: The NPM library is referenced/linked in package.json as "ziti-console-lib": "file:dist/ziti-console-lib".
    This library includes the pure javascript code it shared with ziti-console, and the Angular code it shares with other apps.

1. Then in a separate window run & watch changes in the main application **app-ziti-console**

    ```bash
    ng build ziti-console-node --watch
    ```

  This ensures changes made to the NPM library get pulled into the Angular app as you are developing

