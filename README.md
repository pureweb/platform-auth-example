![image info](./images/pureweb.png)

# Acquiring your PureWeb platform credentials (example framework)

This project provides an example framework for building a single-page application (SPA) to externally authenticate users using the [Auth0](https://auth0.com/) platform. The example framework uses the [PassportJS](http://www.passportjs.org/) middleware and [Express](https://expressjs.com/) web application framework. Once a user authenticates through the SPA, you can use your PureWeb project’s **ClientID** and **Client Secret** to request credentials for access to the PureWeb platform. You can then use the credentials to submit launch requests and initiate agents on the PureWeb platform.

A launch request prompts the PureWeb platform to initialize a game stream and connect the stream to web browsers. Agents connect to the PureWeb platform to either consume or contribute data.

## Contents

  * [Getting started](#getting-started)
    + [Configure environment variables](#configure-environment-variables)
    + [Set up an Auth0 account](#set-up-an-auth0-account)
    + [Set up a PureWeb account](#set-up-a-pureweb-account)
  * [Build the example framework](#build-the-example-framework)
  * [Run the example framework](#run-the-example-framework)

## Getting started

### Configure environment variables

The environment variables required to configure this example framework are stored in an `.env` file. 

Include `packages/.env` to specify the file’s location. 

**To configure environment variables:**
1) Copy the example file provided, `.env-example`, to a new `.env` file. 
2) Add the account configuration for your Auth0 account to the `.env` file; see [Set up an Auth0 account](#set-up-an-auth0-account).
3) Add the account configuration for your PureWeb account to the `.env` file; see [Set up a PureWeb account](#set-up-a-pureweb-account). 

### Set up an Auth0 account

1) Create an [Auth0](https://auth0.com/) account.
2) Create a regular web application (from the left panel in your account) and go to the **Settings** tab for your new application.
3) In the `.env` file you copied earlier, add or update the values for the following variables with the corresponding values on the **Settings** tab:
* `AUTH0_CLIENT_ID`
* `AUTH0_DOMAIN`
* `AUTH0_CLIENT_SECRET`
4) Also in the `.env` file you copied earlier, set `Allowable Callback URLs` to:
`http://localhost:3000/callback, http://localhost:8000/callback`
5) Finally, set `Allowed Logout URLs` to:
`http://localhost:3000/, http://localhost:8000/`

### Set up a PureWeb account

1) Sign in to the [PureWeb Console](https://console.pureweb.io/).
2) Create a trial account if you don't already have one, and upload your project to the PureWeb console.
3) Click the cog icon in your project to open the **Project Settings** page.
4) Add or update the value for the `PUREWEB_PROJECT_CLIENT_ID` variable in the `.env` file you copied earlier with the **Client ID** on the **Project Settings** page.
5) Add or update the value for the `PUREWEB_PROJECT_CLIENT_SECRET` variable in the `.env` file you copied earlier with the **Client Secret** on the **Project Settings** page.

## Build the example framework

1) Install the required NPM packages:
* `yarn install`

>Note:
>The required PureWeb library [@pureweb/platform-admin-sdk](https://www.npmjs.com/package/@pureweb/platform-admin-sdk) is automatically installed via NPM.

2) Run the server:
* `yarn dev`

This builds the code and runs a local development server (at http://localhost:8000).

## Run the example framework

In a separate terminal window, run the client:
* `yarn ui`

This launches the client in a new browser window (at http://localhost:3000).

You should now be able to create an account and sign in. You can either create an account using an email/password combination, or using Google Single Sign-on (SSO).

Once you successfully log in, click the **PureWeb Credentials** button to acquire credentials to the PureWeb platform. 

To view your user account information from Auth0, click the **User Profile** button.
