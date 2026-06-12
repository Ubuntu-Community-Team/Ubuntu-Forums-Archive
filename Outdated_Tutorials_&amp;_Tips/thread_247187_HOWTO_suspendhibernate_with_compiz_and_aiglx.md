---
title: "HOWTO suspend/hibernate with compiz and aiglx"
date: 2006-08-30
forum: Outdated Tutorials &amp; Tips
---

### Post by crazy___cow on 2006-08-30
When I installed AIGLX and Compiz I have had problem on resume from suspend and hibernate (never properly wakes up). I think that it's a problem of compiz. To resolve this, just add two simple scripts to acpi: the idea is to kill compiz and to load metacity on suspend/hibernate and to reload compiz after resume.

First script is "/etc/acpi/suspend.d/25-compiz-stop.sh"

#!/bin/bash
#/etc/acpi/suspend.d/25-compiz-stop.sh

PID_COMPIZ_REAL=`ps -Ao pid,comm | grep compiz.real | awk '{print $1}'`
if [ "$PID_COMPIZ_REAL" == "" ]; then PID_COMPIZ_REAL=0; fi
if [ "$PID_COMPIZ_REAL" -gt 0 ]; then
export COMPIZUSER=`ps -Ao user,comm | grep compiz.real | awk '{print $1}'`
sudo -b -H -u $COMPIZUSER /usr/bin/metacity --display=:0.0 --replace gconf &
PID_COMPIZ_TRAY=`ps -Ao pid,comm | grep compiz-tray | awk '{print $1}'`
if [ "$PID_COMPIZ_TRAY" -gt 0 ]; then
kill -s 15 $PID_COMPIZ_TRAY &
fi
fi
if [ "$PID_COMPIZ_REAL" == 0 ]; then
export COMPIZUSER=`ps -Ao user,comm | grep gnome-power-man | awk '{print $1}'`
fi




The second one is "/etc/acpi/resume.d/99-compiz-resume.sh"

#!/bin/bash
#/etc/acpi/resume.d/99-compiz-resume.sh

export DISPLAY=:0.0
if test -z $COMPIZUSER;then
echo "Setting COMPIZUSER....."
PID_COMPIZ_REAL=`ps -Ao pid,comm | grep compiz.real | awk '{print $1}'`
if [ "$PID_COMPIZ_REAL" == "" ]; then PID_COMPIZ_REAL=0; fi
if [ "$PID_COMPIZ_REAL" -gt 0 ]; then
export COMPIZUSER=`ps -Ao user,comm | grep compiz.real | awk '{print $1}'`
fi
if [ "$PID_COMPIZ_REAL" == 0 ]; then
export COMPIZUSER=`ps -Ao user,comm | grep gnome-power-man | awk '{print $1}'`
fi
fi
PID_COMPIZ_TRAY=`ps -Ao pid,comm | grep compiz-tray | awk '{print $1}'`
if [ "$PID_COMPIZ_TRAY" == "" ]; then PID_COMPIZ_TRAY=0; fi
if [ "$PID_COMPIZ_TRAY" == 0 ]; then
echo "Starting compiz-tray-icon...."
sudo -H -b -u $COMPIZUSER /usr/bin/compiz-tray-icon &
fi


Hope this could help someone with the same problem!

---

### Post by kecci on 2006-08-30
Great, this seems to work with latest aiglx from beerorkid repos on my i915 laptop! Thanks!!

---

### Post by d-Pixie on 2006-09-05
Tried with same setup as Kecci, but after last big update of Compiz (today/yesterday). Still working for you guys? Or could you update the scripts to work with the new version?

If it is still working for you after the Quinnstorm repo update, how's that ;o) Did: "sudo gedit /path/to/file1" and dito for file 2. Hiber and startup enden in a black screen. So i did: "sudo chmod +x /path/to/file" hiber and startup ended in black screen ... Anything I'm missing?

Thx for the effort btw! Would realy like the fix. After fixing the wlan today the hiber is all that stands in the way for a compleat Ubuntu laptop ;o)

---

### Post by crazy___cow on 2006-09-07
The compiz development team changes everything everytime!
Now the gnome-compiz-manager (and compiz-tray-icon) doesn't work anymore with the latest update: they switch from gconf to csm (a new  utility to configure compiz, plugins, etc) and they modify binaries names and options.

I'm trying to change my scripts to fix things.

[SIZE="3"]
[COLOR="Red"]#!/bin/bash
#/etc/acpi/suspend.d/25-compiz-stop.sh

PID_COMPIZ_REAL=""
PID_COMPIZ_CGWD=""
PID_COMPIZ_REAL=`ps aux | grep compiz | grep -v grep | head -n 1 | awk '{print $2}'`
if [ "$PID_COMPIZ_REAL" == "" ]; then PID_COMPIZ_REAL=0; fi
if [ "$PID_COMPIZ_REAL" -gt 0 ]
then
export COMPIZUSER=`ps aux | grep compiz | grep -v grep | head -n 1 | awk '{print $1}'`
sudo -b -H -u $COMPIZUSER /usr/bin/metacity --display=:0.0 --replace gconf &
PID_COMPIZ_CGWD=`ps aux | grep compiz | grep -v grep | head -n 1 | awk '{print $2}'`
if [ "$PID_COMPIZ_CGWD" == "" ]; then PID_COMPIZ_CGWD=0; fi
if [ "$PID_COMPIZ_CGWD" -gt 0 ]
then
kill -s 15 $PID_COMPIZ_CGWD &
fi
fi
if [ "$PID_COMPIZ_REAL" == 0 ]; then
export COMPIZUSER=` ps aux | grep gnome-power-man | grep -v grep | head -n 1 | awk '{print $2}'`
fi[/COLOR][/SIZE]


The resume script has some problems....in my ubuntu if you enable the last line, compiz crashes...I don't know why! If you try it on a terminal works perfectly....so I decided to leave alive metacity after suspend/hibernate. If you want compiz, open a terminal and write 'compiz-start' to start compiz!


[SIZE="3"][COLOR="Red"]#!/bin/bash
#/etc/acpi/resume.d/99-compiz-resume.sh

export DISPLAY=:0.0
if test -z $COMPIZUSER;then
PID_COMPIZ_REAL=""
PID_COMPIZ_REAL=`ps aux | grep compiz | grep -v grep | head -n 1 | awk '{print $2}'`
if [ "$PID_COMPIZ_REAL" == "" ]; then PID_COMPIZ_REAL=0; fi
if [ "$PID_COMPIZ_REAL" -gt 0 ]; then
export COMPIZUSER=`ps aux | grep compiz | grep -v grep | head -n 1 | awk '{print $1}'`
fi
if [ "$PID_COMPIZ_REAL" == 0 ]; then
export COMPIZUSER=` ps aux | grep gnome-power-man | grep -v grep | head -n 1 | awk '{print $2}'`
fi
fi
#sudo -H -b -u $COMPIZUSER /usr/bin/compiz-start &[/COLOR][/SIZE]


I'll wait for the next release hoping THEY fix things....
With Compiz and AIGLX I'm unable also to switch console with Ctrl+Alt+Fn: when I return on X with Ctrl+Alt+F7 the screen hangs! The only thing I can do is reboot with Ctrl+Alt+Canc!! Do you have the same problem?

---

### Post by Hobbes on 2006-09-07
u try the line compiz-start without the '&' ?

---

### Post by crazy___cow on 2006-09-07
Sure! No difference with or without '&' and the end of the line. So I decide to comment it out by adding a "#" at the beginning of the line and wait for next releases....
I have also tried to add a sleep command before 'compiz-start', to launch compiz after n seconds....no way....

---

### Post by d-Pixie on 2006-09-07
Tried the "without &" above. Didn't work. Compiz doesn't crach but it doesn't start eather.

So, now I can hiber (cinda). Tnx! How about the "blank screen" funktion? Related probelm. Compiz cant get the screen to reinitiate on sleep or blank screen (closing the lid or when it turns off the screen when the screensaver has be on for to long) ... Any help to be had here?

Tried the Alt+Ctrl+Fn to, didn't get the screent back. Think it hang or smthn... Any fix would be great. But right now the blank screen and compiz-start not working on resume is more urgent. What does the options to sudo do in the last line (call me lazy)?

---

### Post by rob martin on 2006-09-22
Bump ....please..

---

### Post by jost on 2006-10-07
This (simplified) version of the same scripts 
works for me, using kubuntu dapper, aiglx and beryl:

---------------------------
#!/bin/bash
#/etc/acpi/suspend.d/07-compiz-stop.sh

PID_BERYL=`ps -Ao pid,comm | grep beryl | awk '{print $1}'`
if [ "$PID_BERYL" != "" ]; then
kill -s 15 $PID_BERYL &
fi
------------------------------

------------------------------
#!/bin/bash
#/etc/acpi/resume.d/99-beryl-resume.sh

export DISPLAY=:0.0
BERYLUSER=`ps -Ao user,comm | grep startkde | awk '{print $1}'`
PID_BERYL=`ps -Ao pid,comm | grep beryl-manager | awk '{print $1}'`
if [ "$PID_BERYL" == "" ]; then PID_BERYL=0; fi
if [ "$PID_BERYL" == 0 ]; then
echo "Starting beryl-manager...."
sudo -H -b -u $BERYLUSER /usr/bin/beryl-manager &
fi
------------------------

N.B.
Since the first script uses "grep beryl" to find the pids of 
beryl and beryl-manager it is important that the script name does not contain "beryl" .... (this is why it is still called *compiz-stop.sh)

---

### Post by jopsen on 2006-10-17
Have anyone made the resume script for aiglx and beryl work??? I'm running Ubuntu (gnome) and it doesn't work... I even tried adding beryl-manager in the end of the script, but no luck... Have anyone got it working???

The suspend script works great, it just isn't nice to start beryl manually without another window-manager :)

---

### Post by Bastanteroma on 2006-10-17
How do you set these scripts up?

---

### Post by jopsen on 2006-10-18
> **Bastanteroma said:**
> How do you set these scripts up?

This is how I did with the scripts for Ubuntu/Aiglx/Beryl, I had the first one working but not the second one, which means I have to start beryl manually from a shortcut on my desktop...
```

sudo su
gedit /etc/acpi/suspend.d/07-compiz-stop.sh

```

Copy paste the first script from this thread...

```

sudo su
gedit /etc/acpi/resume.d/99-beryl-resume.sh

```

Copy paste the second script from this thread...

---

### Post by NMUrugbysteve on 2006-10-20
Anyone got a resume script that works with the beryl suspend one? I don't know enough about scripting to make it work with gnome and not kde.

---

### Post by linuxmad on 2006-10-20
I am Also having the same problem. I am able to suspend but not able to resume:mad:

---

### Post by caillou on 2006-10-24
ok... i think i see where the problem is:

the script jost gave works with kde only ;) but most of the people here most likely run gnome.

what the resume script does in the following line

```

[FONT="Courier New"]BERYLUSER=`ps -Ao user,comm | grep startkde | awk '{print $1}'`
                                               ^ put the user ino
                                                 the variable BERYLUSER
                               ^ of all the running progs show
                                 only startkde
            ^ give me all running programs
 ^ define the variable BERYLUSER [/FONT]
```

is that it tries to guess what user shoul restart the [FONT="Courier New"]berly-manager[/FONT] by finding out who started [FONT="Courier New"]startkde[/FONT], which no one does in gnome ;) 

one way to modify this linie is

```

BERYLUSER=`ps -Ao user,comm | grep emerald | awk '{print $1}'`

```

which should work in both, gnome and kde... (because emerald is started with beryl but not suspended by the [FONT="Courier New"]07-compiz-stop.sh[/FONT] script)

so, to resume, generate the two following files:

```

sudo su
gedit /etc/acpi/suspend.d/07-compiz-stop.sh

```

and fill in what jost described earlyer:

```
#!/bin/bash
#/etc/acpi/suspend.d/07-compiz-stop.sh

PID_BERYL=`ps -Ao pid,comm | grep beryl | awk '{print $1}'`
if [ "$PID_BERYL" != "" ]; then
kill -s 15 $PID_BERYL &
fi
```

and for the second file
```
sudo su
gedit /etc/acpi/resume.d/99-beryl-resume.sh
```

fill in with the modified linie:

```

#!/bin/bash
#/etc/acpi/resume.d/99-beryl-resume.sh

export DISPLAY=:0.0
BERYLUSER=`ps -Ao user,comm | grep emerald | awk '{print $1}'`
PID_BERYL=`ps -Ao pid,comm | grep beryl-manager | awk '{print $1}'`
if [ "$PID_BERYL" == "" ]; then PID_BERYL=0; fi
if [ "$PID_BERYL" == 0 ]; then
echo "Starting beryl-manager...."
sudo -H -b -u $BERYLUSER /usr/bin/beryl-manager &
fi

```

let me know if that works for you...

---

### Post by linuxmad on 2006-10-24
yep ..:D :D :D This is working now. I have not tested fully but it appears to be working ok....We will see... if this solves our troubles.. It seems so;)

---

### Post by madscience on 2006-10-27
I can now resume from hibernate OK, but beryl-manager isn't restarting and I have no window decorations, even using that last version of 99-beryl-resume.sh

Any ideas?

---

### Post by madscience on 2006-10-27
bump

---

### Post by madscience on 2006-10-28
Running compiz-stop and then beryl-resume in a console gives me the following error:
sudo: no passwd entry for 1000!

How do I resolve this?

---

### Post by crazy___cow on 2006-10-30
I have no more problem with beryl+aiglx on my i915 after a fresh edgy installation! No problem with susped/hibernate, no problem with VT switch (Ctrl+Alt+Fn). There are only some issues with video players(as expected). XV works only with mplayer, while there are some quirks (screen artifacts) with totem (gstreamer and XV output).
Does anyone have a solution for these problems without disable XV? If I use X11 as video output, I have problems to view movies (framedropping, bad quality).

PS: I use this tutorial to install beryl...it's very simple!!
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft)

---

### Post by gerard67 on 2006-12-10
> **caillou said:**
> ok... i think i see where the problem is:

the script jost gave works with kde only ;) but most of the people here most likely run gnome.

what the resume script does in the following line

[...]

let me know if that works for you...

This works for me ... but only one time ! After a first suspend/resume with AIGLX/Beryl where all went fine, I can't suspend anymore with any window manager. Network is disconnecting, that means that at least some of the suspend scripts works OK ... now I'm looking for any clues ...

thanks,
Mathieu

---

### Post by viz_e on 2006-12-13
I still can not resume kubuntu with AIGLX and beryl. Any idea what to check?

Edit: even if I "kwin --replace, pkill emerald, pkill beryl" before suspending I don't get a working resume... :\

---

### Post by johnalewis on 2007-01-20
Here's a different set of scripts I've been using.  These will handle multiple running beryl-manager sessions and will also only restart beryl on resume if it stopped it on suspend.  Instead of killing/starting the processes outright, it uses the USR2 signal that causes beryl-manager to toggle window managers.

> #!/bin/bash
# /etc/acpi/suspend.d/25-beryl-suspend.sh

pids=""
for pid in `pidof /usr/bin/beryl-manager`
do
  ps -o comm= --ppid $pid | grep -q '^beryl$'
  if (($? == 0)); then
    pids="$pid $pids"
    kill -USR2 $pid
  fi
done
export BERYLMGRPIDS="$pids"

> #!/bin/bash
# /etc/acpi/resume.d/99-beryl-resume.sh

for pid in $BERYLMGRPIDS
do
  (sleep 10 && kill -USR2 $pid)&
done


---

### Post by kilou on 2007-01-24
How do you link these scripts so that they are launched when clicking on the shutdown menu in GNOME where you can logout, hibernate, suspend, shutdown, restart etc???

---

### Post by jopsen on 2007-01-24
You don't have to link them, when you place the script in the /etc/acpi/suspend.d/ or /etc/acpi/resume.d/ directories the scripts should be executed at suspend or resume respectively...
All you have to do is to save the scripts in the right directory...

---

### Post by kilou on 2007-01-25
Oh OK! Thanks Jopsen.

---

### Post by kilou on 2007-01-25
The scripts work find with suspend but don't with hibernate. I get a message "failed to activate device" and something after that I don't have time to read. Is this related to the scripts or is this another problem?

---

### Post by kilou on 2007-01-27
Any idea?

---

### Post by jonlatane on 2007-02-01
I'm using Beryl/AIGLX on a Thinkpad T43 (Radeon Mobility X300, open-source drivers).  None of the solutions worked for me.  Since the T43 is a standard at UNC (my school), lots of us CS majors have had problems with this.  However, I believe I just came up with a solution, and it's much simpler than anything else out there.  In fact, nothing interacts with Beryl.  I have this working on Edgy, by the way.

First, make sure you remove any of the files you put in your suspend.d and resume.d directories from other people's suggestions.  Or just chmod -x all of them.

Now do
```

sudo gedit /etc/acpi/suspend.d/99-terminal-change.sh

```

In the file put:
```

#!/bin/bash
/usr/bin/chvt 13

```

What this will do is switch you to a separate virtual terminal in text mode.  You don't need to put anything in resume.d, since it will resume back in the terminal that started the suspend (terminal 7).

Normally, this would interfere with the standard terminals you get by doing Ctrl-Alt-F1, however since you don't have an F13, this terminal is (basically) unimportant!

I'm not sure if this is some kind of horrible security thing or not, I'm far from a Linux or X guru.  But this does work for me.

---

### Post by kilou on 2007-02-01
Works for me too :) In fact it works with less jerks than the other solution! You're a genius! Thanks

However I still get the same error when doing hibernate but this is certainly related to another problem ("failed to activate device...").

---

### Post by Twiggy794 on 2007-02-01
I can't get my Pavilion to suspend but hibernate works fine.  When I wake it up I can hear it start spinning again but the wifi light never blinks back on and I get nothing on screen, it doesn't even turn back on.  Any ideas?  I've tried all 3 script pairs in the thread so far.

---

### Post by 5-HT on 2007-02-02
> **jonlatane said:**
> 

Now do
```

sudo gedit /etc/acpi/suspend.d/99-terminal-change.sh

```In the file put:
```

#!/bin/bash
/usr/bin/chvt 13

```What this will do is switch you to a separate virtual terminal in text mode.  You don't need to put anything in resume.d, since it will resume back in the terminal that started the suspend (terminal 7).

Normally, this would interfere with the standard terminals you get by doing Ctrl-Alt-F1, however since you don't have an F13, this terminal is (basically) unimportant!

I'm not sure if this is some kind of horrible security thing or not, I'm far from a Linux or X guru.  But this does work for me.

Works like a charm!
Thanks

---

### Post by julipanno on 2007-03-08
Beryl seems to work rather fine (for me) after waking from suspend without any additional configuration or scripts. The only problem is that the window decorator makes all window border garbled and needs to be restarted on wake. I can do this from the commandline with the command ```
emerald --replace
``` but placing the command in a script to be executed in /etc/acpi/resume.d/ does not seem to have any effect.
My script is simply this:```
#!/bin/bash
emerald --replace
```
I can run it manually fine using the command /etc/acpi/resume.d/99-emerald-restart.sh which works like it should, but it does not seem to be executed on wake.

peace,
Stian

---

### Post by fmaste on 2007-05-31
I managed to make suspend/hibernate work on my DELL inspiron 9400 without scripts doing this

NOTE: I'm using feisty with beryl installed from the beryl repos, all the other setting are the default ones (I never manually edit xorg.conf or acpi-support and beryl setting were are the default ones) and suspend/hibernate was working out of the box without beryl.

- Disable "Sync To VBlank" in beryl.
It is located on general options of the veryl manager. Just unckeck it.

- Update your /etc/X11/xorg.conf and add an "Option "NvAGP" "1" line in the "Section "Device":
(must look like this)
Section "Device"
...
Option "NvAGP" "1"
EndSection

- Disable warm-booting the video hardware on resume by editing your /etc/default/acpi-support as follows :
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

Good luck!!

---

### Post by rogun on 2007-07-28
Hey thanks!

That worked for me too! I'd already disabled warm-booting to get Metacity to work, and had tried the other two in various combinations for Compiz, but apparently not both together yet.

For the record, I have a desktop with an ASUS A7N8X Deluxe motherboard and a Nvidia 7600 GT video card. Use this command to disable "Sync To VBlank" in Compiz:

gconftool -s /apps/compiz/general/screen0/options/sync_to_vblank -t boolean false

---

### Post by Kavjik on 2007-08-28
Thx a lot. the chage in gconf worked. :)

---

### Post by gladenko on 2007-09-27
My problem is that the script is ok if i exec manual but when i press start button to resume system i return in gnome but beryl-manager is not running because /etc/acpi/resume.sh is not start

Where is the script to call resume.sh when i press start button?

Thank You 

glady:popcorn:

---

### Post by dahlheim on 2007-10-09
> **Kavjik said:**
> Thx a lot. the chage in gconf worked. :)

thanks!  disabling sync to vblank worked for me too.

-dell xps m1210

---

### Post by balaji.ramasubramanian on 2008-10-25
I don't know why, but I did not have to make any changes to Compiz settings. My suspend was not working fine earlier. It used to come back up when I opened my laptop, but the display would simply be blank and even if it did resume once in a while, Compiz was dead slow then and I had to actually kill Compiz and re-fire it anyway. So here's what I did:

I wrote a script that simply reads as follows:


#!/bin/bash
# This is a small script that will just kill compiz before suspend

COMPIZ_PID=`ps -eaf | grep compiz.real | grep -v grep | awk '{print $2}'`
kill -9 $COMPIZ_PID

# That's all


I saved this program in /etc/acpi/suspend.d/25-compiz-stop.sh and that's all. I didn't even have to write a script to restart Compiz upon resume. I wanted to test if Compiz was successfully killed or not. But when I resumed, it just worked perfectly. I think one of the scripts there must be doing that already. Anyway, try this out.

---

