---
title: "Trying to install Flash..."
date: 2008-07-16
forum: New to Ubuntu
---

### Post by projecthikari on 2008-07-16
Alright, just to begin, I'm stupid new at this Ubuntu thing. Like, 4 hours old new. I installed Ubuntu as a last chance to try and make my internet work, since XP was newly installed and being a pill. I was expecting this overly complicated, hard to understand OS, and I have to say I'm deeply in love. I'm sold.
Now, If only I could figure out some of this lingo...

I'm trying to install Flash, and I simply ran into trouble. It just wont go for it... It's saying something to me, which, I tried to figure out the problem myself but gave up pretty quickly.

...Help? *must look like a fool.*	:-\"

I'm determined to figure this perfectly wonderful OS out!!

---

### Post by snowpine on 2008-07-16
Hi, ignore the method you've been using so far. Open a terminal window and type:

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

That will install Flash plus some other goodies like mp3 playback. :)

Good luck, post back if you have any problems!

---

### Post by framinglory on 2008-07-16
download flash from here, unpack the archive, and place the libflashplayer.so in /home/yourname/.mozilla/plugins you may have to create the plugins directory in .mozilla. To show folders that begin with a . in nautilus (hidden folders/files) hit ctrl+h
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash)

edit: do what was said above, that way is easier. the way i mentioned is to manually install it, (what the picture you posted appeared to be doing, but failed to do)

---

### Post by sdowney717 on 2008-07-16
or
just use synaptic gui
from menu item
system - administration - synaptic package manager

search for flash or adobe.

It is best to stay within ubuntu packages since the package manager keeps track of packages that you installed. And some of these have been optimized for Ubuntu. Means they will work better!

---

### Post by gandaran on 2008-07-16
why not install the flash from the repos?
open synaptic, look for flashplugin-nonfree, check for install and click the apply button.
or use this command, type in the terminal **sudo apt-get install flashplugin-nonfree** and press enter.

---

### Post by silkstone on 2008-07-16
Use Synaptic to install flashplugin-nonfree as suggested. That gives you Flash version 9.

However, if that doesn't work too well and you get problems with flash playback on certain websites, you can install Flash 10.

Take a look here...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

... and scroll right down to "Troubleshooting - Adobe Flash Player"

That gives a good method of installing the beta version of Flash 10. Note that there are actually two beta versions now, and many people have found that the first version works better than the second.

---

### Post by projecthikari on 2008-07-16
Thanks guys! Man. this was quick and helpful.
I was attempting the "sudo apt-get install..." stuff, and then i popped up with "[sudo] password for jen" and I was once again lost. Is it my Name password? I typed that in, and It said it was invalid...

Ah despite, I used the Synaptic and got myself flash. :] Thank you all!

...Expect more questions in the near future. XD

---

### Post by sdowney717 on 2008-07-16
regarding flash 10, I tried both and sorry to say they dont work well for me. 
BBC and CNN do not recognoze the flash 10 player
And I had problems with it being jerky. Not smooth like the one in Ubuntu repository. 
I assume when it is officially finalized it will be ok.

---

### Post by gandaran on 2008-07-16
> **projecthikari said:**
> Thanks guys! Man. this was quick and helpful.
I was attempting the "sudo apt-get install..." stuff, and then i popped up with "[sudo] password for jen" and I was once again lost. Is it my Name password? I typed that in, and It said it was invalid...

Ah despite, I used the Synaptic and got myself flash. :] Thank you all!

...Expect more questions in the near future. XD
 

it's your root password, the same one you use to login.

---

### Post by Thelasko on 2008-07-16
> [sudo] password for jen
You just enter the password you use to login.  If it didn't work before, you probably just mistyped it.

---

### Post by projecthikari on 2008-07-16
It seems that I have to type it very quickly and press enter... I need something to test this on.

...Anything anybody else wanna give to me to play with in the terminal? :D XD

---

### Post by silkstone on 2008-07-16
> **sdowney717 said:**
> regarding flash 10, I tried both and sorry to say they dont work well for me. 
BBC and CNN do not recognoze the flash 10 player
And I had problems with it being jerky. Not smooth like the one in Ubuntu repository. 
I assume when it is officially finalized it will be ok.

I'm using Flash 10 (beta 1) and the BBC and CNN play very well. The only thing that doesn't work properly is transparency, so the clock on the BBC home page has a black background.

I installed the Flash 10 plugin using the instructions in the link I posted above. That's not the same as installing using the flashplayer-installer. ;)

---

### Post by cardinals_fan on 2008-07-16
> **projecthikari said:**
> It seems that I have to type it very quickly and press enter... I need something to test this on.

...Anything anybody else wanna give to me to play with in the terminal? :D XD
Just type it carefully - it should work :)

---

### Post by carandraug on 2008-07-16
> **projecthikari said:**
> It seems that I have to type it very quickly and press enter... I need something to test this on.

...Anything anybody else wanna give to me to play with in the terminal? :D XD

The most useful thing in the terminal is```
man name_of_a_program
```This will show you the documentation for the program (shift+Q to leave the manual once you have read what you want).
Also, check [LinuxCommands]("http://www.linuxcommand.org/").

And if you want to use it more, you have mpg123 as music player and rtorrent to download torrents.

---

### Post by joshfantoo on 2008-07-16
tried the code in terminal and to get flash installed and this came up: 


david@david-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [189B]          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US  
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Fetched 3B in 1s (3B/s)  
Reading package lists... Done
david@david-desktop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
david@david-desktop:~$ 

lash still does not work after this  and i tried adobe and flash search in synaptic package manager and can not find flash in there. i am new also installed last night.

---

### Post by AndyCooll on 2008-07-16
System > Administration > Synaptic Package Manager

Settings > Repositories > Ubuntu Software

Place a tick against all the "downloadable from the Internet" options.
It will then ask you to reload. Then do another search for the the restricted-extras package.

:cool:

---

### Post by pelle.k on 2008-07-16
It's in the "multiverse" repos, you can activate that, and "universe" as well. It's there because it's non-free software basically...
You can do this from "synaptic" (the package manager in Administration menu), or in "software sources".
Good luck!

---

### Post by joshfantoo on 2008-07-16
thanks i placed the ticks and reloaded and searched for flash ans found the flash non free and installed it thanks to all i appreciate it. really helpful forum.

---

### Post by aysiu on 2008-07-17
Next time you can just visit a Flash website and click the *Install missing plugins* prompt. More details (with screenshots) here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

