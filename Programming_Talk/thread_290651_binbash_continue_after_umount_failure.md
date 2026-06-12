---
title: "/bin/bash continue after umount failure"
date: 2006-11-01
forum: Programming Talk
---

### Post by someusernoob on 2006-11-01
This is my first script. I found a lot on the internet, but can't find a solution to my current problem, which is kinda frustration.

So far so good the script works for me, except one little annoyance. Let me explain.

The script is written for automounting a network share when the remote PC is powered on after my PC is powered on (so /etc/fstab won't automount it anymore). It is for my NFS network.

I run the script every 5 minutes with cron.

Here is the script:
```

#!/bin/bash

## Simple script which will automount shared folders when another computer is online.
## Run this script every 5 or 10 minutes with cron.

## Below is the personal data section. Change those to your situation.
SHARE="/home/<user>/Remote/Share/"	# The path of the shared folder on the remote PC
RMTIP="10.0.0.14"			# The IP of the remote PC
MNT="/media/Share/"			# The path where you want to mount SHARE
GRP="Unreachable"			# This is in the error I get when a ping fails. If you use another language, type 'ping -c 1 <invalid ip adres>' and see if you can get something simular.

## Those commands will check if the other computer is online, and if the shared folder is allready mounted.
X="$(ping -c 1 ${RMTIP} | grep -c ${GRP} )"
Y="1"
Z="$(mount | grep -c ${SHARE} )"

## These command are for the log file. Logging isn't necessary, but I thought is was fun to try.
DATE="$(date +%Y-%m-%d@%H:%M:%S)" 
DIR="${HOME}/.nfsmount"
LOG="${DIR}/nfsmount.log"

## This is what happens if the server is online.
if [ $X -lt $Y ]
then
echo "The server is online!"
	if [ $Z = $Y ]
	then
	echo "The share is allready mounted. Will now exit."
	exit
	else
	echo "The share is not mounted. Will now mount."
	gksudo echo
	sudo mount ${RMTIP}:${SHARE} ${MNT}
	export DEBIAN_FRONTEND=dialog
	zenity --info --title="NFSMount" --text="Shared folder on ${RMTIP} has been mounted!"
     	echo "${DATE}: ${RMTIP} is online. Shared folder on ${RMTIP} has been mounted!" >> "${LOG}"
	exit
  	fi
fi

## This is the what happens if the server is offline.
if [ $X = $Y ]
then
echo "The server is offline!"
	if [ $Z -lt $Y ]
	then
	echo "The share is allready unmounted. Will now exit."
	exit
	else
	echo "The share is still mounted. Will now umount."
	gksudo echo
	sudo umount ${MNT}
	fi
fi

## This gives a notification about the status of the unmounting.
if [ $Z = $Y ]
then
export DEBIAN_FRONTEND=dialog
zenity --error --title="NFSMount" --text="Unmounting shared folder has failed! Device is busy!"
echo "${DATE}: ${RMTIP} is offline. Unmounting shared folder has failed! Device is busy!" >> "${LOG}"
exit
else
export DEBIAN_FRONTEND=dialog
zenity --info --title="NFSMount" --text="Shared folder on 10.0.0.14 has been unmounted!"
echo "${DATE}: ${RMTIP} is offline. Shared folder on 10.0.0.14 has been unmounted!" >> "${LOG}"
exit
fi

```

Not the most beautiful script I guess, but it works. It is far from finished, but the basic goal is reached.

I made the script popup a dialog when the network share is mounted, and when it is unmounted. Just to let me know it is there, or not.

After "sudo umount ${MNT}" I can't seem to run any other command if umount gives me "umount: /media/Share: device is busy
". The command I want to run is mount | grep -c ${SHARE}, so I can see if it was succesfully unmounted > then the last 'if' section can find out which dialog to show.

Now it just shows the first dialog that comes after if [ $Z = $Y ] - totally ignoring the else function, because it always chooses the first option.

So basicly my question is, how do I run that command (or any other command) after the 'device is busy' error?

---

### Post by someusernoob on 2006-11-01
I found a workaround for my problem.

sudo umount -fl ${MNT}

Then it gets unmounted without any error. So there is no need anymore for the 'device is busy' dialog.

The script now looks likes this, in case someone wants to try it.
Here you go:

```

#!/bin/bash

## NFSMount
## Version 0.1
## Written for Debian Etch and Ubuntu Edgy Eft using Gnome. 
## I don't use anything else, so I can not test anything else.
##
## Simple script which will automount shared folders on a NFS network when the remote PC 
## appears to be online, and unmounts it if the remote PC appears to be offline.
## Run this script every 5 or 10 minutes with cron if you want it to be automagic -
## otherwise you have to run it yourself every time.
## Try if the script works before you run it with cron!!!
## Read the script for options before you start!


## Below are personal preferences. Change those to your situation!!!

SHARE="/home/<user>/Remote/Share"	# The path to the shared folder on the remote PC
RMTIP="10.0.0.14"			# The IP of the remote PC
MNT="/media/Share"			# The path where you want to mount SHARE, this folder must excist before you continue, e.g.; sudo mkdir /media/Share
GRP="Unreachable"			# This is in the error when a ping fails. If your ping uses another language, type 'ping -c 1 <invalid ip adres>' and see if you can get something similar unique.


## These commands will check if the other computer is online, and if the shared folder is allready mounted.

X="$(ping -c 1 ${RMTIP} | grep -c ${GRP} )"
Y="1"
Z="$(mount | grep -c ${SHARE} )"


## These commands are for the log file. You can modify them if you want to log somewhere else then your home dir.

DATE="$(date +%Y-%m-%d@%H:%M:%S)" 
DIR="${HOME}/.nfsmount"
LOG="${DIR}/nfsmount.log"


## This will check if the dir for the logfiles allready excists, otherwhise it will be created.
## Comment this section if you do not want to log - also see below.

if [ ! -d "${DIR}" ]
then mkdir "${DIR}"
fi 


## This is what happens if the server appears to be online.

if [ $X -lt $Y ]
then
echo "The server is online!"
	if [ $Z = $Y ]
	then
	echo "The share is allready mounted. Will now exit."
	exit
	else
	echo "The share is not mounted. Will now mount."
	gksudo echo
	sudo mount ${RMTIP}:${SHARE} ${MNT}
		# Comment this section if you do not want popup dialogs.
	export DEBIAN_FRONTEND=dialog
	zenity --info --title="NFSMount" --text="Shared folder on ${RMTIP} has been mounted!"
		# End of the section.
		# Comment the line below to disable mount logs!
     	echo "${DATE}: ${RMTIP} is online. Shared folder on ${RMTIP} has been mounted!" >> "${LOG}"
	exit
  	fi
fi


## This is what happens if the server appears to be offline.

if [ $X = $Y ]
then
echo "The server is offline!"
	if [ $Z -lt $Y ]
	then
	echo "The share is allready unmounted. Will now exit."
	exit
	else
	echo "The share is still mounted. Will now umount."
	gksudo echo
	sudo umount -fl ${MNT}
		# Comment this section if you do not want popup dialogs.
	export DEBIAN_FRONTEND=dialog
	zenity --info --title="NFSMount" --text="Shared folder on ${RMTIP} has been unmounted!"
		# End of the section.
		# Comment the line below to disable unmount logs!
	echo "${DATE}: ${RMTIP} is offline. Shared folder on ${RMTIP} has been unmounted!" >> "${LOG}"	
	exit
	fi
fi

## End of the script.
## Goodbye.

```

---

### Post by nero2150 on 2007-05-13
very Helpful will try this thanx :)

---

### Post by Guilden_NL on 2008-09-09
Dank U Wel! :guitar:

---

### Post by u-slayer on 2008-09-10
```
umount -l
```

dude... the "lazy" version of umount.

---

### Post by dwhitney67 on 2008-09-10
You should consider redirecting command output to /dev/null and then checking the return status of the command (to see if it succeeded) versus using the greps.

For instance:
```
ping -c 1 $server >& /dev/null

if [ $? -eq 0 ]
then
        # success... server is available
else
        # failure
fi
```
Try to think of /dev/null as being a bit-bucket (trash can) for unwanted data/output.

---

### Post by -jo- on 2010-06-21
Thank you for the script! It works quite well.

Is there a way to display a message that it's the nfsmount script asking for root password via gksudo when mounting the nfs? (Eg when using cron.)

---

### Post by soltanis on 2010-06-21
gksudo takes an optional argument called --description (also -D). You can use that to set a description for the program that is calling up the gksudo window.

```

gksudo --description "NFS Automounter" ...

```

---

### Post by hannaman on 2010-06-22
Nice script, but did you consider using autofs to handle all of the NFS mounting and unmounting for you instead? 

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by soltanis on 2010-06-22
Bear in mind this thread is about 2 years old now.

---

### Post by -jo- on 2010-06-22
Thank you for your answers. Actually, when I set to run the script as a root cronjob it does not ask for the password anymore (I also set the owner to be root). Everything works great now.
But, will look into autofs later nevertheless, always good to learn something new. Thanks!

---

