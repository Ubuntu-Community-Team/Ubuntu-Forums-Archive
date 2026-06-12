---
title: "dpkg --configure -a Issue, please help!"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by edxmonkey on 2008-06-08
Aside from my sound problem, almost anytime I enter a command in the Terminal or use Synaptic Package Manager I get the error:
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
 
While I understand it may happen from time to time, I don't think it should be happening quite that much.

Any and all help is greatly appreciated.

---

### Post by mac9416 on 2008-06-08
That once happened to me. I eventually gave it a little R@R... Reformat and Reinstall.

---

### Post by edxmonkey on 2008-06-08
Thank you. 

By that you mean completely reinstalling Ubuntu? 

I assume that fixed the issue...?

---

### Post by overdrank on 2008-06-08
> **edxmonkey said:**
> Aside from my sound problem, almost anytime I enter a command in the Terminal or use Synaptic Package Manager I get the error:
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
 
While I understand it may happen from time to time, I don't think it should be happening quite that much.

Any and all help is greatly appreciated.

HI and have you run that command in the terminal 
```
sudo dpkg --configure -a
```

---

### Post by mac9416 on 2008-06-08
> **edxmonkey said:**
> Thank you. 

By that you mean completely reinstalling Ubuntu? 

I assume that fixed the issue...?

Yes, a complete reinstall. I don't recommend it, but keep it in mind.

Oh yes, a complete reinstall will fix almost anything!

You should certainly try what overdrank said first, but it didn't work for me.

---

### Post by edxmonkey on 2008-06-09
Mm, more than once.

If I want to enter almost any command I have to use 'sudo dpkg --configure -a' before anything will go through. 

I think part of the issue is that I suspect that I have damaged files or the like partially installed. I was trying to install the needed codecs, etc so I could at least play music while I tried to figure this out... However the sunjava whatnot is giving me grief. I'm really not sure what to do.

More than anything I'd like to get sound on flash, youtube videos working, or get the needed codecs and whatnot so I can have some form of music.

Learning to use a new OS is hard enough - without music I'm about to go crazy.

---

### Post by overdrank on 2008-06-09
> **edxmonkey said:**
> Mm, more than once.

If I want to enter almost any command I have to use 'sudo dpkg --configure -a' before anything will go through. 

I think part of the issue is that I suspect that I have damaged files or the like partially installed. I was trying to install the needed codecs, etc so I could at least play music while I tried to figure this out... However the sunjava whatnot is giving me grief. I'm really not sure what to do.

More than anything I'd like to get sound on flash, youtube videos working, or get the needed codecs and whatnot so I can have some form of music.

Learning to use a new OS is hard enough - without music I'm about to go crazy.

Ok if this started when installing the java then when you run the dpkg command it should correct the issue. If not then you may use the command ```
sudo apt-get install -f
``` please post back any errors.

---

### Post by mac9416 on 2008-06-09
Man, don't give up on Ubuntu. I had the same issue and considered going back to Windoze exclusively. Don't.
Good luck.

---

### Post by edxmonkey on 2008-06-09
Oh - no I'm not going back, this is just how I learn.

If I don't force myself I won't learn as quickly or efficiently as I should - so I got rid of Windows completely. Now I've super motivation to learn to fully use this. 

Also I will try that and post the results. Thank you. ^^;

---

### Post by edxmonkey on 2008-06-09
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
edward@NOVA:~$ sudo dpkg --configure -a
edward@NOVA:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  binfmt-support sun-java6-fonts sun-java6-plugin ia32-sun-java6-plugin
  ttf-wqy-zenhei
Recommended packages:
  gsfonts-x11
The following packages will be upgraded:
  sun-java6-bin sun-java6-jre
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/33.6MB of archives.
After this operation, 96.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.

Then it gives me another few lines similar the the one above and jumps to a package configuration for sun-java6 bin.

I'm sure it's some user error - but any ideas?

---

### Post by Paqman on 2008-06-09
> **edxmonkey said:**
> I was trying to install the needed codecs, etc so I could at least play music while I tried to figure this out... However the sunjava whatnot is giving me grief. I'm really not sure what to do.

More than anything I'd like to get sound on flash, youtube videos working, or get the needed codecs and whatnot so I can have some form of music.


Java, Flash and multimedia codecs are all included in the package ubuntu-restricted-extras.

---

### Post by Fixman on 2008-06-09
system->administration->software sources->download from->main server.

Open terminal and write
```
 sudo apt-get update 
```

That should make it.

---

