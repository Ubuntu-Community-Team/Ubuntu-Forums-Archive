---
title: "Bash scripting with process bar, help?"
date: 2007-08-19
forum: Programming Talk
---

### Post by markp1989 on 2007-08-19
I have created a small script for backing up my Usb flash drive to a folder in my home partition. 

#!/bin/bash
cd /media/MARKSUSB1GB/
mkdir 	/home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` 
echo Backup Started `date` >> /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y`/backuplog
cp -rf * /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` 
cp * /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` 
echo Files coppied `ls -alth` >> /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` /backuplog
echo Backup Completed `date` >> /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` /backuplog
ls -alth 


I was wondering if there is a way to add a process bar to show me how long it is going to take, and if there have been any problems etc......Any help will be appreciated, and  i thank you all in advanced

---

### Post by walkerk on 2007-08-19
> **markp1989 said:**
> I have created a small script for backing up my Usb flash drive to a folder in my home partition. 

#!/bin/bash
cd /media/MARKSUSB1GB/
mkdir 	/home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` 
echo Backup Started `date` >> /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y`/backuplog
cp -rf * /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` 
cp * /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` 
echo Files coppied `ls -alth` >> /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` /backuplog
echo Backup Completed `date` >> /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` /backuplog
ls -alth 


I was wondering if there is a way to add a process bar to show me how long it is going to take, and if there have been any problems etc......Any help will be appreciated, and  i thank you all in advanced

take a look at zenity --progress :)
```
man zenity
```

---

### Post by markp1989 on 2007-08-19
> **walkerk said:**
> take a look at zenity --progress :)
```
man zenity
```

wow that was a quick reply, thank you , with the zenity do i add that to the start of the bash script, or what?

im rather new to this sort of stuff, so sorry if i ask any stupid questions

---

### Post by markp1989 on 2007-08-19
i got the progress bar working, here is how i have used the zenity program, 

#!/bin/bash
# ===========================
# Welcome text
# ===========================

zenity --text "Marks USB Backup.

This backup program will make a backup this usb drive to
home/mark/Usbbackup/Usbbackup

Press ''OK'' When ready.
" --info


	(
cd /media/MARKSUSB1GB/
mkdir 	/home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` 
echo Backup Started `date` >> /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y`/backuplog
		echo "40" ; sleep 1
cp -rf * /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` 
cp * /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` 
		echo "70" ; sleep 1
echo Files coppied `ls -alth` >> /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` /backuplog
echo Backup Completed `date` >> /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` /backuplog
ls -alth 
		echo "100" ; sleep 1
	) | zenity --progress


tell me if this is the wrong way to use this, but it seems to work

---

### Post by walkerk on 2007-08-19
> **markp1989 said:**
> i got the progress bar working, here is how i have used the zenity program, 

#!/bin/bash
# ===========================
# Welcome text
# ===========================

zenity --text "Marks USB Backup.

This backup program will make a backup this usb drive to
home/mark/Usbbackup/Usbbackup

Press ''OK'' When ready.
" --info


	(
cd /media/MARKSUSB1GB/
mkdir 	/home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` 
echo Backup Started `date` >> /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y`/backuplog
		echo "40" ; sleep 1
cp -rf * /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` 
cp * /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` 
		echo "70" ; sleep 1
echo Files coppied `ls -alth` >> /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` /backuplog
echo Backup Completed `date` >> /home/mark/Usbbackup/Usbbackup-`date +%d`-`date +%m`-`date +%Y` /backuplog
ls -alth 
		echo "100" ; sleep 1
	) | zenity --progress


tell me if this is the wrong way to use this, but it seems to work

That looks ok.

---

### Post by markp1989 on 2007-08-19
> **walkerk said:**
> That looks ok.

Ok thanks for the help :D

---

