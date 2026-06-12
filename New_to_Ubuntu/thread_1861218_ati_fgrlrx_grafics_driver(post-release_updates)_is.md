---
title: "ati fgrlrx grafics driver(post-release updates) issue/question?"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by werty2010 on 2011-10-15
i did a fresh install of ubuntu 11.10 on my laptop and almost everything seems to work out of the box so far except a few minor issues.
on the additional driver window for the graphics card(ati hd 5650 ) i have 2 available instead of one:
-ati/amd fgrlrx grafics driver(post-release updates)
-ati/amd fgrlrx grafics driver

(why 2?)

i tried the first one:it downloaded it,started to install it and in the end it gave this message:
```

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```

despite the message and the indicator that it wasnt installed,  i think it actually install something because i have now the"amd catalyst control center" installed.
so my questions are:
should i worry? is it actually installed?
if yes,would i have the next update releases of the driver when they're ready?

---

### Post by Irony on 2011-10-15
Run this;
```
~$ fglrxinfo
```
And you should get something like this;
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4300/4500 Series    
OpenGL version string: 3.3.10317 Compatibility Profile Context
```

If you don't then it hasn't installed correctly.

---

### Post by dralaroc on 2011-10-15
Werty, I am getting the same message :)

---

### Post by werty2010 on 2011-10-15
[Irony]("http://ubuntuforums.org/member.php?u=27663") thanks, i checked as you said,so i guess im running the ati drivers
[dralaroc]("http://ubuntuforums.org/member.php?u=74387") good to know im not the only one

if anyone could answer to the rest of my questions, please do

---

### Post by werty2010 on 2011-10-16
bump

---

### Post by asadmalik on 2011-10-16
i am having the same issue after upgrading from 11.04. the post release update fails to install and gives the same error message as stated in #1.

Output of 
$ fglrxinfo


display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series        
OpenGL version string: 3.3.11005 Compatibility Profile Context

---

### Post by alco75 on 2011-10-19
I get the same message.

In Additional Drivers, the ATI driver that says 'post-release updates' does not install/activate without error.

However, the ATI driver that *doesn't* say 'post-release updates' installs/activates okay.

---

### Post by bks07 on 2011-10-20
jap, I got the same problem and same output as asadmalik. :(

---

### Post by growingneeds on 2011-10-21
I have the same problem. ATI updates for post-release fails to install. I have an AMD C-50 netbook.

---

### Post by dyallo on 2011-10-21
Try this
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

or  this
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch)

(Basically the same thing)
I had problems with ATI, now, not so much (still a bit buggy now and then) ATI HD5850


display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series
OpenGL version string: 4.1.11079 Compatibility Profile Context

---

### Post by linbetwin on 2011-10-30
I have the same issue.
Running 11.10 amd64 on a desktop with an ATI 4870.
I installed betas and RC's of Oneiric many times and the "post-release updates" driver always fails to install (or at least it says it failed). Now I've reinstalled Oneiric once again but haven't yet activated the proprietary drivers.

Should I disregard the error message or should I install the second driver?
How can I find out which versions these two drivers are before installing them?

---

### Post by Bucic on 2011-10-31
Catalyst from the *Jokey* applet gives me the worst performance possible compared to the default drivers or Intel GM 4500.

**A supposed to be solution posted by GinoMan2440**
[http://ubuntuforums.org/showthread.php?p=11385354#post11385354](http://ubuntuforums.org/showthread.php?p=11385354#post11385354)

---

### Post by sundman on 2011-11-08
A good source on fglrx driver installation issues of all sorts is cchtml.org. For Oneiric installation guidelines using the packages provided see [Using Ubuntu-supplied fglrx/Catalyst]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide  Using Ubuntu-supplied fglrx/Catalyst")

To my experience jockey (a.k.a. Hardware drivers) won't install or enable fglrx. Manually installing means installing the driver and let it first generate a X.org file and then adjust it with the Catalyst Control Center.

Also note that there is two versions of the driver fglrx and fglrx-updates - which is, surprise, surprise, a more recent version!

---

### Post by sundman on 2011-11-18
Weird - suddenly the updates version of the driver performance dropped to a crawl.

It was a real mess reverting back fgrlx but it works OK again.

---

