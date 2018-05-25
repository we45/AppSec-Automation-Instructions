# LayerOne - we45 DevSecOps and AppSec Automation Training - 1 Day

## Instructions on the VM
- You will need to use the root username and password whenever you need to authenticate to the computer. Username: **root**, Password: **we45**. There's another user in the VM, with Username: **we45** and password: **we45**
- All the examples and code from the lab are yours to keep. 
- We have used multiple tools for the lab. We have only used Open Source tools as we are only allowed to use open source tools, due to commercial licensing restrictions. 
- We also have a number of vulnerable machines running in Docker Containers on this Virtual Machine. Some of these are available open source and some of them have been developed by us at we45 for our training workshops
- You will need to use the Linux Command line to run all of the exercises today. However, please don’t fret if you are not familiar with Linux. The commands to run everything have been documented in the exercise manual.


## Applications and Passwords

### Jenkins 
username: `we45`, password: `we45`

## wecare application
usernames: `betty.ross@we45.com`, `bruce.banner@we45.com`
password: `secdevops`

## Bandit Jenkins
* Goto Browser (Firefox/Chrome)
* Enter: `http://localhost:8080`
* Login to Jenkins with username `we45`	and password `we45`
* Run the `Bandit SAST` Job, by checking on `Build now`
* Click on the Build that you just initiated and click on `Bandit Vulnerability Results`

## NodeJS Scan
* Open Terminal on Desktop
* Command: `start_nodejsscan.sh`
* Goto Browser (Firefox/Chrome)
* Enter: `http://localhost:9090`
* Upload `ctf.zip` from the Downloads folder and observe the results
* Close the browser
* Run `stop_all_containers.sh` from the Terminal

## OWASP Dependency Check - Jenkins
* Goto Browser (Firefox/Chrome)
* Enter: `http://localhost:8080`
* Login to Jenkins with username `we45`	and password `we45`
* Run the `OWASP DepChecker` Job, by checking on `Build now`
* Click on the Build that you just initiated and click on `Dependency-Check Results`

## Custom SAST with Bandit and Jenkins
* Goto Browser (Firefox/Chrome)
* Enter: `http://localhost:8080`
* Login to Jenkins with username `we45`	and password `we45`
* Run the `Custom_Bandit_SAST` Job, by checking on `Build now`
* Click on the Build that you just initiated and click on `Bandit Vulnerability Results`

## Brakeman SAST and Jenkins
* Goto Browser (Firefox/Chrome)
* Enter: `http://localhost:8080`
* Login to Jenkins with username `we45`	and password `we45`
* Run the `Brakeman SAST` Job, by checking on `Build now`
* Click on the Build that you just initiated and click on `Brakeman Vulnerability Results`

## NightwatchJS - Selenium - OWASP ZAP Example
* Open Terminal and type `stop_all_containers.sh` to stop all running containers
* Open Terminal and type: `start_wecare.sh`. Wait approx 10 seconds after the Docker container starts
* Go to: `cd /Desktop/tooling/OWASP-ZAP-JSON-RPC-Service`
* Type: `source venv/bin/activate`
* type: `python ZAPJSONRpc.py`
* Goto: `cd /Desktop/tooling/Nightwatch-ZAP/`
* Type: `./node_modules/.bin/nightwatch`
* On the Desktop, you can open `report.json` with Firefox
* Run `stop_all_containers.sh` and close all Terminals

## ZAP REST API Test
* Open Terminal and type `stop_all_containers.sh` to stop all running containers
* Open Terminal and type: `start_flask.sh`
* Go to: `cd /Desktop/tooling/REST_ZAP`
* Type: `source venv/bin/activate`
* type: `robot ZAPWebService.robot`
* To read the source code: `mousepad ZAPWebService.robot`
* Read the report with command `firefox flask_api.json`

## RoboZap - Selenium Test
* Open Terminal and type `stop_all_containers.sh` to stop all running containers
* Open Terminal and type: `start_wecare.sh`. Wait approx 10 seconds after the Docker container starts
* Go to: `cd /home/we45/Desktop/tooling/ZapRobotSelenium`
* Type: `source venv/bin/activate`
* Type: `export PATH=$PATH:/home/we45/Desktop/tooling/ZapRobotSelenium`
* type: `robot ZapSeleniumTest.robot`
* To read the source code: `mousepad ZapSeleniumTest.robot`

## ZAP API Tour
* Open Terminal and type `stop_all_containers.sh` to stop all running containers
* Open Terminal and type: `start_flask.sh`
* Open Terminal and type: `start_wecare.sh`. Wait approx 10 seconds after the Docker container starts
* Go to: `cd /home/we45/Desktop/tooling/ZAP-Mini-Workshop`
* Type: `source venv/bin/activate`
* Type: `jupyter notebook`, this should start a python program and automatically open firefox
* Follow the instructor

## A minimal Pentest Pipeline
* Open Terminal and type `stop_all_containers.sh` to stop all running containers
* Open Terminal and type: `start_flask.sh`
* Goto: `cd /home/we45/Desktop/tooling/Pentest_Pipeline`
* Type: `source venv/bin/activate`
* Run: `robot MyTestPipeline.robot` and observe the results

## ZAP Custom Scripting

### Active Scan Rules
* Open OWASP ZAP from the Desktop
* In the Sidebar, click on the + icon and open scripts
* Click on `Active Rules` and enable all the rules by right clicking and selecting
* Save the Script by right clicking on the script
* Close ZAP
* Open Terminal and type `stop_all_containers.sh` to stop all running containers
* Open Terminal and type: `start_flask.sh`
* Go to: `cd /Desktop/tooling/REST_ZAP`
* Type: `source venv/bin/activate`
* type: `robot ZAPWebService.robot`
* To read the source code: `mousepad ZAPWebService.robot`
* Comment out the `Kill ZAP` Test Case

### Targeted Script - Struts2 (CVE-2017-5638)
* Open OWASP ZAP from the Desktop
* In the Sidebar, click on the + icon and open scripts
* Copy the script from Desktop/tooling/zap_scripts
* Create a new "Targeted" Script
* Choose the jython option forthe Scripting Engine
* Paste the script you copied into the new script
* Open Terminal enter `start_struts.sh`
* Open up the browser, click on the Fox icon next to the address bar. In the drop down, select OWASP ZAP. This will ensure that all requests from the browser are proxied through ZAP
* Now, in the address bar, type in `localhost:7777`, and you will get a signup screen.  
* Now, go to OWASP ZAP, and in the "Sites" window, you should see `http://localhost:7777/`, click and select any node of the site tree. Right click on any node and click on "Invoke with Script", select the `Struts2 Vulnerability` Script and observe the results in the Script Output Window
