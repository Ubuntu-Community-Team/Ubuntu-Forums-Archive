---
title: "Wine cannot install due to broken packages?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by sharrakor on 2008-08-13
So I've been trying to install wine. I followed the instructions here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

The problem is that after running the last command, and clicking the link it gave me, it asks if i want to update. I click yes. Then it comes up with the error: "Can not install "wine" (E:Unable to correct problems, you have held broken packages.)"

What do I do to correct this? I'm running off a Live CD and completely new to Ubuntu. Hoping to get wine running before my plane leaves later today.

Thanks

EDIT: By the way, the hard drive is broken on that computer. I do have a USB flash drive in it though.

---

### Post by ggaaron on 2008-08-13
Isn't wine in normal repositories?

---

### Post by sharrakor on 2008-08-13
Wish I knew what you meant, but if you are asking if it is included in the Live CD, then no, it isn't. Just downloaded my Live CD this morning.

---

### Post by Blue_Lander on 2008-08-13
Yeah, ggaaron is right, Wine is in the normal repositories (for at least the last few versions of Ubuntu anyways). You should be able to open your Synaptic Package Manager by going to System->Administration->Synaptic Package Manager. 

Just search for Wine, check the box and hit apply!

---

### Post by ggaaron on 2008-08-13
I mean that you don't need to do any additional steps to get wine. Restart LiveCD to get clean environment and run synaptic (in GNOME it's in system menu or something), search for wine and install. No need to add additional repositories.

---

### Post by sharrakor on 2008-08-13
Sweet, thanks guys. By the way, I've heard good and bad things about Wine. Is it much slower than if the application was running under normal windows xp? What are its limitations?

Also, how can I access the place it installs programs? It says it installed to C:\, but that can't be because I don't have a hard drive, and my flash drive is not labeled as a letter under Ubuntu (and I couldn't find the files on it).

Sorry for such noob questions.

EDIT: Ok, I managed to find Applications > Wine. But I still don't know where the program files folder is... it isn't one of the options it gives.

---

### Post by ggaaron on 2008-08-13
> **sharrakor said:**
> Sweet, thanks guys. By the way, I've heard good and bad things about Wine. Is it much slower than if the application was running under normal windows xp? What are its limitations?

Also, how can I access the place it installs programs? It says it installed to C:\, but that can't be because I don't have a hard drive, and my flash drive is not labeled as a letter under Ubuntu (and I couldn't find the files on it).

Sorry for such noob questions.

I've heard it is faster for some applications=) It depends on application, on this site [http://appdb.winehq.org/](http://appdb.winehq.org/) you can search for your application and see how good does it do.

Wine installs programs in ~/.wine/, where ~ is your home folder (or livecd home folder). Files with leading dot are hidden so to access this dir you have to run nautilus (file manager) and add to path line '/.wine/'. There will be drive_c or something folder and it will be your wine c: drive.

GNU doesn't use letter labeled drives. Look in /media dir - there are auto mounted drives. Or you can hotplug it to running system and a window should pop-up with open option.

LiveCD doesn't use your drive - it uses virtual drive in memory.

And don't be sorry - this is the place to ask such questions=)

---

### Post by sharrakor on 2008-08-13
Thanks, that worked as well. So I ran the application under wine, but it didn't come up with anything. Any ideas?

---

### Post by Thelasko on 2008-08-13
Wine can be tricky.  Most questions about it will be answered on [this page.]("http://ubuntuforums.org/showthread.php?t=497332")  If you have any more questions (please specify the program you are trying to run) let us, or the people in the wine section of the boards know.

---

### Post by ggaaron on 2008-08-13
You mean that the application didn't work? (No window or something?) To see the backtrace or anything that could lead to a resolution you'd need to run wine from terminal like gnome-terminal. Command would be like 'wine ~/.wine/drive_c/something else/app.exe'. You can use tab to auto complete path you are writing.

---

### Post by sharrakor on 2008-08-13
Fisrt off I would read that link (and do appriciate it!) but I don't have the time before I leave, I'm tending to last minuite things and checking back on the comp once in a while. So I guess I will just get it to work when I come back and deal without for now.

Ggaar, It had no window. That command said LIbrary MFC42.DLL was not found. It is Multiplicty 1.01 by the way.

And thanks for that Tab info. That will make things a lot less painful.

---

### Post by hypoluxa68 on 2008-08-13
Hi guys. I also am having a wine problem and maybe you can help me. i have the kubuntu 8.04 live cd and i'm trying to get things working before a full install. my problem is that wine shows up as being installed in adept but it will not open any programs.

i have tried with simcity socities so far and that is really all. my brother told me it was a simple as choosing "open with" and selecting wine. that is not an option when i right click.

any help is greatly appreciated.

thanks in advance.

---

### Post by ggaaron on 2008-08-13
I don't think this will do. It seems that this application is designed for Microsoft Windows and it won't work on systems with other architecture (as GNU that you are trying to use this application on), you should find application for Unix-like systems that does this job.

---

### Post by sharrakor on 2008-08-13
Ok, I see. How can I tell, in the future, what can and cannot work?

---

### Post by ggaaron on 2008-08-13
> **hypoluxa68 said:**
> Hi guys. I also am having a wine problem and maybe you can help me. i have the kubuntu 8.04 live cd and i'm trying to get things working before a full install. my problem is that wine shows up as being installed in adept but it will not open any programs.

i have tried with simcity socities so far and that is really all. my brother told me it was a simple as choosing "open with" and selecting wine. that is not an option when i right click.

any help is greatly appreciated.

thanks in advance.

You won't do this from LiveCD if you don't have LOTS of ram... Everything is written to ram on LiveCD - installation and other things... But to run something - either use command line, or as your brother told you use open with and write manually wine in the input line. If wine won't be enough then /usr/bin/wine should work.

---

### Post by hypoluxa68 on 2008-08-13
i was under the assumption that wine was used to run windows based programs. will none of my games made for windows run on linux? 

i am a complete newbie to linux and would like to be able to make it my primary os but this will greatly influence my decision. my new laptop came with vista :( preinstalled and i've tried xp but i have driver conflicts that cannot be resolved.

---

### Post by ggaaron on 2008-08-13
> **sharrakor said:**
> Ok, I see. How can I tell, in the future, what can and cannot work?

The features of this application seem to be integrated with Microsoft Windows, you should remember that GNU+Linux is very different in architecture and while wine can act as a compatibility layer it can't do anything. Programs that are used to control Microsoft Windows won't control GNU+Linux. So wine can run Firefox, OpenOffice but probably won't be able to run applications that control monitor settings, hardware drivers and such.

For drivers there are some hacks to make them work, but it is not wine.

---

### Post by ggaaron on 2008-08-13
> **hypoluxa68 said:**
> i was under the assumption that wine was used to run windows based programs. will none of my games made for windows run on linux? 

i am a complete newbie to linux and would like to be able to make it my primary os but this will greatly influence my decision. my new laptop came with vista :( preinstalled and i've tried xp but i have driver conflicts that cannot be resolved.

Games are all OK. Not all work, but because wine is not perfect, not because it just can't do this and probably never will. If you want to use games check them on appdb, if they won't work under wine try cedega - it is a proprietary port of wine made for games.

---

### Post by bodhi.zazen on 2008-08-13
> **hypoluxa68 said:**
> i was under the assumption that wine was used to run windows based programs. will none of my games made for windows run on linux? 

i am a complete newbie to linux and would like to be able to make it my primary os but this will greatly influence my decision. my new laptop came with vista :( preinstalled and i've tried xp but i have driver conflicts that cannot be resolved.

In general you need to look to wine HQ for how to run games on wine. It takes some work and technical skills to get them going.

You look up your game in the application data base :

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by hypoluxa68 on 2008-08-13
I will try it out again and look into cedega.

Thanks for all your help :)

---

### Post by sharrakor on 2008-08-13
Got it, thanks guys.

---

### Post by Thelasko on 2008-08-13
[Wikipedia for Multiplicity (software)]("http://en.wikipedia.org/wiki/Multiplicity_(software)")
> Alternatives

    * Synergy — A Free software option that allows users to use a single keyboard and mouse to control multiple computers over TCP/IP. It is multiplatform (Supporting Windows, linux, and others), and supports text copy and paste.

    * Any remote desktop software that runs on the X Window System, together with a suitable window manager, can achieve the same effect, though not as efficiently. This approach does not require the use of multiple displays, but Xinerama can be used if multiple displays are desired, if at least one of the machines is capable of connecting to multiple displays at the same time. However, the fact that this approach works by actually transporting the display output from the other machine(s) to the primary machine could make it too slow for demanding apps such as video/audio apps.


---

### Post by hypoluxa68 on 2008-08-13
back again. 

tried some other programs and i get an error message that "the package 'wine' could not be found". i know its installed because it shows up in the program manager list.

please help. thanks.

---

### Post by ggaaron on 2008-08-13
I don't have GNOME so I can't test, but in open with dialog there must be some use other application or search for application and then search for '/usr/bin/wine'

---

### Post by Thelasko on 2008-08-13
open the terminal and type:
```
winecfg
```

---

