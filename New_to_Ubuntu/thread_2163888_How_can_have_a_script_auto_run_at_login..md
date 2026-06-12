---
title: "How can have a script auto run at login."
date: 2013-07-20
forum: New to Ubuntu
---

### Post by Reavernine on 2013-07-20
Ok so i have been at this for days now and have not been able to find a solution. i have been all over these forums and others for hours at a time trying to find something that works. I will post the two scripts below that i am refering to. Basicly is what i am trying to do is have the ability to  click on my "run" script which will perform an action such as "apt-get update && apt-get upgrade" then create another script and then restart my computer...this second script "or series of commands" would then run once to call upon a third script to perform actions. what I have tried thus far is to have the "run" script perform its actions, create the runonce script and then restart. The runonce script should then launch at login to perform other actions and then delete itself from what ever folder or command its in that caused it to run at login so that it doesnt run again at next reboot. then it should call upon a third script to continue a chain of these instances of Action>reboot>runonce>action>reboot>runonce ......this will eventually be a script i use to automate setting up all of my update,adding repos, downloading my packages, and setting my configurations anytime i choose to reinstall Ubuntu.

Both of my scripts perform their functions like it is suppose to, i just cant get the runonce at login thing to work with bash scripts. I have tried having the "run" script create  .desktop file in the /etc/xdg/autostart directory, which will cause the script to show up in the "startup application" menu, but it doesnt work. I have also tried adding the runonce script to the /usr/bin directory with a launcher in /etc/xdg/autostart directory, but it also does nothing at reboot (even with X-GNOME-Autostart-enabled=true tag in the launcher)

The only thing i have gotten to even kind work at login is by having my "run" script add the runonce to the rc.local. Yes it did launch at reboot, however because rc.local runs as root and does not show the terminal on my user screen, this will not work. infact the only reason i was able to know that it was working was by having one have commands in rc.local add a new empty document to my users desktop so i could see that the script did indeed run.

so I know that both my below scripts as well as the launcher create by "run" all work if i click on them to launch. I just need to know how I get a script to run one time at login (not boot, and not root) with a terminal window in my view to see what the script is doing and so i can answer any Yes, No, or ENTER questions.

Also I am using UBUNTU 12.04.2 i386 clean install with no updates (updating is the scripts job)

This first script is called "run" ....it is the script i would launch first to start this entire process(sorry about the messy scripting, ill clean it up later)


```
#!/bin/bash

###initial ubuntu 12.04Lts i386 upgrade

#sudo apt-get update
#sudo -y apt-get upgrade



###create runonce on login
sudo cp /home/reaver/Desktop/kalbuntu/runonce /usr/bin

touch runonce.desktop
chmod +x runonce.desktop

echo [Desktop Entry] > runonce.desktop
echo Type=shell script >> runonce.desktop
echo Terminal=true >> runonce.desktop
echo Name=deleterunonce >> runonce.desktop
echo Icon=/usr/share/icons/LoginIcons/apps/64/computer.svg >> runonce.desktop
echo Exec=runonce >> runonce.desktop
echo X-GNOME-Autostart-enabled=true >> runonce.desktop

sudo mv runonce.desktop /etc/xdg/autostart


cat /etc/xdg/autostart/runonce.desktop

echo Starting
echo
echo
echo ubuntu will shut down in 10 seconds
sleep 1
echo ubuntu will shut down in 9 seconds
sleep 1
echo ubuntu will shut down in 8 seconds
sleep 1
echo ubuntu will shut down in 7 seconds
sleep 1
echo ubuntu will shut down in 6 seconds
sleep 1
echo ubuntu will shut down in 5 seconds
sleep 1
echo ubuntu will shut down in 4 seconds
sleep 1
echo ubuntu will shut down in 3 seconds
sleep 1
echo ubuntu will shut down in 2 seconds
sleep 1
echo ubuntu will shut down in 1 seconds
sleep 1

sudo reboot 
```



This second script is called runonce and its the one that I am trying to get autorun after login to open a terminal in my view  and then run the commands.

```
#!/bin/bash

echo This is just a test
sleep 5
##delete runonce
sudo rm /usr/bin/runonce
echo Removed /usr/bin/runonce


sudo rm /etc/xdg/autostart/runonce.desktop
echo Removed /etc/xdg/autostart/runonce.desktop



sleep 2
echo completed
sleep 5

```



using rc.login doesnt work and using "startup applications" doesnt work....and yes all scripts are made as executables.

please please please help me....I never ask for help because i can usually figure these things out on my own but this really has me stumped.

Thank you for any help.

---

### Post by sudodus on 2013-07-20
Welcome to the Ubuntu Forums :-)

I'm not sure it is a good idea to update and upgrade unattended. I think it is better to use the script manually (or simply run the commands manually). If you want unattended upgrades, you can use the graphical user interface for it

```
 /usr/bin/update-manager
```

You can change the ***settings*** to install automatically when there are security updates.

But to answer you question, there is also cron. You can use

```
crontab -e
``` and ```
sudo crontab -e
``` for cron jobs that should be run as your user and as root. There are good tutorials to be found on the internet. Browse a few of them and use the one you find best for your purpose (browse for ***cron tutorial***).

---

