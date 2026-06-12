---
title: "hardy with ATI driver"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by akimatsu123 on 2008-04-26
hi,

i just installed a fresh installation of Hardy (not an upgrade). i previously used Gutsy with an ATI restricted driver. 

In Gutsy, as soon as i started the computer it told me that it was using a restricted driver. To use compiz fusion, i also had to install the xorg package for ATI. 

I tried to do that for Hardy, but the xorg won't install (it says my computer is not supported). Compiz manager won't install either because it says it needs special hardware or my computer isn't supported. 

what do i do? by the way, i also cant enable the simple effects under 

system --> appearance --> visual effects

when i try to, it just spits a box saying "effects could not be enabled" or something. How do i deal with the ATI video driver on hardy? 

thanks.

---

### Post by SOULRiDER on 2008-04-26
You cant enable them because the propietary ATI drivers arent installed. What kind of ATI card do you have?

---

### Post by akimatsu123 on 2008-04-26
i'm not sure. how do i check? I have an IBM T60p if that helps at all.

---

### Post by Redsandro on 2008-04-26
I have a similar problem. This morning I had **Ubuntu 7.10** on my **Compaq Evo N610c** laptop [SIZE="1"](with *Ati Radeon Mobility 7500*)[/SIZE], with Visual Effects (compiz?) working out of the box. Using **Fn + F4**, I could also swap between LCD and TV.

[SIZE="1"](Strange thing, the restricted manager told me my computer does not need a restricted driver, but I thought that was the only way to see Visual Effects and play games.)[/SIZE]

This afternoon I upgraded to **Ubuntu 8.04**, and suddenly I cannot enable Visual Effects and I cannot swap to TV anymore. I checked my *xorg.conf* but it's still using the 'ati' driver that it also used when everything worked before the upgrade.

I'd like to get this working, especially the swapping to tv. I had no extra section in my xorg.conf to get it working as it worked out of the box.

---

### Post by Redsandro on 2008-04-26
Just as a part of trial-and-error research, I tried:
```
aticonfig --initial --input=/etc/X11/xorg.conf
```
but then not only X did not work, also al my tty terminals were zoomed in to 10% of the actual screen, making it nasty to repair. I have never seen that. Anyway, I got X back. Still no proper ATI functions though. :(

---

### Post by vidus on 2008-04-26
worked for me:

go to synaptic, search for envy, mark for installation the core and the gtk. apply.

once installed you will find it in the apps > system tools.

run it, select auto install ati drivers. apply.

reboot, your done.

---

### Post by Redsandro on 2008-04-26
omg.. I screwed up my X..
I tried some other threads' instructions and now anything moving on my screen (scrolling, dragging) goes like 1 fps!

Here's what I did:

```
sander@RED-N610c:~$ **sudo compiz &#8211;&#8211;replace**
[sudo] password for sander: 
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 
*(terminal not responding, so close)*

sander@RED-N610c:~$ **sudo apt-get install xserver-xgl**
[sudo] password for sander: 
*(blahblah)*
```
Then on your panel it will say:

> **Xgl server setup changed**

The Xgl server will now be started automatically next time you login.  It is no longer necessary to use any special X session to start Xgl, and such sessions will likely fail to work properly.  Please select a regular session from your session manager next time you log in.  To disable Xgl autostart for this user, create a file named ~/.config/xserver-xgl/disableReboot and..
Tadah! Your X is now screwed up.
Don't do it. :(

---

### Post by Redsandro on 2008-04-26
> **vidus said:**
> go to synaptic, search for envy, mark for installation the core and the gtk. apply.
once installed you will find it in the apps > system tools.
run it, select auto install ati drivers. apply.

I' m getting a few crash reports and then the app sais failed. :(

Nice one though, might help someone else. :)

---

### Post by alof8k on 2008-04-27
I have a similar problem. I installed hardy just this morning and after I logged into ubuntu, it had a resolution of 640x480 with the default install. I have a ati radeon x1650 pro (512MB) agp card so I decided to install the ati driver via the restricted driver manager icon/applet. when i did that, it asked me to restart the pc where I did but now I can't even log into gnome because everything seems messed up.  I can't even get a clear screen in X. 

all i see is some lines on screen and I'm assuming something went horribly wrong. any ideas? please help

---

### Post by Helios1276 on 2008-04-27
What about trying Envy? Moving to Hardy from Gutsy solved my ATI issues but I used to use Envy on Gutsy.

---

