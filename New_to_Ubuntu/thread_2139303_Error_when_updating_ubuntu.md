---
title: "Error when updating ubuntu"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by Keshav2050 on 2013-04-26
After using sudo apt-get update I'm getting warning and error as

```
W: Failed to fetch http://dl.google.com/linux/talk/talkplugin/deb/dists/stable/main/binary-i386/Packages  404  Not Found [IP: 74.125.236.194 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.



```

Recently I tried to install google talk plugin to use in empathy, but it is able to recognize online google accounts but I'm not able to select any other option other than chat like audio call video call chat etc.
Can anyone please help with the issues.

---

### Post by fantab on 2013-04-26
"Failed to fetch [http://dl.google.com/linux/talk/talkplugin/deb/dists/stable/main/binary-i386/Packages](http://dl.google.com/linux/talk/talkplugin/deb/dists/stable/main/binary-i386/Packages)  404  Not Found [IP: 74.125.236.194 80]"

That link is not working. Hence the Error. You should check if the address is correct or you will have to either find a working link to the target, or delete that in 'sources.list'.
And this is your 'talkplugin' ppa I guess.

Use:

gksudo gedit /etc/apt/sources.list

... to edit sources.list

---

### Post by Keshav2050 on 2013-04-26
Thanks for the reply, the list in my 'sources.list' is:

```

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)]/ precise main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://in.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ quantal main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ quantal-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://in.archive.ubuntu.com/ubuntu/ quantal universe
deb http://in.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ quantal-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://in.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ quantal-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main
# deb http://dl.google.com/linux/deb/ testing non-free

```

I'm not able to find the link, can you please tell me what I should do.

---

### Post by Bashing-om on 2013-04-26
Keshav2050; Hi !

See if it is in the sources.list.d directory
```
 ls -la /etc/apt/sources.list.d 
```[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by Keshav2050 on 2013-04-26
in 'sources.lists.d' I got

```

total 180
drwxr-xr-x 2 root root 4096 Apr 26 21:23 .
drwxr-xr-x 6 root root 4096 Apr  9 22:05 ..
-rw-r--r-- 1 root root  204 Apr 26 20:45 apt-fast-stable-precise.list
-rw-r--r-- 1 root root  134 Apr  2 22:59 apt-fast-stable-precise.list.distUpgrade
-rw-r--r-- 1 root root  204 Apr 26 20:45 apt-fast-stable-precise.list.save
-rw-r--r-- 1 root root  204 Apr 26 20:45 atareao-atareao-precise.list
-rw-r--r-- 1 root root  134 Apr  2 22:59 atareao-atareao-precise.list.distUpgrade
-rw-r--r-- 1 root root  204 Apr 26 20:45 atareao-atareao-precise.list.save
-rw-r--r-- 1 root root  204 Apr 26 20:45 deluge-team-ppa-precise.list
-rw-r--r-- 1 root root  134 Apr  2 22:59 deluge-team-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  204 Apr 26 20:45 deluge-team-ppa-precise.list.save
-rw-r--r-- 1 root root  232 Apr 26 20:45 fossfreedom-rhythmbox-plugins-precise.list
-rw-r--r-- 1 root root  162 Apr  2 22:59 fossfreedom-rhythmbox-plugins-precise.list.distUpgrade
-rw-r--r-- 1 root root  232 Apr 26 20:45 fossfreedom-rhythmbox-plugins-precise.list.save
-rw-r--r-- 1 root root  176 Apr 26 20:45 google-chrome.list
-rw-r--r-- 1 root root  176 Apr  2 22:59 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  176 Apr 26 20:45 google-chrome.list.save
-rw-r--r-- 1 root root  177 Apr 26 21:19 google.list
-rw-r--r-- 1 root root   64 Apr 26 20:45 google_list.list
-rw-r--r-- 1 root root   64 Apr 26 20:45 google_list.list.save
-rw-r--r-- 1 root root  118 Apr 26 20:45 google.list.save
-rw-r--r-- 1 root root  180 Apr 26 21:23 google-talkplugin.list
-rw-r--r-- 1 root root  238 Apr 26 20:45 indicator-multiload-stable-daily-precise.list
-rw-r--r-- 1 root root  168 Apr  2 22:59 indicator-multiload-stable-daily-precise.list.distUpgrade
-rw-r--r-- 1 root root  238 Apr 26 20:45 indicator-multiload-stable-daily-precise.list.save
-rw-r--r-- 1 root root  218 Apr 26 20:45 jonoomph-openshot-edge-precise.list
-rw-r--r-- 1 root root  148 Apr  2 22:59 jonoomph-openshot-edge-precise.list.distUpgrade
-rw-r--r-- 1 root root  218 Apr 26 20:45 jonoomph-openshot-edge-precise.list.save
-rw-r--r-- 1 root root  318 Apr 26 20:45 medibuntu.list
-rw-r--r-- 1 root root  285 Apr  2 22:59 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root  318 Apr 26 20:45 medibuntu.list.save
-rw-r--r-- 1 root root  214 Apr 26 20:45 scopes-packagers-ppa-precise.list
-rw-r--r-- 1 root root  144 Apr  2 22:59 scopes-packagers-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  214 Apr 26 20:45 scopes-packagers-ppa-precise.list.save
-rw-r--r-- 1 root root  200 Apr 26 20:45 team-xbmc-ppa-precise.list
-rw-r--r-- 1 root root  130 Apr  2 22:59 team-xbmc-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  200 Apr 26 20:45 team-xbmc-ppa-precise.list.save
-rw-r--r-- 1 root root  150 Apr 26 20:45 ubuntu-x-swat-x-updates-quantal.list
-rw-r--r-- 1 root root  150 Apr 26 20:45 ubuntu-x-swat-x-updates-quantal.list.save
-rw-r--r-- 1 root root  113 Apr 26 20:45 virtualbox.list
-rw-r--r-- 1 root root   78 Apr  2 22:59 virtualbox.list.distUpgrade
-rw-r--r-- 1 root root  113 Apr 26 20:45 virtualbox.list.save
-rw-r--r-- 1 root root  224 Apr 26 20:45 webupd8team-y-ppa-manager-precise.list
-rw-r--r-- 1 root root  154 Apr  2 22:59 webupd8team-y-ppa-manager-precise.list.distUpgrade
-rw-r--r-- 1 root root  224 Apr 26 20:45 webupd8team-y-ppa-manager-precise.list.save



```

Should I remove or change anything, or is it alright?

---

### Post by Bashing-om on 2013-04-27
Keshav2050;

Well, we know we have this error:
> "Failed to fetch [http://dl.google.com/linux/talk/talk...-i386/Packages]("http://dl.google.com/linux/talk/talkplugin/deb/dists/stable/main/binary-i386/Packages")  404  Not Found [IP: 74.125.236.194 80]"
that is not generated from /etc/apt/sources.list; which means it must be generated from within the sources.list.d.
The more likely source is:
> -rw-r--r-- 1 root root  180 Apr 26 21:23 google-talkplugin.list
So, what is contained in this file ?
```
cat /etc/apt/sources.list.d/ google-talkplugin.list
```
Then perhaps move that file out of the update directory path, to some place safe that maybe at a later time restore it ?
Then run the "update and upgrade" commands again for results.[INDENT=2]
just my thoughts

[/INDENT]

---

### Post by Keshav2050 on 2013-04-28
Thanks for replying

I pasted the command as 

cat /etc/apt/sources.list.d/ google-talkplugin.list
I got the output as:

cat: /etc/apt/sources.list.d/: Is a directory
cat: google-talkplugin.list: No such file or directory



I actually don't know what I did is right or wrong just to be sure I removed the space between '/' and 'google-talkplugin.list' as


cat /etc/apt/sources.list.d/google-talkplugin.list
and I got the output as:

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

Can I know what should I do

---

### Post by Bashing-om on 2013-04-28
Keshav2050;

My bad as  /etc/apt/sources.list.d/: Is indeed a directory. My mind must have been off in left field !

A simpler method to de-source that ppa is from software sources -> other and simply uncheck the related box for the ppa.
[INDENT=2]
I hope this helps

[/INDENT]

---

### Post by Keshav2050 on 2013-04-28
This time for sudo apt-get update I got the output as:

**Reading package lists... Done**
**W: Duplicate sources.list entry [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages)**
**W: Duplicate sources.list entry [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages)**
**W: Duplicate sources.list entry [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages)**
[B]W: You may want to run apt-get update to correct these problems



[/B]As in the first post I doubt that the talk plugin is working, though it once worked but I don't know what changes I might have done

---

### Post by Bashing-om on 2013-04-28
Keshav2050;

That last is an advisory of the get file is duplicated. Look in both /etc/sources.list and /etc/sources.list.d 's directory for double entries.
Might be easier for you to look in the GUI Software sources as well as Software Sources -> other software.
[INDENT=2]
hth

[/INDENT]

---

### Post by Keshav2050 on 2013-04-29
Thanks I think the problem's solved. Actually the same ppa was marked 4 times, after removing 3 of them there were no errors or warnings. And chat option was also working after I removed and again added my account, I wasn't able to add contacts but after removing and adding the same account it worked fine, thank you for your help.

---

### Post by Bashing-om on 2013-04-29
Keshav2050;

Good things do come true ! Your efforts proved well worth while.

Pleased that there is resolution.[INDENT=2]
Happy 'buntu'n
[/INDENT]

---

