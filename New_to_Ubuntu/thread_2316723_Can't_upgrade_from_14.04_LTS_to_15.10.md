---
title: "Can't upgrade from 14.04 LTS to 15.10"
date: 2016-03-10
forum: New to Ubuntu
---

### Post by jedi_knight2 on 2016-03-10
Hey everyone I am trying for some days now to upgrade to ubuntu 15.10. I always get an error message saying ''Cannot calculate the upgrade'', I tried the commands : ```
sudo apt-get -f install
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove



```
I tried using this command too ```
grep Broken /var/log/dist-upgrade/apt.log
```
But it seems I have too many broken packages, and I don't know which to remove cause I am afraid I am going to break my system. I tried Synaptic but it won't even list my broken packages!
Help!!!

---

### Post by Bucky Ball on 2016-03-10
Synaptic will fix your broken packages though, or try to.

Your post is very vague. How are you intending to upgrade 14.04 LTS to 15.10? That won't happen unless you upgrade to 14.10 first, and that is no longer supported. You'd then need to upgrade that to 15.04, also EOL, then upgrade that to 15.10.

If you have that many broken packages that Synaptic can't fix, then your system is broken anyway and removing things is not going to make any difference (just break it further). 

Back up what you don't want to lose and clean install 15.10 if that's the release you want. Might be better to mark this as resolved and post a new thread in an attempt to fix 14.04 LTS, though. That will upgrade directly to 16.04 LTS later in the year, negating the requirement to negotiate all the end-of-life releases on an already dodgy system as LTS to LTS upgrade leap-frogs the EOL releases.

---

### Post by jedi_knight2 on 2016-03-10
I tried upgrading to 14.10 first through terminal, but the same thing happened. I also installed 14.04 LTS a while ago, it hasn't been two full weeks yet.

---

### Post by grahammechanical on 2016-03-10
Ubuntu 16.04 will be released at the end of April 2016. And there will be a direct upgrade path from Ubuntu 14.04 to 16.04. In fact for a few days 14.04 users will be nagged about upgrading to 16.04.

Ubuntu 15.10 will reach end of life at the end of July 2016. So, anyone using 15.10 will have to upgrade to 16.04. So, it seems to me most sensible for 14.04 users to be patient and upgrade to 16.04 when it is released and not try to upgrade to 15.10.

There have been a few posts on this forum where users thought that upgrading to a newer release would fix problems. It did not. But a fresh install will fix problems because it will over-write the existing OS with a new one.

In preparation for upgrading to a new release of Ubuntu we should backup our data; revert to using an open source video driver; revert the desktop to as default a state as possible; disable any PPAs. And read the release notes.

Regards

---

### Post by jedi_knight2 on 2016-03-10
Ah okay I didn't know heh, I should have done more research. Well thanks anyway.

---

### Post by Bucky Ball on 2016-03-10
No rush to get to 15.10. The latest isn't always the greatest. LTS are intended to be very stable.

If I say, if you are having so many issues, broken packages etc., boot Synaptics in the first instance and 'Fix Broken Packages'. When you boot Synaptic, if you have got broken packages, it will tell you in the info bar, bottom left.

If this is resolved, please use the first link in my signature below.

---

### Post by jedi_knight2 on 2016-03-11
It says 0 broken, but when I run this command: ```
grep Broken /var/log/dist-upgrade/apt.log
```
It shows me multiple broken packages.

---

### Post by jedi_knight2 on 2016-03-11
[ATTACH]267749[/ATTACH]

Here are the details of the broken files.

---

### Post by Bucky Ball on 2016-03-11
Yuck. That really didn't go well. Please run these commands one at a time and copy and paste the output between code tags (not a file) in a post here. See my signature at the bottom of this post for how to use code tags.

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by jedi_knight2 on 2016-03-11
sudo apt-get autoremove:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
sudo apt-get update:
```
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://ppa.launchpad.net trusty InRelease                        
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable Release                                        
Ign http://ubuntu.otenet.gr trusty InRelease                                   
Ign http://archive.canonical.com trusty InRelease                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages              
Get:1 http://ubuntu.otenet.gr trusty-updates InRelease [65,9 kB]               
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty Release                                
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ubuntu.otenet.gr trusty-backports InRelease                         
Get:2 http://ubuntu.otenet.gr trusty-security InRelease [65,9 kB]              
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ubuntu.otenet.gr trusty Release.gpg                                 
Get:3 http://ubuntu.otenet.gr trusty-updates/main Sources [262 kB]             
Get:4 http://ubuntu.otenet.gr trusty-updates/restricted Sources [5352 B]       
Get:5 http://ubuntu.otenet.gr trusty-updates/universe Sources [151 kB]         
Get:6 http://ubuntu.otenet.gr trusty-updates/multiverse Sources [5946 B]       
Get:7 http://ubuntu.otenet.gr trusty-updates/main amd64 Packages [714 kB]      
Get:8 http://ubuntu.otenet.gr trusty-updates/restricted amd64 Packages [15,9 kB]
Get:9 http://ubuntu.otenet.gr trusty-updates/universe amd64 Packages [339 kB]  
Get:10 http://ubuntu.otenet.gr trusty-updates/multiverse amd64 Packages [13,2 kB]
Get:11 http://ubuntu.otenet.gr trusty-updates/main i386 Packages [692 kB]      
Get:12 http://ubuntu.otenet.gr trusty-updates/restricted i386 Packages [15,6 kB]
Get:13 http://ubuntu.otenet.gr trusty-updates/universe i386 Packages [340 kB]  
Get:14 http://ubuntu.otenet.gr trusty-updates/multiverse i386 Packages [13,6 kB]
Get:15 http://ubuntu.otenet.gr trusty-updates/main Translation-en [361 kB]     
Get:16 http://ubuntu.otenet.gr trusty-updates/multiverse Translation-en [7227 B]
Get:17 http://ubuntu.otenet.gr trusty-updates/restricted Translation-en [3699 B]
Get:18 http://ubuntu.otenet.gr trusty-updates/universe Translation-en [182 kB] 
Hit http://ubuntu.otenet.gr trusty-backports/main Sources                      
Hit http://ubuntu.otenet.gr trusty-backports/restricted Sources                
Hit http://ubuntu.otenet.gr trusty-backports/universe Sources                  
Hit http://ubuntu.otenet.gr trusty-backports/multiverse Sources                
Hit http://ubuntu.otenet.gr trusty-backports/main amd64 Packages               
Hit http://ubuntu.otenet.gr trusty-backports/restricted amd64 Packages         
Hit http://ubuntu.otenet.gr trusty-backports/universe amd64 Packages           
Hit http://ubuntu.otenet.gr trusty-backports/multiverse amd64 Packages         
Hit http://ubuntu.otenet.gr trusty-backports/main i386 Packages                
Hit http://ubuntu.otenet.gr trusty-backports/restricted i386 Packages          
Hit http://ubuntu.otenet.gr trusty-backports/universe i386 Packages            
Hit http://ubuntu.otenet.gr trusty-backports/multiverse i386 Packages          
Hit http://ubuntu.otenet.gr trusty-backports/main Translation-en               
Hit http://ubuntu.otenet.gr trusty-backports/multiverse Translation-en         
Hit http://ubuntu.otenet.gr trusty-backports/restricted Translation-en         
Hit http://ubuntu.otenet.gr trusty-backports/universe Translation-en           
Get:19 http://ubuntu.otenet.gr trusty-security/main Sources [106 kB]           
Get:20 http://ubuntu.otenet.gr trusty-security/restricted Sources [4035 B]     
Get:21 http://ubuntu.otenet.gr trusty-security/universe Sources [34,0 kB]      
Get:22 http://ubuntu.otenet.gr trusty-security/multiverse Sources [2750 B]     
Get:23 http://ubuntu.otenet.gr trusty-security/main amd64 Packages [431 kB]    
Get:24 http://ubuntu.otenet.gr trusty-security/restricted amd64 Packages [13,0 kB]
Get:25 http://ubuntu.otenet.gr trusty-security/universe amd64 Packages [125 kB]
Get:26 http://ubuntu.otenet.gr trusty-security/multiverse amd64 Packages [4991 B]
Get:27 http://ubuntu.otenet.gr trusty-security/main i386 Packages [404 kB]     
Get:28 http://ubuntu.otenet.gr trusty-security/restricted i386 Packages [12,7 kB]
Get:29 http://ubuntu.otenet.gr trusty-security/universe i386 Packages [125 kB] 
Get:30 http://ubuntu.otenet.gr trusty-security/multiverse i386 Packages [5175 B]
Hit http://ubuntu.otenet.gr trusty-security/main Translation-en                
Hit http://ubuntu.otenet.gr trusty-security/multiverse Translation-en          
Hit http://ubuntu.otenet.gr trusty-security/restricted Translation-en          
Hit http://ubuntu.otenet.gr trusty-security/universe Translation-en            
Hit http://ubuntu.otenet.gr trusty Release                                     
Hit http://ubuntu.otenet.gr trusty/main Sources                                
Hit http://ubuntu.otenet.gr trusty/restricted Sources                          
Hit http://ubuntu.otenet.gr trusty/universe Sources                            
Hit http://ubuntu.otenet.gr trusty/multiverse Sources                          
Hit http://ubuntu.otenet.gr trusty/main amd64 Packages                         
Hit http://ubuntu.otenet.gr trusty/restricted amd64 Packages                   
Hit http://ubuntu.otenet.gr trusty/universe amd64 Packages                     
Hit http://ubuntu.otenet.gr trusty/multiverse amd64 Packages                   
Hit http://ubuntu.otenet.gr trusty/main i386 Packages                          
Hit http://ubuntu.otenet.gr trusty/restricted i386 Packages                    
Hit http://ubuntu.otenet.gr trusty/universe i386 Packages                      
Hit http://ubuntu.otenet.gr trusty/multiverse i386 Packages                    
Hit http://ubuntu.otenet.gr trusty/main Translation-en                         
Hit http://ubuntu.otenet.gr trusty/multiverse Translation-en                   
Hit http://ubuntu.otenet.gr trusty/restricted Translation-en                   
Hit http://ubuntu.otenet.gr trusty/universe Translation-en                     
Ign http://ubuntu.otenet.gr trusty/main Translation-en_US                      
Ign http://ubuntu.otenet.gr trusty/multiverse Translation-en_US                
Ign http://ubuntu.otenet.gr trusty/restricted Translation-en_US                
Ign http://ubuntu.otenet.gr trusty/universe Translation-en_US                  
Fetched 4522 kB in 53s (85,0 kB/s)                                             
Reading package lists... Done

```
sudo apt-get upgrade:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
sudo apt-get dist-upgrade:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
:confused::confused:

---

### Post by Geoffrey_Arndt on 2016-03-11
Sometimes it's much easier to do a standard re-install than it is to go from an LTS to a 9 mth point realease two versions later.   Just asking for trouble UNLESS one is very experienced and knows Zactly what to do.

At this late point - - with Xenial coming out in April, it makes more sense just to install the most current beta of 16.04 and the online upgrade process for that will be seamless.

Anyway, just my preference, based on 100+ installs & upgrades since 2003 (not just Ubuntu).

---

### Post by jedi_knight2 on 2016-03-11
How can I get the beta release? Is it possible not to lose my files? But won't have the same outcome with the error message ''Could not calculate the upgrade''?

---

### Post by Geoffrey_Arndt on 2016-03-11
Re your reply . . . . "none of the above" assumptions are correct . . . _PROVIDED_ you backup or just do a plain copy/paste to a USB flash-stick or external hard drive.    

Now, . . . . . about getting the beta . . . .  [URL="http://cdimage.ubuntu.com/daily-live/current/"]http://cdimage.ubuntu.com/daily-live/current/
[/URL]

Edit:   an clean/fresh install will provide the same basic or core programs you had when you first installed 14.04 . . . so, those programs you've installed since the initial install, will need to be re-installed via the new package manager provided by 16.04.   For me, I can do that in less than 30" from the CLI or just a little longer from the gui.    Also, while 16.04 is relatively stable, it is still technically a beta . . . so, there might be a couple rough edges, but those will get smoothed out in the next 4-8 weeks . . . .

---

### Post by Bucky Ball on 2016-03-11
> **jedi_knight2 said:**
> How can I get the beta release? Is it possible not to lose my files? But won't have the same outcome with the error message ''Could not calculate the upgrade''?

Getting back to the original problem, when are you getting the 'Could not calculate upgrade' message as your output says:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Calculating upgrade... Done**
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I see no message about not being able to calculate upgrade. Looks like it is achieving that. Please let us know when this message appears.

---

### Post by jedi_knight2 on 2016-03-11
That's what I get now >.> <.< .
[IMG]http://i68.tinypic.com/2iixdy.png[/IMG]
Edit:
Here it is:
[IMG]http://i66.tinypic.com/2edo1l2.png[/IMG]

---

### Post by Bucky Ball on 2016-03-11
Ok. You're getting it when trying to upgrade. Well, that could be because of reasons already given. In your screenshot, the first error could be the cause if you are trying to upgrade to 16.04 LTS; in my opinion, not a good idea. Failing that, if you are attempting to upgrade to 14.10, the third reason may be the cause. 14.10 is EOL so the packages aren't supported by Canonical any longer (and the repos are moved).

---

### Post by mc4man on 2016-03-11
I'm sorta surprised you can still boot to the 14.04 install you tried to upgrade to 15.10. I had a 14.04 install here I didn't care about & it's now thoroughly destroyed by Software Updater > Upgrade to new(est) release. 
(the fact that Software Updater would even allow such an ill-fated action is a serious flaw..
So in your case not too sure it actually followed thru as your sources list is still on trusty not wily, ect. If your only ill effect is Software Updater & it's message then just use some other means to update packages when needed. Otherwise do a fresh install of 14.04 or 15.10 or 16.04

---

### Post by Bucky Ball on 2016-03-11
Yes, your install seems to be working fine. You had no error whatever from an update/upgrade and that is a good sign. What problems are you actually having with 14.04? Upgrading an LTS with five years support to an interim release with nine months support when the next LTS is a month away is probably not the greatest course of action.

If 14.04 LTS is working, why not stay there? That will upgrade directly to 16.04 LTS later, and both releases will be supported, unlike your current predicament (which can only be trouble and I wouldn't go there unless you have a decent chunk of time to waste on the pursuit).

---

### Post by jedi_knight2 on 2016-03-12
Yea I will wait till 16.04 LTS, I just wanted to show you the error message as you told me to do so. So I guess I am going to flag this as Solved.

---

