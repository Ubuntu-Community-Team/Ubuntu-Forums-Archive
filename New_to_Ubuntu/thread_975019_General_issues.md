---
title: "General issues"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by xXJaYXx on 2008-11-08
Hi everybody

So i'm totally green in this environment "Linux"

It seems that I cannot even install a single program, share a folder etc.
When trying to install "wine" through the terminal this just happens:

jay@JaY:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  msttcorefonts
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7506kB of archives.
After this operation, 55.8MB of additional disk space will be used.
Selecting previously deselected package wine.
(Reading database ... 101341 files and directories currently installed.)
Unpacking wine (from .../wine_1.0.1-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up wine (1.0.1-0ubuntu2) ...
 * Setting kernel variables (/etc/sysctl.conf)...                        [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-console-messages.conf)...  [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-network-security.conf)...  [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-process-security.conf)...  [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/30-tracker.conf)...           [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/wine.sysctl.conf)...          [ OK ] 

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
jay@JaY:~$ 

I can see that the program is installed, but - I get the feeling that it's not, because I cannot install Steam afterwords

jay@JaY:~/Desktop$ wine start SteamInstall.msi
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found


I have done so many google searches, but cannot find the answer I'm looking for. So this is my last try. Anybody who can help?

(I know this should work, because on my other machine it works just fine)

Thanks
John

---

### Post by Elfy on 2008-11-08
I think you need to do this first

```
winecfg
```

then you should be able to eithere double click or

```
wine SteamInstall.msi
```

or ```
wine thing.exe
```

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by xXJaYXx on 2008-11-08
Hi Forestpixie.

Thx for the advice
But unfurtunally that did not get me anywhere.

I suspect that there may be something wrong with my Ubuntu installation :(

---

### Post by Elfy on 2008-11-08
Never used wine myself other than looking at it and having a go ;)

What error do you get?

Did wincfg do it's thing - it has to be run before anything else - I do remember it taking a while to show on the desktop.

Where did you get from steam from - save me a search :) I'll have a look

---

### Post by LowSky on 2008-11-08
command to install steam goes like so

```
cd /file/path/to/steam.msi
```
```
wine steaminstall.msi
```

also make sure you use proper spelling and capitalization, linux isn't like windows, in linux "A" and "a" are two different things

---

### Post by ugm6hr on 2008-11-08
You should be able to just right-click the .msi file and use "Open with wine" - that's how I installed utorrent.exe

Of course - learning to use the command line is useful in the long run.

---

### Post by xXJaYXx on 2008-11-08
That helped thanks :)

But as you said, learning to use command lines is useful in the long run
I guess I was trying to hard - But think it is funny that it worked on my other computer through the terminal and not on this "primary" computer.

Well anyway thank you all for your help.

But I still feel that I have 10000 questions more :p

---

### Post by xXJaYXx on 2008-11-08
one last thing.
Anybody fermilure with Ubuntu runnig a tad slow ?
Feels like om back in the 80's - Everything hacking lagging etc.

---

### Post by ugm6hr on 2008-11-08
> **xXJaYXx said:**
> one last thing.
Anybody fermilure with Ubuntu runnig a tad slow ?
Feels like om back in the 80's - Everything hacking lagging etc.

Generally hardware dependent.

Ubuntu needs minimum 256MB RAM, but realistically 512MB for a speedy experience.

Additionally, Windows apps are not really designed for Ubuntu, so wine is not necessarily a good comparison.

---

### Post by xXJaYXx on 2008-11-08
Well
Have a AMD 3500+
3GB DDR2 PC3500
GeForce 8800 GT

So that should not be a problem :)
Proberbly me who screwed up something :P

---

### Post by Elfy on 2008-11-08
Ata guess I would suggest that ti coul;d be grpahic related - do you have the driver for your card installed - check in System Admin Menu - Hardware Drivers

---

