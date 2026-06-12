---
title: "New and with many problems. Acting strange."
date: 2019-01-04
forum: New to Ubuntu
---

### Post by zacguide on 2019-01-04
New to Linux in general and having a load of issues. System is acting strange.

Laptop came with Endless OS pre-installed and I had a techie uninstall that and install Ubuntu 18.04 for me

I have had to hard reset after the system has frozen twice in the 2 weeks I have used it. 

Tonight I was playing the preinstalled Mahjongg and the screen dimmed and the program froze, won't continue, can't quit. Other programs working fine except...

Several times tonight I have clicked on the Show Applictions and it flashed on the screen and disappeared. 

I have installed a few apps and needed online support help to install them, although I hear that is not so unusual as it depends on the code they write for installation. 

My experience so far has been extremely unpleasant

Any help greatly appreciated.

---

### Post by overdrank on 2019-01-04
Hi and welcome, if you can provide some specs on the laptop someone may be able to help. ;)

---

### Post by Impavidus on 2019-01-04
Let's see if something strange is going on with the installed software. Can you run these commands?```
sudo apt update
sudo apt upgrade
```That will just check for upgrades and install them. Show us the output, then we know if you're using non-standard software sources or are not fully up-to-date in any way. Note that it will ask for your password. Just type it and hit enter; you'll see no feedback in the terminal while typing.

---

### Post by oldfred on 2019-01-04
Best never to do hard reset unless absolutely nothing else works.
As new user, you should only be installing software from Ubuntu repository. Other software may or may not be ok, but can cause issues.

If you cannot get to terminal, always try this to reboot.
       Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system 
    
If you can get to terminal, you can run top to see processes & process number (pid). Then run kill to stop runaway process.
       top
ps -aux | grep "name of app"
sudo kill pid

---

### Post by oldrocker99 on 2019-01-05
Htop makes killing a process very easy. Hit F3 to search, and then F9 to give a menu of kill commands. I use SIGKILL myself.
```
sudo aptt install htop
```

It can be given an icon, which in fact can change appearance depending on your theme.

---

### Post by zacguide on 2019-01-09
Sorry, I didn't see any of these replies. I thought I'd get an email message. Thanks, I will try now...

---

### Post by zacguide on 2019-01-09
I executed the 
sudo apt update
sudo apt upgrade

See screenshots
This site is only allowing 1 attachment, see next message

---

### Post by zacguide on 2019-01-09
Ok, I set this forum to notify by email.

I cannot seem to attach a 2nd screenshot. I go to advanced => attachments => browse (photos) => choose file => upload = no dice

Doesn't show up in the box alongside my 1st attachment

The second 
sudo apt upgrade results listed 17 packages that can be upgraded, y or n? I pressed y

Long list of "preparing to unpack" and "unpacking..."

Don't know how to attach a 2nd screenshot

Thanks

---

### Post by zacguide on 2019-01-09
Sorry, I am actually not sure what to call what I did. I just held down the power button until the computer went off. I will be more careful with language.

I have to install some things not in the repository, for instance my VPN app. Otherwise yes, I stick to the repository.

If I execute top, how do I know which ones are runaway/problematic?

---

### Post by Impavidus on 2019-01-09
I've never had any trouble attaching multiple screenshots on this forum. It's supposed to work. But in case of terminal output, it's better to copy the text from the terminal and paste it in your post. Put it in [noparse]```
code tags
```[/noparse] to make it easy to read.

> **zacguide said:**
> 
I have installed a few apps and needed online support help to install them, although I hear that is not so unusual as it depends on the code they write for installation. 

How did you install those applications? There are many ways to install software from other sources than the official repositories and it's easy to damage your system that way.

---

### Post by zacguide on 2019-01-09
I installed them the way I was guided to by the support teams of the various apps. Via terminal and provided code developed for linux. These apps aren't available in the repositories, like VPNs for instance. How else would I install my VPN account for this computer without using their code?

Thanks for the help

---

### Post by oldfred on 2019-01-09
Never force shutdown your system. That can cause file damage.

Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
      
 R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system 
    
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by zacguide on 2019-01-09
> **oldfred said:**
> Never force shutdown your system. That can cause file damage.

Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
      
 R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system 
    
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

OK, thanks. Not something I would know to do and then can't research it while the system is frozen. 

The bigger issue though is why it froze in the first place. This was before many downloads. Maybe before any. I have hardly anything on the computer. Seems odd for a new system.

---

### Post by zacguide on 2019-01-09
Ok, here is a copy and paste for the given code:

```
user@zach:~$ sudo apt update
[sudo] password for user: 
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]    
Hit:2 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic InRelease               
Get:3 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]   
Get:4 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB] 
Get:5 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [480 kB]
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 Packages [180 kB]
Get:7 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [417 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages [237 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main Translation-en [89.3 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 Packages [108 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages [110 kB]
Get:13 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [261 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe Translation-en [62.4 kB]                                                  
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [14.8 kB]                                           
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [39.7 kB]                                              
Get:17 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 48x48 Icons [58.2 kB]                                                 
Get:18 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [111 kB]                                                  
Get:19 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [700 kB]                                                   
Get:20 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [708 kB]                                                  
Get:21 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [200 kB]                                           
Get:22 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 48x48 Icons [180 kB]                                              
Get:23 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [331 kB]                                              
Get:24 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]                                        
Get:25 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [5,816 B]                                        
Fetched 4,542 kB in 19s (236 kB/s)                                                                                                          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
```

---

### Post by zacguide on 2019-01-09
Sometimes when I slick on the "show apps" button, Did I damage files in the hard reset? Any way to check that? So that is still happening after the upgrades.

---

