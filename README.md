# JBoss EAP Clustered SSO Demo

## Prerequisites to Run This Demo

- JDK 1.8+ is required
- Maven 3+ required if you're planning to play with the source code
- JBoss EAP & JBoss JDG install packs are needed to be placed in install directory. See [the required JBoss packages](./install/README.md)

## Prepare the Demo

- Clone the source code:

  ```git clone https://github.com/serhat-dirik/eap-sso```
-  Place [the required JBoss packages](./install/README.md) in install directory
-  Execute ```init.sh``` script under the root folder

## How to Demo

- if you successfully executed the init.sh, the all the required start scripts should be prepared for you
- First execute the ```startJDG.sh``` script under the target directory, wait until it starts
- Execute ```startEAP1.sh``` and ```startEAP2.sh``` script under the target directory
- You  have one JDG instance that used to store EAP cluster data & http sessions data
- Open http://localhost:8081/sso-app1 page that hosted on EAP instance 1. Place some key-value pairs in the http session. Check cache stats and note session identity
- Open a new tab on the browser and go to http://localhost:8082/sso-app2 page that hosted on EAP instance 2. Validate that you have the session id on this app and you can access to same http session stored data. Store some additional session data, switch to the first tab, either refresh the page or click on the "get session data" button to see http session stored data. You should see all the data stored in the session cache
- At this point you can try restarting your EAP instances and validating session info is still there
- Login to the one of the applications. This action invalidates your current session and gives you a new one. Switch to the other application and refresh the page. You should see that you're logged in and session is still shared between apps
- Logout from one of the apps and check that session is invalidated & both apps are still sharing the session
- In order to access jdg statistics use http://localhost:8081/sso-app1/jdg.jsp page
   Enjoy!
