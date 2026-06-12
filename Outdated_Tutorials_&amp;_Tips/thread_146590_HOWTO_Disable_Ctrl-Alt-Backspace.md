---
title: "HOWTO: Disable Ctrl-Alt-Backspace"
date: 2006-03-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Amaranth on 2006-03-18
I'm sure everyone has hit these three buttons before. So annoying! Here is how to disable them:
[LIST]
[*]Open xorg.conf for editing
```
sudo gedit /etc/X11/xorg.conf
```
[*]Add these 3 lines to the end:```
Section "Serverflags"
Option "DontZap"      "yes"
EndSection
```
[*]Save the file and close gedit
[/list]
Now all you have to do is run 'sudo invoke-rc.d gdm restart', hit ctrl-alt-backspace (last time it will work), or log out and ctrl-alt-backscape will be dead! \\:D/

---

### Post by Keymaster on 2008-10-06
Actually I've discovered that ServerFlags is not the right section (at least not on the 2 Ubuntu 8.04 Desktop systems I just installed)

On both my systems putting that in ServerFlags caused X to go into 640x480 and get stuck there.  Not sure why, but putting it in ServerLayout worked perfectly. ;)  Now my users can't kick each other off when they lock the screen.

BTW: If you want to prevent use switching from a locked screen I'd suggest changing the permissions on /usr/bin/gdmflexiserver to 750.  User switching can still occur from unlocked sessions though. ;)

---

### Post by marcus0263 on 2009-05-09
> **Amaranth said:**
> I'm sure everyone has hit these three buttons before. So annoying! Here is how to disable them:
[LIST]
[*]Open xorg.conf for editing
```
sudo gedit /etc/X11/xorg.conf
```
[*]Add these 3 lines to the end:```
Section "Serverflags"
Option "DontZap"      "yes"
EndSection
```
[*]Save the file and close gedit
[/LIST]
Now all you have to do is run 'sudo invoke-rc.d gdm restart', hit ctrl-alt-backspace (last time it will work), or log out and ctrl-alt-backscape will be dead! \\:D/
Can you please not have this as a default setting?
users "accidently" hitting ctl-alt-backspace is laughable.  :rolleyes: This is a "core" function in linux and essential when X locks up your system.

---

### Post by Npl on 2009-05-09
> **marcus0263 said:**
> Can you please not have this as a default setting?
users "accidently" hitting ctl-alt-backspace is laughable.  :rolleyes: This is a "core" function in linux and essential when X locks up your system.essential as X locks up all the time?
why dont you just hit reset on your PC-Case if X locks up, for users this is pretty much the same as anything running on X will be killed and lost anyway if you hit Ctrl-Alt-Del.

---

### Post by marcus0263 on 2009-05-09
> **Npl said:**
> essential as X locks up all the time?
why dont you just hit reset on your PC-Case if X locks up, for users this is pretty much the same as anything running on X will be killed and lost anyway if you hit Ctrl-Alt-Del.
Why reboot the system and do a hard reset, therefore increasing chances of file corruption when all you have to do is kill X?

Serously the lame excuse of "accidently hitting ctrl-alt-backspace" is laughable.

---

### Post by Amaranth on 2009-05-09
This is an Xorg upstream default change, not an Ubuntu-specific change. We just agree with their decision so did not override it.

If you want Ctrl-Alt-Backspace to work you are not a regular user (they have no idea what it is anyway) so you should have no problem turning it back on.

```
Section "Serverflags"
Option "DontZap"      "no"
EndSection
```

---

### Post by marcus0263 on 2009-05-09
> **Amaranth said:**
> This is an Xorg upstream default change, not an Ubuntu-specific change. We just agree with their decision so did not override it.

If you want Ctrl-Alt-Backspace to work you are not a regular user (they have no idea what it is anyway) so you should have no problem turning it back on.

```
Section "Serverflags"
Option "DontZap"      "no"
EndSection
```
Yeah I'll take this upstream, this is idiotic IMO.  As to the "regular user", people I've converted over to Linux use this, why?  If they've had X lock up on them I've told them just hit ctrl-alt-backspace and log back in.  Just because a "newb" doesn't know how to use a feature doesn't mean it's useless let alone remove it.  ;)

I've read the upstream thread on this, this change was brought about because "some" Emac's users hit it by mistake.  So an extremely small (and shrinking BTW) group is behind this change?  :rolleyes::rolleyes:

Anyway, thanks for responding

Cheers

---

### Post by Amaranth on 2009-05-09
No, it has almost nothing at all to do with emacs users. One person mentioned that and everyone kind of jumped on it.

---

### Post by Bodsda on 2009-05-10
I also agree that this is a bad change but whats done is done so instead I offer a quick-fire way of enabling/disabling this, install the package dontzap

```
sudo apt-get install dontzap
```

Then to enable ctrl+alt+backspace issue this command

```
dontzap -d
```

To disable it, run

```
dontzap -e
```

Hope this helps,

Bodsda

---

### Post by hyperdude111 on 2009-05-10
> **Bodsda said:**
> I also agree that this is a bad change but whats done is done so instead I offer a quick-fire way of enabling/disabling this, install the package dontzap

```
sudo apt-get install dontzap
```

Then to enable ctrl+alt+backspace issue this command

```
dontzap -d
```

To disable it, run

```
dontzap -e
```

Hope this helps,

Bodsda

Brilliant advice. 

This has been disabled as default in jaunty and it is more useful installed. I used it on the occasion x froze and i did not want to manual re-boot. I have never hit those three keys by accident. This is like saying they should remove terminal because you *could* rm your whole system. This link proves the vast majority think the same way [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6645669](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6645669)

---

### Post by monsterstack on 2009-05-10
This command has got me out of more than a few tight spots before.

---

### Post by lwwalker on 2009-05-21
> **marcus0263 said:**
> Can you please not have this as a default setting?
users "accidently" hitting ctl-alt-backspace is laughable.  :rolleyes: This is a "core" function in linux and essential when X locks up your system.

Well . . . not entirely laughable.  I'm an intermediate user, and I've accidentally hit ctl-alt-backspace far more times than X has borked.  My laptop's backspace key is a hair's breadth from the PageDn key.  I've had a good handful of cuss-fests when aiming for ctl-alt-PageDn (change tab in gedit) and hit ctl-alt-backspace.  So, accidental X11 restarts *can* happen.

---

### Post by oomingmak on 2009-05-23
> **lwwalker said:**
> Well . . . not entirely laughable.  I'm an intermediate user, and I've accidentally hit ctl-alt-backspace far more times than X has borked.  My laptop's backspace key is a hair's breadth from the PageDn key.  I've had a good handful of cuss-fests when aiming for ctl-alt-PageDn (change tab in gedit) and hit ctl-alt-backspace.  So, accidental X11 restarts *can* happen.
So then surely you should disable it on *your *system, rather than it being forced onto the majority of users who have never had such a problem.

But as was said earlier; "what's done is done".

---

### Post by thahir1986 on 2010-06-27
i tried to install the dontzap like u mentioned it

sudo apt-get install dontzap

but it returns ,

Counldn't find package dontzap

---

### Post by ronnielsen1 on 2010-06-27
>  tried to install the dontzap like u mentioned it

sudo apt-get install dontzap

but it returns ,

Counldn't find package dontzap 	


Actually I wondered why Ubuntu didn't have this enabled by default. It's a very useful feature.

> **Ubuntu Karmic 9.10 or Higher**

 Ctrl+Alt+Backspace (i.e. the shortcut which was used to  restart the X server) has to be enabled or disabled in a different way  with respect to previous releases of Ubuntu. 
This is due to the fact that "[DontZap]("https://wiki.ubuntu.com/DontZap")" is no longer an  option in the X server and has become an option in XKB instead. 
As a result, now it's very easy to use your Desktop  environment of choice (e.g. GNOME, KDE) to enable or to disable the  Ctrl+Alt+Backspace shortcut. It is also possible to do it without KDE or  GNOME. 
It is recommended that you do  it from your desktop environment of choice (as you may find it easier  to do so). 
 
**Using GNOME**

 * Get to the  System->Preferences->Keyboard menu. 
* Select the "Layouts" tab and click on the "Layout  Options" button. 
* Then select  "Key sequence to kill the X server" and enable "Control + Alt +  Backspace". 
If this  doesn't work (e.g. the option is unchecked but the key sequence still  works), you can edit your /etc/X11/xorg.conf as explained  below, [#Ubuntu  Jaunty 9.04]("https://wiki.ubuntu.com/X/Config/DontZap#Ubuntu+Jaunty+9.04"). 

[https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)

---

### Post by serialband on 2010-09-13
> **ronnielsen1 said:**
> Actually I wondered why Ubuntu didn't have this enabled by default. It's a very useful feature.



[https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)


Where is DontZap?  I can't seem to get it for Lucid Lynx.  I want CTRL-ALT-Backspace turned on for numerous systems and I don't want to have to go sit down at each gnome or KDE desktop to do it.


```
apt-get install dontzap
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package dontzap

```

 ```
setxkbmap -option terminate:ctrl_alt_bksp 
``` doesn't work for me.  It gives

```
Error loading new keyboard description
```
I don't want to have to set this for each an every user.  I want it on the system.

---

