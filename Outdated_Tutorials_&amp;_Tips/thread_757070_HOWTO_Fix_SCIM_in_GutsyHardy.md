---
title: "HOWTO: Fix SCIM in Gutsy/Hardy"
date: 2008-04-16
forum: Outdated Tutorials &amp; Tips
---

### Post by terrukallan on 2008-04-16
Note: Based on Michal77's post [here]("http://ubuntuforums.org/showpost.php?p=3676161&postcount=6").

The default setup of SCIM on Gutsy and Hardy produces some irritating errors including the inability to rename files in Nautilus (Gutsy), inability to type jump to files in Nautilus by typing the first few letters (Hardy), and Firefox 3's URL matching in the location bar lagging by a character (Hardy).  There are quite likely others, but these are the ones I have personally experienced.

All of these problems can be fixed by installing scim-bridge and using that instead of xim.

To install scim-bridge on Gutsy:
```
sudo apt-get install scim-bridge

```

To install scim-bridge on Hardy:
```
sudo apt-get install scim-bridge-agent scim-bridge-client-gtk scim-bridge-client-qt scim-bridge-client-qt4
```

Now open the scim config file:
```
sudo gedit /etc/X11/xinit/xinput.d/scim
```
and chage the following lines:
```

GTK_IM_MODULE=xim
QT_IM_MODULE=xim

```
to:
```

GTK_IM_MODULE="scim-bridge"
QT_IM_MODULE="scim-bridge"

```

Restarting SCIM is **not** sufficient so restart X either by restarting the computer (System->Quit->Restart) or hitting [CTL][ALT][BACKSPACE].

**_WARNING_**:  [CTL][ALT][BACKSPACE] will immediately log out and restart X.  Make sure to save anything important before doing this.

---

### Post by Abiezer on 2008-04-28
Many thanks! I upgraded yesterday to find SCIM not working; having read about the change in default hotkeys I fiddled around with that for ages thinking that was my problem, but your fix has sorted everything. It seems every upgrade breaks SCIM :(
&#29616;&#22312;&#26159;&#21319;&#32423;&#20043;&#21518;&#31532;&#19968;&#27425;&#33021;&#25171;&#20013;&#25991;&#65281;&#38750;&#24120;&#24863;&#35874;&#65281;

---

### Post by xand on 2008-04-28
Thanks for this, i had a problem with that too posted here [http://ubuntuforums.org/showthread.php?p=4822346#post4822346](http://ubuntuforums.org/showthread.php?p=4822346#post4822346).

I had already tried your how-to, but it didn't work without the step of deleting '.scim' and '.xinit.d' folders before restarting X. Hope this can be a helpful step for people with HH like me.

---

### Post by tacutu on 2008-04-29
isn't it easier to just do:

im-switch -z all_ALL -s scim-bridge

instead of editing the files?
(instead of all_ALL you can  also select the desired locale)

this can be done as user, for a user-based setup or as root, for system-wide defaults.

---

### Post by cchi on 2008-04-30
> **tacutu said:**
> isn't it easier to just do:

im-switch -z all_ALL -s scim-bridge

instead of editing the files?
(instead of all_ALL you can  also select the desired locale)

this can be done as user, for a user-based setup or as root, for system-wide defaults.

Yes, in Ubuntu 8.04 this was all I needed to do too.  Thank you!

Interestingly, SCIM was working fine for the admin user that I installed Japanese Input Support with.  But, for any other users, including users where I created them after installing Japanese support, SCIM was not enabled.

The above command run in the other users' accounts worked a treat.

---

### Post by huczek on 2008-05-29
Ubuntu 8.04 Hardy Heron x86
Firefox 3 beta 5 and Firefox 3 RC
output in terminal: errors while firefox running
```
(firefox:6773): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6773): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```
The firefox often interrupts and exits. I've changed the SCIM using: im-switch -z all_ALL -s scim-bridge
and I have still the same problem:
```
Segmentation fault
```

---

### Post by dmizer on 2008-05-29
> **huczek said:**
> Ubuntu 8.04 Hardy Heron x86
Firefox 3 beta 5 and Firefox 3 RC
output in terminal: errors while firefox running
```
(firefox:6773): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6773): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```
The firefox often interrupts and exits. I've changed the SCIM using: im-switch -z all_ALL -s scim-bridge
and I have still the same problem:
```
Segmentation fault
```

this problem is not related to scim, it's probably related to a firefox add-on of some kind.  try disabling your add-ons one by one until the problem disappears.  if it does not, please start a new thread.

---

### Post by huczek on 2008-05-31
Well it looks like problem with flash player. After uninstalling and disabling of all add-ons. Still I have the problem. I have changed player to the default 9 in ubuntu with/without library flash support. Now I have the error after closing tab with site using flash content i.e.:
[http://at-tic.com](http://at-tic.com)
[http://www.websearchfactory.pl](http://www.websearchfactory.pl)
[http://www.myspace.com/stevepageot](http://www.myspace.com/stevepageot)

After changing of plugin from 10 beta to default 9  - the error looks like:
```
(firefox:5996): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```
I also turned off loading of module-x11-xsmp into PulseAudio.

**Maybe it has something to do with SCIM?**

It seems I still can't use a flash player. That's a disaster. I tried all advices I had found on the forum. There's no information about the error "g_object_unref: assertion" on Internet.

---

### Post by dmizer on 2008-05-31
> **huczek said:**
> Well it looks like problem with flash player. After uninstalling and disabling of all add-ons. Still I have the problem. I have changed player to the default 9 in ubuntu with/without library flash support. Now I have the error after closing tab with site using flash content i.e.:
[http://at-tic.com](http://at-tic.com)
[http://www.websearchfactory.pl](http://www.websearchfactory.pl)
[http://www.myspace.com/stevepageot](http://www.myspace.com/stevepageot)

After changing of plugin from 10 beta to default 9  - the error looks like:
```
(firefox:5996): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```
I also turned off loading of module-x11-xsmp into PulseAudio.

**Maybe it has something to do with SCIM?**

It seems I still can't use a flash player. That's a disaster. I tried all advices I had found on the forum. There's no information about the error "g_object_unref: assertion" on Internet.

if you've run this command:
```
im-switch -z all_ALL -s scim-bridge
```
or followed the directions in the first post ... then no, it doesn't have anything to do with scim.

are you running 64 bit ubuntu?

---

### Post by huczek on 2008-05-31
after using im-switch -z all_ALL -s scim-bridge it returns nothing. With sudo it returns:

```
kononowicz@anin:~$ sudo im-switch -z all_ALL -s scim-bridge
[sudo] password for kononowicz: 
update-alternatives: Cannot find alternative `/etc/X11/xinit/xinput.d/scim-bridge'.
```
I installed scim bridge and edited manually scim like described in the first post.

I use x86 32bit hardy heron lts.

---

### Post by dmizer on 2008-05-31
> **huczek said:**
> after using im-switch -z all_ALL -s scim-bridge it returns nothing. With sudo it returns:

```
kononowicz@anin:~$ sudo im-switch -z all_ALL -s scim-bridge
[sudo] password for kononowicz: 
update-alternatives: Cannot find alternative `/etc/X11/xinit/xinput.d/scim-bridge'.
```
I installed scim bridge and edited manually scim like described in the first post.

I use x86 32bit hardy heron lts.

running it as user never returns results.  it simply changes the im-switch setting to scim for all packages on the system.  if the problem disappears when you remove flash, then you should look into possible solutions for flash plugin.  which plugin are you using for flash?

---

### Post by huczek on 2008-05-31
> **dmizer said:**
> if the problem disappears when you remove flash, then you should look into possible solutions for flash plugin. which plugin are you using for flash?

I'm not so sure if it is just the plugin.

As I have written I used adobe flash player 10 beta and returned to the default. So now it's a nonfree **Adobe Flash Player 9.0.124.0ubuntu2**.
As I have also written I tried with and without libflashsupport.
Firefox 3 beta 5 and Firefox 3 RC1.

---

### Post by dmizer on 2008-05-31
the errors you posted earlier:
```
(firefox:6773): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6773): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```
these are related to gtk.  are you running a custom theme in firefox, or in gnome?

---

### Post by huczek on 2008-05-31
No. I run default gnome theme - human.
I had turned off all the possible add-ons to check source of errors. The errors are related with the flash player. I'm not sure if related directly with flash plug in. Maybe something has influence on the plugin.

---

### Post by freemant on 2008-06-27
In Hardy, I also get the "cannot find alternative" error. To fix that, I used:
```
update-alternatives --config xinput-all_ALL
```

and chose "skim" (I used KDE).

---

