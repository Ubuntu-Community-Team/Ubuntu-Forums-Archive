---
title: "Bonager: The Boot Scan Manager - Control the filesystem scan that happens at bootup!"
date: 2006-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by AgenT on 2006-11-07
[CENTER][SIZE=6][COLOR=#000000][FONT=Times New Roman][B]Bonager: The Boot Scan Manager
[/B][/FONT][/COLOR][/SIZE]From the author of [ParolaPass: The Password Generator]("http://www.ubuntuforums.org/showthread.php?t=299823")

[SIZE=5][COLOR=Red]**PLEASE DO NOT USE Bonager!!**[/COLOR][/SIZE][B]

[COLOR=Magenta][SIZE=4][COLOR=DarkOrange]GREAT NEWS![/COLOR][/SIZE][COLOR=DarkRed] 
[SIZE=4]Starting with 9.04, Ubuntu now has this functionality built-in![/SIZE]

[COLOR=Magenta][SIZE=4]=D> THANK YOU EVERYONE FOR SUPPORTING BONAGER [/SIZE][/COLOR][/COLOR][/COLOR][/B][B][COLOR=Magenta][COLOR=DarkRed][COLOR=Magenta]=D>
[/COLOR][/COLOR][/COLOR]You made it possible for Ubuntu developers to finally incorporate a boot-scan cancel button![/B][B][COLOR=Magenta][COLOR=DarkRed][COLOR=Magenta]
[/COLOR][/COLOR][/COLOR][/B][SIZE=3]
Need to cancel the boot scan?
**Press the [COLOR=Navy]ESCAPE[/COLOR] key during the scan to cancel!**
Remember, this functionality is built-in![/SIZE]

[SIZE=3]**If you use an older version of Ubuntu (before 9.04), you can try Bonager out. It should work.** Please note, however, it is no longer supported by me.[/SIZE]
[B][COLOR=Magenta][COLOR=DarkRed]
[/COLOR][/COLOR]Bonager is no longer supported!
(it may possibly break your system, especially ext4 that comes with 9.10)


[/B][/CENTER]
[COLOR=#000000][FONT=Times New Roman][SIZE=4]Apologies to everyone for not updating this thread for a long time. And I would like to give a [COLOR=Magenta]**[SIZE=5]HUGE THANK YOU[/SIZE]**[/COLOR] to all Bonger users for helping each other out in this thread. You guys are great! Thank you again![/SIZE][/FONT][/COLOR] =D>
[COLOR=#000000][FONT=Times New Roman][SIZE=4]

------------------------------------------------------


[/SIZE][/FONT][/COLOR]** Bonager is an easy way to manage that unpredictable and sometimes very annoying disk scan that happens when the computer is turned on.** 

When installed, you take control of when you want that disk scan to occur. You even receive a warning before the next scan happens so that you are not surprised by it. And of course, you are given the option to postpone the scan.

Bonager is EASY to use. So easy, that everything can be done within three clicks and requires no configuration. Seriously.

Bonager is [freedom software]("http://www.gnu.org/philosophy/"). You have the freedom to use it, modify it, sell it, change it and the like. Freedom, pure and simple. Bonager is licensed under the [GPLv2]("http://www.gnu.org/copyleft/gpl.html").

And to top it off, Bonager is SAFE to use. It does NOT modify any system files or configurations! Never worry about Bonager making a change to your system that creates conflicts with upgrades or other programs.

**FEATURES:**
[LIST]
[*] Only a tray icon, so it does not get in the way
[*] Detection of impending scan
[*] Postpone a scan that is scheduled for the next bootup
[*] Force a scan
[*] Only a maximum of 3 clicks needed to do anything
[*] Knows what actions to make available based on your system
[*] No system configurations or settings are modified
[*] Autostart ability
[*]Now with localization [nationalization/translations] support
[*]Ubuntu Dapper and above support
[*]Icon shows status & useful information
[*] UUID and /dev compatible
[*] No configuration needed
[*]No Tray Icon mode
[*]Quick output to terminal (great for scripts!)
[/LIST]
**SMART Feature Details:**
No one likes to mock around with unnecessary configurations or options. Bonager determines what your best option is for the moment and only presents you with a simple [NO] [YES] choice. When Bonager detects that your next boot will force a scan, it will ask you whether or not you would like to postpone it. If Bonager does not detect an impending scan, it will ask you if you would like to force a scan yourself.

**INSTRUCTIONS:**
Before you install, you must download the installation program (deb file) given below.
[LIST]
[*] Installation: 1) double-click on the deb file 2) click "Install"
[*] Starting Bonager: 1) click Applications -> Accessories -> Bonager
[*] Quiting Bonager: 1) right-click on Bonager system tray icon 2) click "OK"
[*] Using Bonager: 1) left-click on Bonager system tray icon 2) choose between "NO" and "YES"
[*] Enabling Autostart: 1) right-click on Bonager system tray icon 2) select "Autostart Bonager" 3) select either [NO] or [YES]
[/LIST]
*Simple, easy, elegant and fast.*

**FREQUENTLY ASKED QUESTIONS:**
Q: Does Bonager support Dapper AND Edgy (and Feisty)?
A: Yes. Bonager now supports both Dapper AND Edgy (and Feisty)!

Q: Does Bonager work with Xubuntu (XFCE)?
A: Yes.

Q: Does Bonager work on AMD64 and PowerPC?
A: Yes, Bonager will work on ANY architecture available, including AMD64 and PPC.

Q: If Bonager is used to force a scan or to delay a scan, will quitting Bonager affect this choice?
A: No. This is especially useful for those with little screen space. Just select the option you want and quit Bonager.

Q: What languages does Bonager support?
A: English, French and German. If  you would like to help and translate Bonager just download the translate.txt file (see "attachment" section on the bottom of this post). It will only take about 5-10 minutes of your time and you DO NOT have to dig into the Bonager source code. 

Q: Does Bonager support KDE (Kubuntu)?
A: No, Bonager does not support KDE (or QT to be more exact) right now. If enough people ask for a KDE version, I will consider creating a KDE version of Bonager. As of now, only one person posted with a request.

Q: Does Bonager support XFCE (Xubuntu)?
A: I do not know. No one has tested this yet. It may work or it may not. You can always try it and remove it. If you decide to test it in XFCE, please post your results in this thread. See requirements question below.

Q: Bonager's tray does not use my system tray colour, why? [or, Bonager's tray is not transparent, why?]
A: This is because the tray is not using the theme's default colour. Bonager does change its tray background colour, but only to the theme's default background colour. This is a limitation that has nothing to do with Bonager and therefore cannot be changed. One workaround would be to switch the tray colour back to theme default and change the theme default colour to the colour wanted. Technical details: this is a pygtk limitation where it is not possible to detect the actual panel color, but only the default panel theme color - Bonager does NOT set any color for the "icon background" and just always uses the panel theme color.

Q: Why was the icon changed?
A: Icon was changed because there needed to be a notify icon in addition to the standard icon that only differed in colour and made sense. Also, the previous icon [was not free]("http://en.wikipedia.org/wiki/Free_software").

Q: I use XFCE (Xubuntu) and when autostart is set to on, two Bonager icons are loaded in the system tray/notification area. Why?
A: This is because you have the program autostart in both your GNOME and XFCE sessions, so XFCE loads both.

Q: Does Bonager support any filesystem besides ext3?
A: No, Bonager only supports ext3 which is the default filesystem on Ubuntu and many other distributions. The reason for this is simple: the developer only uses ext3 and does not have access to non-ext3 partitioned systems.

Q: How are the new command line arguments used [No Tray Icon & Quick Output]?
A: Type this in the terminal: bonager --help

Q: What are the requirements?
A: python (>=2.4), python-gnome2-extras (>=2.14.2) | python2.4-gnome2-extras (>=2.14.0), python-gtk2 (>=2.8.6)

**SCREENSHOTS:**
(version 0.3)[COLOR=#000000][FONT=Times New Roman]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=19313&stc=1&d=1163445801[/IMG]
[/FONT][/COLOR] [tray details][COLOR=#000000][FONT=Times New Roman]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=19311&stc=1&d=1163445801[/IMG]
[/FONT][/COLOR] [smart action]

[COLOR=#000000][FONT=Times New Roman][IMG]http://ubuntuforums.org/attachment.php?attachmentid=19312&stc=1&d=1163445801[/IMG]
[/FONT][/COLOR] [applications menu location][COLOR=#000000][FONT=Times New Roman]
[/FONT][/COLOR]
**WHAT'S NEW**
[LIST]
[*]fix rc update problem
[*]command line check trigger (type bonager --help for details)
[*]command line tray icon trigger (type bonager --help for details)
[*]fix postpone question from poping up if it has already been answered in current boot
[/LIST]
WHAT'S NEW (version 0.5)
[LIST]
[*]Localization enabled
[*]Localization support: Bonager now supports English, French and German
[*]Easier to understand buttons and text
[*]Fixed the tray icon from properly showing that a scan was postponed on startup
[*]Removed the number from tray icon
[*]On quit menu, YES is now default for fast and easy quitting of Bonager (especially useful for those with little desktop space)
[*]0.5.1 addition: Now Bonager works on ANY architecture!
[/LIST]
WHAT'S NEW (version 0.4)
[LIST]
[*]Fixed bug that caused the warning events for impending scan not show up at the correct time (it was one mount off)
[*]Fixed bug where negative # is shown for mounts left if scan was postponed
[*]Fixed postponed scan x times dialog
[*]Changed some of the messages to make them more easily understandable
[/LIST]
WHAT'S NEW (version 0.3):
[LIST]
[*]New icons
[*]Bonager icon in every window
[*]Icon now shows status: changes icon to notify state when scan will happen at next boot (removed 0.2 background change)
[*]Support for multiple partitions!
[*]Smart selection of the partition that will force a scan first: now Bonager uses information from the partition that requires a scan for warnings, etc.
[/LIST]
WHAT'S NEW (version 0.2):
[LIST]
[*]Dapper is now supported! Edgy and Dapper are supported in one deb file!
[*] Background of tray icon changes colour to warn of scan on the next bootup.
[*] Changes the tray icon digit to always be 2 digits - the tray icon will no longer change its size.
[*] Tray icon now shows the number of mounts before next forced scan.
[*] Fixed bugs that caused crashes and other problems.
[/LIST]
**DOWNLOAD:**
**:KS>>> DOWNLOAD DELETED! SEE TOP OF PAGE FOR THE REASON ****<<<:KS**

**SUGGESTIONS, CRITICISMS & FEEDBACK:**
Please make suggestions and criticisms in this forum. Any feedback about Bonager is VERY much appreciated!

---

### Post by Not the man I once was on 2006-11-07
Greetings All,

That is an absolutely excellent looking application and I can't wait to use it on my system although I realise that it's only just been released and there are certainly going to be issues. I see simplicity is the main aim of this program and I'm certainly taken by the icon you've designed, it fits into the feeling of the Operating System well.

Well done on your project and I wish you luck on progressing your application. What format would you prefer feedback to be in? Are you taking suggestions for future versions of the program and do you plan the expand the feature set?

Regards,

Not the man I once was

---

### Post by maniacmusician on 2006-11-07
planning a QT frontend, or not so much?

---

### Post by kvonb on 2006-11-07
EXCELLENT!

Did you write this?  If so then you are my hero of the week :D

I just tried to install it, (Dapper 686 32bit), but the following happened:

(see attached screenshots)

---

### Post by AgenT on 2006-11-07
> **Not the man I once was said:**
> I see simplicity is the main aim of this programYes, simplicity was a major factor in how this program was designed. After all, it is a program that is meant to solve a simple problem. "Keep it simple" - that's the motto, one may say.

> **Not the man I once was said:**
> I'm certainly taken by the icon you've designed, it fits into the feeling of the Operating System well.This is NOT my design. I found it somewhere and in the next release or two, I intend on giving credit to the author of the icon. Right now, I do not know who the author is exactly, but I do know that the icon is an icon under the common license (the GPL for media).

> **Not the man I once was said:**
>  Well done on your project and I wish you luck on progressing your application.Thank you!

> **Not the man I once was said:**
> What format would you prefer feedback to be in? What do you mean by format? As in thread reply, email or something else? For now, please reply to this thread.

> **Not the man I once was said:**
> Are you taking suggestions for future versions of the program and do you plan the expand the feature set? YES, please give any and all suggestions you can muster! Do not be shy about criticism. In terms of feature expansion: YES, please make any suggestions. But please keep in mind that this program should stay SIMPLE and (this being VERY important) SAFE to use. Safe includes being true to system (Ubuntu in this case) default configurations and settings.

---

### Post by AgenT on 2006-11-07
> **maniacmusician said:**
> planning a QT frontend, or not so much?No plan to start on one right now, but who knows. The nice thing about this program is that the behind the scenes stuff is done with the backend, while the front end manages, well, what you see. This should make making a QT tray icon easier.

However, please note that this is my first python applications and my first gnome/gtk application. And I have never coded anything for QT, nor do I use it (although I can always install it).

What I would really like is to make it DE neutral, but am not sure that this is possible with tray programs.

Also, it may be possible to use this without having GNOME, but you will need to install the gnome dependencies.

---

### Post by DoctorMO on 2006-11-07
AgentT, You seem to have a good eye for the usability aspects of software development. perhaps we can come up with a barter your skills for mine. Dohickey (dohickey.sourceforge.net) if you could give it the once over to find any nooks that might get the end user confuised it would save time in the future.

---

### Post by AgenT on 2006-11-07
> **kvonb said:**
> EXCELLENT!

Did you write this?  If so then you are my hero of the week :D
Yes, I wrote this (but did NOT design the icon - see post above).
> **kvonb said:**
> I just tried to install it, (Dapper 686 32bit), but the following happened:
  I do not have Dapper (currently using Edgy), and have made the deb file according to the dependencies that I used and know make the program work.

If you give me the following information, I can make a deb for Dapper. But this will be at your own risk and I cannot test the deb for Dapper compatibility. The information I need is this:

Please provide me with the full output of these commands (and tell me what output corresponds to what command):
```
dpkg-query -s python | grep Version
dpkg-query -s python-gnome2-extras | grep Version
dpkg-query -s python-gtk2 | grep Version
dpkg-query -L python-gnome2-extras
```Please wrap your ouput in code tags so that it is easier to read.

---

### Post by AgenT on 2006-11-07
> **DoctorMO said:**
> AgentT, You seem to have a good eye for the usability aspects of software development. perhaps we can come up with a barter your skills for mine. Dohickey (dohickey.sourceforge.net) if you could give it the once over to find any nooks that might get the end user confuised it would save time in the future.Thank you for your compliments. As a courtesy to other forum readers, I will not answer further questions about this very nice, but offtopic, post in this thread. However, please private message me using the forum (click on my name) and we can talk about it further.

---

### Post by darkhatter on 2006-11-07
I think you should take all these little tools that have been coming out, and make a ubuntu style yast.

---

### Post by AgenT on 2006-11-07
> **darkhatter said:**
> I think you should take all these little tools that have been coming out, and make a ubuntu style yast.Thank you for your reply (and compliment!). You may be in luck! See this [thread]("http://www.ubuntuforums.org/showthread.php?t=207894") for a project that seems like what you describe. Also, please read the "SUGGESTIONS & CRITICISMS" section of my first post (do not worry, you did not miss it because it was added when you typed this reply!)

---

### Post by paul6 on 2006-11-07
I'm having some sort of problem...

```
paul@ubuntu:~$ **sudo dpkg -i bonager_0.1_i386.deb**
Selecting previously deselected package bonager.
(Reading database ... 111480 files and directories currently installed.)
Unpacking bonager (from bonager_0.1_i386.deb) ...
Setting up bonager (0.1) ...
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
        [-i interval[d|m|w]] [-j] [-J journal_options]
        [-l] [-s sparse_flag] [-m reserved_blocks_percent]
        [-o [^]mount_options[,...]] [-r reserved_blocks_count]
        [-u user] [-C mount_count] [-L volume_label] [-M last_mounted_dir]
        [-O [^]feature[,...]] [-T last_check_time] [-U UUID] device
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
        [-i interval[d|m|w]] [-j] [-J journal_options]
        [-l] [-s sparse_flag] [-m reserved_blocks_percent]
        [-o [^]mount_options[,...]] [-r reserved_blocks_count]
        [-u user] [-C mount_count] [-L volume_label] [-M last_mounted_dir]
        [-O [^]feature[,...]] [-T last_check_time] [-U UUID] device

paul@ubuntu:~$ **bonager**
Traceback (most recent call last):
  File "/usr/bin/bonager", line 276, in ?
    seqnum2 = int(seqnum)
ValueError: invalid literal for int(): 
paul@ubuntu:~$ **sudo bonager**
Traceback (most recent call last):
  File "/usr/bin/bonager", line 276, in ?
    seqnum2 = int(seqnum)
ValueError: invalid literal for int(): 
paul@ubuntu:~$ 
```

This is under Ubuntu 6.10, with fluxbox.

---

### Post by kvonb on 2006-11-07
Output as requested:

```
kev@kev:~$ dpkg-query -s python | grep Version
Version: 2.4.2-0ubuntu3
```

```
kev@kev:~$ dpkg-query -s python-gnome2-extras | grep Version
Version: 2.14.0-0ubuntu3
```

```
kev@kev:~$ dpkg-query -s python-gtk2 | grep Version
Version: 2.8.6-0ubuntu1
```

```
kev@kev:~$ dpkg-query -L python-gnome2-extras
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/python-gnome2-extras
/usr/share/doc/python-gnome2-extras/copyright
/usr/share/doc/python-gnome2-extras/examples
/usr/share/doc/python-gnome2-extras/examples/egg
/usr/share/doc/python-gnome2-extras/examples/egg/recent
/usr/share/doc/python-gnome2-extras/examples/egg/recent/Bonobo_Sample_Hello.xml
/usr/share/doc/python-gnome2-extras/examples/egg/recent/populate-recent.py
/usr/share/doc/python-gnome2-extras/examples/egg/recent/gtk-view.py.gz
/usr/share/doc/python-gnome2-extras/examples/egg/recent/bonobo-view.py.gz
/usr/share/doc/python-gnome2-extras/examples/egg/trayicon.py
/usr/share/doc/python-gnome2-extras/examples/gdl
/usr/share/doc/python-gnome2-extras/examples/gdl/gdl_test.py
/usr/share/doc/python-gnome2-extras/examples/gtkhtml2
/usr/share/doc/python-gnome2-extras/examples/gtkhtml2/simple-browser.py
/usr/share/doc/python-gnome2-extras/examples/gtkspell
/usr/share/doc/python-gnome2-extras/examples/gtkspell/test.py
/usr/share/doc/python-gnome2-extras/examples/gtkspell/gtkspell.py.gz
/usr/share/doc/python-gnome2-extras/changelog.gz
/usr/share/doc/python-gnome2-extras/changelog.Debian.gz
kev@kev:~$
```

Risk gladly accepted...you're a gentleman and a scholar, thankyou :D

---

### Post by katgfan on 2006-11-07
Nice one. hats off to AgenT

---

### Post by AgenT on 2006-11-07
> **paul6 said:**
> I'm having some sort of problem...Thank you for your detailed bug report.

A few questions so that I can try solving this bug:
1) Do you have gnome installed? (you are using fluxbox, but maybe you have gnome installed). If not, how did you install fluxbox? From a server/custom install of Ubuntu? From Xubuntu? From Kubuntu?
2)  Please provide me with the full output of these commands (and tell me what output corresponds to what command):
 [LEFT]```
dpkg-query -s python | grep Version
dpkg-query -s python-gnome2-extras | grep Version
dpkg-query -s python-gtk2 | grep Version
dpkg-query -L python-gnome2-extras
tune2fs
dpkg-query -l e2fsprogs
```[/LEFT]
 Please wrap your ouput in code tags so that it is easier to read.

Comments:
The TraceBack python errors when you run bonager look like they are due to not having enough information from the backend. This is a good error because it shows that the code can be improved with fail safe aborts (will try to incorporate this into next release). 

Your first error, the tune2fs, is what I assume caused this. You may have a different (and incompatible) version of tune2fs. I did not expect this because tune2fs is VERY old and I assumed that it was standardized. If version difference is what caused this then I need to add a new dependency to the requirements.

---

### Post by AgenT on 2006-11-07
> **kvonb said:**
> Output as requested:
....
Risk gladly accepted...you're a gentleman and a scholar, thankyou :DAccording to your output of  dpkg-query -L python-gnome2-extras, you do not have the necessary gnome files to run this program. As you can see, that package only provides you with examples and not the actual libraries (yes, that is strange!). There are only two known (as far as I know) python gtk tray icon libraries. The one that I used and a newer one that only the newest GNOME version has. As you can see, whatever library I would have chosen, users with older versions of GNOME would be out of luck.

Could you provide me with the output of (just in case):
```
dpkg-query -S trayicon.so
```If you want, I can provide you with the missing library, but this is really stretching it because I have no idea if it will work with your version of python and gtk. Also, you must realize that this has a very high chance of breaking your system if you decide to upgrade to Edgy AND forget to remove the library before the upgrade. But if you remove it before any dist-upgrade you should be fine. Your choice and it is up to you if you want to take the risk. Please let me know what you decide.

---

### Post by AgenT on 2006-11-07
> **katgfan said:**
> Nice one. hats off to AgenT Thank you. If you use it, please give me some feedback (see  SUGGESTIONS & CRITICISMS section in the first post). Even if you have no suggestions or criticisms, I also appreciate feedback that only states that the program works.

---

### Post by kvonb on 2006-11-07
```
kev@kev:~$ dpkg-query -S trayicon.so
python2.4-gnome2-extras: /usr/lib/python2.4/site-packages/gtk-2.0/egg/trayicon.so
kev@kev:~$
```


```
If you want, I can provide you with the missing library, but this is really stretching it because I have no idea if it will work with your version of python and gtk. Also, you must realize that this has a very high chance of breaking your system if you decide to upgrade to Edgy AND forget to remove the library before the upgrade. But if you remove it before any dist-upgrade you should be fine. Your choice and it is up to you if you want to take the risk. Please let me know what you decide.
```

I won't be upgrading to Edgy because of problems with my video card (ATI 9200), and when I do I will most likely do a clean install anyway, so if you have the time to waste on me I will give it a try.

Regards,  Kev

---

### Post by DoctorMO on 2006-11-07
It's better to develop things for dapper and extend support upwards so you keep lib deps at the last LTS.

---

### Post by paul6 on 2006-11-07
> **AgenT said:**
> 
1) Do you have gnome installed? (you are using fluxbox, but maybe you have gnome installed). If not, how did you install fluxbox? From a server/custom install of Ubuntu? From Xubuntu? From Kubuntu?

Full, fresh install of Ubuntu 6.10 Edgy :)  Not the server install.

Here's the information you requested:

```
paul@ubuntu:~$ **dpkg-query -s python | grep Version**
Version: 2.4.3-11ubuntu3
paul@ubuntu:~$ **dpkg-query -s python-gnome2-extras | grep Version**
Version: 2.14.2-0ubuntu6
paul@ubuntu:~$ **dpkg-query -s python-gtk2 | grep Version**
Version: 2.10.3-0ubuntu3
paul@ubuntu:~$ **dpkg-query -L python-gnome2-extras**
/.
/usr
/usr/lib
/usr/lib/python-support
/usr/lib/python-support/python-gnome2-extras
/usr/lib/python-support/python-gnome2-extras/python2.5
/usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0
/usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0/egg
/usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0/egg/recent.so
/usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0/egg/trayicon.so
/usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0/gtkmozembed.so
/usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0/gdl.so
/usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0/gda.so
/usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0/gksu
/usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0/gksu/_gksu.so
/usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0/gksu/ui.so
/usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0/gtkspell.so
/usr/lib/python-support/python-gnome2-extras/python2.4
/usr/lib/python-support/python-gnome2-extras/python2.4/gtk-2.0
/usr/lib/python-support/python-gnome2-extras/python2.4/gtk-2.0/egg
/usr/lib/python-support/python-gnome2-extras/python2.4/gtk-2.0/egg/recent.so
/usr/lib/python-support/python-gnome2-extras/python2.4/gtk-2.0/egg/trayicon.so
/usr/lib/python-support/python-gnome2-extras/python2.4/gtk-2.0/gtkmozembed.so
/usr/lib/python-support/python-gnome2-extras/python2.4/gtk-2.0/gdl.so
/usr/lib/python-support/python-gnome2-extras/python2.4/gtk-2.0/gda.so
/usr/lib/python-support/python-gnome2-extras/python2.4/gtk-2.0/gksu
/usr/lib/python-support/python-gnome2-extras/python2.4/gtk-2.0/gksu/_gksu.so
/usr/lib/python-support/python-gnome2-extras/python2.4/gtk-2.0/gksu/ui.so
/usr/lib/python-support/python-gnome2-extras/python2.4/gtk-2.0/gtkspell.so
/usr/share
/usr/share/doc
/usr/share/doc/python-gnome2-extras
/usr/share/doc/python-gnome2-extras/copyright
/usr/share/doc/python-gnome2-extras/examples
/usr/share/doc/python-gnome2-extras/examples/egg
/usr/share/doc/python-gnome2-extras/examples/egg/recent
/usr/share/doc/python-gnome2-extras/examples/egg/recent/Bonobo_Sample_Hello.xml
/usr/share/doc/python-gnome2-extras/examples/egg/recent/populate-recent.py
/usr/share/doc/python-gnome2-extras/examples/egg/recent/gtk-view.py.gz
/usr/share/doc/python-gnome2-extras/examples/egg/recent/bonobo-view.py.gz
/usr/share/doc/python-gnome2-extras/examples/egg/trayicon.py
/usr/share/doc/python-gnome2-extras/examples/gdl
/usr/share/doc/python-gnome2-extras/examples/gdl/gdl_test.py
/usr/share/doc/python-gnome2-extras/examples/gtkspell
/usr/share/doc/python-gnome2-extras/examples/gtkspell/test.py
/usr/share/doc/python-gnome2-extras/examples/gtkspell/gtkspell.py.gz
/usr/share/doc/python-gnome2-extras/changelog.gz
/usr/share/doc/python-gnome2-extras/NEWS.gz
/usr/share/doc/python-gnome2-extras/changelog.Debian.gz
/usr/share/python-support
/usr/share/python-support/python-gnome2-extras
/usr/share/python-support/python-gnome2-extras/gtk-2.0
/usr/share/python-support/python-gnome2-extras/gtk-2.0/gksu
/usr/share/python-support/python-gnome2-extras/gtk-2.0/gksu/__init__.py
/usr/share/python-support/python-gnome2-extras/gtk-2.0/egg
/usr/share/python-support/python-gnome2-extras/gtk-2.0/egg/__init__.py
paul@ubuntu:~$ **tune2fs**
tune2fs 1.39 (29-May-2006)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
        [-i interval[d|m|w]] [-j] [-J journal_options]
        [-l] [-s sparse_flag] [-m reserved_blocks_percent]
        [-o [^]mount_options[,...]] [-r reserved_blocks_count]
        [-u user] [-C mount_count] [-L volume_label] [-M last_mounted_dir]
        [-O [^]feature[,...]] [-T last_check_time] [-U UUID] device
paul@ubuntu:~$ **dpkg-query -l e2fsprogs**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  e2fsprogs      1.39-1         ext2 file system utilities and libraries
paul@ubuntu:~$ 
```

---

### Post by AgenT on 2006-11-07
> **DoctorMO said:**
> It's better to develop things for dapper and extend support upwards so you keep lib deps at the last LTS.You are correct and this is how it should be done. The problem is that this is not possible with this program. Please [see this post]("http://ubuntuforums.org/showthread.php?t=295262&p=1729816") for more details.

---

### Post by DoctorMO on 2006-11-08
In this instance it apears that it has deps wich need to be avoided completly in order to make the program compatable.

I don't like deps, they but undue presure on the application. if anything extra needs to be installed then it needs to have been available for a long time or come with the app.

---

### Post by AgenT on 2006-11-08
> **paul6 said:**
> Full, fresh install of Ubuntu 6.10 Edgy :)  Not the server install.
You seem to have all requirements met and tune2fs is the version that is confirmed to work with Bonager. Please run these commands and post the output:
```
sudo /etc/init.d/bonager start
cat /var/cache/bonager/drive_info
bonager
```

---

### Post by paul6 on 2006-11-08
> **AgenT said:**
> You seem to have all requirements met and tune2fs is the version that is confirmed to work with Bonager. Please run these commands and give me the output:
```
sudo /etc/init.d/bonager start
cat /var/cache/bonager/drive_info
bonager
```

Here you go:

```
paul@ubuntu:~$ **sudo /etc/init.d/bonager start**
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
        [-i interval[d|m|w]] [-j] [-J journal_options]
        [-l] [-s sparse_flag] [-m reserved_blocks_percent]
        [-o [^]mount_options[,...]] [-r reserved_blocks_count]
        [-u user] [-C mount_count] [-L volume_label] [-M last_mounted_dir]
        [-O [^]feature[,...]] [-T last_check_time] [-U UUID] device
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
        [-i interval[d|m|w]] [-j] [-J journal_options]
        [-l] [-s sparse_flag] [-m reserved_blocks_percent]
        [-o [^]mount_options[,...]] [-r reserved_blocks_count]
        [-u user] [-C mount_count] [-L volume_label] [-M last_mounted_dir]
        [-O [^]feature[,...]] [-T last_check_time] [-U UUID] device
paul@ubuntu:~$ **cat /var/cache/bonager/drive_info**
  
paul@ubuntu:~$ **bonager**
Traceback (most recent call last):
  File "/usr/bin/bonager", line 276, in ?
    seqnum2 = int(seqnum)
ValueError: invalid literal for int(): 
paul@ubuntu:~$ 

```

---

### Post by svasie on 2006-11-08
Great app for laptop users.
He're it comes my suggestion: on autostart keep it hidden until some mounts, possibly configurable, are remaining until next scan. We shouldn't mess up the system tray with too many icons/apps like in windows.

---

### Post by mssever on 2006-11-08
Great idea!

A couple of bugs/suggestions: The file attached to the original post has a .zip extension, which implies that it is a ZIP archive. This confused me when I got an error trying to unzip it (the file command told me that it's really a deb). Furthermore, the graphical frontend to dpkg refused to open the package (giving me a security warning) until I renamed it to bonager*.deb.

I also think that it would be more logical to install bonager in Applications > System Tools.

---

### Post by AgenT on 2006-11-08
> **svasie said:**
> Great app for laptop users.Thank you.
> **svasie said:**
> on autostart keep it hidden until some mounts, possibly configurable, are remaining until next scan. Sounds interesting. However, I am not sure how this would be implemented. For example, right now it is possible for a user to click on the icon at any time and force a scan. This would not be possible if the icon was hidden - yet this may be what some people want. Also, if the icon was hidden, how would the user make it visible again? How would the user quit the program? 

The mounts will NOT be configurable. The reason is that this would 1) break the SAFE to use guarantee of the program and 2) break the honoring system defaults guarantee. I know some users would like to change the default and doing this is actually very easy (they don't need Bonager for that). However, this is NOT recommended and highly discouraged by Ubuntu developers. Bonager was made as a "compromise".

---

### Post by AgenT on 2006-11-08
> **mssever said:**
> The file attached to the original post has a .zip extension, which implies that it is a ZIP archive. This confused me when I got an error trying to unzip it (the file command told me that it's really a deb). Furthermore, the graphical frontend to dpkg refused to open the package (giving me a security warning) until I renamed it to bonager*.deb.You are correct, this does confuse users. However, one line below the Download link was a warning explaining why this was given the .zip extension. This warning no longer exists (see below).

I have [contacted ubuntu-geek]("http://ubuntuforums.org/showthread.php?t=295269") (forum owner) and asked him to add the ability to attach deb files in the forum. He agreed and has enabled deb attachments so this will no longer be an issue. THANK YOU ubuntu-geek!

This has been fixed with a new .deb file uploaded.

> **mssever said:**
>  I also think that it would be more logical to install bonager in Applications > System Tools.That was the original plan. However, by default Ubuntu has System Tools hidden. And because Bonager is a tray icon program, Accessories seemed like a decent place for it. In fact, Accessories in NOT where Bonager is told to be located, but under Application;_Utility_. Ubuntu throws all programs that are listed as a Utility in Accessories. Most, if not all, tray icon applications are also listed under Accessories (because they specify "Utility" as their category). Freedesktop.org desktop menu specifications was also reviewed which indicates "Utility" was the correct place for this type of program.

---

### Post by AgenT on 2006-11-08
> **paul6 said:**
> Here you go:
....Thank you for your support in getting this bug fixed.

Please post the output of:
```
sudo tune2fs -l /dev/hda1
cat /etc/fstab
cat /etc/fstab.pre-uuid
```

---

### Post by UbuWu on 2006-11-08
Would it be possible to add an option to scan either now or on next shutdown???

---

### Post by AgenT on 2006-11-08
> **UbuWu said:**
> Would it be possible to add an option to scan either now or on next shutdown???Short answer: No.

Long answer: This is not possible because the scan occurs after the filesystem is mounted, which by default happens when the computer starts. There is only one realistic way around this: force scan -> reboot -> scan -> shutdown. There are options in terms of when to shutdown. It is possible to shutdown the computer after the scan, but there is a problem with this: the shutdown will never be immedietly after the scan. Thus if a shutdown is forced it can cause major damage to the filesystem.

---

### Post by AgenT on 2006-11-09
I just realized that this may not be the proper forum for this application. Can anyone suggest what forum this thread should be in? Hardware & Laptops? Desktop Environments?

---

### Post by kvonb on 2006-11-09
Some suggestions:

1) Applet background:  Is there a way to make the applet background transparent?

2) Change the applet's icon when a scan is imminent, (see attachments for my mockup), ie when the user has requested a scan, OR when there is an impending scan that the system has scheduled (when the count is nearing max).  This helps give a warning.

3) Change the digit readout to be a countdown rather than 'times mounted', and also add a leading '0', (it bugs me when an applet changes it's size :D ), as the count reaches a low number, ie 2, the icon changes to a different colour to warn you that a scan is imminent, (again see attachments).

Excellent applet, well done :)

Regards,   Kev :)

PS attachments is not working for me right now, so these are links to the images)

[http://wamrfixit.homeip.net:8000/themes/bonager-01.png](http://wamrfixit.homeip.net:8000/themes/bonager-01.png)
[http://wamrfixit.homeip.net:8000/themes/bonager-02.png](http://wamrfixit.homeip.net:8000/themes/bonager-02.png)

---

### Post by AgenT on 2006-11-10
**[COLOR=Red]Bonager 0.2 is out! Now with Dapper and Edgy support![/COLOR]**

A lot of tweaks and and bug fixes. See first post for details and download link.

A [SIZE=5]BIG[/SIZE] **thank you** to [COLOR=Black]**kvonb**[/COLOR] for all of his help and support. He made Dapper support possible and gave very good bug reports and feedback.

---

### Post by paul6 on 2006-11-10
> **AgenT said:**
> **[COLOR=Red]Bonager 0.2 is out! Now with Dapper and Edgy support![/COLOR]**

A lot of tweaks and and bug fixes. See first post for details and download link.

A [SIZE=5]BIG[/SIZE] **thank you** to [COLOR=Black]**kvonb**[/COLOR] for all of his help and support. He made Dapper support possible and gave very good bug reports and feedback.

After upgrading to v0.2, all my previous problems seem to have disappeared :) Thanks for the great utility AgenT.

---

### Post by kvonb on 2006-11-10
Excellent!

Well done AgenT, look forward to any more useful apps you might have in the pipeline :).

Regards,  Kev :)

---

### Post by AgenT on 2006-11-10
> **kvonb said:**
> Well done AgenT.Again, thank you!

> **kvonb said:**
>  1) Applet background:  Is there a way to make the applet background transparent?
FREQUENTLY ASKED QUESTIONS (FAQ) has been updated with an answer to that question (as well as other questions).

---

### Post by .t. on 2006-11-11
Yeah: This is a great little app!

---

### Post by AgenT on 2006-11-11
> **.t. said:**
> Yeah: This is a great little app!Thank you. Are you using it on Feisty Fawn? Does everything seem to work?

---

### Post by .t. on 2006-11-11
Well, so far Feisty isn't too different from Edgy, and it's working fine!

---

### Post by kewldude606 on 2006-11-12
Is the source available for this app?  I would love to have a look-see.

---

### Post by DoctorMO on 2006-11-12
I believe it's python based which means that it's always available.

---

### Post by kewldude606 on 2006-11-12
> **DoctorMO said:**
> I believe it's python based which means that it's always available.

My bad.  I didn't even look after installing the .deb.

Thanks.

---

### Post by AgenT on 2006-11-13
> **kewldude606 said:**
> Is the source available for this app?  I would love to have a look-see.I would highly recommend NOT looking at the python source because it is not standard. You should not write code the way I wrote it. Bonager was my first Python application and I plan on rewriting it in a proper fashion.

---

### Post by AgenT on 2006-11-13
> **.t. said:**
> Well, so far Feisty isn't too different from Edgy, and it's working fine!
Updating FAQ with this information. Thank you.

---

### Post by DoctorMO on 2006-11-13
If it's his first appication then perhaps you can show him your revised versions with comments as to why it was changed?

---

### Post by kewldude606 on 2006-11-13
> **AgenT said:**
> I would highly recommend NOT looking at the python source because it is not standard. You should not write code the way I wrote it. Bonager was my first Python application and I plan on rewriting it in a proper fashion.

I wasn't looking for the coding, I was looking to see how it did what it did.  I now know that it just touches some files :).

---

### Post by AgenT on 2006-11-13
[SIZE=4]**Bonager 0.3 is out! **[/SIZE]

New fixes and features! See "What's New" for details. See FAQ (which was updated) for answers to questions you may have.

---

### Post by PapaWiskas on 2006-11-13
I cant tell if you have had a XFCE user test this out or not, so I will be downloading this tonight and give a whirl.  I run Xubuntu most of the time and dont see why this wouldn't work, I will post here to let you know.

---

### Post by AgenT on 2006-11-13
> **PapaWiskas said:**
> I cant tell if you have had a XFCE user test this out or not, so I will be downloading this tonight and give a whirl.  I run Xubuntu most of the time and dont see why this wouldn't work, I will post here to let you know.Taken from the FAQ:
>  Q: Does Bonager support XFCE (Xubuntu)?
A: I do not know. No one has tested this yet. It may work or it may not. You can always try it and remove it. If you decide to test it in XFCE, please post your results in this thread. Please post your results after you try Bonager out.

UPDATE: FAQ updated with "What are the requirements?"

---

### Post by PapaWiskas on 2006-11-13
Just installed it in XFCE and it is working.  One issue did pop up for some reason.  I had autostart set to on, rebooted and when the desktop loaded it had two Bonager icons loaded in the system tray/notification area.

---

### Post by .t. on 2006-11-14
This is because you have the program to auto-start in your GNOME and XFCE sessions, so XFCE loads both.

---

### Post by AgenT on 2006-11-14
Thank you PapaWiskas for posting your results and .t. for the solution. FAQ has been updated with the information both of you provided.

---

### Post by AgenT on 2006-11-14
> **kvonb said:**
> look forward to any more useful apps you might have in the pipeline You asked for it, so here goes:

[ParolaPass: The Password Generator]("http://www.ubuntuforums.org/showthread.php?t=299823")
ParolaPass is a secure password generator with support for many types of passwords. A very useful utility to fight against identity theft and crackers. Uses very powerful password generation algorithms. ParolaPass uses multiple algorithms depending on your needs.

Small, niche and useful applications. That is what I tried to create so far. Hopefully someone will benefit from ParolaPass.

---

### Post by AgenT on 2006-11-15
[SIZE=4]**[[COLOR=Purple]Bonager 0.4 is out![/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=295262")**[/SIZE]
Many bugs fixed and lots of code cleanup (makes the program run even smoother)

---

### Post by AgenT on 2006-11-16
Thread moved from Community Chat to Faqs, Howto, Tips & Tricks.

Tags updated.

If anyone finds any links broken or other anomalies (due to the move), please report them in this thread.

---

### Post by tzulberti on 2006-11-16
Great App...

---

### Post by autocrosser on 2006-11-16
Good looking App-I'll be autostarting it & see how it works---Thumbs up!!

---

### Post by canard on 2006-11-17
Hi,

Nice work man!

If i may, i'd make one or two comments. In my opinion, as i use it on my laptop which is rather small (11" screen) i don't need bonager to be in the tray icon at all time. So an interesting feature would be that as soon as you log into gnome the icon is shown on the tray and a window popups to ask you what you want to do. Let's say that it'll tell you how many mounts left there are, if you wan to force or skip a check at next boot. And then it'll ask you if you want it to stay in the tray or "disappear". 
What would also be interesting is that as you tell gnome to shut down the popup window appears again and recall the infos and your choices, and let you change what you'd want to do.

That will definitely be nice because the last time i decided to force a check at next boot i had forgotten about it. And then I wanted to show something to my boss but my laptop was off, and we had to wait 5 minutes before we could use it. And he was like "man, how can you say linux is more powerfull if it takes you 5-10 minutes to boot"!](*,) 

I don't know if this would be easy or not but in my opinion this will be an interesting feature as i don't really need to see bonager telling my how many mounts left i have all the time.

Anyway thanks for your cool app, and good luck!

---

### Post by McDuff on 2006-11-20
i would prefer to chose between "yes" and "no", when the application asks if i wanted to force a scan for the next boot. i'm not an english native speaker, but i suppose that in english the word "cancel" can be understood in the appropriate way in this question. but its translation in other languages doesnt necessarily cover all the same meanings, making it difficult to understand what to do.
but the app is very fine and useful. thanks!

---

### Post by AgenT on 2006-11-20
> **autocrosser said:**
> Good looking App-I'll be autostarting it & see how it works---Thumbs up!!
Thank you. Does it work? ;)

---

### Post by 56phil on 2006-11-20
AgenT - ***THANKS*** - Great app! I just loaded it and the important parts all work. When do you plan on fixing autostart?:D

---

### Post by AgenT on 2006-11-20
> **canard said:**
> Nice work man!Thank you.
> **canard said:**
> In my opinion, as i use it on my laptop which is rather small (11" screen) i don't need bonager to be in the tray icon at all time.Agreed... 
> **canard said:**
> So an interesting feature would be that as soon as you log into gnome the icon is shown on the tray and a window popups to ask you what you want to do. Let's say that it'll tell you how many mounts left there are, if you wan to force or skip a check at next boot. And then it'll ask you if you want it to stay in the tray or "disappear".  Great idea!.... however:
> **canard said:**
>  What would also be interesting is that as you tell gnome to shut down the popup window appears again and recall the infos and your choices, and let you change what you'd want to do.This is not possible as far as I know. Once shutdown is made, GNOME "freezes" and does not allow any program to function except to shutdown. Maybe this is wrong and if anyone has more information, please share.

> **canard said:**
>  I don't know if this would be easy or not but in my opinion this will be an interesting feature as i don't really need to see bonager telling my how many mounts left i have all the time.A few people requested this feature; however, you are the first person to give a potential solution to this.

---

### Post by AgenT on 2006-11-20
> **McDuff said:**
> i would prefer to chose between "yes" and "no", when the application asks if i wanted to force a scan for the next boot. i'm not an english native speaker, but i suppose that in english the word "cancel" can be understood in the appropriate way in this question. but its translation in other languages doesnt necessarily cover all the same meanings, making it difficult to understand what to do.
but the app is very fine and useful. thanks!Thank you for for your insight, it is very helpful. I will look into changing this.

Is there anything else that you feel a user that is not a native English speaker would have a hard time understanding?

---

### Post by AgenT on 2006-11-20
> **56phil said:**
> AgenT - ***THANKS*** - Great app! I just loaded it and the important parts all work. When do you plan on fixing autostart?:DThank you.

What is wrong with autostart? Please be specific as you are the first person that is reporting it broken and it works for me.

---

### Post by ciscosurfer on 2006-11-20
App works great.  Good Job!

---

### Post by McDuff on 2006-11-21
> **AgenT said:**
> 
Is there anything else that you feel a user that is not a native English speaker would have a hard time understanding?

no, that was the only thing i noticed.

if you would like it, i could provide you with a german translation of the strings.

---

### Post by AgenT on 2006-11-21
> **McDuff said:**
> no, that was the only thing i noticed.

if you would like it, i could provide you with a german translation of the strings.
Yes, please provide a German translation. Danke.

---

### Post by Ziggy72 on 2006-11-21
Thank you for this excellent program - easy to install & easy to use. A very useful tool :)

---

### Post by canard on 2006-11-21
> **AgenT said:**
> 
This is not possible as far as I know. Once shutdown is made, GNOME "freezes" and does not allow any program to function except to shutdown. Maybe this is wrong and if anyone has more information, please share.

A few people requested this feature; however, you are the first person to give a potential solution to this.

Hi,

Thanks for the answer, i was expecting that kind of thing. 
But would it be possible to detect when the user press the "quit" button that shows the "logout/shutdown/restart" window? And then if you can detect it, you can let's say postpone it and show bonager before? 
(ok as i'm writing this i guess that it's not easier than my first suggestion :mrgreen: )

Anyway i'll be pleased to see in the next version the other features that i have suggested.

And by the way, if you're interested i did a quick translation in french. I just put the modified /usr/bin/bonager file as an attachment to this post.
I don't have time to do a .deb file so you can just take it and do as you want.

---

### Post by McDuff on 2006-11-22
german translation of /usr/bin/bonager uploaded the same way canard did, as i have no idea how to build a .deb package (and at the moment no time to search for howtos).
didn't translate error-messages yet.
greetings
georg

---

### Post by AgenT on 2006-11-22
Thank you for the translations! There is no need to create a deb file.

---

### Post by AgenT on 2006-11-25
> **canard said:**
> Thanks for the answer, i was expecting that kind of thing. 
But would it be possible to detect when the user press the "quit" button that shows the "logout/shutdown/restart" window? And then if you can detect it, you can let's say postpone it and show bonager before? This is not possible. I have tried many approaches including trying to block shutdown until Bonager pops up giving a warning. It does not work.

This is why I have NOT removed the icon. However, I did make two big changes: 1) removed the number of mounts to save space making Bonager half the size and 2) made the Quit dialog easier and faster to use so that you can always quit Bonager (see FAQ on more information about quitting Bonager).

I am still trying to come up with a good solution to this problem.

---

### Post by AgenT on 2006-11-25
[SIZE=5][COLOR=RoyalBlue]**Bonager 0.5 is out!**[/COLOR][/SIZE]

See WHAT'S NEW and the updated FAQ for details. A [SIZE=5]BIG[/SIZE] THANK YOU to McDuff for his German translation and canard for his French translation. And thank you both for your great suggestions.

---

### Post by canard on 2006-11-25
Hi!
Here is the french translation for the new version 0.5, i also tranlsated the .desktop file.

You'll find both files in attachment.

See you!

---

### Post by canard on 2006-11-25
hey!
Nice idea to remove the boot number from the systray applet, i takes much less space now....
I guess what would be also interesting is to provide the localization as an option, don't you think?

And about the transparency of the systray icon, wouldn't it be possible to set the basckground color to be the same as the one of the panel rather than the colour of the gtk theme? (i guess there should be a way to link these two ones, since other stuff like nm-applet or gnome-power-manager can do it).

---

### Post by AgenT on 2006-11-25
Thank you for the translation. From now on, please use the included translate.txt file provided in the post (see FAQ for more information). It is easier for you and easier for me.

> **canard said:**
> I guess what would be also interesting is to provide the localization as an option, don't you think?No. The reason is that the translation should be chosen system wide, not in every single program. If you chose to have your system localization in French, every program that has French localization ability should be in French. I do not know of any program that has localization as an option within the actual  program and do not see any need for it.

If you are having trouble enabling French localization it may be because 1) there is a bug in Bonager or 2) you do not have the proper localization files. Please give your reasons for wanting localization to be an option.

I tested localization in German and it worked great. I even had two desktops running at the same time, one in English and one in German and Bonager worked how it was supposed to in both. That is, Bonager was in English on the English desktop and in German in the German desktop.

> **canard said:**
>  And about the transparency of the systray icon, wouldn't it be possible to set the basckground color to be the same as the one of the panel rather than the colour of the gtk theme? (i guess there should be a way to link these two ones, since other stuff like nm-applet or gnome-power-manager can do it).This was already discussed in a post above. A quick summery: I was told by one of the pygtk developers that this is not possible. My guess would be that nm-applet and gnome-power-manager do not use pygtk and are not python applications.

Thank you for you feedback, it is appreciated and makes Bonager that much better. :)

---

### Post by Loursalacampagne on 2006-11-26
It seems to be a useful app, but i am on the x86_64 architecture, and so it doesn't work...

Any solution ? :confused:

---

### Post by tatare99 on 2006-11-26
I installed the last version of Bonager and when I try to start the tool, I get the following error:

sed: can't read /var/cache/bonager/drive_info: No such file or directory
ERROR: Mount root entry is not valid
0

Can someone help me ?

Thanks in advance !

---

### Post by AgenT on 2006-11-26
> **Loursalacampagne said:**
> It seems to be a useful app, but i am on the x86_64 architecture, and so it doesn't work...

Any solution ? :confused:
What does not work? Installing? Running the program? Please be more specific and please provide the error that you get.

---

### Post by AgenT on 2006-11-26
> **tatare99 said:**
> I installed the last version of Bonager and when I try to start the tool, I get the following error:

sed: can't read /var/cache/bonager/drive_info: No such file or directory
ERROR: Mount root entry is not valid
0

Can someone help me ?

Thanks in advance !
Is this your first time running Bonager or did a previous version of Bonager work for you?

Please give me the output of:
```
cat /etc/fstab
cat /var/cache/bonager/drive_info
cat /var/cache/bonager/fstab_info
```

---

### Post by magisterludi on 2006-11-26
I haven't seen any source packages. Ubuntu is an open source project. It would be nice if you make it available, too.

---

### Post by AgenT on 2006-11-26
> **magisterludi said:**
> I haven't seen any source packages. Ubuntu is an open source project. It would be nice if you make it available, too.If you are looking for the Ubuntu source code this is not the thread to ask for it. 

Bonager has nothing to do with Ubuntu as Ubuntu is just a distribution and Bonager should work on any Debian based distribution. Bonager is released under the GPLv2 or above license. 

If your question referred to getting the source of Bonager, please read the thread dealing with that above.

Hopefully that answers your question (because I am not exactly sure what it is).

---

### Post by tatare99 on 2006-11-26
> **AgenT said:**
> Is this your first time running Bonager or did a previous version of Bonager work for you?

Please give me the output of:
```
cat /etc/fstab
cat /var/cache/bonager/drive_info
cat /var/cache/bonager/fstab_info
```

Yep, it's my time running Bonager.
I never tried to run a previous version.

```
**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


**cat /var/cache/bonager/drive_info**
cat: /var/cache/bonager/drive_info: No such file or directory

**cat /var/cache/bonager/fstab_info**
cat: /var/cache/bonager/fstab_info: No such file or directory

```

Thanks for your help.

---

### Post by AgenT on 2006-11-26
> **tatare99 said:**
> ```
**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


**cat /var/cache/bonager/drive_info**
cat: /var/cache/bonager/drive_info: No such file or directory

**cat /var/cache/bonager/fstab_info**
cat: /var/cache/bonager/fstab_info: No such file or directory

```Thanks for your help.Are you running Dapper?

Can you give me the output of:
```
sudo /usr/sbin/bonager_check
```

---

### Post by tatare99 on 2006-11-26
> **AgenT said:**
> Are you running Dapper?

Can you give me the output of:
```
sudo /usr/sbin/bonager_check
```

Yes, I'm running Dapper.
```
sudo /usr/sbin/bonager_check
``` returns nothing...
Should I try to re-install Bonager ?

---

### Post by AgenT on 2006-11-26
> **tatare99 said:**
> Yes, I'm running Dapper.
```
sudo /usr/sbin/bonager_check
``` returns nothing...
Should I try to re-install Bonager ?If it returns nothing it should mean that it worked and you should be able to have the two files mentioned above. Please see what output you get with the following, and if it says file does not exist, something is wrong either in your fstab on in how Bonager reads it:
```
 cat /var/cache/bonager/drive_info
cat /var/cache/bonager/fstab_info
```
If the above do show information, restart Bonager to see if it works.

---

### Post by Loursalacampagne on 2006-11-26
> **AgenT said:**
> What does not work? Installing? Running the program? Please be more specific and please provide the error that you get.

When I clic on the .deb, i get the message 'Error: Wrong architecture: 'i386''

And when i try to install it with the terminal, i get :
```
sudo dpkg -i Desktop/bonager_0.5_i386.deb 
dpkg: error processing Desktop/bonager_0.5_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 Desktop/bonager_0.5_i386.deb

```

Thanks for help

---

### Post by tatare99 on 2006-11-26
> **AgenT said:**
> If it returns nothing it should mean that it worked and you should be able to have the two files mentioned above. Please see what output you get with the following, and if it says file does not exist, something is wrong either in your fstab on in how Bonager reads it:
```
 cat /var/cache/bonager/drive_info
cat /var/cache/bonager/fstab_info
```
If the above do show information, restart Bonager to see if it works.

Ok... this time it worked... I didn't change anything... this is weird but ok, it works. Thanks ! (Well... if you could explain what happened, that'd be great :))

---

### Post by mssever on 2006-11-26
> **Loursalacampagne said:**
> When I clic on the .deb, i get the message 'Error: Wrong architecture: 'i386''

And when i try to install it with the terminal, i get :
```
sudo dpkg -i Desktop/bonager_0.5_i386.deb 
dpkg: error processing Desktop/bonager_0.5_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 Desktop/bonager_0.5_i386.deb

```Thanks for help

Looks like Architecture: all should be set in debian/control.

---

### Post by mssever on 2006-11-26
I just installed bonager 0.5 on my Dapper machine (last time I tried, bonager didn't support dapper). When I try to run it, I get the following error: ```
sed: can't read /var/cache/bonager/drive_info: No such file or directory
ERROR: Mount root entry is not valid
0
``` and bonager won't start (it exits with a 0 exit status--probably should be nonzero, given the error condition). When I checked, I discovered that the directory /var/cache/bonager doesn't exist.

For reference, here's my fstab: ```
[FONT=Courier New]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>          <options>                               <dump>  <pass>
proc            /proc           proc            defaults                                0       0
/dev/hda4       /               ext3            defaults,errors=remount-ro              0       1
/dev/hda3       /home           ext3            defaults                                0       2
#/dev/hda1      /media/hda1     ntfs            defaults,nls=utf8,umask=007,gid=46,ro   0       1
/dev/hda1       /media/hda1     ntfs-3g         defaults,locale=en_US.utf8              0       1
/dev/hda2       none            swap            sw                                      0       0
/dev/hdc        /media/cdrom0   udf,iso9660     user,noauto                             0       0

#NFS Stuff
192.168.1.50:/home/scott/webmaster      /home/scott/webmaster   nfs     rw,hard,intr    0 0
192.168.1.50:/                          /media/scott-desktop    nfs     rw,hard,intr    0 0
192.168.1.50:/home/scott/bin    /media/scott-desktop/home/scott/bin     nfs     rw,hard,intr    0 0
192.168.1.50:/media/EXTERNAL_HD         /media/EXTERNAL_HD      nfs     rw,hard,intr    0 0[/FONT]
```

---

### Post by AgenT on 2006-11-26
[SIZE=4]**Bonager 0.5.1 is out!**[/SIZE]
Small fix to enable installation on all architectures, including amd64 and powerpc.

** mssever**,
Another user experienced your problem. This is probably a deb packaging problem and I will look into it later. Read starting with comment #79 for a solution. And that 0 is not an exit code - those last two lines are created by my own custom debug code to make debugging Bonager easier. ;) [UPDATE: the above post will not solve your issue, read below for more information]

[SIZE=5]** UPDATE (EVERYONE PLEASE READ THIS):**[/SIZE]
This bug is pretty severe as it disables Bonager from retreiving partition information. It is times like this that it's good to know Bonager is SAFE and cannot harm your system. This bug makes Bonager run but it will not know what your system status is. This bug crept into version 0.5. I  do not have time right now to fix it but **EVERYONE** should do this (only need to do this one time after Bonager is installed or upgraded):
```
sudo update-rc.d bonager defaults
sudo /etc/init.d/bonager start
```

---

### Post by mssever on 2006-11-26
> **AgenT said:**
> And that 0 is not an exit code - those last two lines are created by my own custom debug code to make debugging Bonager easier. ;) 

Right. The reason I know that it was exiting 0 is that I've customized my prompt to display the exit status of the last command ($?).

Your fix worked for me. Nice app.

---

### Post by McDuff on 2006-11-27
if i understood right, the program should choose the correct localization on its start, but neither french nor german localization seem to be included. (0.5.1)

---

### Post by McDuff on 2006-12-05
where is AgenT? i hope he's still alive.

i'm missing the localized files in the package and the file for translations in the first post.

---

### Post by AgenT on 2006-12-05
> **McDuff said:**
> where is AgenT? i hope he's still alive.

Not dead but very busy.

---

### Post by AgenT on 2006-12-05
[SIZE=5][B]Bonager 0.5.2 is out!

[/B][/SIZE]Bug fix release. No new features. This release should fix the localization problem *and* the post-install problem in the above posts.

Both problems were tested and the test showed that they are now fixed. If someone is still experiencing these problems, please post here.

---

### Post by lazyd2 on 2006-12-05
I get```
ERROR: Mount root entry is not valid
0
```
[Edgy]

---

### Post by AgenT on 2006-12-05
> **lazyd2 said:**
> I get```
ERROR: Mount root entry is not valid
0
```[Edgy]
Does this fix your problem?:
```
 sudo update-rc.d bonager defaults
sudo /etc/init.d/bonager start
```

---

### Post by lazyd2 on 2006-12-05
> **AgenT said:**
> Does this fix your problem?:
```
 sudo update-rc.d bonager defaults
sudo /etc/init.d/bonager start
```No, still the same message ](*,)

---

### Post by AgenT on 2006-12-05
> **lazyd2 said:**
> No, still the same message ](*,)
What is the output of these commands:
```
 cat /etc/fstab
cat /var/cache/bonager/drive_info
cat /var/cache/bonager/fstab_info
```

---

### Post by atlas95 on 2006-12-06
Could you make the systray icon transparent please ? :)
See the -Big sorry- screenshot ;)
[[img]http://img145.imageshack.us/img145/5755/capturesw8.th.png[/img]](http://img145.imageshack.us/my.php?image=capturesw8.png)

Best Regards

---

### Post by lazyd2 on 2006-12-06
> **AgenT said:**
> What is the output of these commands:
```
 cat /etc/fstab
cat /var/cache/bonager/drive_info
cat /var/cache/bonager/fstab_info
```Here's the /etc/fstab. The other 2 commands do not give any output...:-k

---

### Post by ArsGeek on 2006-12-06
Hi,

I've just installed this and I'm already loving it.  I'm going to put a post up on my blog (ArsGeek) to let more folks know about it.

Great job!

---

### Post by AgenT on 2006-12-06
> **atlas95 said:**
> Could you make the systray icon transparent please ? :)
Best Regards
Malheureusement, ce n'est pas possible. Sous "FREQUENTLY ASKED QUESTIONS":
> Q: Bonager's tray does not use my system tray colour, why? [or, Bonager's tray is not transparent, why?]
A: This is because the tray is not using the theme's default colour. Bonager does change its tray background colour, but only to the theme's default background colour. This is a limitation that has nothing to do with Bonager and therefore cannot be changed. One workaround would be to switch the tray colour back to theme default and change the theme default colour to the colour wanted.

---

### Post by AgenT on 2006-12-06
> **lazyd2 said:**
> Here's the /etc/fstab. The other 2 commands do not give any output...:-kThat is one HUGE fstab file. ;)

Here are the partitions that have fsck (the scan that happens at boot) enabled:
```
# /dev/sda5
UUID=0fcc5ebf-c157-4f97-8119-38aa083d693e /               reiserfs defaults          0       1
# /dev/sda6
UUID=023e1598-cc94-4ddd-bf13-88ff2fcbfcb7 /home           reiserfs defaults        0       2
# /dev/sdc1
UUID=2f3562e4-a63f-4dc0-b6e7-7664567f697d /media/sdc1     reiserfs defaults        0       2
```Notice a trend in those partitions?  They all are reiserfs. Bonager only supports ext3. Why only ext3? Because the tool that shows statistics about mounts that is used by Bonager only supports ext*.

Is it possible to add reiserfs support to Bonager? Yes, unless there is no reiserfs stat tool. Am I willing to add reiserfs support? It is definitely not on my to-do list, but I can look into it. The problem is that I do not have a reiserfs partition or the reiserfs stat program to test with.

I will add a FAQ entry about this. Thank you for your contribution.

---

### Post by AgenT on 2006-12-06
> **ArsGeek said:**
> Hi,

I've just installed this and I'm already loving it.  I'm going to put a post up on my blog (ArsGeek) to let more folks know about it.

Great job!
Please post a link to the article when it is posted.

---

### Post by Old Pink on 2006-12-06
One minor criticism:
[IMG]http://www.filehive.com/files/1206/Screenshot-1.png[/IMG]

^^ The icon isn't transparent, and looks disgusting should it be used on a non-default/transparent panel. This alone will stop me using Bonager.

Also, an option to quickly check the amount of boots remaining without having the application running in a terminal would be appreciated, is this possible? :)

---

### Post by lazyd2 on 2006-12-06
> **AgenT said:**
> That is one HUGE fstab file. ;)

Here are the partitions that have fsck (the scan that happens at boot) enabled:
```
# /dev/sda5
UUID=0fcc5ebf-c157-4f97-8119-38aa083d693e /               reiserfs defaults          0       1
# /dev/sda6
UUID=023e1598-cc94-4ddd-bf13-88ff2fcbfcb7 /home           reiserfs defaults        0       2
# /dev/sdc1
UUID=2f3562e4-a63f-4dc0-b6e7-7664567f697d /media/sdc1     reiserfs defaults        0       2
```Notice a trend in those partitions?  They all are reiserfs. Bonager only supports ext3. Why only ext3? Because the tool that shows statistics about mounts that is used by Bonager only supports ext*.

Is it possible to add reiserfs support to Bonager? Yes, unless there is no reiserfs stat tool. Am I willing to add reiserfs support? It is definitely not on my to-do list, but I can look into it. The problem is that I do not have a reiserfs partition or the reiserfs stat program to test with.

I will add a FAQ entry about this. Thank you for your contribution.

Thanks for the reply. I'll try it with my 64-bit ubuntu then:-D

---

### Post by AgenT on 2006-12-06
> **Old Pink said:**
> One minor criticism:
[IMG]http://www.filehive.com/files/1206/Screenshot-1.png[/IMG]

^^ The icon isn't transparent, and looks disgusting should it be used on a non-default/transparent panel. This alone will stop me using Bonager.This was already answered a few times in this thread, including about 3 posts above yours. The answer is also in the FAQ.

> **Old Pink said:**
>  Also, an option to quickly check the amount of boots remaining without having the application running in a terminal would be appreciated, is this possible? :)Do not run Bonager from terminal or run it with a &. Run it using the menu so that it is in the tray only. You can always launch Bonager and then quit it (right-click). I made quiting very quick and easy for this reason. Just right-click on icon -> press return key. Maybe I do not understand your question.

Thank you for your feedback.

---

### Post by ciscosurfer on 2006-12-07
@AgenT,

I could've sworn that b/c of Bonager, my reiserFS partiton was scanned...at least it said it was....what gives if it's not implemented?  I'm very curious about this.  I'll check it again, but I am 99% sure my reiserFS partition was checked.

---

### Post by Old Pink on 2006-12-07
> **AgenT said:**
> Do not run Bonager from terminal or run it with a &. Run it using the menu so that it is in the tray only. You can always launch Bonager and then quit it (right-click). I made quiting very quick and easy for this reason. Just right-click on icon -> press return key. Maybe I do not understand your question.

Thank you for your feedback.

I don't run it from the terminal. What I'm saying is I don't want the ugly icon in my panel all day just to show how many boots are left. 

If I could run "bonager -c" or "bonager --check" in terminal, and it just gave me this information in the terminal, this would be ideal. 

I'm just saying having an application running constantly for something you only check once or twice a week seems silly. :rolleyes:

As for the FAQ:> This is because the tray is not using the theme's default colour. Bonager does change its tray background colour, but only to the theme's default background colour. This is a limitation that has nothing to do with Bonager and therefore cannot be changed. One workaround would be to switch the tray colour back to theme default and change the theme default colour to the colour wanted.I'm sure the "limitation" has something to do with Bonager, why can AmaroK, aMSN, GAIM, etc. do it but you can't?

---

### Post by AgenT on 2006-12-07
> **ciscosurfer said:**
> @AgenT,

I could've sworn that b/c of Bonager, my reiserFS partiton was scanned...at least it said it was....what gives if it's not implemented?  I'm very curious about this.  I'll check it again, but I am 99% sure my reiserFS partition was checked.
Forcing on delaying a scan should work on any Linux file system. However, Bonager is not able to read the filesystem information and thus cannot give information and warnings about impending scans.

---

### Post by AgenT on 2006-12-07
> **Old Pink said:**
> If I could run "bonager -c" or "bonager --check" in terminal, and it just gave me this information in the terminal, this would be ideal. 

I'm just saying having an application running constantly for something you only check once or twice a week seems silly. :rolleyes:I agree and was looking for a solution to this. There are many posts in this thread about this topic. Your solution is a very good one and I will try to implement it into the next release. Thank you for your sugestions.

> **Old Pink said:**
>  As for the FAQ:I'm sure the "limitation" has something to do with Bonager, why can AmaroK, aMSN, GAIM, etc. do it but you can't?The FAQ was updated with an explanation of this. Bonager uses pygtk and the egg tray icon module. Not all programs use pygtk. The limitation is with pygtk and this was confirmed by one of the pygtk developers.

---

### Post by Old Pink on 2006-12-07
> **AgenT said:**
> I agree and was looking for a solution to this. There are many posts in this thread about this topic. Your solution is a very good one and I will try to implement it into the next release. Thank you for your sugestions.

The FAQ was updated with an explanation of this. Bonager uses pygtk and the egg tray icon module. Not all programs use pygtk. The limitation is with pygtk and this was confirmed by one of the pygtk developers.

OK, thanks. :) 

Any chance of this entering the repositories?

---

### Post by originof on 2006-12-07
i take this...
> 
manuel@unix:~$ bonager
ERROR: Mount root entry is not valid
0

manuel@unix:~$ sudo bonager
Password:
ERROR: Mount root entry is not valid
0

manuel@unix:~$ 

I have XFS...
Is it supported ?

---

### Post by AgenT on 2006-12-07
> **Old Pink said:**
> Any chance of this entering the repositories?
Not right now, but I do plan on submitting it to Debian once it is more polished and the releases are not so frequent.

---

### Post by AgenT on 2006-12-07
> **originof said:**
> i take this...


I have XFS...
Is it supported ?
The answer to this question is in the "Frequently Asked Questions" of post #1.

---

### Post by da_foz on 2006-12-07
Seemed to work fine for me, thanks:)

I took a quick look around but did not see anything so I shall ask.
Does fsck make a log file anywhere?  I am curious to check the results of the scan.

---

### Post by AgenT on 2006-12-07
> **da_foz said:**
> Seemed to work fine for me, thanks:)Thank you.

> **da_foz said:**
> I took a quick look around but did not see anything so I shall ask.
Does fsck make a log file anywhere?  I am curious to check the results of the scan.On Linux, most if not all system log files are found in /var/log. the fsck log files are found here: ```
/var/log/fsck/
```

---

### Post by AgenT on 2006-12-11
[SIZE=5][B][COLOR=Purple]Bonager 0.6 is out!

[/COLOR][/B][/SIZE]This release fixes a major bug and contains two new features. Both features are most requested.

New Features:[LIST]
[*][SIZE=4]Bonager without Tray Icon![/SIZE]
[*][SIZE=4]Bonager Quick Output (via command line)![/SIZE][/LIST]Thank you everyone for your suggestions and help in making Bonager a better program. A [SIZE=5]BIG[/SIZE] thank you to **Old Pink** for his great ideas on how to implement these new features.

For instructions on how to use the command line arguments, type the following at the command line (terminal):
```
bonager --help
```Output:
```
$ bonager --help
usage: bonager [options]

options:
  -h, --help     show this help message and exit
  -c, --check    print number of mounts remaining until next scan
  -t, --no-tray  disable tray icon
```

---

### Post by AgenT on 2006-12-15
I have noticed that no one has responded to this thread since the announcement of Bonager 0.6.0. Is anyone still interested in this project?

The plan was to clean up the current code, fix a few more outstanding issues and make Bonager compatible with KDE, GNOME and any other Window Manager. Currently, Bonager only works in GNOME but it seems possible to make it work without GNOME. There were also plans on possibly supporting non-ext3 filesystems.

My question is: does anyone still use Bonager? If so, what would you like to see improved? If no one uses it, maybe it is time to abandon this project.

---

### Post by ciscosurfer on 2006-12-15
> **AgenT said:**
> I have noticed that no one has responded to this thread since the announcement of Bonager 0.6.0. Is anyone still interested in this project?

The plan was to clean up the current code, fix a few more outstanding issues and make Bonager compatible with KDE, GNOME and any other Window Manager. Currently, Bonager only works in GNOME but it seems possible to make it work without GNOME. There were also plans on possibly supporting non-ext3 filesystems.

My question is: does anyone still use Bonager? If so, what would you like to see improved? If no one uses it, maybe it is time to abandon this project.I've used it in the past and I suppose I found it useful.  But it's just as quick for me to issue a few commands in a shell and accomplish the same thing.  For those who like using point-and-click apps (and I know you just instroduced command line access to it, but...), then it deserves attention, for sure.  Adding support for other DE's as well as other FS's will probably make me come back to this project.  For right now, though, I don't really have a need for it. That being said, I think you did a fantastic job in creating the app and my thanks to you are in order for providing an alternative method to check disks =D>

---

### Post by lazyd2 on 2006-12-16
Using it and it works great. 
Please keep up the good work!=D>

---

### Post by Loursalacampagne on 2006-12-16
> **lazyd2 said:**
> Using it and it works great. 
Please keep up the good work!=D>

+1

---

### Post by .t. on 2006-12-16
I use it. I only don't respond as I've nothing to complain about. :D

But what I really want is a transparent icon - it's the only applet that's not atm on my panel.

---

### Post by autocrosser on 2006-12-16
As above---no problem=no comments

Great Little App!!!

---

### Post by AgenT on 2006-12-27
I was just made aware that there are potential Bonager users that are in doubt whether or not Bonager is [freedom software]("http://www.gnu.org/philosophy/"). Bonager is freedom software. Bonager has always been freedom software. Bonager is licensed under the GPLv2 and has always been licensed under the [GPLv2]("http://www.gnu.org/copyleft/gpl.html"). Every source code file has the standard GPLv2 preamble and the standard License file contains the standard GPLv2 text usually included in the License file.

I have updated the first post of this thread to make this more clear.

---

### Post by apalacheno on 2006-12-28
Great and very useful app!
Would be nice to have it in the repos! Do you consider creating a wiki page for bonager?

Cheers,
apalacheno

---

### Post by .t. on 2006-12-28
Where is the source deb?

It won't get into universe unless you follow the instructions outlined at [https://wiki.ubuntu.com/MOTU/Packages/New](https://wiki.ubuntu.com/MOTU/Packages/New)

---

### Post by AgenT on 2006-12-28
The source debs are on my computer. I do not post them because 1) if you want the source, just extract the normal deb and 2) this forum has a 5 file limitation per post.

To extract the deb, you do not need a deb based system, apt or even dpkg. A deb file is just a plain ar archive file with a renamed extension. And the the deb file archive, when extracted, will provide all the files that the orig.tar.gz archive has because nothing is compiled. 

It takes as much effort to extract an ar archive as it does a tar. You can even use the GNOME fileroller to extract it. ar is available on just about every Linux system because it is part of the GNU utitlites. If you can tar, you can ar (that should be a slogan!).

Another reason for not including the orig.tar.gz, .dsc or source deb files is the forum file upload limit. Only 5 files maximum per post. There are ways of getting around that, but it's a hassle when doing updates.

I do not intend on submitting the current version of Bonager into the official Debian and Ubuntu repositories. My reasons are outlined in a post above.

I also do not intend on creating a wiki for Bonager right now. I would rather spend that time creating other programs and improving Bonager.

If you would like the source deb or orig.tar.gz file, please private message me and I will send them to you.

---

### Post by .t. on 2006-12-28
OK. That's cool. Just people would like it to be in Universe, I think.

---

### Post by AgenT on 2006-12-28
> **.t. said:**
> OK. That's cool. Just people would like it to be in Universe, I think.
So would I. However, I do not think Bonager is ready for that. Remember, being in Universe means being stuck to that version for 6 months.

And if someone would like to create a wiki page for Bonager, please go ahead. I can answer any questions that anyone may have.

---

### Post by Lunar_Lamp on 2006-12-28
Is it possible to get this to look after several partitions? I'm sure it is, but at the moment even though I know I have 3 ext3 partitions (and one swap), it just tells me I have 13 mounts until next scan.  I'd like to be able to see figures for all partitions!  (I see that support for multiple partitions was in 0.3 - but I don't see how I can enable any option to show me information about more than 1 partition at once!).

---

### Post by AgenT on 2006-12-28
> **Lunar_Lamp said:**
> Is it possible to get this to look after several partitions? I'm sure it is, but at the moment even though I know I have 3 ext3 partitions (and one swap), it just tells me I have 13 mounts until next scan.  I'd like to be able to see figures for all partitions!  (I see that support for multiple partitions was in 0.3 - but I don't see how I can enable any option to show me information about more than 1 partition at once!).
Bonager is smart enough to look at all of your partitions and calculate when the next most recent scan will occur.

To use your example, you have 13 mounts left until your next most recent scan will occur. When you allow Bonager to manage when your next scan occurs, either by forcing your next scan now or by choosing [Yes] or [No] when Bonager warns you of the impending scan, the next scan will reset all of your partitions' mount count. This means that if right now you have 3 partitions, the first having 13 mounts remaining, the second 14 and the third 15, after the next scan all three will reset. Thus after the scan you should see "29 mounts remaining". This is assuming all three partitions are set to a scan every 30 mounts.

As far as forcing Bonager to show you all of your partition statistics: this is not possible. If enough people ask for it I will implement this feature.

Please keep in mind that there are limitations. Thus far, Bonager only support ext2 and ext3 partitions. SWAP partitions never evoke fsck.

If you have any further questions, please do not hesitate to ask.

---

### Post by apalacheno on 2006-12-29
Hi AgenT!
Is it possible to reduce the memory footprint? System Monitor tells me that Bonager consumes 4 MB of memory; that seems a bit much to me for a program that does nothing more than sit in the background and show the mount counts.

By the way, if a check is forced and Bonager resets the mount count for all partitions, will all partitions get checked or only the one with the most mountcounts?

Cheers,
apalacheno

---

### Post by AgenT on 2006-12-29
> **apalacheno said:**
> Hi AgenT!
Is it possible to reduce the memory footprint? System Monitor tells me that Bonager consumes 4 MB of memory; that seems a bit much to me for a program that does nothing more than sit in the background and show the mount counts.I will see what I an do.

> **apalacheno said:**
>  By the way, if a check is forced and Bonager resets the mount count for all partitions, will all partitions get checked or only the one with the most mountcounts?All partitions are scanned.

---

### Post by Lunar_Lamp on 2006-12-29
> **AgenT said:**
> Bonager is smart enough to look at all of your partitions and calculate when the next most recent scan will occur.

To use your example, you have 13 mounts left until your next most recent scan will occur. When you allow Bonager to manage when your next scan occurs, either by forcing your next scan now or by choosing [Yes] or [No] when Bonager warns you of the impending scan, the next scan will reset all of your partitions' mount count. This means that if right now you have 3 partitions, the first having 13 mounts remaining, the second 14 and the third 15, after the next scan all three will reset. Thus after the scan you should see "29 mounts remaining". This is assuming all three partitions are set to a scan every 30 mounts.

As far as forcing Bonager to show you all of your partition statistics: this is not possible. If enough people ask for it I will implement this feature.

Please keep in mind that there are limitations. Thus far, Bonager only support ext2 and ext3 partitions. SWAP partitions never evoke fsck.

If you have any further questions, please do not hesitate to ask.

Sorry, I know that swap partitions don't get fsck'd, didn't mean to give that impression.  I'll have a look at the source code and see if I can make a patch myself to do what I want (and then give it to you if I manage it).  I'd definitely like to be able to view/control all valid partitions!

---

### Post by AgenT on 2006-12-29
> **Lunar_Lamp said:**
> Sorry, I know that swap partitions don't get fsck'd, didn't mean to give that impression.  I'll have a look at the source code and see if I can make a patch myself to do what I want (and then give it to you if I manage it).  I'd definitely like to be able to view/control all valid partitions!
Warning: the source code is a mess. The next release will have it all re-written. But your patch will be very much appreciated and I will incorporate it into the next release if applicable. So please do **not** think your work will go to waste if you write a patch: it will not.

---

### Post by Rinzwind on 2007-01-07
> **ArsGeek said:**
> Hi,

I've just installed this and I'm already loving it.  I'm going to put a post up on my blog (ArsGeek) to let more folks know about it.

Great job!

I found this app cuz of above post on the blog :)

- Great app TS :)
- Great website ArsGeek :)

---

### Post by Rinzwind on 2007-01-08
Maybe something to think about:

If you'd make it so that inside the icon the number of 'mounts to go' would be shown I think it would save people time (otherwise you need to go over to the icon to see the tooltip with the number of 'mounts to go'.

---

### Post by AgenT on 2007-01-08
> **Rinzwind said:**
> Maybe something to think about:

If you'd make it so that inside the icon the number of 'mounts to go' would be shown I think it would save people time (otherwise you need to go over to the icon to see the tooltip with the number of 'mounts to go'.
Thank you for your input. There was something similar in the first release: the number was right next to the icon, but many people complained that it wasted space.

How would the number fit within the icon? It would have many problems visually I think.

---

### Post by Richard Kut on 2007-01-08
Hello! I would like to try your application, but I am hooked on Kubuntu. Please add my name to the list of people that would very much like a KDE port of this applet. Thanks in advance.

---

### Post by Lunar_Lamp on 2007-01-08
To be honest, I would have expected this to run on kde if you have the right gnome libraries installed.

---

### Post by AgenT on 2007-01-08
> **Lunar_Lamp said:**
> To be honest, I would have expected this to run on kde if you have the right gnome libraries installed.
In truth it is probably not worth it to install such a small application with half of GNOME. Not to mention that running this application would also mean running some of those libraries. Another problem is with the tray icon: I am not sure if the tray library works with KDE's panel.

The next release of Bonager will be an almost complete re-write and will use a toolkit that works on any DE and WM that is standards compliant (most are, including GNOME & KDE). It will also have almost no library requirements that are not already installed by default on every system with python.

Unfortunately I do not have much time for Bonager, but work is progressing.

---

### Post by earobinson on 2007-01-09
Can we get the source code?

Edit: nevermind

---

### Post by bull8042 on 2007-01-10
> **AgenT said:**
> In truth it is probably not worth it to install such a small application with half of GNOME. Not to mention that running this application would also mean running some of those libraries. Another problem is with the tray icon: I am not sure if the tray library works with KDE's panel.

The next release of Bonager will be an almost complete re-write and will use a toolkit that works on any DE and WM that is standards compliant (most are, including GNOME & KDE). It will also have almost no library requirements that are not already installed by default on every system with python.

Unfortunately I do not have much time for Bonager, but work is progressing.

WHOOHOO!!! I have read through 15 pages of posts hoping to get to one like this. I too am hooked on KDE and this alone is keeping me from installing Bonager. Keep up the good work.
Bull

---

### Post by Rinzwind on 2007-01-10
> **AgenT said:**
> Thank you for your input. There was something similar in the first release: the number was right next to the icon, but many people complained that it wasted space.

How would the number fit within the icon? It would have many problems visually I think.

Can't you just put a digit over the icon?
Or what might be cool too: have black dots inside the green counting down from 5 or 10. Like a countdown :)

13 mounts till next scan :mrgreen: 

I like it alot AgenT!!! :)

---

### Post by AgenT on 2007-01-10
> **Rinzwind said:**
> Can't you just put a digit over the icon?
Or what might be cool too: have black dots inside the green counting down from 5 or 10. Like a countdown :)

13 mounts till next scan :mrgreen: 

I like it alot AgenT!!! :)
Adding a number inside the icon would definitely be visually displeasing. The icon is just not made to have any text on top of it. Using a different method, however, is definitely possible.

Your dot idea sounds good. Also maybe a gradual color change, with a big leap in color going to red when 1 mount is remaining.

What does everyone think?

---

### Post by rocco on 2007-01-11
When I try to start bonager from command line I got the message

ERROR: Mount root entry is not valid
0

---

### Post by AgenT on 2007-01-12
> **rocco said:**
> When I try to start bonager from command line I got the message

ERROR: Mount root entry is not valid
0
You most likely either do not use the ext3 filesystem on your partitions requiring fsck, have fsck disabled or both. If this is not the case, a few people have already had this problem. Just search for that error in this thread.

If you still are having problems, post your /etc/fstab config (in code tags).

---

### Post by dixonstalbert on 2007-01-17
hello

I am having trouble with bonager on my dapper install.

package installer reported no errors on install

The tray icon starts, runs for about 14 seconds with 'starting' icon  , then dies. clicking right or left mouse button has no effect. 

dmesg, syslog report no errors. system monitor says bonager still in memory but sleeping.

here is output of commands you suggested to others:
```
dixon2@athlon:~$ cat /var/cache/bonager/drive_info
/ 19 30
/media/hda7 6 30
dixon2@athlon:~$ cat /var/cache/bonager/fstab_info
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /media/hda7     ext3    defaults        0       2

dixon2@athlon:~$ bonager -c
10

```

What can I do to find out what went wrong?

---

### Post by AgenT on 2007-01-17
> **dixonstalbert said:**
> hello

I am having trouble with bonager on my dapper install.

package installer reported no errors on install

The tray icon starts, runs for about 14 seconds with 'starting' icon  , then dies. clicking right or left mouse button has no effect. 

dmesg, syslog report no errors. system monitor says bonager still in memory but sleeping.

here is output of commands you suggested to others:
```
dixon2@athlon:~$ cat /var/cache/bonager/drive_info
/ 19 30
/media/hda7 6 30
dixon2@athlon:~$ cat /var/cache/bonager/fstab_info
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /media/hda7     ext3    defaults        0       2

dixon2@athlon:~$ bonager -c
10

```What can I do to find out what went wrong?
Sounds like a GTK problem. Everything you posted seems normal. What about running Bonager from the command line? What is the output, from the time it starts to the time it dies?

What window manager are you using? Metacity, the default wm for GNOME or something else?

---

### Post by apalacheno on 2007-01-18
When I try to force a fsck upon next boot (right click on the tray icon; 'Force a scan for the next boot?' -> Yes), nothing happens when rebooting. Ubuntu starts as always.

Any idea why no check is performed?

Cheers,
apalacheno

---

### Post by AgenT on 2007-01-18
> **apalacheno said:**
> When I try to force a fsck upon next boot (right click on the tray icon; 'Force a scan for the next boot?' -> Yes), nothing happens when rebooting. Ubuntu starts as always.

Any idea why no check is performed?

Cheers,
apalacheno
Please include the output of the following commands wrapped in code tags:
```
$ cat /etc/fstab
$ cat /var/cache/bonager/drive_info
$ cat /var/cache/bonager/fstab_info
$ bonager -c
```

---

### Post by apalacheno on 2007-01-18
Hi AgenT,

$ cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e8099fca-434e-4acd-bc79-065957ca020f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=9e4aa25d-1b2e-417a-9de4-c28f4c725a43 /home           ext3    defaults        0       2
# /dev/sda2
UUID=229cff06-4857-44a6-9dd6-4a744ea5612b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

$ cat /var/cache/bonager/drive_info:
```
/ 22 30
/home 22 30
```

$ cat /var/cache/bonager/fstab_info:
```
UUID=e8099fca-434e-4acd-bc79-065957ca020f /               ext3    defaults,errors=remount-ro 0       1
UUID=9e4aa25d-1b2e-417a-9de4-c28f4c725a43 /home           ext3    defaults        0       2
```

$ bonager -c:
```
7
```

Cheers,
apalacheno

---

### Post by AgenT on 2007-01-18
> **apalacheno said:**
> Hi AgenT,

$ cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e8099fca-434e-4acd-bc79-065957ca020f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=9e4aa25d-1b2e-417a-9de4-c28f4c725a43 /home           ext3    defaults        0       2
# /dev/sda2
UUID=229cff06-4857-44a6-9dd6-4a744ea5612b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```$ cat /var/cache/bonager/drive_info:
```
/ 22 30
/home 22 30
```$ cat /var/cache/bonager/fstab_info:
```
UUID=e8099fca-434e-4acd-bc79-065957ca020f /               ext3    defaults,errors=remount-ro 0       1
UUID=9e4aa25d-1b2e-417a-9de4-c28f4c725a43 /home           ext3    defaults        0       2
```$ bonager -c:
```
7
```Cheers,
apalacheno
Looks like Bonage is working the way it is supposed to when it comes to getting information about your system and processing it. The problem just seems to be the tray icon.

Sounds like a GTK problem. Everything you posted seems normal. What about running Bonager from the command line? What is the output, from the time it starts to the time it dies?

What window manager are you using? Metacity, the default wm for GNOME or something else?

It may be that some recent GNOME upgrade broke Bonager. The tray icon toolkit used by Bonager is actually being phased out by GNOME. Maybe they are breaking things in the process. :( 

And just in case anyone asks, Bonager with Beryl does not work correctly. It works, but the icon disappears after it updates the icon status.

If worse comes to worse, you can still use bonager -c to determine how many boots you have left until next scan. And if the problem is only with the tray icon, you can use bonager -t to disable the tray icon and Bonager will still warn you when impending scan is about to occur. Bonager will just be invisible until the warning pops up (just make sure Bonager autostarts).

---

### Post by apalacheno on 2007-01-19
Hi AgenT,
What command does Bonager use to tell the system to fsck at the next boot?

Just noticed, a 
```
sudo shutdown -rF now
```

doesn't do anything either. Ubuntu starts as usual without any fsck being performed.

Cheers,
apalacheno

---

### Post by AgenT on 2007-01-19
> **apalacheno said:**
> Hi AgenT,
What command does Bonager use to tell the system to fsck at the next boot?

Just noticed, a 
```
sudo shutdown -rF now
```doesn't do anything either. Ubuntu starts as usual without any fsck being performed.

Cheers,
apalacheno
Now that is strange! What about when doing nothing, do you get the fsck when your mount count reaches 30? Check how many mounts you have left using bonager -c. When bonager tells you 0 left, your next boot should give you an fsck. If you do not have many mounts left and are able to reboot your system, try rebooting it until your reach 0 and see if the next reboot forces a scan. Does it work?

After that, your mount count will reset and bonager -c will give show 28 mounts remaining. Then, try this:
```
sudo touch /forcefsck
```Reboot. That should force fsck. Does it work?

---

### Post by dixonstalbert on 2007-01-20
> **AgenT said:**
> Sounds like a GTK problem. Everything you posted seems normal. What about running Bonager from the command line? What is the output, from the time it starts to the time it dies?

What window manager are you using? Metacity, the default wm for GNOME or something else?

running from command line, didnt get tray icon, let it run for 2 min then hit ctrl-c and got this:

```
dixon2@athlon:~$ bonager

Traceback (most recent call last):
  File "/usr/bin/bonager", line 518, in ?
    gtk.main()
KeyboardInterrupt

```


running from application menu, tray icon runs for 15 seconds before dying.

---

### Post by AgenT on 2007-01-20
> **dixonstalbert said:**
> running from command line, didnt get tray icon, let it run for 2 min then hit ctrl-c and got this:

```
dixon2@athlon:~$ bonager

Traceback (most recent call last):
  File "/usr/bin/bonager", line 518, in ?
    gtk.main()
KeyboardInterrupt

```
running from application menu, tray icon runs for 15 seconds before dying.
The 15 seconds icon is actually weird GNOME behavior where it will "pause" the programs' icon for about 15 seconds after launch.

The python error when hitting ctrl-c is the normal pygtk error you get when you kill the application via ctrl-c. The main loop is basically freaking out and it quickly gives the reason (KeyboardInterrupt). This is no real error and cannot be fixed.

You still have not answered these questions:  
[LIST=1]
[*]What desktop environment are you using? GNOME?
[*]What window manager are you using? Metacity, the default wm for GNOME or something else?[/LIST]

---

### Post by dixonstalbert on 2007-01-21
> **AgenT said:**
> 
You still have not answered these questions:  
[LIST=1]
[*]What desktop environment are you using? GNOME?
[*]What window manager are you using? Metacity, the default wm for GNOME or something else?[/LIST]

sorry

I am using Gnome/metacity. I run 2 monitors with "DesktopSetup" 'horizontal" and Viewport 0 0 in my xorg.conf

---

### Post by AgenT on 2007-01-21
> **dixonstalbert said:**
> sorry

I am using Gnome/metacity. I run 2 monitors with "DesktopSetup" 'horizontal" and Viewport 0 0 in my xorg.conf
In truth, you are experiencing a problem that I cannot reproduce. Trying Bonager with all Ubuntu updates in Metacity/GNOME works fine for me.

Because I cannot reproduce your problem and am unable to understand what is happening on your system, it will be very difficult to fix it and in truth not worth the effort.  Better to put that effort into the new Bonager.

For now, just start Bonager without tray icon support. It should still warn you about impending scans.
```
bonager -t
```or
```
bonager --no-tray
```They both do the same thing. For more information, type:
```
bonager --help
```Note that you will more than likely want to background the process by adding a "&" like so:
```
bonager -t &
```

---

### Post by apalacheno on 2007-01-22
> **AgenT said:**
> Now that is strange! What about when doing nothing, do you get the fsck when your mount count reaches 30? Check how many mounts you have left using bonager -c. When bonager tells you 0 left, your next boot should give you an fsck. If you do not have many mounts left and are able to reboot your system, try rebooting it until your reach 0 and see if the next reboot forces a scan. Does it work?

After that, your mount count will reset and bonager -c will give show 28 mounts remaining. Then, try this:
```
sudo touch /forcefsck
```Reboot. That should force fsck. Does it work?

Hi AgenT!
When the mount count reaches 30, a fsck is done. So far so good. Bonager now shows 28 mounts remaining.
Doing a ```
sudo touch /forcefsck
``` works also.

Strange.

---

### Post by AgenT on 2007-01-22
> **apalacheno said:**
> Hi AgenT!
When the mount count reaches 30, a fsck is done. So far so good. Bonager now shows 28 mounts remaining.
Doing a ```
sudo touch /forcefsck
``` works also.

Strange.
Something seems to be wrong with GTK or pyGTK somewhere because now two people are having icon trouble plus you are having strange behavior where answering "Yes" to "Force scan on next boot?" does nothing. It should ask you for your (sudo) password which it is not and then it should add the forcefsck file to the appropriate folder.

This is actually a good reason to have a force fsck option in the command line so someone such as yourself could use that when the GUI goes wrong (or if you prefer to use the command line which is nice in scripts, etc.). I will make this a feature in the new Bonager.

---

### Post by apalacheno on 2007-01-22
Good idea!

Thanks AgenT!

---

### Post by AllesMeins on 2007-01-25
I can't remove the bonager-package.

```

~$ sudo apt-get remove bonager
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bonager
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bonager
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 115kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 134493 files and directories currently installed.)
Removing bonager ...
update-rc.d: /etc/init.d/bonager exists during rc.d purge (use -f to force)
dpkg: error processing bonager (--remove):
 subprocess pre-removal script returned error exit status 1
 System startup links for /etc/init.d/bonager already exist.
Errors were encountered while processing:
 bonager
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas how that might have happend?

---

### Post by reacocard on 2007-01-25
> **AllesMeins said:**
> I can't remove the bonager-package.

```

~$ sudo apt-get remove bonager
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bonager
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bonager
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 115kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 134493 files and directories currently installed.)
Removing bonager ...
update-rc.d: /etc/init.d/bonager exists during rc.d purge (use -f to force)
dpkg: error processing bonager (--remove):
 subprocess pre-removal script returned error exit status 1
 System startup links for /etc/init.d/bonager already exist.
Errors were encountered while processing:
 bonager
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas how that might have happend?

I'm having the same problem.  Any ideas?

---

### Post by AgenT on 2007-01-25
That is what I get for trying to fix the install bug. End up fixing it and creating a remove bug. ;)

Try the solution that the error gave: remove the rc files.

```
apt-get -f install
update-rc.d bonager remove
apt-get remove bonager
```

If the above does not work, try this:
```
apt-get -f install
apt-get purge bonager
```

If that does not work, try the following:
```
dpkg --force-all purge bonager
```

---

### Post by reacocard on 2007-01-25
Well, none of your commands did it on its own, but I figured it out.  Do these in order:

```
sudo update-rc.d -f bonager remove
sudo rm /etc/init.d/bonager
sudo dpkg -P --force-all bonager
```

---

### Post by karlsebal on 2007-01-30
Bonager seems to have Problems with my fstab. Installation gives:

```
ERROR: Unrecognized /etc/fstab format
Debug information: LABEL=e-tt

```

above only after I deleted the comment-lines, before that I got:

```
ERROR: Unrecognized /etc/fstab format
Debug information: #

```

thanks for bonager
Karl

---

### Post by karlsebal on 2007-01-30
after getting it worked with a fstab clean enough for bonager (pls fix the comment and LABEL= problem) I can tell:
SystemTray works fine in KDE (although it's not transparent...;-) )

fine work, thank you
karl

---

### Post by AgenT on 2007-01-30
> **karlsebal said:**
> after getting it worked with a fstab clean enough for bonager (pls fix the comment and LABEL= problem) I can tell:
SystemTray works fine in KDE (although it's not transparent...;-) )

fine work, thank you
karl
Can you post the broken fstab in full? This will help me determine how to fix up Bonager. Otherwise, I cannot incorporate this into Bonager because my fstab files are correct and work.

---

### Post by karlsebal on 2007-01-30
that's it. thank you

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
LABEL=d-sf / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6 -- converted during upgrade to edgy
LABEL=d-tt /media/d-tt ext3 defaults 0 2
# /dev/hda7 -- converted during upgrade to edgy
UUID=44D6-953B /media/fat vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2 -- converted during upgrade to edgy
LABEL=home /media/may ext3 defaults 0 2
# /dev/sda1 -- converted during upgrade to edgy
LABEL=e-tt	/media/e-tt ext3 defaults 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=8630CF0F30CF0561 /media/wixp ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=42dff6ae-ca81-4f0d-a1d9-967599bbf9a7 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by karlsebal on 2007-02-03
Hi!

Bonager now works properly and I am enthralled. Only thing is: bonager does not autostart. I at the moment use a script in autostart for that. Session Manager is KDE 3.5.5

Greetings
Karl

---

### Post by bodhi.zazen on 2007-02-07
Nice How-to

This thread has been added to the UDSF wiki.

[Bonager:_The_Boot_Scan_Manager](http://doc.gwos.org/index.php/Bonager:_The_Boot_Scan_Manager)

---

### Post by undercode on 2007-02-07
Hi! this is my first spanish translated version for bonager 0.6 from /usr/bin/bonager

Diego Bas

---

### Post by AgenT on 2007-02-07
Thank you bodhi.zazen for the Wiki addition.

Thank you undercode for the Spanish translations. Gracias!

karlsebal: you surprise me with your enthusiasm in trying to get Bonager working in KDE. It really does look like there are people out there that would benefit from a Bonager that works on multiple desktops.

Please note that while development of the new version has slowed down, it is still going on. The contributions made to Bonager from the community of users is helping in Bonager development. It not only makes the program better but also gives encouragement.

---

### Post by karlsebal on 2007-02-08
> **AgenT said:**
> It really does look like there are people out there that would benefit from a Bonager that works on multiple desktops.

I found there sooo many scripts trying to give the possibility to postpone the fscheck or make ubuntu perform it at shutdown (by the way good feature I think: possibility to check at shutdown) - bonager is the most elegant and userfriendly and aesthetical solution - I only wonder, why I did not find open ears among the developers to implement it in the official release.

For now I found bonager it does not matter any more


Many thanks again
Karlsebal

---

### Post by AgenT on 2007-02-08
Thank you for your feedback. Scan on shutdown is not possible (see man fsck) and the scripts that claim to have scan on shutdown are not being truthful. They work by first forcing a  scan on next boot, restarting your computer, starting scan, then forcefully shutting down the computer after the scan completes. The major problem with that is the forcing the shutdown. This is done as a bootup service script which can cause major problems because the computer should never halt when services are being started. In summery, the scan at shutdown is a very dirty hack.

---

### Post by Nikron on 2007-02-08
Is postponing the scan a wise thing to do?

---

### Post by AgenT on 2007-02-09
> **Nikron said:**
> Is postponing the scan a wise thing to do?
Doing it once or twice, yes. Doing it over and over and never letting your computer do a scan is not. Bonager is meant as a warning tool more than a postponing tool. But a postpone may be required sometimes. Whenever someone tries to postpone more than once, they are given a warning stating that they should not postpone multiple times because it may lose their data. If they decide to postpone 60 times in a row and they lose their data because of it then as far as I am concerned, it was their own fault.

---

### Post by ramjet_1953 on 2007-02-22
Great application!

Install went flawlessly!

 I have been embarassed a couple of times in the past, when visiting clients and we had to wait until my system went through a disk scan.

Now that is a thing of the past.

Regards,
Roger :cool:

---

### Post by unabatedshagie on 2007-03-01
I'm having problems getting this to run,

I installed the deb from the first post but when I run it I nothing appears to happen.

If I run it from the terminal I get the following message```
bonager
ERROR: Mount root entry is not valid
4
/  
```

The contents of my fstab file```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a0db9dac-b626-40a9-a1e8-892798f057d7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6ecfd003-75d0-4f2a-835d-8cdc38ac11f4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# removed floppy drive
#/dev/           /media/floppy0  auto    rw,user,noauto  0       0
#
#
# 80GB torrents drive
UUID=b72c9c61-18bb-4e17-904c-ddfb0d83cd78   /mnt/torrents   ext3    defaults  0   0
#
# 160GB documents drive
UUID=d1818eaa-1a1e-48d7-94d0-ec05221b058c   /mnt/documents  ext3    defaults  0   0
#
# 160GB media drive
UUID=bb5021b9-df97-4059-b522-5da25af830b0   /mnt/media      ext3    defaults  0   0

``` results of cat /var/cache/bonager/drive_info```
/
``` results for cat /var/cache/bonager/fstab_info```
UUID=a0db9dac-b626-40a9-a1e8-892798f057d7 /               ext3    defaults,errors=remount-ro 0       1
``` Any ideas?

---

### Post by AgenT on 2007-03-01
What is the output of:
```
# cat /dev/disk/by-uuid/a0db9dac-b626-40a9-a1e8-892798f057d7
```

---

### Post by unabatedshagie on 2007-03-01
No such file or directory

---

### Post by AgenT on 2007-03-01
Either your fstab entry is wrong or your system is broken. Or both.

If UUID a0db9dac-b626-40a9-a1e8-892798f057d7 does not exist on your system then your fstab entry is wrong.

If /dev/disk/by-uuid/ folder does not exist, your system is broken. That is, you are missing the necessary programs that create those UUID dev entries.

---

### Post by bravemosquito on 2007-04-07
I have a problem with removing **Bonager**:

```
root@dontouch:~# aptitude remove bonager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  bonager 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 115kB will be freed.
Writing extended state information... Done
(Reading database ... 182806 files and directories currently installed.)
Removing bonager ...
update-rc.d: /etc/init.d/bonager exists during rc.d purge (use -f to force)
dpkg: error processing bonager (--remove):
 subprocess pre-removal script returned error exit status 1
 System startup links for /etc/init.d/bonager already exist.
Errors were encountered while processing:
 bonager
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

```
root@dontouch:~# aptitude remove -f bonager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  bonager 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 115kB will be freed.
Writing extended state information... Done
(Reading database ... 182806 files and directories currently installed.)
Removing bonager ...
update-rc.d: /etc/init.d/bonager exists during rc.d purge (use -f to force)
dpkg: error processing bonager (--remove):
 subprocess pre-removal script returned error exit status 1
 System startup links for /etc/init.d/bonager already exist.
Errors were encountered while processing:
 bonager
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

```
root@dontouch:~# apt-get remove bonager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-bin libsdl-gfx1.2-4 libgnome32 gnome-libs-data libart2 libgnorbagtk0 libsdl-net1.2 libossp-uuid15 libxcb1
  libxml++2.6c2a python-irclib libgnomeui32 libdb3 libgtk2-gladexml-perl libpthread-stubs0-dev libpthread-stubs0
  python-wxversion libxcb-xlib0 liborbit0 libgnomesupport0 libxcb-xlib0-dev python-wxgtk2.6 libxcb1-dev libgnorba27
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bonager
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 115kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 182806 files and directories currently installed.)
Removing bonager ...
update-rc.d: /etc/init.d/bonager exists during rc.d purge (use -f to force)
dpkg: error processing bonager (--remove):
 subprocess pre-removal script returned error exit status 1
 System startup links for /etc/init.d/bonager already exist.
Errors were encountered while processing:
 bonager
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
root@dontouch:~# dpkg -r bonager
(Reading database ... 182806 files and directories currently installed.)
Removing bonager ...
update-rc.d: /etc/init.d/bonager exists during rc.d purge (use -f to force)
dpkg: error processing bonager (--remove):
 subprocess pre-removal script returned error exit status 1
 System startup links for /etc/init.d/bonager already exist.
Errors were encountered while processing:
 bonager
```

Any ideas?

---

### Post by reacocard on 2007-04-07
> **bravemosquito said:**
> I have a problem with removing **Bonager**:

<snip><snip><snip>

Any ideas?

I had the same problem, see this post: [http://ubuntuforums.org/showpost.php?p=2063365&postcount=170](http://ubuntuforums.org/showpost.php?p=2063365&postcount=170)

---

### Post by bravemosquito on 2007-04-07
> **reacocard said:**
> I had the same problem, see this post: [http://ubuntuforums.org/showpost.php?p=2063365&postcount=170](http://ubuntuforums.org/showpost.php?p=2063365&postcount=170)

Thank you =D>

---

### Post by Senilix on 2007-04-18
Feisty with encrypted root.

$ bonager
/usr/bin/bonager:30: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  import egg.trayicon   # egg == python-gnome2-extras
ERROR: Mount root entry is not valid

$ mount | grep "/ "
/dev/mapper/root on / type ext3 (rw,errors=remount-ro)

---

### Post by chrisccoulson on 2007-04-22
^^^ I get the same error as this on Feisty. My root is on a DMRAID volume so is also a /dev/mapper/.... device.

sudo /etc/init.d/bonager start gives:

```
ERROR: Unrecognized /etc/fstab format
Debug information: /dev/mapper/nvidia_dgcadeeg6
```

cat /etc/fstab:

```
proc                                            /proc                   proc            defaults                                        0 0
/dev/mapper/nvidia_dgcadeeg6                    /                       ext3            defaults,errors=remount-ro                      0 1
#/dev/sda1
UUID=7cfd1f74-70d1-412e-8dfd-1c1ed4dd9526       /home                   ext3            defaults,user_xattr,errors=remount-ro           0 3
/dev/mapper/nvidia_dgcadeeg3                    /boot                   ext3            defaults,errors=remount-ro                      0 2
/dev/mapper/nvidia_dgcadeeg5                    /tmp                    ext3            defaults,errors=remount-ro                      0 0
/dev/mapper/nvidia_dgcadeeg7                    none                    swap            sw                                              0 0
/dev/mapper/nvidia_dgcadeeg9                    /var                    ext3            defaults                                        0 4
/dev/mapper/nvidia_dgcadeeg8                    /var/lib/vmware         ext3            defaults,errors=remount-ro                      0 5
/tmp                                            /var/tmp                none            defaults,bind                                   0 0

```

I also can't use dpkg to remove it from my system as I get the following error:

```
chr1s@chris-desktop:~$ sudo dpkg -r bonager
(Reading database ... 154857 files and directories currently installed.)
Removing bonager ...
update-rc.d: /etc/init.d/bonager exists during rc.d purge (use -f to force)
dpkg: error processing bonager (--remove):
 subprocess pre-removal script returned error exit status 1
 System startup links for /etc/init.d/bonager already exist.
ERROR: Unrecognized /etc/fstab format
Debug information: /dev/mapper/nvidia_dgcadeeg6
Errors were encountered while processing:
 bonager

```

To remove it, I had to rebuild the package after changing the following line in the prerm script:

```
update-rc.d bonager remove
```

to:

```
update-rc.d -f bonager remove
```

I then used dpkg to upgrade to the modified package and then I was able to remove it afterwards.

---

### Post by sup on 2007-05-07
Thanks, a nice app, do you still work on it? I would like to see this in the repos...
There is also a bug on launchpad that might be solved with bonager... [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/22460]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/22460")

---

### Post by BuffaloX on 2007-05-07
Very good idea, and an extremely nice implementation.
Thanx. :popcorn:

---

### Post by NoWhereMan on 2007-06-09
you saved my life with this tool, thank you!

Suggestion: the checkbox with the question "autostart bonager?" under the other question "quit bonager?" may be misleading. 

At a first glance I clicked "ye"s to answer to the checkbox question :P I didn't care about the checkbox widget, I just answered the frist question I saw; maybe change that label

great work, though, thanks!

---

### Post by PsyWolf on 2007-08-04
I have one major problem with this program.  The background of the green cog icon is white.  My notification area is transparent.  It looks really tacky.  

[IMG]http://s4.photobucket.com/albums/y149/RidgeWolf/?action=view&current=blah.png[/IMG]

where does the icon get installed to so that i can modify it, and please change the package to inclue a trasnparent background.  This will also make alot of AWN people happy.

---

### Post by PsyWolf on 2007-08-04
ah, I see the not about this on the first post.  Sorry.  You should make an effort to use a different language then.  Composite desktops are the future IMO and stuff needs to have transparent backgrounds.

---

### Post by bg1256 on 2007-08-09
Great little tool

Big shout out to the developers!  Well done! :guitar:

---

### Post by gespertino on 2007-08-21
Spanish translation. :)

Cool app! Thank you!

---

### Post by oomingmak on 2007-08-27
Is it possible to have the bonager tray icon hidden until an fsck is imminent (at which point the icon would unhide itself and display as a visual notification that an fsck scan is due). 

I've read the whole of this thread, but it's not clear to me if that is how the icon hiding works.

Thanks.

---

### Post by brunoscunha on 2007-09-16
Hi nice app but can't make it run on my laptop. Can someone tell me how to uninstall the bonager?

Thanks

---

### Post by sup on 2007-09-19
Provided you installed the deb, it should be as simple as sudo apt-get remove bonager

---

### Post by enervation on 2007-09-21
Nice tool! However I think with your quest for simplicity, you have gone slightly too far and it is now confusing. For instance, the tooltip says 'left click: smart action', without describing what 'smart action' is. I would suggest this instead:

```

Left click on the bonager icon to display this menu:
----------------------------
| 19/35 mounts left        |      Number of mounts left
----------------------------
|  |=======          |     |      Bar showing the same information graphically
----------------------------
| []Check on next boot?    |    Tick box to show whether to check on next book
----------------------------

Right click on the bonager icon to display this menu:

----------------------------
| [] Autostart Bonager?    |      Tickbox for autostarting bonager
----------------------------
| Exit Bonager             |       'Exit bonager' button
----------------------------

```
This way, every action is available within 2 clicks, and it should be more understandable.

---

### Post by sup on 2007-09-23
I am afraid this software is no longer under developement:-(

---

### Post by NoWhereMan on 2007-09-25
> **reacocard said:**
> I had the same problem, see this post: [http://ubuntuforums.org/showpost.php?p=2063365&postcount=170](http://ubuntuforums.org/showpost.php?p=2063365&postcount=170)

thanks

---

### Post by raywjohnson on 2007-10-12
Thanks for the great program. The best ones are simple, install with no issues, and solve a problem. I am a Bonager user!

--RayJ

---

### Post by sidney_v on 2007-11-01
> Q: What languages does Bonager support?
A: English, French and German. If you would like to help and translate Bonager just download the translate.txt file (see "attachment" section on the bottom of this post). It will only take about 5-10 minutes of your time and you DO NOT have to dig into the Bonager source code.

This is a french translation (based on Canard works) for Bonager but **how to use it** ? 

I need to create a file or just put it in a special directory or use poedit software or anything else ?

Thanks for help ;)

---

### Post by eudyptula on 2007-11-03
One more request for a KDE version!

---

### Post by gottferdamnt on 2007-11-05
I am very interested about a KDE version !

---

### Post by mssever on 2007-11-08
> **eudyptula said:**
> One more request for a KDE version!

> **gottferdamnt said:**
> I am very interested about a KDE version !

Given that Bonager is a tray application, I would think that it should work in KDE already.

If you want it to match your Qt theme, I've heard of software that makes GTK apps look like Qt apps. I'm not a KDE user, so I don't know any more.

---

### Post by NoWhereMan on 2007-11-10
I think bonager is no longer being developed

---

### Post by Rohit_K on 2007-11-14
Thank you very much!

---

### Post by atlas95 on 2007-11-15
Could you make the png background transparent please?
Or someone can help me to do it, I have a black panel so it isn't very beautifull...

---

### Post by sidney_v on 2007-11-15
Hi,

PNG format is not a solution as described in old messages in this thread (see it for more informations)

---

### Post by EddieT on 2007-12-02
Excellent tool, thanks for your efforts!

---

### Post by durand on 2007-12-04
Works on Hardy! Thanks!

PS: The tray icon seems to be missing the countdown numbers....But it shows them on mouseover.

---

### Post by durand on 2007-12-04
> **sidney_v said:**
> Hi,

PNG format is not a solution as described in old messages in this thread (see it for more informations)

SVG?

---

### Post by sidney_v on 2007-12-04
> **durand said:**
> SVG?

Hi Durand, why do you speak about SVG ? I don't know if SVG will solve your problem but i read in this thread that PNG format will not.

Link : [Wikipedia - SVG]("http://en.wikipedia.org/wiki/Scalable_Vector_Graphics")

---

### Post by durand on 2007-12-04
No, I meant, wouldn't you be able to make a transparent tray icon with svg..

---

### Post by DoctorMO on 2007-12-04
PNG supports transparencies so i have no idea what you problem is.

---

### Post by durand on 2007-12-05
> **sidney_v said:**
> Hi,

PNG format is not a solution as described in old messages in this thread (see it for more informations)

I'm just suggesting using SVG if png isn't the solution here..

---

### Post by dominikgeisler on 2007-12-27
Hi, 

I installer Bonager, but it didn't work (tried to open /dev/ubuntu--7.10-root, which doesn't exist; only  /dev/ubuntu-7.10 exists). Trying to uninstall I got this: 

```

sudo aptitude purge bonager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  bonager{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 115kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 174641 files and directories currently installed.)
Removing bonager ...
update-rc.d: /etc/init.d/bonager exists during rc.d purge (use -f to force)
dpkg: error processing bonager (--purge):
 subprocess pre-removal script returned error exit status 1
 System startup links for /etc/init.d/bonager already exist.
tune2fs: No such file or directory while trying to open /dev/ubuntu--7.10-root
Couldn't find valid filesystem superblock.
tune2fs: No such file or directory while trying to open /dev/ubuntu--7.10-root
Couldn't find valid filesystem superblock.
Errors were encountered while processing:
 bonager
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done   

```

I have an excrypted filesystem (set up using alternate install CD for ubuntu 7.10). /etc/fstab is: 
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/ubuntu--7.10-root
UUID=3ca7b952-9bf0-4c57-a98d-acc7e7861cd0 /               ext3    defaults,errors=remount-ro,noatime 0       1
# /dev/sdb1
UUID=090ae96a-6d76-43b5-b97b-623a2d7b7e0f /boot           ext3    defaults        0       2
# /dev/mapper/ubuntu--7.10-swap_1
UUID=15d90119-da85-44e6-b2cd-3d24cd0cfc49 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda1       /media/system   ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda5       /media/programs ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hda6       /media/FAT16    vfat    defaults 0 0 

```

Any ideas on how to fix or remove Bonager? Using apt-get instead of Aptitude didn't help, and neither did using -f (as suggested by aptitude).

**EDIT: Solution for uninstall is at [http://ubuntuforums.org/showpost.php?p=2063365&postcount=170](http://ubuntuforums.org/showpost.php?p=2063365&postcount=170)**

---

### Post by sidney_v on 2007-12-27
Hi,

To uninstall Bonager, try to do this :
```
sudo update-rc.d -f bonager remove
sudo rm /etc/init.d/bonager
sudo dpkg --purge bonager
```

I think filesystem is not the problem.

---

### Post by Pirate_Hunter on 2008-03-16
well im late but heck dont care thanx for this just stumble on it while googling on system check up but very useful and simple app

---

### Post by mtbsoft on 2008-06-20
Also just came across Bonager...  installed it, love it!

One suggestion for it: user coloured icon indicating how close forced fsck is, with user configurable values e.g. goes yellow at 3 boots away and red when next boot will force reboot.

---

### Post by Gourgi on 2008-06-20
installation fine !
and i've done the following 3 steps ...
running : 
```

gourgi@gourgi:~$ sudo bonager
ERROR: Mount root entry is not valid
0

```

more
```

gourgi@gourgi:~$ bonager
ERROR: Mount root entry is not valid
0

```

uninstall : 

```
gourgi@gourgi:~$ sudo apt-get remove bonager 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bonager
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 119964 files and directories currently installed.)
Removing bonager ...
update-rc.d: /etc/init.d/bonager exists during rc.d purge (use -f to force)
dpkg: error processing bonager (--remove):
 subprocess pre-removal script returned error exit status 1
 System startup links for /etc/init.d/bonager already exist.
Errors were encountered while processing:
 bonager
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
purging : 
```

gourgi@gourgi:~$ sudo apt-get purge bonager 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bonager*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 119964 files and directories currently installed.)
Removing bonager ...
update-rc.d: /etc/init.d/bonager exists during rc.d purge (use -f to force)
dpkg: error processing bonager (--purge):
 subprocess pre-removal script returned error exit status 1
 System startup links for /etc/init.d/bonager already exist.
Errors were encountered while processing:
 bonager
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

now what?
how can i remove it from my system ?

---

### Post by Valeryan_24 on 2009-03-09
Hello,

I "up" an old topic, but this small application Bonager was very useful to me also.

Since I upgraded to Ubuntu Jaunty alpha, I'm totally unable to run it anymore, I get this message :


"[I]ERROR: Mount root entry is not valid
0[/I]"

And nothing can arrnage that, I tried command *sudo bonager_check* without success.

Does someone have a solution ?

Thanks a lot ! :D

---

### Post by mtbsoft on 2009-03-09
Couple of things occur to me...

Firstly, It may just need a recompile against the new release but that's something you'd have to look into.

Next, have you chosen to use an ext4 file system, instead of ext3?  If so, perhaps it isn't compatible with ext4.

Finally, it's still an alpha release and could change/fix the problem before release - perhaps you should just wait and see what the beta release does.  (I'm hoping you are playing with a test machine and not an important production/live machine; if you've upgraded your day-to-day machine to an alpha o/s release then, sorry, you're a fool.)

As far as I recall, Bonager isn't actively supported at the moment so you (we) may all be up the creek once we upgrade to Jaunty, but that's an issue I'm putting off for now.

---

### Post by Valeryan_24 on 2009-03-10
Hello,

Thanks for your answer.

Unfortunately I don't know anything on programming, I'm not able to correct it.

You're right, I use ext 4 file system with Jaunty alpha, but can't say where is the problem.

I made a bug report to Ubuntu Launchpad :
[https://bugs.launchpad.net/ubuntu/+bug/340005](https://bugs.launchpad.net/ubuntu/+bug/340005)

But as Bonager isn't an official package, it has been invalided, which is understandable.

I hope we will find a solution :-)

---

### Post by hzFVOW00pw on 2009-04-08
I made a dutch translation for Bonager. Can't contact the author, no reply. Here's the Dutch translation files attached (bzipped). bonager.po is the source. bonager.mo should be placed in /usr/share/locale/nl/LC_MESSAGES and chmodded to 644 root root.

---

### Post by rrll1977 on 2009-07-16
**Error on terminal console:**
ERROR: Mount root entry is not valid
0

**My system:**

Xubuntu Jaunty (Release 9.04)
Kernel Linux 2.6.28.13-generic
Gnome 2.26.1

Memory: 939.2 Mb
Procesor: Intel(R) Celeron(R) D CPU 3.06GHz

Available disk space 68.6 Gb

---

### Post by BlueerSkies on 2009-09-15
Bismillaah.   Peace, to all.   I was a bit apprehensive concerning installation of Bonager, after reading some of the post regarding failure, and the fact that it is no longer supported. 

What I later discovered was that if esc, is pressed during boot up, the scan can be disabled.  After doing this several times it seems to have become quite intuitive.  It now skips the scan all by itself!  I don't know if this is a permanent arrangement. Time will tell.  


BlueerSkies

---

### Post by AgenT on 2009-10-31
[CENTER] [SIZE=5][COLOR=Red]**PLEASE DO NOT USE Bonager!!**[/COLOR][/SIZE]

** [COLOR=Magenta][SIZE=4][COLOR=DarkOrange]GREAT NEWS![/COLOR][/SIZE][/COLOR]**
**[COLOR=Magenta][COLOR=DarkRed] [SIZE=4]Starting with 9.04, Ubuntu now has this functionality built-in![/SIZE][/COLOR][/COLOR]**

**[COLOR=Magenta][COLOR=DarkRed] [COLOR=Magenta][SIZE=4]=D> THANK YOU EVERYONE FOR SUPPORTING BONAGER [/SIZE][/COLOR][/COLOR][/COLOR]****[COLOR=Magenta][COLOR=DarkRed][COLOR=Magenta]=D>[/COLOR][/COLOR][/COLOR]**
**You made it possible for Ubuntu developers to finally incorporate a boot-scan cancel button!**

[SIZE=3] Need to cancel the boot scan?[/SIZE]
[SIZE=3] **Press the [COLOR=Navy]ESCAPE[/COLOR] key during the scan to cancel!**[/SIZE]
[SIZE=3] Remember, this functionality is built-in! No need for Bonager.[/SIZE]

[SIZE=3]**If you use an older version of Ubuntu (before 9.04), you can try Bonager out. It should work.** Please note, however, it is no longer supported by me.[/SIZE]

**Bonager is no longer supported!**
** (it may possibly break your system, especially ext4 that comes with 9.10)**


[/CENTER]
[COLOR=#000000][FONT=Times New Roman][SIZE=4]Apologies to everyone for not updating this thread for a long time. And I would like to give a [COLOR=Magenta]**[SIZE=5]HUGE THANK YOU[/SIZE]**[/COLOR] to all Bonger users for helping each other out in this thread. You guys are great! Thank you again![/SIZE][/FONT][/COLOR] =D>

---

### Post by garnayden on 2009-11-26
Sorry for my english, I have a great problem, today I install Bonager, because I want to check my portatil hard disk, se when the installation finish I restart the computer and ubuntu do not want start, ubuntu do not show me the login screen only a black screen and the pointer in mode wait, What can I do?

---

### Post by trungduy on 2011-02-17
It doesn't work.

Dependency is not satisfiable: python-gnome2-extras (>= 2.14.2)|python2.4-gnome2-extras (>= 2.14.0)

---

