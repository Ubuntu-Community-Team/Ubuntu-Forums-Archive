---
title: "Need an Expert to look over some code."
date: 2010-11-19
forum: Programming Talk
---

### Post by argedion on 2010-11-19
I need an expert to look over some code for me to ensure that I have written this script right. It is a Backup Script file but its kind of long and I'm not sure about posting it here. It has 144 lines of code. If its ok for me to post it here I will. If someone knows of a better place then please inform me. I need you to look at a Bash Script

---

### Post by Hippytaff on 2010-11-19
if you post it doing
[code] your script[/code ]

it will be fine (note don't put the the space before the last bracket in [/code ]

---

### Post by argedion on 2010-11-19
```
#!/bin/bash
set -e

####################################################################
#####                   Argedion                               #####    
#####         Wed 17 Nov 2010 07:18:48 PM EST                  #####
#####               File Name: abs.sh                          #####
####################################################################
#version: 1.0.3
# My First Linux Bash Backup Script
#


#Get The Date
today=`date +%m%d%Y`
CurTime='date +%H-%M-%S'

################Start Script####################

####Variables
# the home directory in linux
defaulthome="/home/argedion"
defaultsave="home_$today"
#My Home Directory for all systems
myhome="/media/Myne_/Argedion"
phsave="argedion_$today"
#Log file name and location
backuplog="/media/320WDPassport/Backup/Argedion/backuplog"
#My Master Picture Folder
mypictures="/media/Myne_/Pictures"
picsave="Pictures_$today"
#backup directory
savedir="/media/320WDPassport/Backup/Argedion"
#Display the user
user=whoami
#User Input
choice=" "


#########################################################################
##### Functions

function savehome
{
	echo "Now saving home folder - $defaulthome - @ $Curtime" >> $backuplog
	tar cPf - $defaulthome | 7za a -si ${savedir}/${defaultsave}.tar.7z
}

function savepersonal
{
	echo "Now saving My Home folder - $myhome - @ $Curtime" >> $backuplog
	tar cPf - $myhome | 7za a -si ${savedir}/${phsave}.tar.7z
}	

function savepictures
{
	echo "Now Saving My Pictures -$mypictures - @ $Curtime" >> $backuplog
	tar cPf - $mypictures |7za a -si ${savedir}/${picsave}.tar.7z
}


function errstatus
{
		#Check error status of script display using zenity
	if [ $? == 0 ]; then
		zenity --info --text="Backup was Successful" &
		echo "Backup Succeeded @ $today {$Curtime} " >> $backuplog
	else
		#there was a problem
		zenity --error --text="Backup has failed try set +x" &
		echo "Backup Failure! @ $today {$Curtime} " >> $backuplog
	fi
}

#Start Logging
echo "Backup Started by $user @ $today " >> $backuplog
echo "Started By $user @ hostname " >> $backuplog
echo $Curtime >> $backuplog

##########################################################################
######## Menu Section 

echo "####################################################################"
echo "#####                                                          #####"   
echo "#####               Argedion Backup Script                     #####"
echo "#####                                                          #####"
echo "####################################################################"
echo
echo "Choose Which Type of Backup you want to do"
echo "1. Backup only the Home directory [/home/user]"
echo "2. Backup only your personal directory [/media/Myne_/Argedion]"
echo "3. Backup only your Pictures Folder [/media/Myne_/Argedion]"
echo "4. Do A Full Backup [All the Above] !!This will take a long time!!"
echo "5. Exit Script"

#base backup type on Users Choice
read choice

## now get condition using loop

	while [[ $choice != 0 ]]
		do
			case $choice in
				1) clear;
					#save the home directory when done exit script
					savehome;
					echo "Backup Process has finished" >> $backuplog;
					errorstatus;
					exit;
					;;
				2) clear;
					#save my personal directory when done exit script
					savepersonal;
					echo "Backup Process has finished" >> $backuplog;
					errorstatus;
					exit;
					;;
				3) clear;
					#save the pictures directory when done exit script
					savepictures;
					echo "Backup Process has finished" >> $backuplog;
					errorstatus;
					exit;
					;;
				4) clear;
					#save all directorys when done exit script 
					savehome
					savepersonal
					savepictures
					echo "Backup Process has finished" >> $backuplog;
					errorstatus;
					exit;
					;;
				5) clear;
					echo "Exiting Argedion's Backup Script!";
					exit;
					;;
				*) clear;
					echo "Not a Valid Selection! Please Try Again";
					;;
			esac


done
```

This is the code obviously hope this isn't to much

---

### Post by hakermania on 2010-11-20
You can download virtualbox and test your script in a virtual machine. Only this way you can be sure. That's what I would do.

---

### Post by argedion on 2010-11-20
I ran the code an only found a few errors. 

1. CurTime was not formatted properly I believe I fixed this also when using CurTime I messed up and had Curtime. Bash couldn't find that command (duh) 

2. I have function errstatus and yet I tried to call errorstatus so again bash couldn't find the command.

3. CurTime did not work as I wanted it to. It just kept the same time so either i will have to just invoke the date +%H%M%S each time I want to write the current time to the log file. If someone knows of how I can set a variable for this I would appreciate the insight. 

4. I also didnt format the "whoami" command properly it should have been ` (a back apostrophe found with the tilde sign) instead of ' (a normal apostrophe) 

5. I have to go back to the menu if I mess up and hit the wrong key. I don't believe there is a "goto" in bash like there is in that redmond crap.

You are Free to modify the code for your own use however you wish. :)

---

### Post by Rushyang on 2010-11-20
rsync commands and cron jobs are more convenient options for backing up the data. I assume it will dramatically reduce your code.

---

### Post by Rushyang on 2010-11-20
Also, there are many wrong things going on, on the internet about choosing the environment for your bash script..

I'm no expert, but as per experts say on bash script's irc channel of freenode.com.... You should write
#!/usr/bin/env bash
for choosing a bash environment.

---

### Post by TiBaal89 on 2010-11-20
rsync would dramatically reduce your run time.  I don't know how many pictures (for instance) you have, but something like that can commonly run into the many GB range.  You're tar-ing the entire thing for every back up even if very little or nothing has changed.  rsync only propagates changes.

---

### Post by argedion on 2010-11-20
Thanks for the advice guys. One question how would I use rsync? I have the signature "command line flunkie" for a reason *L* I am still learning all this. I have been playing with Linux Systems for a while but never really got into the command line but now I'm wanting to learn. Eventually I want to be able to create a backup that will run over the network. I have 3 other computers here at home and want to store backups on one of the other computers that's running Fedora 14. The other 3 of those are running that Redmond crap but wife and kids are not ready for a real system *L* 

Forever Grateful to those kind souls who have been more than willing to help me :D

Yeah my Pictures folder is like 5 gig the same as my home folder so yeah the backup now gets run right as I go to bed *lol*

---

