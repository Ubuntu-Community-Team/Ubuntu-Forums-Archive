---
title: "[64-bit] Install AVG free and pro anti-virus for Ubuntu 64-bit"
date: 2007-11-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2007-11-25
**Tested:** Ubuntu 7.10 &#8226; 8.04   64 bit - Gnome

This guide show you how to install AVG Professional Edition for Ubuntu 64-bit.

1.  F.A.Q. - Please read - Important
2. Guide - AVG Professional Edition for Ubuntu 64-bit
3. Guide - AVG Free Version for Ubuntu 64-bit
4. Links


**[size=5]1. - F.A.Q.[/size]**

Q: **Are viruses, trojans and malware a threat to a linux system as in Windows?**

A: No, there's a very few viruses to linux and the few are not out in the wild. The way a Linux/unix is build up makes it difficult to do any serious damage to the system, in fact I've never heard from people who got their Linux/unix system infected.

Q: **So why install an anti-virus application/program?**

A: For an ordinary Linux Home user with only one OS system their's no need for Anti-virus, but people who's running network, server or dual booting with win OS this tool can be very handy to scan for virus.

Q: **I'm a home user only running Linux do I need it?**

A: No, a firewall is way better as protection in that case.


_Please also read;_ [[color=red] Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812) and [[color=red] Are firestarter and clamav really necessary ??[/color]](http://ubuntuforums.org/showthread.php?t=131616)



**[size=5]2. AVG Professional Edition for Ubuntu 64-bit[/size]**

**Before Installation**

First you need some tool to edit/build .deb packages. To the terminal;

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential dpkg-dev fakeroot
```


**Installation**

Download avg75lms-r49-a1124.i386.deb and avggui-1.0-4.i386.deb from [here](http://www.grisoft.com/doc/downloads/us/crp/0?prd=avl) to your Desktop.

Fire up the terminal;

```
cd ~/Desktop
mkdir avg75ms
dpkg-deb --extract avg75lms-r49-a1124.i386.deb avg75ms
dpkg-deb --control avg75lms-r49-a1124.i386.deb avg75ms/DEBIAN
nano avg75ms/DEBIAN/control
```

Under **Architecture:** change i386 to amd64

Save [ctrl]+[o]
Exit [ctrl]+[x]

Then;

```
dpkg --build avg75ms
sudo dpkg -i avg75ms.deb
```

If it fails - Double click the newly made .deb package.

```
sudo avgscan -register
```
Insert your registration code.

Now to the AVG Gui;
```
mkdir avggui 
dpkg-deb --extract avggui-1.0-4.i386.deb avggui
dpkg-deb --control avggui-1.0-4.i386.deb avggui/DEBIAN
nano avggui/DEBIAN/control
```

Under **Architecture:** change i386 to amd64

Save [ctrl]+[o]
Exit [ctrl]+[x]

Then;

```
dpkg --build avggui
sudo dpkg -i avggui.deb
sudo nano /usr/share/applications/avggui.desktop
```

Change: **Exec=avggui** to **Exec=gksudo avggui**
Change: **Categories=GNOME;KDE;Application;Utility;** to **Categories=GNOME;KDE;Application;System;**

Save [ctrl]+[o]
Exit [ctrl]+[x]

AVG is now ready to be used.
You can start it by **Applications** tab ---> **System Tools** ---> **AVG for Linux Workstation**



**[size=5]3. AVG Free Version for Ubuntu 64-bit[/size]**

**Before Installation**

First you need some tool to edit/build .deb packages. To the terminal;

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential dpkg-dev fakeroot
```


**Installation**

Download the .deb file [here](http://free.grisoft.com/doc/5390/us/frt/0?prd=afl) to your Desktop.

Fire up the terminal;

```
cd ~/Desktop
mkdir free-avg
dpkg-deb --extract avg75fld-r49-a1130.i386.deb free-avg
dpkg-deb --control avg75fld-r49-a1130.i386.deb free-avg/DEBIAN
nano free-avg/DEBIAN/control
```

Under Architecture: change i386 to amd64

Save [ctrl]+[o]
Exit [ctrl]+[x]

```
dpkg --build free-avg
sudo dpkg -i free-avg.deb
sudo nano /usr/share/applications/avggui.desktop
```

Change: **Exec=avggui** to **Exec=gksudo avggui**
Change: **Categories=GNOME;KDE;Application;Utility;** to **Categories=GNOME;KDE;Application;System;**

Save [ctrl]+[o]
Exit [ctrl]+[x]

AVG is now ready to be used.
You can start it by Applications tab ---> System Tools ---> AVG for Linux Workstation



**[size=5]4. Links[/size]**

[ F-Prot (anti-virus) for Ubuntu 64-bit](http://ubuntuforums.org/showthread.php?p=3840826)
[Build the  latest of Pidgin + Plugins](http://ubuntuforums.org/showthread.php?p=4072317)
[Build the latest of Audacious](http://ubuntuforums.org/showthread.php?p=4072585)

---

### Post by bodhi.zazen on 2007-11-25
AI : As always it looks good to me. I really like the way you addressed security FAQ.

I can not test it out as i do not have the hardware :(

two small suggestions :

1. I would spell out windows here :

Q: So why install an anti-virus application/program?

A: For an ordinary Linux Home user with only one OS system their's no need for Anti-virus, but people who's running *a mixed*network, server or dual booting with *Windows* this tool can be very handy to scan for virus.


2. Nano is a fine editor :) You *might* want to consider advising gedit.

Otherwise, what needs be done to approve it ?

---

### Post by be4truth on 2007-11-26
I have used earlier the free version on Windows machine but found after one year of usage that AVG free doesn't catch quite a number of trojans. I don't know about the professional version.

---

### Post by Perfect Storm on 2007-11-26
Guide updated - Now also containing the free version.

---

### Post by pedro_cesar on 2007-11-27
When I try to run: 
```
sudo dpkg -i free-avg.deb
``` I receive this error message:

```
pedro@pedro-desktop:~/Setups$ sudo dpkg -i free-avg.deb
(Leyendo la base de datos ...  
122312 ficheros y directorios instalados actualmente.)
Desempaquetando avg75fld (de free-avg.deb) ...
dpkg: error al procesar free-avg.deb (--install):
 intentando sobreescribir `/opt/grisoft/lib/libgcc_s.so.1', que está también en el paquete avg75lms
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar:
 free-avg.deb

```

This is the translation (which might not be 100% acurate)

```
pedro@pedro-desktop:~/Setups$ sudo dpkg -i free-avg.deb
(Reading Data Base ...  
122312 Files and directories currently installed.)
Unpacking avg75fld (from free-avg.deb) ...
dpkg: error while processing free-avg.deb (--install):
 trying to overwrite `/opt/grisoft/lib/libgcc_s.so.1', which is also currently in the package avg75lms
dpkg-deb: the subprocess "paste" was terminated by signal (Broken Pipe)
Errors were found while processing:
 free-avg.deb


```

P.S.------------------------------------------------------------------------------------------------
I am dual booting with Windows Vista, and already have FireStarter installed, I wanted to know how strong is the AVG FREE edition's protection? Do I need to/should configure some other things to make my system more secure? Which things? Is it enough with what I already have (assuming I do install AVG AntiVirus)?

---

### Post by Perfect Storm on 2007-11-27
Try doubleclick the .deb instead.
If it doesn't work;

delete libgcc_s.so.1 in the /opt/grisoft/lib folder. Then try again.

Anti-virus application is not really needed. It's used for scanning for Windows virus.

---

### Post by pedro_cesar on 2007-11-28
I did so, and then it gave me the same error for the other file in the folder, so I erased it too (I didn't erase the /lib folder) and then it gave me the same error but for 
> /opt/grisoft/avg7/bin/avgqrtctl I don't how smart will it be to erase a bin file.

---

### Post by Sukarn on 2007-12-02
pedro_cesar, seems to me like you already installed avg once. if that is so, and you're trying to re-install or to install a new version, then you should just remove the old package and install the new one, or else delete all the files manually and install the new one.

---

### Post by Herman on 2007-12-21
I had the same problem as pedro_cesar and I did 'sudo rm -rf /var/lib/dpkg/info/avg75*', and I was able to install AVG alright after that.
```
sudo rm -rf /var/lib/dpkg/info/avg75*
```Regards, Herman :)

---

### Post by vnpenguin on 2007-12-26
:)thanks! It worked very good!

---

### Post by stellar22 on 2008-01-09
thank you this works perfectly.

Q: when i install WinXP on another partition, will AVG Linux be able to scan and clean those drives?

---

### Post by Perfect Storm on 2008-01-09
AVG can scan, not clean.

---

### Post by stellar22 on 2008-01-09
got it. thanks for the quick reply :)

---

### Post by Perfect Storm on 2008-01-09
If you're looking for something to clean use F-prot.

---

### Post by will1384 on 2008-01-13
I am getting 

"Can't get license information,
avgscan output:

sh: avgscan: not found"

when I run the avggui program

when I go to /opt/grisoft/avg7/bin it shows the file is there,
but even from the terminal and in that directory it will not 
let me run it  - it will do this

username@username-desktop:~$ cd /opt/grisoft/avg7/bin
username@username-desktop:/opt/grisoft/avg7/bin$ dir
avgdmilter  avgqrtctl  avgscan  avgspmctl  avgupdate
username@username-desktop:/opt/grisoft/avg7/bin$ avgscan
bash: /usr/bin/avgscan: No such file or directory
username@username-desktop:/opt/grisoft/avg7/bin$ 
username@username-desktop:/opt/grisoft/avg7/bin$ sudo avgscan
[sudo] password for username:
sudo: unable to execute /usr/bin/avgscan: No such file or directory
username@username-desktop:/opt/grisoft/avg7/bin$ 

why is it listed - but I can not run it

- I am using Ubuntu 7.10 - I installed from ubuntu-7.10-desktop-amd64.iso 
- I also install all updates

---

### Post by will1384 on 2008-01-13
I after having trouble using AVG, I installed F-Prot
from this post

 "[[64-bit] F-Prot (anti-virus) for Ubuntu 64-bit - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=4027250")"

and my AVG starts working - not sure why - 
I still had go to the terminal window and 
do the 

"sudo avgscan -register" and I used this key

70FREE-TX-IB-P1-C01-S139FC-327-9FPB

---

### Post by Sammi on 2008-01-13
I find this wikipedia article to be both relevant and interresting: [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms)

---

### Post by SilverWave on 2008-01-19
List of commands that I used successfully after downloading the newest deb to Desktop.
In place of:
nano free-avg/DEBIAN/control
I had to use:
sudo nano free-avg/DEBIAN/control

Thanks for the How To!


cd ~/Desktop
ls
mkdir free-avg
ls
dpkg-deb --extract avg75fld-r50-a1236.i386.deb free-avg
dpkg-deb --control avg75fld-r50-a1236.i386.deb free-avg/DEBIAN
ls
sudo nano free-avg/DEBIAN/control
dpkg --build free-avg
sudo dpkg -i free-avg.deb
sudo nano /usr/share/applications/avggui.desktop

---

### Post by Herman on 2008-01-22
I'm pleased to be able to report that AVG works well. I captured a folder that was suspected of containing a virus from the root of someone's Windows 'C' drive and took it home in my Ubuntu USB flash memory stick. 
When I scanned it with my AVG in my big AMD64  Ubuntu computer, AVG found and identified three viruses!
Thanks Artificial Intelligence! 

Regards, Herman :)

---

### Post by xuanthu20061984 on 2008-03-04
Thank for sharing. good

---

### Post by Perfect Storm on 2008-04-10
Guide now tested on 8.04 64-bit

---

### Post by nitrokid759 on 2008-05-09
how do you uninstall this?

---

### Post by Perfect Storm on 2008-05-09
Open synaptic and search for the packages. Then pick completly remove.

---

### Post by hvw on 2008-07-29
why shouldn't simply use:
```
dpkg --force-architecture -i avg75fld-r51-a1243.i386.deb
```
The result is the same:
```
AVG 7.5 Anti-Virus Free for Linux successfully installed.
```

---

### Post by Perfect Storm on 2008-07-29
Because forcing is not only bad policy but also it can break stuff to do so.

---

### Post by monjope on 2008-08-18
Awesome!!. Thank you for this extraordinary tutorial!!! =D>

---

### Post by b1blancer on 2008-10-28
Where do I find "Architecture" in order to change it from I386 to AMD64??

---

### Post by Perfect Storm on 2008-10-28
When you do; nano avggui/DEBIAN/control

If it's not there, you properly made a mistake somewhere in te guide.

---

### Post by b1blancer on 2008-10-29
> **Artificial Intelligence said:**
> When you do; nano avggui/DEBIAN/control
Ok.  I'll give the process a try.

---

### Post by b1blancer on 2008-10-29
That got it.  The lights dimmed a couple of times, but everything seems to be working.  :)

---

### Post by Panarchy on 2008-11-12
> **Artificial Intelligence said:**
> **Tested:** Ubuntu 7.10 • 8.04   64 bit - Gnome

**[size=5]3. AVG Free Version for Ubuntu 64-bit[/size]**

**Before Installation**

First you need some tool to edit/build .deb packages. To the terminal;

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential dpkg-dev fakeroot
```

**Installation**

Download the .deb file [here](http://free.grisoft.com/doc/5390/us/frt/0?prd=afl) to your Desktop.

Fire up the terminal;

```
cd ~/Desktop
mkdir free-avg
dpkg-deb --extract avg75fld-r49-a1130.i386.deb free-avg
dpkg-deb --control avg75fld-r49-a1130.i386.deb free-avg/DEBIAN
nano free-avg/DEBIAN/control
```

Under Architecture: change i386 to amd64

Save [ctrl]+[o]
Exit [ctrl]+[x]

```
dpkg --build free-avg
sudo dpkg -i free-avg.deb
sudo nano /usr/share/applications/avggui.desktop
```

Change: **Exec=avggui** to **Exec=gksudo avggui**
Change: **Categories=GNOME;KDE;Application;Utility;** to **Categories=GNOME;KDE;Application;System;**

Save [ctrl]+[o]
Exit [ctrl]+[x]

AVG is now ready to be used.
You can start it by Applications tab ---> System Tools ---> AVG for Linux Workstation

:(

Isn't working for me. Had to rename the name of the deb, got to the next command;

```
nano free-avg/DEBIAN/control
```

Gave me a blank 'document'. Tried with sudo. Same. Tried with gedit. Same. Tried navigating to free-avg/DEBIAN/control with nautilus. Tried with sudo. All gave me either nothing or an error saying file doesn't exist.

Please tell me how to install it.

Thanks in advance,

Panarchy

Ubuntu 8.10 64-bit

---

### Post by Perfect Storm on 2008-11-12
Make sure to change file name in the terminal as the file keeps changing in every release of AVG.

---

### Post by Jwav3 on 2009-01-23
> **will1384 said:**
> I after having trouble using AVG, I installed F-Prot
from this post

 "[[64-bit] F-Prot (anti-virus) for Ubuntu 64-bit - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=4027250")"

and my AVG starts working - not sure why - 
I still had go to the terminal window and 
do the 

"sudo avgscan -register" and I used this key

70FREE-TX-IB-P1-C01-S139FC-327-9FPB

I got this too.. You need to install the ia32 compat libs.

---

### Post by modmadmike on 2009-02-19
Thanks I did this for the free version but changed the "i386" parameter to "all" and did it manually by extracting the files with ark and then using the dpkg -b command to rebuild the package seems much more easy the way you said to do it :). If only I read this beforehand.for some reason I could not use dpkg to install it but could use gdebi (dpkg said it was a directory...).

---

### Post by modmadmike on 2009-02-19
> **modmadmike said:**
> Thanks I did this for the free version but changed the "i386" parameter to "all" and did it manually by extracting the files with ark and then using the dpkg -b command to rebuild the package seems much more easy the way you said to do it :). If only I read this beforehand.for some reason I could not use dpkg to install it but could use gdebi (dpkg said it was a directory...).

wait nvm I had a directory with the same name duh! ](*,)

---

### Post by runebinder on 2009-03-09
Just followed your guide and it worked perfectly.

Thank you :D

---

### Post by TrueSkyDemon on 2009-04-03
Hi, I just recently installed Ubuntu 8.10 64bit, and I having problem after follow the steps and installed AVG. The problem is that once the package is installed, I do not see AVG in my applications and I do not see the AVG tray icon after reboot, I tried to open the package again it will show that AVG is already installed and ask me if I want to reinstall, but even after re-installation it still the same, can't find it anywhere, I tried looking for it in synaptic with no luck finding it as well, very weird.. but if I go under terminal and type avgscan, it actually shows it's there.. does anyone know what is going on?:confused:

---

### Post by Luis_com_Z on 2009-07-17
> **TrueSkyDemon said:**
> Hi, I just recently installed Ubuntu 8.10 64bit, and I having problem after follow the steps and installed AVG. The problem is that once the package is installed, I do not see AVG in my applications and I do not see the AVG tray icon after reboot, I tried to open the package again it will show that AVG is already installed and ask me if I want to reinstall, but even after re-installation it still the same, can't find it anywhere, I tried looking for it in synaptic with no luck finding it as well, very weird.. but if I go under terminal and type avgscan, it actually shows it's there.. does anyone know what is going on?:confused:

I'm having the same problem, although I can find it in Synaptic as 'avg85flx'. Funny thing is, I was able to install it successfully on my notebook earlier last year, following this same HOW-TO (back then it was AVG version 7.5, not 8.5, but same difference). Whatever happened, I think the problem was when I entered

```
sudo nano /usr/share/applications/avggui.desktop
```near the end, it opened a blank file. The command line scan seems to be working fine, the problem is only the absent GUI shortcut. I was thinking that maybe if just copied the 'avggui.desktop' launcher file from my notebook to my desktop /usr/share/applications folder, and maybe made some appropriate changes to it, I could get the GUI to work. Does that sound possible or am I being moronic? (I'm a major noob). I'd try it, but the problem is I botched my notebook Ubuntu installation a while ago trying to force it to update from 8.04 to 9.04 (I'm still kicking myself over it) and now it doesn't even boot. Well, actually it does boot, but it just hangs on a Debian splash screen that I have no friggin' idea where it came from. But I digress... Anyway, if just creating an 'avggui.desktop' file could work, maybe someone could post a sample text of their working file and give me a few pointers as to what I should change, if anything. If that's not feasible, what can I do to fix this? Thanks!

---

### Post by wild_ecstasy1985 on 2009-10-20
avggui.desktop does not exist :(

---

### Post by eewoud on 2010-10-13
I followed these steps to install avg on ubuntu server 10.04 64 bit.
When I try to install the package, I get the following errors:

```

/usr/bin/avgctl: 17: /opt/avg/avg8/bin/avgctl: not found
dpkg: error processing avg85flx (--install):
subproces installed post-installation script returned an errorvalue 127
processing triggers for man-db ...
errors found while processing: avg85flx

```

---

### Post by eewoud on 2010-10-16
> **eewoud said:**
> I followed these steps to install avg on ubuntu server 10.04 64 bit.
When I try to install the package, I get the following errors:

```

/usr/bin/avgctl: 17: /opt/avg/avg8/bin/avgctl: not found
dpkg: error processing avg85flx (--install):
subproces installed post-installation script returned an errorvalue 127
processing triggers for man-db ...
errors found while processing: avg85flx

```

Can anyone help?? I've been looking for a solution to this problem for days, but just can't find any...

---

