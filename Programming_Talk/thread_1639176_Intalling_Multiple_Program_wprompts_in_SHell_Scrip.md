---
title: "Intalling Multiple Program w/prompts in SHell Script"
date: 2010-12-06
forum: Programming Talk
---

### Post by WolfgangCS on 2010-12-06
I am trying to create a shell script to do a multitude of things. I would like this script to be open source and perfect for any clean installation of Ubuntu.

Objectives:
-Show visual Prompts for the $user to continue the the beginning stages of installations

-Keep a single terminal up to show details of the whole process

-Install Chrome and Dropbox

-Update System (without restarting, or restart and continue where script left off)

-Show website of in Chrome example: [Welcome]("http://www.wolfgangcomputer.com/projects/wolfgang-university/computer-installations/ubuntu-installation")

```
#!/bin/bash

$sudo gnome-terminal -x $sudo apt-get update

#SLEEP or another command to wait till completion of task

#Prompt User to continue with next step "Y/n"

#If needing to restart, continue script after reboot

#Re-run Update if needed
$sudo gnome-terminal -x $sudo apt-get update

#Then install Google Chrome

$sudo gnome-terminal -x $sudo wget http://www.google.com/chrome/eula.html?platform=linux_ubuntu_i386

#Update Chrome

$sudo gnome-terminal -x $sudo apt-get update google-chrome

#Prompt $User if they would like to continue, "We are going to Update your system one more time, OK? (Y/n)"

#Re-run Update if needed
$sudo gnome-terminal -x $sudo apt-get update

#Show Specified Website
$sudo google-chrome http://www.wolfgangcomputer.com/projects/wolfgang-university/computer-installations/ubuntu-installation

#Prompt $user: "$user, Update was successful, Are you ready to continue? (Y/n)"

sudo apt-get upgrade nautilus-dropbox

#Prompt $user: "$user, once you have completed and login/created account with dropbox, are you ready to continue? (Y/n)

echo "Welcome to Ubuntu! Please Close this Window"


```

Any ideas or things to change would be great!

---

### Post by WolfgangCS on 2010-12-06
Everything runs fine but I would like to get the two updates to complete before Chrome or Dropbox if's begin.

Ideas?

Remove the "sleep #" to make it run faster for testing. I thought it just gave it a "hard working program" look.

```
#!/bin/bash

clear

#Welcome and instructions

echo  "Welcome to Ubuntu Quick Setup"
sleep 3

echo  "Please choose the from the options below."
sleep 3

echo  "Answer Y/n (Y=yes & n=no) ONLY"
sleep 8

#Setup selections

read  -p "Update System? " Update1
read  -p "Update System again? " Update2
read  -p "Install Google Chrome? " Chrome
read  -p "Install Dropbox? " Dropbox

echo  "Thanks! Compling List"
sleep 5

clear


if [ "$Update1" == "Y" ]
then
     echo "Adding Update to list"
else
     echo "First Update will not take place. Warning: This is highly recommend. Please, press Ctrl-C to cancel. Then run setup file again."
fi

sleep 3

if [ "$Update2" == "Y" ]
then
     echo "Will complete second update..."
else
     echo "Second Update will not take place. Warning: This is highly recommend. Please press Ctrl-C to cancel. Then run setup file again."
fi

sleep 3

if [ "$Chrome" == "Y" ]
then
     echo "Adding Google Chomre to list"
else
     echo "Not installing Google Chrome Browser..."
fi

sleep 3

if [ "$Dropbox" == "Y" ]
then
     echo "Adding Dropbox to list"
else
     echo "Not installing Dropbox..."
fi

sleep 3

clear

#Start Setup
#Let the craziness commence

if [ "$Update1" == "Y" ]
then
     sudo apt-get update
else
     echo "Skipping first Update"
fi

sleep 3

clear

if [ "$Update2" == "Y" ]
then
     sudo apt-get update
else
     echo "Skipping Second Update"
fi

sleep 3

clear

if [ "$Chrome" == "Y" ]
then
     wget http://www.google.com/chrome/eula.html?platform=linux_ubuntu_i386
else
     echo "Skipping Google Chrome Browser..."
fi

sleep 3

clear

if [ "$Dropbox" == "Y" ]
then
     sudo apt-get upgrade nautilus-dropbox
else
     echo "Skipping Dropbox..."
fi

sleep 3

clear

#Ending Script

echo "Your done! Window will close in a momment."
sleep 10

sudo google-chrome http://www.wolfgangcomputer.com/projects/wolfgang-university/computer-installations/ubuntu-installation

exit 0


```

---

### Post by roccivic on 2010-12-06
I have no idea why anyone would want such a script, but anyway:

replace "sudo apt-get update" for "sudo apt-get update -y"
remove "sudo" from "sudo google-chrome yadda-yadda"
don't make it sleep so much all the time, people hate waiting.
what if a person chooses not to install google-chrome? is it fair enough to still try to open that website with said browser?

---

### Post by WolfgangCS on 2010-12-06
oh! Well said...

is there a way call up a website without specifying the current default browser?

I have clients that are less techie and this would simplify my after work, or theirs, if a script did all the work. I just need some examples to complete the full idea.

a little more to go on

Ok I know Update will not run twice since it will have to restart

Is it possible to get the script to confirm the completion of the update, reboot system, and continue the script

If I can get the script to add itself to the "startup applications" list, I could.....EXAMPLE....

```
 #!/bin/bash

clear

sudo apt-get update

#Apply changes to be made in update manager VIA-script

#Confirm Competition of update

#add itself to "startup apps"

#Delete the above lines so it will not repeat the same actions again

#reboot

#continue script...


```

---

### Post by Vaphell on 2010-12-06
gnome-open uses default apps for the task, ie
gnome-open something.mp3 will run totem (or whatever is supposed to run mp3 by default), gnome-open [http://something.com](http://something.com) will run your default browser.

---

### Post by roccivic on 2010-12-06
you never need to reboot after
```
sudo apt-get update
```
only after
```
sudo apt-get upgrade
```
and even then only if there was a kernel upgrade

---

