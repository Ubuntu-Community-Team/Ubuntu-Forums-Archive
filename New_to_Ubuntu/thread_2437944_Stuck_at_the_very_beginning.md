---
title: "Stuck at the very beginning"
date: 2020-03-03
forum: New to Ubuntu
---

### Post by weevie56 on 2020-03-03
I am new to Ubuntu and am trying to install Nagios on Ubuntu 18.04 desktop

I am following LHAMMONDS link and get an ERROR : CANNOT VERIFY GITHUBS Certificate !
use '--no-check-certificate'
How ?
I cannot therefore download Nagios

Any advice please

---

### Post by yancek on 2020-03-03
Nagios is available in the Ubuntu repositories.  Is there some reason you don't want that version.  What is "LHAMMONDS"?  Some tutorial site?  If it is you might post a link to it.

[https://kifarunix.com/how-to-install-and-configure-nagios-core-on-ubuntu-18-04/](https://kifarunix.com/how-to-install-and-configure-nagios-core-on-ubuntu-18-04/)

---

### Post by ajgreeny on 2020-03-03
I assume weevie56 is talking about this thread
[https://ubuntuforums.org/showthread.php?t=1986743&highlight=lhammonds+nagios](https://ubuntuforums.org/showthread.php?t=1986743&highlight=lhammonds+nagios)

However, I will have to leave it to others using servers to come to the rescue here for more help, though I note that the linked thread is now 8 years old (for 12.04) so may be very outdated and need some edits or changes.

---

### Post by weevie56 on 2020-03-04
> **yancek said:**
> Nagios is available in the Ubuntu repositories.  Is there some reason you don't want that version.  What is "LHAMMONDS"?  Some tutorial site?  If it is you might post a link to it.

[https://kifarunix.com/how-to-install-and-configure-nagios-core-on-ubuntu-18-04/](https://kifarunix.com/how-to-install-and-configure-nagios-core-on-ubuntu-18-04/)

I am aware that Nagios is available - ALL over the place - but am experiencing incredible difficulty installing Nagios 
Is there any reason why Nagios should not install on Ubuntu 18.04.4 LTS desktop
I am unable to access ROOT !
Also - the damned thing won't connect to the net for updates - I have added a ssl cert and it allows browsing - but not system updates
Any help welcome

---

### Post by CelticWarrior on 2020-03-04
> **weevie56 said:**
> but am experiencing incredible difficulty installing Nagios 
Is there any reason why Nagios should not install on Ubuntu 18.04.4 LTS desktop

Only if you aren't installing from the official repositories. Again, why not?

---

### Post by weevie56 on 2020-03-04
> **CelticWarrior said:**
> Only if you aren't installing from the official repositories. Again, why not?

I am installing from official repositories - but cannot even figure out why the Software updater will not allow any updates
I have checked SETTINGS and all is correct - but when I try updating - I get "FAILED TO DOWNLOAD PACKAGE FILES - Check your internet connection"
Download from Server for UK

---

### Post by CelticWarrior on 2020-03-04
That message indicates you have other issues with software, like broken packages and/or incorrect PPAs.

Please check with ```
sudo apt update
```
The error messages in full are helpful to troubleshoot.

---

### Post by oldrocker99 on 2020-03-04
When the described problem comes up, it's likely a down server. Go to Software Sources (iirc) and click "test servers." I have gotten good results from the MIT repos; of course, I do live in New England...

---

### Post by Impavidus on 2020-03-04
Instead of guessing what could be the problem, let's have a look at some actual commands and their output. Error messages tend to be really helpful on Ubuntu. Can you show us the exact and complete output of these commands:```
sudo apt update
sudo apt upgrade
sudo apt install nagios3
```I assume the nagios3 package is what you need on Ubuntu 18.04.

If you're unable to "access root", we have to find out why. Maybe your system is completely messed up, maybe you have a very basic misunderstanding of how sudo works, or one of many possibilities inbetween. In the second case, reading this may clear up some things: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by weevie56 on 2020-03-05
I am now ROOT !!
I am trying the package manager and (on a new/clean installation of Ubuntu 18.0.4) I get an error "Unable to fetch some archives ............" when I try running [FONT=monospace]# apt-get -y install apache2 php php-cgi libapache2-mod-php php-common php-pear php-mbstring
I have run apt-get update - which appears to update most - but on re-running [/FONT][FONT=monospace]# apt-get -y install apache2 php php-cgi libapache2-mod-php php-common php-pear php-mbstring - STILL gives same error !!
[/FONT]

---

### Post by weevie56 on 2020-03-05
> **Impavidus said:**
> Instead of guessing what could be the problem, let's have a look at some actual commands and their output. Error messages tend to be really helpful on Ubuntu. Can you show us the exact and complete output of these commands:```
sudo apt update
sudo apt upgrade
sudo apt install nagios3
```I assume the nagios3 package is what you need on Ubuntu 18.04.

If you're unable to "access root", we have to find out why. Maybe your system is completely messed up, maybe you have a very basic misunderstanding of how sudo works, or one of many possibilities inbetween. In the second case, reading this may clear up some things: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudo apt update - works --YIPEE - But only provides a list of upgradeable components - doesn't actually upgrade/update them - how is this achieved ?
sudo apt upgrade - again, downloads heaps - but "FAILED  TO FETCH.. ****"
sudo apt install nagios3 - does what it says - " where does it  put it ?  its not in "downloads" then errors "failed to  fetch http://gb.archive****" (many times over)

---

### Post by TheFu on 2020-03-05
weevie56, Linux isn't like Windows. We don't download setup.exe files to be installed.

a) please run the commands requested.  You're jumping all over the place.  1-thread, 1-issue please.
b) If one command has any failure, STOP!  Post the requested output. Get help. Get that issue solved. Only then, move onto the next step.

We cannot read your mind.  If we don't see the output from commands, we won't assume you've actually gotten anything working. There is a mandatory order to the commands. Throwing random command or out of order commands can break a system.  Unix assumes the admin actually knows what they are doing, even if it is stupid.

Hammon has reasonable guides, but they are per-release.  Using a guide that is for the wrong release usually won't work and may break things.

Since you are so new, please read this primer: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) to understand the big picture first. 

Installing nagios is something beyond most beginners, especially if they've only used point-n-click stuff previously. When it comes to all Unix-like systems, we have to crawl, stand, wobble, walk, jog, run, sprint  - - IN THAT ORDER.  Nagios is a "walk" level skill, IMHO.  Mainly because it has lots of dependencies to be useful.  Every prior skill is necessary before we can sprint.

---

### Post by Impavidus on 2020-03-05
Indeed, **sudo apt update** refreshes the list of available software in the repositories and provides a list of upgradeable components. The next command, **sudo apt upgrade**, is the one that downloads and installs them. The packages that get downloaded are stored in /var/cache/apt/archives, but that's not important to you.

To provide more help, we need the exact and full output of those commands. Select it in your terminal, copy-paste it to the forum and put it in code tags. We're quite experienced looking for the root cause of an error in apt output.

Also, is there anything we should know about your network? Firewalls, proxy servers, things like that.

---

### Post by weevie56 on 2020-03-05
OK In case I have done irreparable damage to the installation - I am reinstalling Ubuntu desktop
No proxys, we have firewalls but they are easy to bypass !

---

### Post by weevie56 on 2020-03-05
I have now got a fresh clean installation to work from
Step 1 updates ?

---

### Post by TheFu on 2020-03-05
> **weevie56 said:**
> I have now got a fresh clean installation to work from
Step 1 updates ?

There are lots of "1st Five Minutes on a New Server" Articles out there.
Here's mine: [https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

---

### Post by weevie56 on 2020-03-11
Could somebody please confirm that Nagios will install on Ubuntu desktop - not just server ?

---

### Post by Impavidus on 2020-03-11
The difference between a desktop installation and a server installation is the set of default software. The repositories and with that the set of installable software are the same.

The same applies to the differences between the various flavours.

---

### Post by oldrocker99 on 2020-03-11
```
I am now ROOT !!
I am trying the package manager and (on a new/clean installation of Ubuntu 18.0.4) I get an error "Unable to fetch some archives ............" when I try running # apt-get -y install apache2 php php-cgi libapache2-mod-php php-common php-pear php-mbstring
I have run apt-get update - which appears to update most - but on re-running # apt-get -y install apache2 php php-cgi libapache2-mod-php php-common php-pear php-mbstring - STILL gives same error !!
```

NEVER, ever log in as root. ALWAYS use sudo. Root on all the time is a recipe for disaster. Sudo gives super user access for ~10 minutes, and is 100% safer.

---

