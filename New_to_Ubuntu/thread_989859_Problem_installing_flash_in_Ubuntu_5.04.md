---
title: "Problem installing flash in Ubuntu 5.04"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Tony007 on 2008-11-22
Hi all .I got few  ubuntu 5.04 LIVE cds . I need to installed flash to be able to view youtube videos but when i install the flash player never shows up to play the video!! Like a while ago it was working fine!! Did flash chage the installation path or firefox ? I installed from terminal and it says installation completed but the player never shows up !! Could you guys help me fix this problem without having to burn a newer version of Ubuntu ?Looking forward for replies.Thanks

---

### Post by jimmy the saint on 2008-11-22
5.04 is so different from the current generation that there are probably many, as opposed to one or two, issues preventing you from being able to do what you want.  The packages are designed for current distros which have different versions of libs, different folder structures, different software, and so on and so forth.  I can't definitively say that it can't be done, but it would probably be FAR easier to just download 8.10 and be done with it.

---

### Post by Tony007 on 2008-11-22
> **jimmy the saint said:**
> 5.04 is so different from the current generation that there are probably many, as opposed to one or two, issues preventing you from being able to do what you want.  The packages are designed for current distros which have different versions of libs, different folder structures, different software, and so on and so forth.  I can't definitively say that it can't be done, but it would probably be FAR easier to just download 8.10 and be done with it.

Thanks for your reply . I just did what you told and burned a copy of ubuntu 8.04 but still the flash doesn't install . In fact i don't know how to install it from terminal as in this version it doesn't give me to run in terminal by right clicking the file!! Could you tell step by step what should i do?Thanks

---

### Post by mikewhatever on 2008-11-22
5.04 has reached it's end of cycle long long ago. There are no repositories to install software and updates, and the current (version 10) debs of flashplayer would most certainly not work. You could probably install an older version, if you can find it. Unless your primary goal is messing around with Ubuntu, get a more recent version.

---

### Post by Tony007 on 2008-11-22
> **mikewhatever said:**
> 5.04 has reached it's end of cycle long long ago. There are no repositories to install software and updates, and the current (version 10) debs of flashplayer would most certainly not work. You could probably install an older version, if you can find it. Unless your primary goal is messing around with Ubuntu, get a more recent version.

I said in my last post that i burned a cd of **ubuntu 8.04** and don't know how to install falsh on it!! Can you tell me how to install flash on it ? I need flash very badly for my work.Thanks

---

### Post by mikewhatever on 2008-11-22
> **Tony007 said:**
> I said in my last post that i burned a cd of **ubuntu 8.04** and don't know how to install falsh on it!! Can you tell me how to install flash on it ? I need flash very badly for my work.Thanks

Right, sorry for misunderstanding.

<sudo apt-get install flashplugin-nonfree>

---

### Post by Tony007 on 2008-11-22
> **mikewhatever said:**
> Right, sorry for misunderstanding.

<sudo apt-get install flashplugin-nonfree>


Many thanks i tried your code but i got this error:

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
ubuntu@ubuntu:~$ 

I downloade flash from this  site [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
i selected the **.tar.gz for linux**.I be happy if you help me install it and enjoy youtube videos...

**Note **:the folder that is downloaded is called  **install_flash_player_10_linux.tar.gz** and it is saved in /home/Desktop

---

### Post by flanagan on 2008-11-22
Since flashplugin-nonfree has literally many dependencies, you might try to use  System > Administration > Synaptic Package Manager to make sure you get them all.

---

### Post by shifty_powers on 2008-11-22
if you are using 8.04, then do

```
sudo apt-get install ubuntu-restricted-extras
```

if you are using a release from 2005, please update it. it is no longer supported, has no repositiories and will have security flaws which have not been patched...

the above is in the terminal of course/...

---

### Post by Tony007 on 2008-11-22
> **flanagan said:**
> Since flashplugin-nonfree has literally many dependencies, you might try to use  System > Administration > Synaptic Package Manager to make sure you get them all.

i am just new to linux world so can you tell me how to to use System > Administration > Synaptic Package Manager?

---

### Post by flanagan on 2008-11-22
> **Tony007 said:**
> i am just new to linux world so can you tell me how to to use System > Administration > Synaptic Package Manager?

In your main panel, usually at the top of the screen by default, click the menu that says System. click the sub-menu that says "Administration", click Synaptic Package Manager.

In the resulting app, type "flashplugin-nonfree" (without the quotes) in the Quick Search box. Click the checkbox next to "flashplugin-nonfree", then click the "Apply" button at the top (with the big check mark). Synaptic will tell you which dependencies it needs.

---

### Post by mikewhatever on 2008-11-22
> **Tony007 said:**
> Many thanks i tried your code but i got this error:



I downloade flash from this  site [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
i selected the **.tar.gz for linux**.I be happy if you help me install it and enjoy youtube videos...

**Note **:the folder that is downloaded is called  **install_flash_player_10_linux.tar.gz** and it is saved in /home/Desktop

1. cd ~/Desktop
2. tar -xvvf install_flash_player_10_linux.tar.gz
3. cd install_flash_player_10_linux
3. ./flashplayer-installer

then follow prompts.

---

### Post by Tony007 on 2008-11-22
Mike whatever many thanks for your help but i followed what you told me and still the flash player doesn't show !!

> 
ubuntu@ubuntu:~/Desktop$ tar -xvvf install_flash_player_10_linux.tar.gz
drwxr-xr-x buildmeister/buildmeister 0 2008-10-05 03:15 install_flash_player_10_linux/
-r-xr-xr-x buildmeister/buildmeister 21701 2008-10-05 03:15 install_flash_player_10_linux/flashplayer-installer
-rwxr-xr-x buildmeister/buildmeister 10017140 2008-10-05 03:15 install_flash_player_10_linux/libflashplayer.so
ubuntu@ubuntu:~/Desktop$ cd install_flash_player_10_linux
ubuntu@ubuntu:~/Desktop/install_flash_player_10_linux$ ./flashplayer-installer

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 10 for Linux

Adobe Flash Player 10 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 10 will be installed in your home directory.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 10 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...





----------- Install Action Summary -----------

Adobe Flash Player 10 will be installed in the following directory:

Mozilla installation directory  = /home/ubuntu/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n): n


Please log out of this session and log in for the changes to take effect.


The Adobe Flash Player installation is complete.

ubuntu@ubuntu:~/Desktop/install_flash_player_10_linux$ 

---

### Post by Tom--d on 2008-11-22
The best way to install Flash and other programs is in Add/Remove! (Applications > Add/Remove)

Add/Remove is amazing :D:D

---

### Post by mikewhatever on 2008-11-22
> Mike whatever many thanks for your help but i followed what you told me and still the flash player doesn't show !!

I've just removed the flash installed from the repositories and installed the downloaded tar.gz. It works, so not sure what's wrong. Can you post the output of the following without brackets: <ls .mozilla/plugins>.

---

### Post by ikisham on 2008-11-22
Tony, calm down. If you look better, instead of downloading .tar.gz for linux, you'll see there's an option for ubuntu 8.04+. It installs automatically just like in Windows.
Cheers.

---

