---
title: "How to create custom X sessions."
date: 2005-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Stormy Eyes on 2005-10-19
I've created a HOWTO for [Custom X Sessions](https://wiki.ubuntu.com/CustomXSession) on the Wiki. Please post all comments and questions here.

---

### Post by zipmegabyte on 2005-10-19
Man, that was awesome! You're good with documentation, are you a teacher? Please keep up the good work. I'll try this guide out when I get tired of watching Naruto. ^__^

Thank you!

---

### Post by Stormy Eyes on 2005-10-19
[QUOTE=zipmegabyte]Man, that was awesome! You're good with documentation, are you a teacher? Please keep up the good work.[/QUOTE]

Thank you. I'm not a teacher, though; I'm a programmer by trade who writes as a hobby.

---

### Post by 5-HT on 2005-12-16
Thanks a lot for for the tutorial!

You've managed to easily demystify X session scripts for me.


Just one quick question though (bear in mind that I've just started learning shell scripts, so this may seem rather stupid)...

Is there a reason for using ```
 #!/usr/bin/env bash 
``` instead of ```
 #!/bin/bash 
``` to specify the shell used?

---

### Post by Stormy Eyes on 2006-02-09
[QUOTE=5-HT]Thanks a lot for for the tutorial!

You've managed to easily demystify X session scripts for me.[/quote]

You're welcome! I'm glad it helped you.

[QUOTE=5-HT]Is there a reason for using ```
 #!/usr/bin/env bash 
``` instead of ```
 #!/bin/bash 
``` to specify the shell used?[/QUOTE]

It's just a Stormy-ism, really. I remember reading somewhere that while bash isn't always installed in /bin, just about every linux machine out there has /usr/bin/env, which will invoke whatever shell is passed to it as an argument. I've seen other scripts use it as well, and just copied.

---

### Post by chugru on 2006-03-24
Nice tutorial!

I'm really ok with the KDE X session in kubuntu. 

I would, however,  like to set up my box such that, by default, I boot only to console and then must bring up KDE with the **startx** command.

Could you please mention what such a modification would require?

Thanks...

---

### Post by 5-HT on 2006-03-26
[quote=chugru]     Nice tutorial!

I'm really ok with the KDE X session in kubuntu. 

I would, however,  like to set up my box such that, by default, I boot only to console and then must bring up KDE with the **startx** command.

Could you please mention what such a modification would require?

Thanks...[/quote] 
There seem to be a few ways to do this.

1. 
One would be to simply uninstall kdm (or gdm, xdm for that matter).

Uninstalling kdm will also remove the kubuntu-desktop meta-package. Don't worry about that, nothing apart from the meta-package itself will be affected.

It is strongly recommended to reinstall kubuntu-desktop prior to upgrading, however, to avoid possible problems that may come up during an upgrade.

Once kdm is removed, you'll boot into console and startx will bring up whatever you have specified in .xinitrc.


2.
Another way to stop the gdm daemon from starting automatically on boot is described in this thread.
[http://ubuntuforums.org/showthread.php?t=141071]("http://ubuntuforums.org/showthread.php?t=141071")

You'll have to replace any instance of gdm with kdm. 
Also, I haven't tried this method myself so I wouldn't be any good at troubleshooting or know if this will work for kdm as well (though I believe it should).

3.
Other methods involve messing around with runlevels, but I have no experience with such.  However, there are some threads around pertaining to the topic.

Hope that helps

[quote=Stormy Eyes]It's just a Stormy-ism, really...[/quote] 
Thanks for the info (didn't realize you responded until chugru made this post).

---

### Post by slavik on 2006-06-14
great tutorial. I have only one question.

I plan on running firefox in X (only firefox) and was wondering how I can kill X (and restart it) when firefox dies.

---

### Post by HiddenFly on 2006-06-24
[QUOTE=slavik]great tutorial. I have only one question.

I plan on running firefox in X (only firefox) and was wondering how I can kill X (and restart it) when firefox dies.[/QUOTE]

Just press CTRL+ALT+DEL and X will restart itself.

---

### Post by slavik on 2006-06-29
No, I want it automatic, because firefox can be killed with ALT+F4

---

### Post by Dubbayoo on 2006-06-29
I believe you mean CTRL + ALT + Backspace and you can set the default runlevel in /etc/inittab. 2-4 should be what you want depending.

---

### Post by slavik on 2006-06-29
actually, ctrl+alt+backspace is disabled with the dontzap server flag :)

but I wrote a script that checks for firefox' pid and if it's not there, restarts gdm (which then reruns the entire thing like needed. now I need to get it working properly

EDIT:
my .xinitrc (with .xsession linking to it):
```
#!/bin/bash
firefox -fullscreen -P "custom" & #run firefox
echo $! > ff.pid #output the firefox pid
exec metacity #better for this use than twm or fvwm ...
```

and I have gdm start at the end of run level 3 (which is the default) and after gdm, my own custom script which checks every second for the file (ff.pid) and then reads the pid and checks to see if the pid is still there (every second) and if it isn't there, it removes the ff.pid and restarts gdm (gdm-stop && gdm) and the entire script is in a while loop. gdm is set to automatically log the proper user in, which also causes it to read the .xsession (.xinitrc really). it works nicely ... I will try to just restart firefox later and maybe find a way to not have to check for the pid every second (cron job or something?)

---

### Post by Jose Catre-Vandis on 2008-04-19
> **Stormy Eyes said:**
> I've created a HOWTO for [Custom X Sessions](https://wiki.ubuntu.com/CustomXSession) on the Wiki. Please post all comments and questions here.

Minimal install - Gutsy server, openbox

I have successfully set up xinitrc to run startx and have an automatic login with a bash_profile file.

However, if I logout, I am immediately logged back in to the graphical desktop.

Anyway to stop this behaviour?

---

### Post by smCw6GNakQn300£ on 2008-07-30
> **Stormy Eyes said:**
> I've created a HOWTO for [Custom X Sessions](https://wiki.ubuntu.com/CustomXSession) on the Wiki. Please post all comments and questions here.

Hi there,

I'm quite new to scripting in Ubuntu, but I think I need to create one!
Will the tutorial you have posted help me with my problem? :

I have Ubuntu Hardy, with all of the compiz desktop effects enabled (wobbly windows etc.)
I'd like to keep these on, as I like them.

However, I have a game (FM2008) that I run in Wine. This required a modification to the /etc/X11/xorg.conf file to disable the compiz stuff.

Could I use your tutorial to create a session for running default (with all the effects switched on), and a different one for running my game?

Is this possible?

---

### Post by mzuther on 2009-05-04
Hi Stormy Eyes,

it seems that the Wiki has somehow eaten all lines with shebangs.  Maybe you want to correct it, otherwise the average Ubuntu user might wonder where those lines have gone... ;)

Thanks for the Wiki entry,

Martin

---

### Post by birdydon on 2009-11-03
The tutorial was extremely helpful to me in creating a work-around to a bug (#448612) in Ubuntu 9.10. However, if I did not have some knowledge of shell scripts (it's not much), the missing shebangs would have resulted in failure. While the missing entries may not be the fault of the author, they need to be fixed.

---

### Post by jpkotta on 2009-11-24
Why did they remove the default session in Karmic?  Was it too confusing?  They could have renamed it to "custom" or "advanced".  /rant

Anyway, I think I got it back.  Create a file called /usr/share/xsessions/custom.desktop and put the following in it:
```

[Desktop Entry]
Encoding=UTF-8
Name=Custom
Comment=Custom Xsession
Exec=/etc/X11/Xsession
TryExec=xterm
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm
X-Ubuntu-Gettext-Domain=gdm

```

---

### Post by zhangweiwu on 2009-12-09
Hi. Since it is now 9.10 I posted my problem in a separate thread.

Can you hint me if this issue is solvable now? It must be a new issue that comes with 9.10:
Subject: .xession stop working with gdm in 9.10  
[http://ubuntuforums.org/showthread.php?p=8472810#post8472810](http://ubuntuforums.org/showthread.php?p=8472810#post8472810)

---

### Post by jpkotta on 2009-12-10
zhangweiwu, did my solution not work for you?

---

### Post by method139 on 2010-01-29
> **jpkotta said:**
> Why did they remove the default session in Karmic?  Was it too confusing?  They could have renamed it to "custom" or "advanced".  /rant

Anyway, I think I got it back.  Create a file called /usr/share/xsessions/custom.desktop and put the following in it:
```

[Desktop Entry]
Encoding=UTF-8
Name=Custom
Comment=Custom Xsession
Exec=/etc/X11/Xsession
TryExec=xterm
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm
X-Ubuntu-Gettext-Domain=gdm

```

Thank you so much. This did the trick for me as well. Additionally, I'm using [Dropbox]("https://www.dropbox.com/referrals/NTM5NDg5MjU5") to sync my .xsession-file between several computers. Also, I've created a symbolic link from it to ~/.xinitrc, thus being able to use it both when i have to type "startx", and when I use GDM. My .xsession looks as follows:

```
setxkbmap no -option terminate:ctrl_alt_bksp # map to norwegian, enable logout sequence
unclutter& # hide cursor when not in use
xsetroot -solid black # black background
ulimit -c unlimited # unlimited number of processes
xmonad # tiling window manager
```

Also, thanks to *Stormy Eyes* for the excellent HOWTO :)

---

### Post by BoneZZZ on 2010-02-05
I need to run Unison-gtk to sync local and nas folders just before exiting my gnome session, but I cannot find where to place the script. I tryed in /etc/gdm/Postsesion/ but only works when I logout, but not in shutdown or reboot.

---

### Post by alikthename on 2010-09-03
When there is no user home directory and user logs in it's created using /etc/skell as a template.

Is it possible to attach custom script to that "first time log in" event?

Thanks in advance.

---

### Post by eistee85 on 2011-01-11
First of all: Great Tutorial!
I recently used it, to create an .xinitrc which only starts Boxee (boxee.tv), as i want to use this for my htpc.
I don't want Gnome to start, just Boxee.

```
#!/usr/bin/env bash

exec /opt/boxee/run-boxee-desktop --standalone
```

So, when i log off my Gnome-Desktop an choose "User-Defined-Session" to log in again, Boxee starts immediatly. Evrythings fine so far.

Now, i configured my account to auto-login und i chose to start with "User-Defined-Session".
But when i reboot, each time the PC starts Gnome instead of my User-Defined-Session with Boxee.

Any ideas on how i can solve this?

I'm using Ubuntu 10.10 by the way.

Thanks!

Philipp

---

### Post by eistee85 on 2011-01-12
No ideas on how to solve that?

---

