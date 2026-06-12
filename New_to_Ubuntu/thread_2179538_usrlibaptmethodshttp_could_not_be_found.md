---
title: "/usr/lib/apt/methods/http could not be found"
date: 2013-10-08
forum: New to Ubuntu
---

### Post by kristen2 on 2013-10-08
Hi,

I'm unable to install anything from the Ubuntu Software center and am also unable to run apt-get update because I'm receiving this error:
E: The method driver /usr/lib/apt/methods/http could not be found
How do I fix this?

---

### Post by kristen2 on 2013-10-08
I already did Google this problem, thank you... I think the solution probably varies between individuals and their individual computers. I didn't find a solution that helped me. I don't want to play around in terminal when I don't even know what I'm doing either.

I tried this,
```

(precise)kristenxoxox@localhost:~$ sudo apt-get install apt-transport-https
[sudo] password for kristenxoxox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-crypto python-lazr.restfulclient gir1.2-gconf-2.0 libcompizconfig0
  libgail18 python-gnome2 gir1.2-gtk-2.0 brasero-cdrkit gir1.2-unity-5.0
  apport-symptoms libgnomeui-common gir1.2-unique-3.0 mplayer-skins
  update-manager-core libunique-3.0-0 libart-2.0-2 python-wadllib
  libdecoration0 gir1.2-dbusmenu-glib-0.4 libbonoboui2-common libbonoboui2-0
  python-keyring python-pyorbit python-gconf apport ttf-lyx
  compiz-plugins-default python-lazr.uri libglibmm-2.4-1c2a
  gir1.2-dbusmenu-gtk-0.4 python-compizconfig libsigc++-2.0-0c2a libprotobuf7
  libgnomecanvas2-0 libdbusmenu-gtk4 gir1.2-dee-1.0 libgnomeui-0
  gir1.2-notify-0.7 python-problem-report python-launchpadlib
  libgnomecanvas2-common python-apport compiz-core apport-gtk python-keybinder
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libapt-pkg4.12
The following NEW packages will be installed:
  apt-transport-https
The following packages will be upgraded:
  libapt-pkg4.12
1 upgraded, 1 newly installed, 0 to remove and 17 not upgraded.
Need to get 960 kB of archives.
After this operation, 171 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libapt-pkg4.12 apt-transport-https
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libapt-pkg4.12 i386 0.8.16~exp12ubuntu10.12
  404  Not Found [IP: 91.189.92.177 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main apt-transport-https i386 0.8.16~exp12ubuntu10.12
  404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.12_0.8.16~exp12ubuntu10.12_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.12_0.8.16~exp12ubuntu10.12_i386.deb)  404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.16~exp12ubuntu10.12_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.16~exp12ubuntu10.12_i386.deb)  404  Not Found [IP: 91.189.92.177 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Please help. Help would be appreciated. Thank you!

---

### Post by DuckHook on 2013-10-08
It would help us to help you were you to provide the history, background and larger context of what you were trying to do. There are a number of items that are quite perplexing:

1. Why are you logged in to @localhost?
2. Did you activate root account by giving it a password?
3. Are you logged in as root right now? ...or to a recovery root shell?

4. Any idea what caused the apt breakage? Did it stop working after an upgrade? A power outage while updating?

Both pkgs you are trying to install should already be part of a default install. So, might be a corrupted apt database. Do:```
sudo apt-get clean
``````
sudo apt-get install -f
``````
sudo dpkg --configure -a
``````
sudo apt-get update
```If anything chokes along the way, please note chokepoint and post complete output back to this thread (please wrap output in *CODE* marks for easier reading).

---

### Post by kristen2 on 2013-10-10
Hi Duckhook,

Thank your for your answer. I don't know why the packages that should already be installed by default are not installed right now. I've had this computer for a couple of months, and I wasn't having this problem when I first started using it. My laptop is a chromebook, and I have Ubuntu 12.04 (Xfce) installed on it.
I don't know what I did exactly, but I might have deleted something in root that I shouldn't have, at some point. I haven't messed around with my system a lot because I don't know anything about it... but there was a time pretty recently that I was trying to install CUPS, and in trying to do that I deleted some root-protected... file or directory, I don't know. It could be related, but maybe not. I don't remember what it was that I deleted, so that won't really help you to help me. Sorry. Otherwise, I don't know what else could have caused the apt-breakage. I haven't performed or even attempted to perform any upgrades of any kind. So, yeah, I'm not sure.

[COLOR=#000000]**1. Why are you logged in to @localhost?**
[/COLOR]I don't know... because localhost is me, I guess? What's weird about that?
[COLOR=#000000]**2. Did you activate root account by giving it a password?**
[/COLOR]I don't think I've done that. I can log in as root using the sudo su command, though...
**[COLOR=#000000]3. Are you logged in as root right now? ...or to a recovery root shell?[/COLOR]**
I don't know what a recovery root shell is. I can log in as root, but it doesn't make a difference when I try to apt-get update and stuff.
How do I set a password for root? Maybe that would help
[COLOR=#000000]
Oh, and if I run those commands (the codes you posted), is there anything I should be warned about first? Like, will it do anything to applications and such that I currently have installed on my computer?
[/COLOR]

---

### Post by DuckHook on 2013-10-10
> **kristen2 said:**
> ...because localhost is me, I guess? What's weird about that?When you installed your system, it asked you to give your computer a name. Let's call that: computer_name. Your terminal identification should therefore tell you that you are kristenxoxox@computer_name. I am not knowledgeable enough to tell you off the top of my head what @localhost portends, but it is definitely not usual, and when diagnosing problems, it is these "not usuals" that raise flags and sometimes point us to where the problem is.> I don't know what a recovery root shell is.If you don't know what a recovery root shell is, then you are not logged in on one.> How do I set a password for root? Maybe that would helpYou do not need to do this and it would not help. You can do everything you need through sudo.> ...if I run those commands (the codes you posted), is there anything I should be warned about first? Like, will it do anything to applications and such that I currently have installed on my computer?These commands are designed to reset a corrupted apt-get database. They should not harm anything on your computer. HOWEVER, your instincts are sound and you should listen to them. Whenever you are unsure about anything, including advice that you receive on this forum, you should backup all of your important data so that, at worst, you will end up having to reinstall the OS and some apps, but no big catastrophe except a little wasted time.

Go ahead and backup everything before running the commands. Then run them and let us know how it goes.

It's getting late here and I'll be turning in for the night. Will look in on this thread again tomorrow.

---

### Post by varunendra on 2013-10-10
Perhaps it may help to take a look at the outputs of -
```
sudo apt-get update
cat /etc/apt/sources.list
grep -Rv '#' /etc/apt/sources.list.d
```

---

### Post by kristen2 on 2013-10-29
Hey,
I quit this problem, sorry, because I wasn't being able to fix it and I just felt done; I had to let it go. I still need it resolved, though, because there are some things I *need* to install but can't because of this error. Anything I try to install just fails.

I used Varun's commands and this is the output:
```
**(precise)kristenxoxox@localhost:~$ sudo apt-get update**
[sudo] password for kristenxoxox: 
E: The method driver /usr/lib/apt/methods/https could not be found.
**(precise)kristenxoxox@localhost:~$ cat /etc/apt/sources.list**
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
**(precise)kristenxoxox@localhost:~$ grep -Rv '#' /etc/apt/sources.list.d**
/etc/apt/sources.list.d/xfce-4.10.list:deb http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu precise main
/etc/apt/sources.list.d/xfce-4.10.list:deb-src http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu precise main
/etc/apt/sources.list.d/xfce-4.10.list.save:deb http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu precise main
/etc/apt/sources.list.d/xfce-4.10.list.save:deb-src http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/google-chrome.list.save:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/upubuntu-com-office-precise.list:deb http://ppa.launchpad.net/upubuntu-com/office/ubuntu precise main
/etc/apt/sources.list.d/upubuntu-com-office-precise.list:deb-src http://ppa.launchpad.net/upubuntu-com/office/ubuntu precise main
/etc/apt/sources.list.d/upubuntu-com-office-precise.list.save:deb http://ppa.launchpad.net/upubuntu-com/office/ubuntu precise main
/etc/apt/sources.list.d/upubuntu-com-office-precise.list.save:deb-src http://ppa.launchpad.net/upubuntu-com/office/ubuntu precise main

```

---

### Post by Bashing-om on 2013-10-29
kristen2; Hi !

You are wise to be cautious - When in doubt, see the manual:
```

man grep

``` You will find that the command string of concern is but a means to search within "sources.list.d" directory and output what sources are listed therein. 
To the situation at hand:  the error:
> 
E: The method driver /usr/lib/apt/methods/https could not be found.
 is cause for concern. That file should exist ! .. reference my output:
> 
sysop@1304mini:~$ ls -la /usr/lib/apt/methods/https
-rwxr-xr-x 1 root root 35640 Oct  3 10:28 /usr/lib/apt/methods/https
sysop@1304mini:~$

Show us your result:
```
ls -la /usr/lib/apt/methods/https
```

Presently I do not know, but I sure want to know ! To restore that file may prove interesting indeed.


[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by ikt on 2013-10-29
^ going on from above, assuming "/usr/lib/apt/methods/https" doesn't exist:

Boot into an ubuntu live cd (of the same version you have), open file manager, copy:

/usr/lib/apt/methods/https

into this folder on your computer:

/usr/lib/apt/methods/

pray to zeus.

---

### Post by kristen2 on 2013-10-29
Correct. "/usr/lib/apt/methods/https" doesn't exist; however, there is a "/user/lib/apt/methods/http". Should that be the same file or are both http and https distinctly different files? In other words, could I just rename "http" to "https"?

Booting into an ubuntu live cd and copying the https file sounds like a good idea but I don't know how to do that, and I don't think I have an Ubuntu live CD....?
Is there another way to restore the file?

---

### Post by Bashing-om on 2013-10-29
kristen2; Well,

It is possible that the file XXX/https and XXXX/http are one and the same, which begs the question what changed that file name ?
In any event lets see what is:
post back the output of:
```

ls -la /usr/lib/apt/methods/http

```
and let's see if it is a valid file.

[INDENT][INDENT]nothing lost by lookin'[/INDENT][/INDENT]

---

### Post by kristen2 on 2013-10-29
Thanks Bashing-om.  I have no idea what might have changed the file name, if that's the case.  I stay out of terminal as much as I can, and I don't think it could have been anything I've done.  I dunno

```

(precise)kristenxoxox@localhost:~$ ls -la /usr/lib/apt/methods/http
-rwxr-xr-x 1 root root 67640 Apr 18  2013 /usr/lib/apt/methods/http

```
valid file...

---

### Post by Bashing-om on 2013-10-29
kristen2; Nope, I looked at my output again .. and I also show "http" in addition to "https" !
my output:
> 
sysop@1304mini:~$ ls -la /usr/lib/apt/methods/
total 436
drwxr-xr-x 2 root root  4096 Oct 10 16:10 .
drwxr-xr-x 4 root root  4096 May 19 10:54 ..
lrwxrwxrwx 1 root root     4 Oct  3 10:25 bzip2 -> gzip
-rwxr-xr-x 1 root root 31440 Oct  3 10:28 cdrom
-rwxr-xr-x 1 root root 18880 Oct  3 10:28 copy
-rwxr-xr-x 1 root root 18872 Oct  3 10:28 file
-rwxr-xr-x 1 root root 56616 Oct  3 10:28 ftp
-rwxr-xr-x 1 root root 31440 Oct  3 10:28 gpgv
-rwxr-xr-x 1 root root 18952 Oct  3 10:28 gzip
[color=red]-rwxr-xr-x 1 root root 68928 Oct  3 10:28 http[/color]
[color=red]-rwxr-xr-x 1 root root 35640 Oct  3 10:28 https[/color]
lrwxrwxrwx 1 root root     4 Oct  3 10:25 lzma -> gzip
-rwxr-xr-x 1 root root 89696 Oct  3 10:28 mirror
-rwxr-xr-x 1 root root 27320 Oct  3 10:28 rred
-rwxr-xr-x 1 root root 27376 Oct  3 10:28 rsh
lrwxrwxrwx 1 root root     3 Oct  3 10:25 ssh -> rsh
lrwxrwxrwx 1 root root     4 Oct  3 10:25 xz -> gzip
sysop@1304mini:~$ 


I highly suggest we defer to ikt's esteemed advise and burn a liveDVD and copy that file back into place.
With the GUI application "nautilus" is a simple process to copy-paste between opened windows.

[INDENT][INDENT]you can do this
[/INDENT][/INDENT]

---

### Post by kristen2 on 2013-10-29
Oh, also my laptop is a Chromebook and has no CD or DVD drive.

Can't someone just send me an https file.....

---

### Post by Bashing-om on 2013-10-29
kristen2; well,
How about a USB thumb drive ?
Maybe able to provide that missing file .. show:
```

lsb_release -a
uname -a

```
Will see what can be done.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by kristen2 on 2013-10-29
Thanks.

```

(precise)kristenxoxox@localhost:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise


(precise)kristenxoxox@localhost:~$ uname -a
Linux localhost 3.4.0 #1 SMP Thu Sep 12 16:21:05 PDT 2013 i686 i686 i386 GNU/Linux

```

---

### Post by Bashing-om on 2013-10-29
kristen2; well,

I can not help with that file as I have all my boxes running 64 bit and none of them run that 3.4 kernel.
Perhaps others can offer an alternative (?)

Best course is still to download the appropriate .iso file and burn to some medium, and extract that https file. Besides, it is always a good idea to have a liveMedium around for a large number of reasons. This situation is but one case in point.

'tween a rock and a hard place is always tough,
[INDENT][INDENT]could be harder
[/INDENT][/INDENT]

---

### Post by bapoumba on 2013-10-29
> **Bashing-om said:**
> 
...
I can not help with that file as I have all my boxes running 64 bit and none of them run that 3.4 kernel.
Perhaps others can offer an alternative (?)
...

I have been following the thread. I'm still puzzled that there is no https in the sources.list or ppas. Quite strange. Could you please look at every ppa one by one and see if there is anything that the grep command would not have listed ?

---

### Post by varunendra on 2013-10-29
The contents in my sources.list and a couple of PPAs I have also do not contain any https, so I guess that is normal. Although the error made me suspicious of a possible mistyped entry in any of the lines, that's why I tried to search the possibly corrupt line with grep. But everything that came up looks normal to me.

Anyway, back to ikt's solution - the entire contents (except links) of /usr/lib/apt/methods folder from 12.04.2 34bit Live CD is attached in the zip file. Shouldn't hurt trying.

[LIST]
[*]Download the attached .zip file to your desktop > Right-click > Extract here.
[*]Open a terminal and do -[/LIST]
```
sudo chown root:root Desktop/methods/*
sudo chmod +x Desktop/methods/*
sudo cp Desktop/methods/https /usr/lib/apt/methods/
```

Then try -
```
sudo apt-get update
```
Fixed?

---

### Post by bapoumba on 2013-10-30
> **varunendra said:**
> The contents in my sources.list and a couple of PPAs I have also do not contain any https, so I guess that is normal. Although the error made me suspicious of a possible mistyped entry in any of the lines, that's why I tried to search the possibly corrupt line with grep. But everything that came up looks normal to me.

Hello varunendra :)
When I said strange, it was regarding the error, not having https or not in the repos. The output looks normal to me too, that is what puzzles me.

---

### Post by varunendra on 2013-10-30
> **bapoumba said:**
> Hello varunendra :)
When I said strange, it was regarding the error, not having https or not in the repos. The output looks normal to me too, that is what puzzles me.

Hello bapoumba :)

Yeah, I think I now understand your comment better, although I was certainly not knitpicking it (can I dare so?) :P

From the grep command, I was expecting to see some "un-noticible" erroneous instance of "https" (like an extra visible or non-visible character before or after it). But it couldn't find such any line and now the OP doesn't even have the method file at all.

Having no firm background knowledge about it, it seems the apt manager reads all the method files regardless of whether they are needed or not by the sources.list/ppa files. But yeah, can't deny a chance of some problematic entry probably left out of the grep search.

As a side note, the contents of the "sources.list" file are in a form that I had never seen before (no comments, no extra lines for multiverse repos) ! Although technically it is correct. Maybe it is a "Chromebook" thing to keep it short and simple.

I have seen such a case only once before, where the OP's method file somehow got corrupt (don't remember if it was needed or not by their sources/ppa files). But here the entire file is missing!

---

### Post by bapoumba on 2013-10-30
> **varunendra said:**
> Hello bapoumba :)

Yeah, I think I now understand your comment better, although I was certainly not knitpicking it (can I dare so?) :P
Eheh, English is not my first language, so I probably was not that clear either.
> **varunendra said:**
> 
From the grep command, I was expecting to see some "un-noticible" erroneous instance of "https" (like an extra visible or non-visible character before or after it). But it couldn't find such any line and now the OP doesn't even have the method file at all.

Having no firm background knowledge about it, it seems the apt manager reads all the method files regardless of whether they are needed or not by the sources.list/ppa files. But yeah, can't deny a chance of some problematic entry probably left out of the grep search.

As a side note, the contents of the "sources.list" file are in a form that I had never seen before (no comments, no extra lines for multiverse repos) ! Although technically it is correct. Maybe it is a "Chromebook" thing to keep it short and simple.

I have seen such a case only once before, where the OP's method file somehow got corrupt (don't remember if it was needed or not by their sources/ppa files). But here the entire file is missing!
I've read that //: or some other combination in the url can also trigger these errors. I've looked quite carefully at the outputs and could not get anything along these lines.
I agree that the sources.list is not of the conventional form. I hope the OP did not miss some of the outputs.

---

### Post by kristen2 on 2013-12-18
You are all so amazing and smart and I wish I didn't have to keep coming back asking for help.

I'm having trouble with this again. My system crashed yesterday and my computer reset itself so I had to reinstall Ubuntu (It's really, really sad not having backup! There goes my life). I'm using a chromebook so I had to download Crouton ([https://github.com/dnschneid/crouton](https://github.com/dnschneid/crouton)) to install Ubuntu, and it sucks a little bit. I get a lot of problems. Anyway, I don't know if when I installed this last night the https file was missing, or if suddenly my system is being stubborn and refusing to do things now but not before because it's missing, but I need an https file. 

```
(precise)laptop@localhost:~$ lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise
(precise)laptop@localhost:~$ uname -a
Linux localhost 3.4.0 #1 SMP Thu Dec 5 23:25:19 PST 2013 x86_64 x86_64 x86_64 GNU/Linux

```

That's the information I think I need to provide. Can someone attach an https file or methods zip used by this system, for me, please?? Again, please! Thank you.
I feel annoying, I'm so sorry.

---

### Post by varunendra on 2013-12-19
> **kristen2 said:**
> ..and I wish I didn't have to keep coming back asking for help....
You want us to go out of business ? :P *(just kidding)*

I haven't yet upgraded to 12.04.3 (still using 12.04.1), but I believe the same attachment and obviously the same method as in post #19 should work again. Try it and let us know if it does or doesn't. :)

---

