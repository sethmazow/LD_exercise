### Seth's Technical Exercise Instructions 
I built a simple feature flag for this exercise, here's how to set it up. This is meant to be a feature flag with a testing in production use case.

#### Setup the flag in LaunchDarkly 

1. Go to www.launchdarkly.com and set up a new account
2. Once you verify your email, follow the quickstart guide on the right and click on the first option to create your first feature flag.
3. Give the flag a name in the top box.
4. The Key field will suggest a key name based on the name of the flag. You can accept it or change it to something else.
5. If you are going to use the Javascript SDK, check the box that says "SDKs using Client-side ID".
6. Click "Save Flag".
7. Congrats, you've made your first feature flag!
8. Click on the flag to set some targeting rules.
9. Click on "Add user targets" to add some users who you want to see the code when the flag is set to true. People frequently want to have new code turned off in production for most people, but turned on for a small number of specific people, such as their programming partner or manager. Add them in the "true" section.
10. You can create rules to open up the code to the initial groups of users who you want to see your code. For instance, you can add users in a specific country like New Zealand by clicking "Add rule", choosing "country" from the "select an attribute" dropdown and entering the country value your database has for New Zealand (such as NZ). You can also add inidividual customers.
11. In the dropdown below that with the yellow warning triangle, choose "true" to allow the users in the country you have selected for your test to see the true version.
12. If you want to do a canary release and show the new code to a certain percentage of people in New Zealand, choose "percentage rollout" in the "serve" dropdown and choose which percent of people in New Zealand you want to see the new code. Put this percentage in the "true" section.
13. You can add another rule by clicking on the blue plus sign on the right. 
14. Other popular options for testing production are adding groups of users who are in segments (early access program segments, certain pricing tiers, beta groups, etc), but you have to set up the segment first.
15. Change the "default rule" at the bottom to "false". Since you are testing in prodcution, you want most users to see the code without the changes this flag adds. Only those that meet the targeting rules should see the new code. Thus, the default should be false.


#### Copying the flag and Client-side ID keys from LaunchDarkly to your application 

1. Open up the LaunchDarkly hello-js repo by going to https://github.com/launchdarkly/hello-js and downloading the zip file.
2. Open the index.html file in your editor.
3. Go back to LaunchDarkly and copy the client-side ID by going to Account Settings > Projects and then clicking on the name of your project.
4. Click on the client-side ID to copy it to your clipboard.
5. Paste the client-side ID in the quotes in line 14 to define the clientSideId variable as your client-side ID.

``` 
// Set clientSideID to your LaunchDarkly client-side ID
const clientSideID = '';
```

7. Go back to LaunchDarkly and click on Feature Flags in the left sidebar.
8. Find the flag you want to use and click the key (the black text on a grey background right below the name of the flag) to copy it to your clipboard.
9. Paste the flag ID in the quotes in line 17, replacing "my-boolean-flag".

```
// Set flagKey to the feature flag key you want to evaluate
const flagKey = 'my-boolean-flag';
```
10. In the render function beginning on line 37, you can have some fun editing what will show up. For instance, you can edit the text by altering line 37:

```
const label = 'Feature flag ' + flagKey + ' is ' + flagValue + ' for this user';
```
11. You can also add gifs in this function as well.

12. Open `index.html` in your browser.
13. Turn the flag on from the LaunchDarkly UI.

You should see the message in line 37 (and any other gifs or fun stuff you added) in the browser!


