---
title: "[SOLVED] startx after GRUB"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-16
GRUB loads and then I I have to log in (which is fine) and I'm at a black screen with a terminal and I have to type "startx" to get to enlightenment.

How do I get around that and just having to login without typing "startx"?

---

### Post by Aearenda on 2008-06-16
You need a login manager, such as GDM, or Entrance. You mention Enlightenment - which version of Ubuntu have you installed?

OR, you can add 'startx' to your .profile, but make it conditional on not already being in X. I've seen a script on how to do that, will search for it.

---

### Post by AnLGP on 2008-06-16
I'm using a debian minimal install (Lenny) with enlightenment as the window manager.  I could install entrance I suppose.  I would rather just have something tell it that when I'm done entering my password it just starts up enlightenment.

---

### Post by Aearenda on 2008-06-16
Excellent - this is from the .bash_profile for my user on a minimal Debian etch system that uses XFCE, but it should still work for you. Add this to the end of .bash_profile:
```

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty2 ]; then
	rm ~/.serverauth* 2>/dev/null
	echo "Press CTRL and C to stop loop if session fails to start"
	startx -- -dpi 76 -br 2>/dev/null
	sleep 5
	exit 0
fi
```

I got this from another discussion thread but I didn't note where so I can't give due credit.

Notes:
1. I make my system auto-login on tty2 - you can omit the ' && [ $(tty) == /dev/tty2 ]' part to make it work on any tty.
2. The '-dpi 76' part forces the screen dots-per-inch setting. You can omit it.
3. the '-br' part makes the screen black instead of the dot-grey pattern as X starts.
4. I have forgotten why the 'sleep 5' line is there. Maybe you don't need it.
EDIT: It was to allow CTRL/C to quit the logoff/logon loop if this fails to start. Since you aren't logging on automatically, you don't need the sleep or echo lines. So the outcome for you is 
```

if [ -z "$DISPLAY" ]; then
	rm ~/.serverauth* 2>/dev/null
	startx -- -br 2>/dev/null
	exit 0
fi
```

---

### Post by AnLGP on 2008-06-16
Where's .bash_profile?

---

### Post by Aearenda on 2008-06-16
Oh, sorry - in the home directory of your user. It's a hidden file (name starts with a dot) so you have to use ```
ls -a
``` to see it.

---

### Post by AnLGP on 2008-06-16
would I want to put that before

startx /opt/e17/bin/enlightenment_start

?

---

### Post by Aearenda on 2008-06-16
Is that already in .bash_profile? If it is, and you still have to type 'startx' manually, it doesn't work, since it looks like it should start X for you. I'm not a user of Enlightenment - maybe that line is wrong.

My script assumes the desired session type is set as the default. 

If you can post the existing contents of .bash_profile, I'll be able to suggest where my bit should go.

---

### Post by AnLGP on 2008-06-16
# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

startx /opt/e17/bin/enlightenment_start

---

### Post by Aearenda on 2008-06-17
Do you see any error message when you log in? This is definitely an attempt to get Enlightenment to start automatically, but I suspect it does not work. Unfortunately, it would also try to start it again in any command line window inside Enlightenment - which may or may not be a problem -  I just tried that on a gOS E17 virtual system, it complains and then exits.

If 'startx' works from the command line to start Enlightenment, without any other parameters, then I think this is what you need:
```
# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
. ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
PATH=~/bin:"${PATH}"
fi

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
    rm ~/.serverauth* 2>/dev/null
    startx -- -br 2>/dev/null
fi
```

This assumes you log in on tty1, and will also cope with being run inside a nested session. If you log in on tty2 etc, it will be a command line login only.

---

### Post by AnLGP on 2008-06-17
I believe I see a few.  Is there a way to do a screenshot?  I can take a pic w/my phone if that'll help.

---

### Post by Aearenda on 2008-06-17
Let's leave the error messages for a mo - am I right thinking that you have been just typing 'startx' after logon, or are you typing 'startx /opt/e17/bin/enlightenment_start'?

---

### Post by AnLGP on 2008-06-17
just "startx" and then enlightenment loads.

---

### Post by Aearenda on 2008-06-17
Ok, so I think my .bash_profile should work - have you tried it?

---

### Post by AnLGP on 2008-06-17
no.

do I want to place yours before the


startx /opt/e17/bin/enlightenment_start

?

or after it?

---

### Post by Aearenda on 2008-06-17
I posted the complete file. So, you replace 'startx /opt/e17/bin/enlightenment_start' with ```
if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
    rm ~/.serverauth* 2>/dev/null
    startx -- -br 2>/dev/null
fi
```
Then log off and on again to test. If it does not work, switch to tty2 and log in to the command line so we can work out why not.

---

### Post by kerry_s on 2008-06-17
just put "startx" in ~/.bash_profile, no need to get complicated.

for auto log in:
su
apt-get install rungetty

editor /etc/inittab
change the first line for getty
[B]
1:2345:respawn:/sbin/rungetty tty1 --autologin user[/B]

change "user" to your login name

see pics:

---

### Post by AnLGP on 2008-06-17
I tried your option Aearenda and it automatically logs in, but logs into e16.  I want it to log into e17.  Do either of you think that this is possible using either method?

---

### Post by Aearenda on 2008-06-17
kerry_s: If you just put 'startx' in .bash_profile, it will try to start X again whenever you start a command line session - including from inside Enlightenment - which is wasteful, and you also have no way of logging in at the console without X starting for that user - which is ok until the day comes when Enlightenment won't start.

---

### Post by Aearenda on 2008-06-17
AnLGP: I'm sure there's a way - please post the contents of the .xinitrc file in your home directory, if it exists.

---

### Post by AnLGP on 2008-06-17
if i do ls -a in /home/steve I get this:

.                .Blog      ebook        .gnome2_private   .osmo
..               .cache     .fehbg       jwmrc             pictures
.AbiSuite        .cmus      .fehrc       .local            .recently-used.xbel
.adobe           .config    .fluxbox     .macromedia       snowman.blend
archive_key.asc  .dbus      .fontconfig  .mc               snowman.blend1
.bash_history    Desktop    .gconf       .mozilla          snowmanfront1.jpg
.bash_logout     documents  .gconfd      .naimlog          snowmanfront.jpg
.bash_profile    downloads  .gimp-2.4    .nedit            .thumbnails
.bashrc          .e         .gksu.lock   Notes             .Xauthority
.blender         .e16       .gnome2      .openoffice.org2  .xsession-errors

and in /home I get this:

.  ..  steve

I don't think I have an .xinitrc

---

### Post by Aearenda on 2008-06-17
I'm not sure how well E17 will work with Debian's config system. What does ```
update-alternatives --list x-window-manager
``` show (run this as root)?

It may be that you can select E17 from ```
update-alternatives --config x-window-manager
```(again, run as root). Please let me know what you find.

---

### Post by AnLGP on 2008-06-17
/usr/bin/e16

but I know I have e17 installed...

and

There is only 1 program which provides x-window-manager
(/usr/bin/e16). Nothing to configure.

---

### Post by Aearenda on 2008-06-17
OK, so E17 hasn't integrated itself. I think what has been happening for you is that the enlightenment_start command failed in .bash_profile, but left variables set so that E17 did start when you typed 'startx' manually. We need to work out what is failing, so that we can get the startup right for E17.

So, modify the end of .bash_profile from ```
if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
    rm ~/.serverauth* 2>/dev/null
    startx -- -br 2>/dev/null
fi
```

to

```
if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
    rm ~/.serverauth* 2>/dev/null  
    startx /opt/e17/bin/enlightenment_start
fi
```

Then logout and login again. It will probably show the error message you saw before - a photo of it (if small enough and readable) would be useful - and then leave you at the command line. 

This isn't meant to solve the problem yet - it's a diagnostic step. Please tell me what you see happening.

---

### Post by AnLGP on 2008-06-17
> if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
    rm ~/.serverauth* 2>/dev/null  
    startx /opt/e17/bin/enlightenment_start
fi

That solved it.  GRUB boots and now I login and it goes right to e17 :D Thanks :D

---

### Post by Aearenda on 2008-06-17
Amazing! If there is a load of text that scrolls by as it starts that you want to get rid of, you can add '-- -br 2>/dev/null' to the end of the line, so it looks like this:```
startx /opt/e17/bin/enlightenment_start -- -br 2>/dev/null
```

Also, you might like to do what kerry_s suggested to make the system logon automatically on tty1. I do something similar.

Enjoy!

---

### Post by AnLGP on 2008-06-17
once I get to the login prompt everythings ok from there.  It's just beforehand where the text scrolls by.  Is this what you mean when you say I can get rid of it?

---

### Post by Aearenda on 2008-06-17
Yep - the X server startup messages. My code pipes that to /dev/null (the bit bucket) instead of the screen.

EDIT - Wrong! No, I'm confused - the stuff before the login isn't this. If you want to hide that, try usplash and the Debian usplash theme.

---

### Post by AnLGP on 2008-06-17
That's also what I was talking about.  I'm going to thank you once with the ribbon but you've been a huge help :) Thanks :D

---

### Post by kerry_s on 2008-06-17
> **Aearenda said:**
> kerry_s: If you just put 'startx' in .bash_profile, it will try to start X again whenever you start a command line session - including from inside Enlightenment - which is wasteful, and you also have no way of logging in at the console without X starting for that user - which is ok until the day comes when Enlightenment won't start.

that must be something with enlightement then, i use startx when i'm setting up mine, with no problems, later after i set up my xinitrc i change it to just "xinit" and skip the startx stuff for speed.

AnLGP, i'm glad you got it fixed, sorry i been busy.

---

### Post by AnLGP on 2008-06-17
It's ok kerry no need to apologize.

I haven't noticed a diff. between having a usplash theme and not having one for speed.

---

### Post by Inxsible on 2008-06-17
I know this thread is solved...but enlightenment 17 will not start with just "startx" and that is because  you have installed it from cvs using a script from morlenux. What that script does is, it installs  E17 under /opt/e17. since this is not in the PATH, you have to explicitly tell the system to look for an X configuration under /opt/e17/bin/enlightenment_start

Just my 2 cents.

---

### Post by Aearenda on 2008-06-17
Inxsible: That's useful info, it explains why we had to work around E16 as we did - thanks.

BTW, I suspect the original way AnLGP was trying to do this (just adding 'startx /opt/e17/bin/enlightenment_start' to .bash_profile) was almost there, but failing because of X authorisation untidiness in the absence of a login manager - the line 'rm ~/.serverauth*' fixes this.

---

