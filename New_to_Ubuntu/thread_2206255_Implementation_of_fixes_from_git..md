---
title: "Implementation of fixes from git."
date: 2014-02-18
forum: New to Ubuntu
---

### Post by manoila-alex on 2014-02-18
Hello,

I probably posted this in the wrong place ... and i apologize in advance. 

I am having some trouble with Muon Software Center (not all results are shown when i search the repos). So my googling began:

- i 1st found that it's a known bug and that it has a fix : [https://projects.kde.org/projects/extragear/sysadmin/muon/repository/revisions/d2a2731615d41375bd82c6f6c244e619aeddb292/entry/installer/ApplicationWindow.cpp](https://projects.kde.org/projects/extragear/sysadmin/muon/repository/revisions/d2a2731615d41375bd82c6f6c244e619aeddb292/entry/installer/ApplicationWindow.cpp)

- next i downloaded the git clone via command line to my home folder

- now i was unsuccesfull in applying the fix because there is no make file, compiling instructions or instructions on installing

I've had this problem a few times now with fixes from github... To summerize : i would like to know how i can implement fixes from github and th example i am using is this fix for Muon Software Cemter.

In case it matters i am using Kubuntu 13.10 Desktop i386
Things i've installed (that i think are relevant): g++, git

I also have to mention that my programming experience is limited, but not absent.

Thank you in advance!

---

### Post by mc4man on 2014-02-18
I don't use kubuntu but that git commit appears to be almost 2 yrs old & was for muon 1.4, you have 2.0.65+git20131008 in 13.10
You might want to search/file a more recent bug report and or ck. in kubuntu forums.

---

### Post by CitadelUniversal on 2014-02-18
If you are using Kubuntu use  the following ppa's - ppa:kubuntu-ppa/ppa & also ppa:kubuntu-ppa/backports  - it sounds like you may have not got those two ppa's on your system - Then do the usual system update.........

---

### Post by manoila-alex on 2014-02-18
Thank you for the quick responses. I am aware of the fact that the Muon fix thread is kinda old, but i am experiencing the exact issues described there. In Muon i have all the repositories set (the PPA's mentioned are also present) but my search results only show plasma workspace widgets. I can install any software through apt-get command so it's not a question of broken repository entries. "sudo apt-get update" restarting and reopening Muon did nothing (i had a similar problem before [just that i had no results at all, unlike now when i get widgets] and "apt-get update" with restart fixed it like a charm (i was using kubuntu 11.04 back then). 

The problem does not interfere with my work, but it's still frustrating (as much as i like command line, sometimes i want to search for a keyword and browse results). Don't know if it's relevant, but i can browse categories and all apps show, but when i search for an app that is present for sure in my repos and i can see it under utilities category ( furiousisomount for example) shows no results whatsoever. "sudo apt-get install furiousisomount" installed the app no problem.

Is there a way i can get Muon replaced with Ubuntu Software Center or some other software manager while keeping the Kubuntu repos ? (i'm guessing that ubuntu repos don't have widgets and/or KDE specific apps) And would this solve my problem or is something written wrong in some repository list somewhere on my system? 

I just did a system restore (not actually a restore, but i always make an image of the /root and /boot partitions of fresh installs and i restored them) leaving my /home partition intact but that had no positive results. I will try now to restore all 3 images (i have fresh /home image) to see what results that gives, but it's not really a solution cuz i have my old /home dir from the previous install, but still i will be closer to identifying the problem and i can reinstall all software i used and just copy the files i need, but it will be time consuming.

Well, i'm off to doing that. Any suggestions or ideas i've not thought about are more than welcome - anyway if that doesn't work i'll restore the old 11.04 images so i can keep working and gunna give 13.10 a try in the weekend when i have more time.

Thanks for your replies - u are really helpfull to the ubuntu community and ur compelling me to donate to UBUNTU due to the forum/support speed and AWESOMENESS. TY UBUNTUFORUMS. TY LINUX COMMUNITY AND THANK YOU, THE USERS THAT MAKE IT SO GREAT.

(when/if i find a solution to this i will post it, i will also post all the steps taken before finding the solution)

---

### Post by manoila-alex on 2014-02-18
PROBLEM FIXED - there was something corrupted in my /home partition - restoring that to the "clean" one fixed the problem

---

