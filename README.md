# Deploy Bedrock+Sage WordPress project to WP Engine

This bash script prepares a WordPress project [Bedrock](https://roots.io/bedrock/) boilerplate with the [Sage](https://roots.io/sage/) starter theme **to the WP Engine hosting platform**.

## Purpose

WP Engine expects to see a standard WordPress project in the document root for your account. Since Bedrock shifts things around a bit, This script moves your files &amp; directories around so WP Engine knows how to serve your Bedrock+Sage site.

This script performs all actions on a separate branch, which it deletes upon completion.

## Installation &amp; Setup

### 1. Setup git push

Follow [these instructions from WP Engine](https://wpengine.com/git/) to setup SSH access and git push for your WP Engine account.

### 2. Set variables

Out the box, this script assumes your theme's name is **wpengine** and your git remote's name is also **wpengine**. Open `wpdeploy.sh` and change the following variables for your application (around line 29).

* Set `themeName` to the **directory name** of your theme (/app/themes/**yourthemename**)
* Set `wpengineRemoteName` to the **origin** you created when setting up git push in your WP Engine account

---

## Usage

In short, it performs a few checks, creates a temporary deployment branch, then builds the site **locally**. It force pushes to the specified environment using WP Engine's git push feature. When complete, it removes the temp branch and puts you back on the branch you started from.

Deploy to staging:

```
sh wpedeploy.sh staging
```

Deploy to production:

```
sh wpedeploy.sh production
```

## Notes

* Deploys the local branch you run it on to whichever remote WP Engine branch you specify (production or staging)
* Completely ignores the uploads directory