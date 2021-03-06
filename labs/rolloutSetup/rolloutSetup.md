# <img src="images/Rollout-blue.svg" alt="CloudBees Rollout Logo" width="40" align="top"> CloudBees Rollout Workshop Setup

## CloudBees Rollout Set-Up
In this lab, you will set up a CloudBees Rollout account and use it to manage feature flags through remote configurations created in the dashboard.

### Create a CloudBees Rollout Account 

1. In a new tab, navigate to the CloudBees Rollout [sign-up URL](https://app.rollout.io/signup).
2. Fill out the form with your name, email, and created password. After confirming your password,  check the box agreeing to Rollout's Terms of Service (which can be viewed [here](https://docs.cloudbees.com/docs/cloudbees-common/latest/subscription-agreement/)).
3. In order to control feature flags from the Rollout dashboard, we have to add the `<ROLLOUT_ENV_KEY>` to our microblog code. On the far left side of the dashboard, click the **App Settings** panel. From the resulting page, select the **Environments** tab. Click to copy your unique `<ROLLOUT_ENV_KEY>` associated with the Production environment and paste it in a notepad for future reference.

<p><img src="images/RolloutEnvKey.png" />

### Create Rollout Feature Flags

1. In Github, navigate to the microblog-frontend repository previously forked to the organization.
2. Click `Branch: master`
3. Type `initRollout` then click **"Create branch: initRollout from master"** to finish creating a new branch.

<p><img src="images/initRolloutBranch.gif" />

4. Ensure you are within the initRollout branch, then click the `src` folder. On the resulting page, click the **Create new file** button.

<p><img src="images/srcCreateNewFile.png" />

5. In the textbox next to `microblog-frontend/src/`, type: `utils/flag.js` and press return (on the keyboard).

<p><img src="images/utilsFlagJS.gif" />

6. In this file, you need to import the Rollout library, create a feature flag for a sidebar element, then setup the connection to the dashboard using the `<ROLLOUT_ENV_KEY>`. To do this, type the follow snippet within the Github code editor. Make sure that you replace `<ROLLOUT_ENV_KEY>` with your unique key copied earlier.
```javascript
import Rox from 'rox-browser'

export const Flags = {
	sidebar: new Rox.Flag(false)
};

Rox.register('default', Flags);

Rox.setup("<ROLLOUT_ENV_KEY>");
```
7. Create a commit message (e.g. Create flag.js) and select **Commit directly to the `initRollout` branch** radio button. The file and its directory path should look similar to the picture below. Then click **Commit new file**.

<p><img src="images/flagJSCommit.png" />

8. **For instructor led workshops please return to the [workshop slides](https://cloudbees-days.github.io/core-rollout-flow-workshop/rollout/#1).**

Otherwise, you may proceed to the next lab: [**Gating a Component with a CloudBees Feature Flag**](../rolloutFeature/rolloutFeature.md) or choose another lab on the [main page](../../README.md#workshop-labs).

**NOTES FOR TEAM**

Need to trigger pipeline/preview to run the application and successful install.
Should this be on master to trigger pipeline and preview?

9. Configuration Fetch Handler
