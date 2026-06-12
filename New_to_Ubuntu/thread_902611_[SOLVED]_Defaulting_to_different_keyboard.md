---
title: "[SOLVED] Defaulting to different keyboard"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by ubalderdash on 2008-08-27
I have recently moved from Windows to Ubuntu and am having trouble with my keyboard.
Although I'm using an English version of Ubuntu my PS2 keyboard is French and I have been unable to get Ubuntu to recognise this situation by default. Instead, each time I boot I have to go to the 'Keyboard preferences' and select the French layout, then select the 'Logitech' brand and the 'Logitech Access Keyboard' model type. This is usually sufficient to get my 'Mitsumi' generic French keyboard working. I have tried setting this as the default setting but Ubuntu seems to completely disregard that. Investigating further, I found the 'SCIM Input Method Setup' where I set the input layout as French. Unfortunately this seems to have no effect either.
I find it improbable that a program that found most of my hardware so easily should fall down on a simple keyboard; I must therefore assume that I am missing something and need help!
Any such help would be very welcome?

---

### Post by Thelasko on 2008-08-27
Open the terminal and enter:
```
sudo dpkg-reconfigure xserver-xorg
```
Then follow the instructions to select your keyboard.

This may be one of the few uses for that command in Hardy.

---

### Post by ubalderdash on 2008-08-28
Many thanks for your response. I followed your instructions without difficulty but the result was less than satisfactory. On restarting the computer the screen resolution had changed to 800x600 and I can no longer get my keyboard to respond in anything but English, i.e. qwerty instead of azerty. This is especially awkward for typing even this text and some of my program windows cannot be closed because command buttons are below the visible screen limits.
Please help me at least to get back to where I was before.

---

### Post by Archmage on 2008-08-28
Kindly provide us with the grafic-card you are using (this way we can go back to your desire screen resultion).

---

### Post by Dougie187 on 2008-08-28
to get back to where you were before, you should be able to recover your xorg.conf file.

Open a terminal and type
```
cd /etc/X11
```
Then, type
```
ls
```
There should be a file called xorg.conf and possibly both an xorg.conf.bak and xorg.conf.failsafe

First, type
```
sudo cp xorg.conf xorg.conf.broke.bak
```
Then type
```
sudo cp xorg.conf.bak xorg.conf
```
After you do this, restart X (Ctrl+Alt+Backspace) and see if your keyboard is working better. If that doesn't work. Then navigate back to the directory and type
```
sudo cp xorg.conf.failsafe xorg.conf
```

If either of the two work, you can remove the old broken xorg file.
```
sudo rm /etc/X11/xorg.conf.broke.bak
```

Let me know if that works to get you back to where you use to be, after that maybe we can look into your keyboard layout issue.

---

### Post by billgoldberg on 2008-08-28
Reconfiguring the x server to change your default keyboard layout is overkill to say the least.

Do this to change it permanently:

Use this command

```
sudo gedit /etc/X11/xorg.conf
```


In the first block of text you’ll see:

> Section “InputDevice”
Identifier “Generic Keyboard”
Driver “kbd”
Option “XkbRules” “xorg”
Option “XkbModel” “pc105&#8243;
Option “XkbLayout” “be”


You would change the last one to the keyboard layout you would like.

"be" is also an azerty layout but I think the french one is a bit differnet, try using "fr".

Then press save.

Log out and back in and the default one will have been changed

---

### Post by ubalderdash on 2008-08-28
> **Dougie187 said:**
> to get back to where you were before, you should be able to recover your xorg.conf file.

Open a terminal and type
```
cd /etc/X11
```
Then, type
```
ls
```
There should be a file called xorg.conf and possibly both an xorg.conf.bak and xorg.conf.failsafe

First, type
```
sudo cp xorg.conf xorg.conf.broke.bak
```
Then type
```
sudo cp xorg.conf.bak xorg.conf
```
After you do this, restart X (Ctrl+Alt+Backspace) and see if your keyboard is working better. If that doesn't work. Then navigate back to the directory and type
```
sudo cp xorg.conf.failsafe xorg.conf
```

If either of the two work, you can remove the old broken xorg file.
```
sudo rm /etc/X11/xorg.conf.broke.bak
```

Let me know if that works to get you back to where you use to be, after that maybe we can look into your keyboard layout issue.

I followed instructions and got as far as the command.
The computers reply was

desktop:~$ cd /etc/X11
pop@pop-desktop:/etc/X11$ ls
app-defaults             xinit                     xserver
cursors                  xkb                       Xsession
default-display-manager  xorg.conf                 Xsession.d
fonts                    xorg.conf.20080828032410  Xsession.options
rgb.txt                  xorg.conf.20080828125940  Xwrapper.config
X                        Xresources
pop@pop-desktop:/etc/X11$ sudo cp xorg.conf xorg.conf.broke.bak
[sudo] password for pop: 
pop@pop-desktop:/etc/X11$ sudo cp xorg.conf.bak xorg.conf
cp: cannot stat `xorg.conf.bak': No such file or directory
pop@pop-desktop:/etc/X11$ 

What now?

---

### Post by ubalderdash on 2008-08-28
> **billgoldberg said:**
> Reconfiguring the x server to change your default keyboard layout is overkill to say the least.

Do this to change it permanently:

Use this command

```
sudo gedit /etc/X11/xorg.conf
```


In the first block of text you’ll see:



You would change the last one to the keyboard layout you would like.

"be" is also an azerty layout but I think the french one is a bit differnet, try using "fr".

Then press save.

Log out and back in and the default one will have been changed
This commqnd produced this result

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

I understand from this that French is already supposed to be the default layout but prqctice suggests otherwise.

---

### Post by Dougie187 on 2008-08-28
Well, i guess that it didn't create a backup file, like I expected it to. So we can't simply revert to the previous one.

I guess we will have to tweak your xorg.conf file. One other option, if you still have it around, is you can boot into the live cd, and email yourself the file 
/etc/X11/xorg.conf
If it has the old settings you were looking for. Then you can just replace the xorg.conf you have currently with the one from the live cd.

---

### Post by ubalderdash on 2008-08-28
When I restart my PC I am now getting about 10 identical warnings like this

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd




I do not have a live CD but is it not possible to download the required file from another source?

---

### Post by Thelasko on 2008-08-28
> **ubalderdash said:**
> Many thanks for your response. I followed your instructions without difficulty but the result was less than satisfactory. On restarting the computer the screen resolution had changed to 800x600 and I can no longer get my keyboard to respond in anything but English, i.e. qwerty instead of azerty. This is especially awkward for typing even this text and some of my program windows cannot be closed because command buttons are below the visible screen limits.
Please help me at least to get back to where I was before.

What version of Ubuntu are you using?  I assumed you were using Hardy, but you know what happens when you assume...

---

### Post by Elfy on 2008-08-28
> Well, i guess that it didn't create a backup file, like I expected it to.I believe that dpkg-reconfigure xserver-xorg results in backups with tiemstamps like

xorg.conf.20080805123458 so the backup will be like that I expect

do a ```
ls /etc/X11/xorg*
``` and check for the xorg backups

---

### Post by ubalderdash on 2008-08-28
The computers reply to that command is here

pop@pop-desktop:~$ ls /etc/X11/xorg/xorg*
ls: cannot access /etc/X11/xorg/xorg*: No such file or directory
pop@pop-desktop:~$ 


I confirm that I am using the Hardy Heron i386. I did previously try the 64bit version but with much less success even though I have an AMD64 Athlon x2. The present i386 was a clean install on a reformatted disk. The only problem that I have found is with the keyboard. Now I have a graphics problem too.

---

### Post by Elfy on 2008-08-28
d'oh sorry - ```
ls /etc/X11/xorg*
``` that should work, I pasted the wrong one :)

---

### Post by Thelasko on 2008-08-28
> I confirm that I am using the Hardy Heron i386.
That's weird, I thought dpkg-reconfigure xserver-xorg didn't touch your video configuration in Hardy.  It's only supposed to configure your keyboard and mouse.

---

### Post by ubalderdash on 2008-08-28
Here is the new result

pop@pop-desktop:~$ ls /etc/X11/xorg* 
/etc/X11/xorg.conf                 /etc/X11/xorg.conf.20080828125940
/etc/X11/xorg.conf.20080828032410  /etc/X11/xorg.conf.broke.bak
pop@pop-desktop:~$

---

### Post by Elfy on 2008-08-28
> That's weird, I thought dpkg-reconfigure xserver-xorgI thought the same, but it might be necessary to use xfix, which should set it. You can see the backups which dpkg created, you can revert to those if you wnat - check out which one you want

```
cat /etc/X11/xorg.conf.20080828125940
cat /etc/X11/xorg.conf.20080828032410
```

Assuming that you still have the drivers installed then replacing the xorg should get you back to where you were, albeit with a keyboard problem - video should be back though.

---

### Post by ubalderdash on 2008-08-28
Assuming the fist 8 letters are the date which of these files might be the earliest?
Please also lead me through the replacement process as I really am a newbie to all this.

---

### Post by Elfy on 2008-08-28
I think the first is at 12:59 second at 03:24 - I would make a copy of the current one first; did you run the command twice?

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak2808
```

To replace xorg.conf with the first

```
sudo cp /etc/X11/xorg.conf.20080828125940 /etc/X11/xorg.conf
```

restart and see if that has video back as it was, if not try again with the other file.

---

### Post by ubalderdash on 2008-08-28
WOW thats a relief. the first option had no effect but the second worked well. I have now recovered my graphics and the error screen has disappeared. Keyboard is still not working but, as you suggested, I was not expecting it to. Thanks for getting me back this far.

---

### Post by Elfy on 2008-08-28
I know that ... :phew: feeling well :)

Post your xorg as it is now then 

```
cat /etc/X11/xorg.conf
```

---

### Post by ubalderdash on 2008-08-28
Here is the result

pop@pop-desktop:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
pop@pop-desktop:~$

---

### Post by Elfy on 2008-08-28
Ok - as you are no doubt aware you have a uk keyboard again lol

Have you tried billgoldbergs post - changing the layout in xorg; I had an oddity recently where Keyboard LAyout GUI was showing uk and xorg was us - once I changed xorg it was fine.


Edit - ok I see you have now I went to look - you could try to comment out Option "XkbVariant" "intl"

> Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "gb"
#Option "XkbVariant" "intl"
EndSection


Also have a look at this thread it might help - [http://ubuntuforums.org/showpost.php?p=4836150&postcount=5](http://ubuntuforums.org/showpost.php?p=4836150&postcount=5)

---

### Post by ubalderdash on 2008-08-28
SUCCESS !!! Total, pure and really sweet:popcorn:

A very sincere thank you goes to all of you who were kind enough to help out a complete newbie who didn't even know what a Live CD was. I also know now why this system is called Ubuntu. It really is a place of humanity and brotherhood. Somebody once said that the meek shall inherit the Earth but all I can add is "Watch out Microsoft!".
Special thanks to the New Forest Pixie who persevered with me to the end and even researched my problem in other threads which led me to the ultimate solution.

Here's the part of my xorg.conf that solved the problem

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "gb" [COLOR="Red"]changed to "fr"[/COLOR]
Option "XkbVariant" "intl" [COLOR="Red"]changed to "latin9"[/COLOR]

---

### Post by Thelasko on 2008-08-28
Glad everything worked out for you.  Sorry my answer ended up causing more problems than solving.

Please mark this thread as solved, by clicking "thread tools" at the top.

---

### Post by Elfy on 2008-08-28
Good work - wasn't sure if that was the issue but thought it might be close, glad to help out when I can.

---

### Post by ubalderdash on 2008-08-29
Thelasko,

Your reply got me started down a road that led to a perfect solution and I really am grateful for that. When one has a problem the first samaritain is always the most welcome!

Thanks!

---

### Post by ubalderdash on 2008-08-29
ForestPixie,
It is you who did the good work. Thanks!

PS New Forest as in Hants?

---

