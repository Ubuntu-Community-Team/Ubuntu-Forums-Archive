---
title: "HOWTO: Install Opera in Ubuntu"
date: 2005-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by joh on 2005-06-09
**Moved!**

[http://ubuntuforums.org/showthread.php?t=40467](http://ubuntuforums.org/showthread.php?t=40467)

The guide is now located in the Hoary forum. The install instructions is the same for Warty and Hoary so I didn't see any point of seperating them.

---

### Post by Majlo on 2005-06-09
Thanks :-)
Great Work

---

### Post by kuleali on 2005-06-09
Nice howto

---

### Post by bugmenot on 2005-06-18
First, thank you for the write up. Was the most helpful one I could find. Also, pardon my utter noobness...

Sadly I wasn't able to get it to work for me. I type the command to install Opera in the Terminal which completes with the following result:

"Setting up opera-static (8.01-20050615.1) ..."

Yet I don't see Opera installed anywhere, other than the Package Manager.

In fact opera.desktop doesn't exist. Completing the rest of the instructions just to cover my bases yields no success. Opera just can't be found.

Any ideas?

---

### Post by Xian on 2005-06-18
[QUOTE=bugmenot]Yet I don't see Opera installed anywhere, other than the Package Manager.[/QUOTE]
Try launching Opera to see if it has installed successfuly.
Right-click on your desktop and choose "Open Terminal'.

At the prompt enter this command and hit the enter key.
Does Opera start-up?

```
$ opera
```

---

### Post by bugmenot on 2005-06-18
I'm such a dunce. Can't believe I didn't think to type opera in the Terminal. Too many years of Windows I guess.

Thanks Xian and OP. For some reason Opera just wouldn't appear in the Applications shortcut (following the full instructions) until I launched it first in the Terminal and accepted the Graphical Ads option.

---

### Post by joh on 2005-06-22
Opera doesn't create the opera.desktop, thats what that part of the HOWTO is about.

Sometimes the GNOME Application menu doesn't update before you restart in.

Doing this in the terminal should do the trick:
```
killall gnome-panel 
```

---

### Post by Riggs on 2005-06-24
The only thing that bothers me still is that Opera is not taking on the color scheme of the theme I am using.  When you select anything in the menus, or in any of the dropdowns, the hightlight is always blue, even though I'm using Clearlooks Olive.  Any suggestions?

---

### Post by Xian on 2005-06-24
AFAIK Opera is a QT based application and does not support GTK theme attributes.

---

### Post by dakira on 2005-07-04
[QUOTE=Riggs]The only thing that bothers me still is that Opera is not taking on the color scheme of the theme I am using.  When you select anything in the menus, or in any of the dropdowns, the hightlight is always blue, even though I'm using Clearlooks Olive.  Any suggestions?[/QUOTE]

Press SHIFT+F12 and in the Skin-Tab select the Opera Standard skin (if not already selected) and in Color scheme select "System color scheme".

That does it for me..

dakira

---

### Post by tread on 2005-07-04
I'm going to add my severely unpopular thread here .. its about [Opera-Gnome visual integration](http://ubuntuforums.org/showthread.php?t=35156) 

I have one more theme to add there - Human .. I'll do that as soon as I get a little time.

---

### Post by Eestlane on 2005-07-16
> **joh]This is the install instructions for the Opera Internet Suite (Web browser +++)

This installs Opera, adds a menu icon and changes the default file handler from kexec to gnome-open.

Please give feedback if you have any tricks to make Opera integrate better with the Ubuntu desktop.

---

1. wget
[http://www.netmirror.org/mirror/opera/linux/801/final/en/i386/shared/opera_8.01-20050615.5-shared-qt_en_sarge_i386.deb](http://www.netmirror.org/mirror/opera/linux/801/final/en/i386/shared/opera_8.01-20050615.5-shared-qt_en_sarge_i386.deb)
2. sudo apt-get install libqt3c102-mt
3. sudo dpkg -i opera_8.0-20050415.6-shared-qt_en_sarge_i386.deb

4. Create the desktop file with: 
sudo gedit /usr/share/applications/opera.desktop
5. Insert the following lines into the file:
 
```
[Desktop Entry]
Encoding=UTF-8
Name=Opera Web Browser
GenericName=Web Browser
Comment=Surf the Internet in a safer, faster, and easier way
Exec=opera %u
Terminal=false
MultipleArgs=true
Type=Application
Icon=/usr/X11R6/include/X11/bitmaps/opera.xpm
Categories=Application said:**
> 
Default File Handler=gnome-open exec,1
Default Directory Handler=gnome-open exec,1
```

10. Save the edited file.
11. Open Opera with Application -> Internet -> Opera Web Browser

3. sudo dpkg -i opera_8.0-20050415.6-shared-qt_en_sarge_i386.deb is now

sudo dpkg -i opera_8.01-20050615.5-shared-qt_en_sarge_i386.deb

---

### Post by joh on 2005-07-28
[QUOTE=Eestlane]3. sudo dpkg -i opera_8.0-20050415.6-shared-qt_en_sarge_i386.deb is now

sudo dpkg -i opera_8.01-20050615.5-shared-qt_en_sarge_i386.deb[/QUOTE]

I fixed it, updated to Opera 8.02.

---

### Post by Madpilot on 2005-07-29
There are Ubuntu-specific Opera .debs now, we shouldn't be linking to the sarge debs. See [Opera Downloads](http://www.opera.com/downloads) and select Ubuntu on the dropdown.

opera-static_8.02-20050727.1-qt_en_i386.deb  is the latest, as of July 28 2005. Just upgraded today... (but no BitTorrent support yet... too bad. 8.03, with luck!)

---

### Post by Grafster on 2005-07-30
This thread is awesome for newbies. The commands are laid out properly and work great.

Thanks!

---

### Post by manicka on 2005-07-30
My menu and some page fonts look cruddy, like they're not picking up truetype settings. How do I fix that?

---

### Post by tea_man on 2005-08-04
> Opera Preferences version 2.0
; Do not edit this file while Opera is running
; This file is stored in UTF-8 encoding
[Settings]
Default File Handler=gnome-open exec,1
Default Directory Handler=gnome-open exec,1

for this what can i put in if i have kubuntu installed 
- kde-open exec ?

---

### Post by cowlip on 2005-08-10
[QUOTE=tea_man]for this what can i put in if i have kubuntu installed 
- kde-open exec ?[/QUOTE]
 Hi, I think "kfmclient exec" is correct

Why is Opera making it a Ubuntu static build, couldn't that be why the fonts are bad?  I just use their dynamic sarge build

---

### Post by linuxa on 2005-08-15
Thanks **joh**, that really helps!

Does anyone know of how to get past the Motif plugin requirment that Opera complains of everytime it starts?

Cheers

---

### Post by cowlip on 2005-08-16
[QUOTE=linuxa]Thanks **joh**, that really helps!

Does anyone know of how to get past the Motif plugin requirment that Opera complains of everytime it starts?

Cheers[/QUOTE]

HI, I think it's sudo apt-get install libmotif3

---

### Post by linuxa on 2005-08-17
Appreicate the reply **cowlip**.

libmotif3 doesn't seem available in the source list that I have.

running your suggested command told me that lesstif2 replaced it ??

So I ran:

sudo apt-get install lesstif2

instead.

Cheers

---

### Post by Jeremy Vaught on 2005-08-17
On the step "sudo dpkg -i opera-static_8.02-20050727.1-qt_en_i386.deb" step

I get the response "dpkg: error processing opera-static_8.02-20050727.1-qt_en_i386.deb (--install): package architecture (i386) does not match system (amd64)"

Any thoughts on this?

Thanks,

---

### Post by Perfect Storm on 2005-08-17
You are on an amd64 and you are trying to install i386 archecture(sp?)

---

### Post by cowlip on 2005-08-18
[QUOTE=linuxa]Appreicate the reply **cowlip**.

libmotif3 doesn't seem available in the source list that I have.

running your suggested command told me that lesstif2 replaced it ??

So I ran:

sudo apt-get install lesstif2

instead.

Cheers[/QUOTE]
 Hmm...I have the one from ubuntuguide.org so I don't know why urs is different...

---

### Post by linuxa on 2005-08-20
[QUOTE=cowlip]Hmm...I have the one from ubuntuguide.org so I don't know why urs is different...[/QUOTE]

Probably because I didn't set up all of the repositories in my sources.list   [-X 

Opera loads way faster now using motif instead of lesstif  \\:D/ 

Cheers.

---

### Post by Jeremy Vaught on 2005-08-23
[QUOTE=Artificial Intelligence]You are on an amd64 and you are trying to install i386 archecture(sp?)[/QUOTE]
Yes.  I couldn't figure any other way to do it.  I eventually tried to install the Windows version in CrossOver but that didn't work either.  When I updated to the kernel image 2.6.10-5 I lost X, and startx is gone.  There was enough I was having trouble with because it was the 64 bit version, so I installed the 32 bit version on some empty hard drive space.  Now, everything works fine.  Opera included.  When I get better at Linux I may go back and try to fix the 64 bit version.  But for now, it is just too much of a headache to make all the stuff 'work' in on a 64bit OS.  I think I will give it some time and allow those bleeding edge folks get everything working like it should.

---

### Post by GameManK on 2005-08-25
any solution to the cruddy fonts?

---

### Post by vij26 on 2005-08-30
Great Work!!!
THX
Vij26
PS: Y not rename the file to: Opera.deb  ](*,)  ](*,)  ](*,)

---

### Post by raggamuffin on 2005-08-30
OK...after following this guide, when i try to run opera, all i get (in the terminal) is...

> Preference initialization failure. Generic failure (-1)

Anybody have any idea what the problem is?

---

### Post by MBro on 2005-08-30
[QUOTE=GameManK]any solution to the cruddy fonts?[/QUOTE]
You have to install qt config to make it look more gnomeish, there's a great howto thread in the forum here.

---

### Post by GameManK on 2005-09-05
[QUOTE=MBro]You have to install qt config to make it look more gnomeish, there's a great howto thread in the forum here.[/QUOTE]

actually the fonts look fine now, though i don't know what i did.
also, i'm in KDE.

the only cosmetic issue i have now is the menus are gray like in windows

---

### Post by linuxa on 2005-10-01
The latest version of Opera (which is now free :D), v8.5 downloaded from opera.com uses Qt and seem to have fixed the font issue.

They are now smooth as :p

---

### Post by WhoKnows on 2005-10-01
Does anyone know how to make the menus smaller. Like in Windows. In Ubuntu thet're so big and ugly. 

I n Win.[http://www.zone.ee/jannza/opera%20win.gif?2]("http://www.zone.ee/jannza/opera%20win.gif?2")

In Ubuntu they're a lot bigger. I think beacause of font size. Would iIchange it somewhere.

---

### Post by ahalin on 2010-02-27
[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

Why is it always so hard..................

---

