---
title: "Display problem with xfce in Oneiric upgrade"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by mlnease on 2011-10-23
Hello,

I recently upgraded Natty to Oneiric via update manager.  Decided to try xfce and loved it.  I haven't got the graphics (icon theme etc.) exactly as I'd like them but still I'd highly recommend it to anyone unhappy with Gnome 3 and Unity on a desktop.

Unfortunately, in tweaking the new system I seem to've broken xfce.  All windows open stuck in the upper left-hand corner and the min-max-close buttons are missing.  Also the screen resolution on maximized windows is bigger than the screen.

Whatever I did also seems to've affected Ubuntu 3D--2D seems OK but there's no dash in 3D.

I've tried reinstalling gnome-shell, xfce and gde but to no avail.  I wouldn't mind starting from scratch but would rather avoid a reinstall if possible.

I wasn't sure whether to post this to Desktop Environments or Installations and Upgrades as I'm not sure where the problem lies--sorry if this is the wrong forum.

Any help would be greatly appreciated!

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
are you running compiz?  I had that problem with running compiz in xfce.  you might edit your login sessions, and possibly go into your /home/(username)/.cache/sessions and delete what is stored in that folder.  for some reason emerald wasn't in the repositories for 11.10 (last I checked) which allowed for easy titlebar editing...
you could download the compizfusion icon, which allows you to choose gtk-window-decorator...
if you have unity you do have compiz.  
you might try running this command in xfce (press Alt+F2, or open the terminal)
xfwm4 --replace

---

### Post by mlnease on 2011-10-23
Thanks for the quick response!  I'll give it a try and get back to you.

---

### Post by mlnease on 2011-10-23
> **TREESofRIGHTEOUSNESS said:**
> are you running compiz?  I had that problem with running compiz in xfce.  you might edit your login sessions, and possibly go into your /home/(username)/.cache/sessions and delete what is stored in that folder.  for some reason emerald wasn't in the repositories for 11.10 (last I checked) which allowed for easy titlebar editing...
you could download the compizfusion icon, which allows you to choose gtk-window-decorator...
if you have unity you do have compiz.  
you might try running this command in xfce (press Alt+F2, or open the terminal)
xfwm4 --replace
Thanks again--I tried ```
xfwm4 --replace
```and received this: 
```
mln@mn-OptiPlex-745:~$ sudo xfwm4 --replace
[sudo] password for mln: 

(xfwm4:3084): GLib-CRITICAL **: g_str_has_prefix: assertion `prefix != NULL' failed

(xfwm4:3084): xfwm4-WARNING **: The property '/general/double_click_distance' of type int is not supported

(xfwm4:3084): xfwm4-WARNING **: Failed to connect to session manager: Failed to connect to the session manager: SESSION_MANAGER environment variable not defined
```I had tried the command without 'sudo' but it didn't seem to be responding.

Anyway, I restarted but the problems persist.

Thanks again for your time and I'll be grateful for any more suggestions.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
[http://wiki.compiz.org/Troubleshooting](http://wiki.compiz.org/Troubleshooting)

this page offers in depth troubleshooting advice.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
Also... I found this post
[http://ubuntuforums.org/showthread.php?t=1866889&highlight=emerald](http://ubuntuforums.org/showthread.php?t=1866889&highlight=emerald)

with this link
[https://launchpad.net/~malteworld/+archive/compiz](https://launchpad.net/~malteworld/+archive/compiz)

to get emerald.  the command "sudo apt-get install emerald" is defunct in 11.10.... 
use the ppa at your own risk.  the gtk-window-decorator will work in Xfce.. I just couldn't find out where to change the window decorations... when I used it.  I will try the ppa sometime, and i will let you know (unless you fix your problem before I get a chance to try it out...)

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
well... it works alright... but installing the ppa is a bit tricky... you have to make sure you get it as natty instead of oneric.  but I have emerald running, and compiz.  everything seems to work fine.
let me know how it goes for you....

---

### Post by mlnease on 2011-10-24
> **TREESofRIGHTEOUSNESS said:**
> well... it works alright... but installing the ppa is a bit tricky... you have to make sure you get it as natty instead of oneric.  but I have emerald running, and compiz.  everything seems to work fine.
let me know how it goes for you....
Thanks again for all your attention.  My specific display problem (stuck  in upper left corner, no buttons) seems to have resolved itself  spontaneously at least for the moment so I guess I'll mark this SOLVED even though I don't know how or why.  Turns out that, though I *did* have Compiz installed, I *didn't*  have CompizConfig Settings Manager.  As Emerald is no longer maintained  (and may be unstable) I think I'll try troubleshooting with CCSM, now I  have it installed.  

Also, I found an existing thread--[Moving to Xfce from Gnome]("http://ubuntuforums.org/showthread.php?t=1866392&highlight=xfce+oneiric")--in Desktop Environments that's probably more appropriate for my questions.

By the way, I also found [this]("http://xfce-look.org/") for further (and much needed) graphics improvement.  Haven't made use of it yet, but am really looking forward to it.

Yet again, many thanks for all your help.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-26
great!!  I find that usually people end up just spurring me on to look until I figure out my problem.
I had an issue with nautilus in xfce... when using nautilus it takes over your desktop, so I couldn't change my background... people kept telling me different stuff and it spurred me to find dconf-tools.
so, I am glad you figured it out.

---

### Post by mlnease on 2011-10-26
> **TREESofRIGHTEOUSNESS said:**
> great!!  I find that usually people end up just spurring me on to look until I figure out my problem.
I had an issue with nautilus in xfce... when using nautilus it takes over your desktop, so I couldn't change my background... people kept telling me different stuff and it spurred me to find dconf-tools.
so, I am glad you figured it out.
Great indeed--I had similar problems with the nautilus conflict on my original update-manager install--very quirky, sometimes the backround would jump back and forth between GNOME and Xfce defaults, loss of various features and so on.  I tried a lot of different things, deleting gnome-shell and gde, reinstalling them etc.  Finally I just did a clean reinstall from a CD and haven't had a serious problem yet.

I could never get the graphics the way I wanted them in the Xfce panels or I would've been quite content.  But after a day of tweaking Cairo dock, Oneiric with Xfce is doing everything I want *without* panels, in some cases even better than GNOME 2.3, which I dearly loved and will always miss a little, due to its (graphically, at least) perfect integration with Ubuntu.

So there you have it--thanks yet again for the help and encouragement and I'll keep an eye on this thread for future developments.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-27
Yeah...  I use the cairo-dock as well as the xfce panel.  It isn't as pretty as the gnome panel in all the aspects or it (i too have always been a fan of Gnome....) but you can do most of the same things....  the semi-transparency...  and all that.

cairo-dock seems to be a favorite of non-unity users.  Unity isn't too bad, except that it cuts off all menus.  if it left menus I would probably never have abandoned it.  The unity dock isn't anywhere near as pretty as cairo-dock, and you can't use a lot of compiz features if you run unity.  I think in the newest ubuntu version, you can use gnome shell, to replicate the classic gnome experience, though I have only updated my Xubuntu machine (this one is my older 'test' computer)... my other one is still 11.04 classic gnome w/ cairo dock the whole compiz cube 3d windows extravaganza.

---

### Post by mlnease on 2011-10-27
Hello Again,

For me, it isn't that Unity's graphics aren't pretty enough, I find them overbearing and unnecessary on anything other than a 'smart' phone or a tablet.  The idea that one DE should work for *both* of those *and* a desktop is a non-starter, far as I'm concerned.  The graphic requirements simply aren't the same.  Also it greatly limits graphical options (as is unfortunately the trend in GNOME too) rather than expanding them--a step in exactly the wrong direction, as I see it.  The 'replicated' GNOME experience is already--well--a serious downgrade graphically, IMHO.

But enough of that.  I'm finding my old options for backing up DVDs aren't working via Xfce.  Any suggestions?

---

### Post by jtarin on 2011-10-27
> **mlnease said:**
> 
I'm finding my old options for backing up DVDs aren't working via Xfce.  Any suggestions?How do you normally back them up? It's been awhile since I have used XFCE but I belive you can still install and run Gnome apps, so I would suggest GnomeBaker which I find an excellent and reliable app to do this.

---

### Post by mlnease on 2011-10-27
> **jtarin said:**
> How do you normally back them up? It's been awhile since I have used XFCE but I belive you can still install and run Gnome apps, so I would suggest GnomeBaker which I find an excellent and reliable app to do this.
Thanks for the quick response (and nice to see Oswald again--*great *graphic).

I'm specifically trying to back up video DVDs so need to shrink them first (to make ISOs to copy to DVDs).  I've depended on DVD Shrink (via Wine) for some time, using K9 Copy as a backup (because DVD Shrink has some very nice features, especially stripping out some DRM features, but doesn't work ofr all my video DVDs).

And yes, I found GnomeBaker worked very well but for me, Brasero worked even better--but for burning, yes?  Not for ripping.

Give my regards to Vladivostok!

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-29
Not sure what to tell you about that one.  I've heard K3B is really nice... but I don't really do much backing up....  I mainly use dvdstyler to make dvd's from home movies.

---

