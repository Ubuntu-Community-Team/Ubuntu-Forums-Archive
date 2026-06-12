---
title: "How To Install Ubuntu 8.04 Hardy Heron On The Asus M50Sv-A1"
date: 2008-05-19
forum: Outdated Tutorials &amp; Tips
---

### Post by hotweiss on 2008-05-19
1. Screen Brightness

The ambient light sensor is the cause of the dim screen, we&#8217;ll have to turn it off. To fix this we will have to create a shell script that will be run on boot up that will increase the brightness.

A) Open Terminal, and type the following:
> sudo nano brightness

B) Now paste the following in the Terminal window:
> #!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typin the following in Terminal:
> sudo mv brightness /etc/init.d
and then
> sudo chmod 755 /etc/init.d/brightness
and then
> sudo update-rc.d brightness defaults 90

E) Reboot, and you will have regained control of your brightness level.

2. Nvidia Driver

Your screen resolution will be limited to 800×600 without the appropriate drivers. Thanks to Alberto Milone&#8217;s Envy the whole process is automated for you, with the only requirement being an internet connection.

A) First we&#8217;ll need to update Ubuntu&#8217;s repositories by typing the following in Terminal:
> sudo apt-get update

B) Now we&#8217;ll need to install Envy by typing the following in Terminal:
> sudo apt-get install envyng-gtk

C) Next we&#8217;ll need run Envy by typing the following in Terminal once again:
> sudo envyng -g

D) Select Nvidia on the left side, now click on &#8220;Nvidia driver Manual selection&#8221;, select 169.12, and finally click apply.

E) Once the installation is completed, reboot and you will once again have a crisp screen.

3. Webcam Driver

The webcam if attempted to be used will crash any application that is trying to access it by default. Thanks to the great tutorial by Bill Giannikos the process of installing your Asus uvc webcam driver is relatively easy.

A) First we&#8217;ll need to install the files needed to build the driver by typing the following in Terminal:
> sudo apt-get install build-essential subversion linux-headers-`uname -r`

B) Now we will build the driver by typing the following commands in Terminal:
> cd /usr/src
and then
> sudo svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
and then
> cd trunk
and then
> sudo make
and then
> sudo cp -a uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/

C) Reboot, and your webcam will now be working.

4. Fingerprint Reader Driver

The fingerprint reader is especially useful in Linux as you are asked for your password before completing any change within the operating system. None the less, I would still not recommend for you to install the fingerprint reader driver due to its&#8217; unstable nature and poor quality. The guide provided by Karol Krizka solved the problem of installing this driver of which I have spent about an hour researching with out any success.

A) First we&#8217;ll need to add the driver source to our software repository by typing the following in Terminal to open the sources list:
> sudo nano /etc/apt/sources.list

B) Now scroll to the end of the file and paste the following line there:
> deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Update the source list by typing the following in Terminal:
> sudo aptitude update

E) Install the fingerprint reader driver by typing the following in Terminal:
> sudo aptitude install fprint-demo libpam-fprint libfprint

F) Enroll your fingerprint by typing the following in Terminal:
> sudo fprint_demo

G) Click on enroll and swipe your finger.

H) Now we will have to tell Ubuntu when to use your fingerprint by editing the fingerprint reader driver&#8217;s configuration file by typing the following in Terminal:
> sudo nano /etc/pam.d/common-auth

I) Paste the following in the file at the end:
> auth sufficient pam_fprint.so
auth required pam_unix.so nullok_secure

J) Hit Ctrl-O to save and then Ctrl-X to exit.

H) Reboot, and you will be now scanning your finger instead of typing your password each time.

---

### Post by Fiandri on 2008-05-25
> **hotweiss said:**
> 
4. Fingerprint Reader Driver

The fingerprint reader is especially useful in Linux as you are asked for your password before completing any change within the operating system. None the less, I would still not recommend for you to install the fingerprint reader driver due to its&#8217; unstable nature and poor quality. The guide provided by Karol Krizka solved the problem of installing this driver of which I have spent about an hour researching with out any success.

A) First we&#8217;ll need to add the driver source to our software repository by typing the following in Terminal to open the sources list:


B) Now scroll to the end of the file and paste the following line there:


C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Update the source list by typing the following in Terminal:


E) Install the fingerprint reader driver by typing the following in Terminal:


F) Enroll your fingerprint by typing the following in Terminal:


G) Click on enroll and swipe your finger.

H) Now we will have to tell Ubuntu when to use your fingerprint by editing the fingerprint reader driver&#8217;s configuration file by typing the following in Terminal:


I) Paste the following in the file at the end:


J) Hit Ctrl-O to save and then Ctrl-X to exit.

H) Reboot, and you will be now scanning your finger instead of typing your password each time.


Hi, thank you for your guide. I am a newbie and I just followed your procedure to activate fingerprint, but in my case it does not work properly. It partially works on login (but I have to swipe finger AND digit password), but it does not work in the other cases: if I try to update Ubuntu, for instance, I can't do it because neither password or fingerprint allow me to do it.

I will try to find a solution for future, but now I just need to know how to deactivate fingerprint and come back to password: what should I do? Do I just have to type

> sudo nano /etc/pam.d/common-auth

and then delete

> auth sufficient pam_fprint.so
auth required pam_unix.so nullok_secure?

Maybe it's a stupid question, but as I said I'm a newbie, and I saw there's another italian user with the same problem.. Thank you in advance!

---

### Post by hotweiss on 2008-06-17
> **Fiandri said:**
> Hi, thank you for your guide. I am a newbie and I just followed your procedure to activate fingerprint, but in my case it does not work properly. It partially works on login (but I have to swipe finger AND digit password), but it does not work in the other cases: if I try to update Ubuntu, for instance, I can't do it because neither password or fingerprint allow me to do it.

I will try to find a solution for future, but now I just need to know how to deactivate fingerprint and come back to password: what should I do? Do I just have to type



and then delete

?

Maybe it's a stupid question, but as I said I'm a newbie, and I saw there's another italian user with the same problem.. Thank you in advance!

That program is really buggy... because of it I had to reinstall everything.

---

