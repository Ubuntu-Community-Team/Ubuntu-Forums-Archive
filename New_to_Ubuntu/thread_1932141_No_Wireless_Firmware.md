---
title: "No Wireless Firmware"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by rocksmtu on 2012-02-26
Total NOOB to Linux here.  Sorry in advance for stupid questions.

I loaded ubuntu 11.10 on a laptop (dell insprion 2200)  everything seems to be working great except for the wireless modem.  I am missing firmware.  I found that I have a :

Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)


after reading up on how to fix this I am still unable to load the missing firmware.

I ran the command 
sudo apt-get install firmware-b43-installer

nothing happened it still says missing firmware.  

Am I supposed to do anthing else or does the "install" command do everything
on its own

I dont see a B43 directory in  /lib/firmware

---

### Post by wildmanne39 on 2012-02-26
Hi, this should work if nothing else needs fixing.

Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here, run the commands one line at a time and watch for errors. Open a terminal and do:
```
cd Desktop
sudo mv b43/* /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
unplug wired connection.
Thanks

---

### Post by rocksmtu on 2012-02-28
Thanks for the help but it didnt work.
Here is what is did, maybe i screwqed something up

:~$ sudo mv b43/* /lib/firmware
[sudo] password for ****: 
mv: cannot stat `b43/*': No such file or directory
:~$ cd Desktop
:~/Desktop$ sudo mv b43/* /lib/firmware
:~/Desktop$ rmmod -f b43
ERROR: Removing 'b43': Operation not permitted
:~/Desktop$ sudo rmmod -f b43
:~/Desktop$ sudo rmmod -f ssb
:~/Desktop$ sudo modprobe b43
:~/Desktop$

* I deleted the username@computername for privacy

Do you have any other suggestions.

Thanks

***
 After i closed firefox i saw that the b43 folder was still on my desk top.  I tried to move it to the lib/firmware by using the GUI (open file system open lib open firmware drag folder from desk top get error message - permission denied -.)  Why dosent it work that way.

---

### Post by lkraemer on 2012-02-29
Look inside the /b43 folder on your desktop.  If your *.fw files are still
there the mv command didn't function.  But, I suspect it did.

If the *.fw files are missing delete that folder named b43.

Then go to Hardware drivers and ENABLE the hardware drivers.

Your Wifi should now function.  You can look for the *.fw files located at:
/lib/firmware and in /lib/firmware/b43
to make sure they were copied.

lk

---

### Post by wildmanne39 on 2012-03-04
Hi, please just copy and paste the commands one line at a time and make sure you enter your user password and see if that helps.
thanks

---

### Post by albert s on 2012-03-04
have a look in synaptic, or on a newer system try the software center,
I have an old DELL laptop and thats how I got the b43 driver for mine.
hardwired to download the software, then unplugged the cable and rebooted and it was working fine on wi-fi.

---

### Post by rocksmtu on 2012-03-05
I solved the problem
 
I used the "dmesg" command and there was a message telling me that I was missing a file in the "b43" and the "b43-open" folders in the firmware directory
 
I wasnt able to create the directories using the GUI but I was able to creat them using sudo.  Then I coppied the missing files from the folder I downloaded from here.  I had to go through a couple of "dmesg" and copy interations before I was able to get the device to work.
 
Im not really sure why I wasnt able to use the GUI to make the directory and copy the files? But it works now. 
 
Thanks everyone for the help.

---

### Post by wildmanne39 on 2012-03-09
Hi, your welcome! Glad you got it working.

---

