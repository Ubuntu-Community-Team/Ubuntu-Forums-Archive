---
title: "Logging into Ubuntu without any keyboard activities (a few users)"
date: 2014-03-22
forum: Programming Talk
---

### Post by mariusz-ciszewski on 2014-03-22
I belive it will be really easy to most of you here to help me (fprintd topic). 

I followed this: 

[https://launchpad.net/~fingerprint/+archive/fprint](https://launchpad.net/~fingerprint/+archive/fprint)

[COLOR=#333333][FONT=Ubuntu Mono]sudo add-apt-repository ppa:fingerprint[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]/fprint[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]sudo apt-get upgrade
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]sudo apt-get install libfprint0 fprint-demo libpam-fprintd gksu-polkit[/FONT][/COLOR]


Then I decided to add several users to the Lubuntu system: 

sudo adduser mariusz1 
sudo adduser mariusz2 
sudo adduser mariusz3 


Then I needed to scan and to add into system fimgerprints for all users: 

fprintd-enroll mariusz 
fprintd-enroll mariusz1 
fprintd-enroll mariusz2 
fprintd-enroll mariusz3 


From this time, when default login manager is displayed you can use the fingerprint reader instead of entering a password via keyboard. Although the password field is left blank, and the screen does not appear any relevant information about the success (or not) of the scan. System is still waiting. You must to hit enter key or use the Sign In button to log in to the system. 


My ask is (current investigations): 

- How to disable the automatic start of Xsession (graphical desktop environment) after computer is powered on (I would like to see a text console only inviteing me to log in) I would like to decide if I need to start graphical environment or not later. 

- When I see text console inviteing me to log on I would like to do it without any keboard activities from my side. I want to use fingerprint only. I need Lubuntu know who I am (based on my fingerprint) and log me in. I need this sollution for few users (not only for me). Every of us have his own system account. 

- When some of us is logged into system then his own script /home/user/scripts/accepted.sh is run (script added into autostart) 

- When someone intruder was trying to log in then some other dennied.sh should be executed 

- A would like also automatically save a fingerprints of intruders locally /database/potential_burglars 

I would like to improve this sollution for my home automation system: 
[http://rasp485berry.wordpress.com/](http://rasp485berry.wordpress.com/) 

Could you please help me? 


Thank you very much for your help. 


Best regards 
Mariusz Ciszewski

---

### Post by zerubbabel on 2014-04-04
Fingerprint GUI, available [here]("http://www.ullrich-online.cc/fingerprint/about.php"), works fine for me for logging in, authenticating sudo, etc., but so far I haven't found a way to use fingerprint authentication for logging in to web sites and apps.

---

