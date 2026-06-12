---
title: "[SOLVED] snaptic package manager problem"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by vangala on 2008-08-28
When i try to run the synaptic package manager .i get the following error


"
Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) isalready running. Please close that application first.naptic manager.. i get the following error"

What should be done now?

---

### Post by Crafty Kisses on 2008-08-28
> **vangala said:**
> When i try to run the synaptic package manager .i get the following error


"
Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) isalready running. Please close that application first.naptic manager.. i get the following error"

What should be done now?

Sounds like you have 2 Synaptic Package Managers running.

---

### Post by SunnyRabbiera on 2008-08-28
well check if you have the update manager running or if you are running apt by going to system> administration> system monitor in the processes tab.
Try logging out first then lets see what happens.

---

### Post by vangala on 2008-08-28
But i havent opened any.

I tried to install kopete using the following command
"sudo apt-get build-dep kopete"
but later stopped it by pressing ctrl+z
 and then ive closed the terminal.I guess that's gotto be the cause

---

### Post by SunnyRabbiera on 2008-08-28
> **vangala said:**
> But i havent opened any.

I tried to install kopete using the following command
"sudo apt-get build-dep kopete"
but later stopped it by pressing ctrl+z
 and then ive closed the terminal.I guess that's gotto be the cause

That might be your issue, sometimes when you halt a package installer it hangs in the BG.
Also if you opened apt in a terminal then yes you will have two package mangers working at the same time if apt didnt close out properly.

---

### Post by vangala on 2008-08-28
so..what should be done now?

---

### Post by SunnyRabbiera on 2008-08-28
> **vangala said:**
> so..what should be done now?

well like I said try logging out or even rebooting and then when you get back into your system see if anything has been messed up by typing in sudo apt-get update in a terminal.

---

### Post by vangala on 2008-08-28
well..ive done wat u said..the output of sudo apt-get update was


Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-en_IN
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-en_IN         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Packages
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages [6607B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Sources  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 34.2kB in 5s (5777B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by vangala on 2008-08-28
anyone plz:confused:

---

### Post by SunnyRabbiera on 2008-08-28
Ah, I had that issue once.
Forget how to fix it though sorry.
But patience is a virtue.

---

### Post by vangala on 2008-08-28
patience for what?
will it fix on its own?plz help me out

---

### Post by SunnyRabbiera on 2008-08-28
> **vangala said:**
> patience for what?
will it fix on its own?plz help me out

meaning I am digging up an answer for you, hold on kay?
try this first:
sudo dpkg --configure -a

---

### Post by vangala on 2008-08-28
Thanx a lot.
owe u..

---

### Post by vangala on 2008-08-28
output was
dpkg: status database area is locked by another process

---

### Post by SunnyRabbiera on 2008-08-28
> **vangala said:**
> output was
dpkg: status database area is locked by another process

huh, well did you try a restart of your system then?

---

### Post by vangala on 2008-08-28
ive logged out and logged in again.
DO u want me to restart?

---

### Post by SunnyRabbiera on 2008-08-28
> **vangala said:**
> ive logged out and logged in again.
DO u want me to restart?

yes restart your whole system.
It might fix it, it might not.
This kind of error comes up a lot I see but sometimes a simple restart can help.

worse comes to worse try this command too:
sudo rm /var/lib/dpkg/lock
or sudo apt-get -f install

there is a chance your installation of kopete messed up so type in sudo apt-get install kopete to try again

---

### Post by pi.boy.travis on 2008-08-28
Not sure if your system will allow either of these, or if they will fix you problem, but try:

sudo apt-get autoremove

sudo apt-get autoclean

Hope this helps. . .

---

### Post by SunnyRabbiera on 2008-08-28
> **pi.boy.travis said:**
> Not sure if your system will allow either of these, or if they will fix you problem, but try:

sudo apt-get autoremove

sudo apt-get autoclean

Hope this helps. . .

those help if you have a bunch of packages/ dependencies you dont need anymore.

---

### Post by vangala on 2008-08-28
SUnny.
I owe u dude...restarting the system has done the issue.
THanks a lot!:)

---

### Post by SunnyRabbiera on 2008-08-28
> **vangala said:**
> SUnny.
I owe u dude...restarting the system has done the issue.
THanks a lot!:)

you are welcome, and I am a girl by the way :D

---

### Post by vangala on 2008-08-28
Oh..newaz..Thanks a lot!:)

---

### Post by mcrene on 2009-01-10
I have been getting the same error code.

tried all advice on here, no help.

reboot = no help

the "reoval" command and "autoupdate" = nothing


no matter what is going on, this POS will not let me get 'exclusive lock' on whatever it needs a lock on.

---

### Post by mcrene on 2009-01-10
some help?

---

