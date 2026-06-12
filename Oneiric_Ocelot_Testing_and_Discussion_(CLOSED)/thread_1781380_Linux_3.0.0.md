---
title: "Linux 3.0.0"
date: 2011-06-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-06-13
...just arrived in routine updates. About to boot into it in my virtual Oneiric. Fingers crossed.

---

### Post by inportb on 2011-06-13
w00t! i got this you got this my friend is by my right, with a kernel update :3

---

### Post by jppr on 2011-06-13
> **coffeecat said:**
> ...just arrived in routine updates. About to boot into it in my virtual Oneiric. Fingers crossed.

Why crossed fingers? Just updated system and everything works fine. I have this HD only OO and sdb1 is windows 7. 
I don´t ever use virtualbox, so i don´t know if with new kernel comes some virtualbox problems.

---

### Post by coffeecat on 2011-06-13
> **jppr said:**
> Why crossed fingers?

If you use an alpha in VirtualBox you **always** keep your fingers crossed! :wink:

---

### Post by sparker256 on 2011-06-13
Does not seem to like my 270.41.06 Nvidia driver. Options?

Bill

---

### Post by cecilpierce on 2011-06-13
> **sparker256 said:**
> Does not seem to like my 270.41.06 Nvidia driver. Options?

Bill

Same here, classic looked like a cross between gnome and classic and ubuntu was a blank screen with just my emergency terminal and synaptic icons so Im back to 39.3 kernel for now.

Still had the udevd error on startup !!!  :(

---

### Post by Quackers on 2011-06-13
Similar here. 
In my gnome-shell OO install I now have a bottom panel, a top panel with Applications and Places headings on the left - neither of which open dash (or whatever it's called :-) ), my window controls (max,min etc) have moved to the left side, I have "no access" type icons in the top panel, which are actually wireless and something else (can't tell because it doesn't open), though wireless is still working. 
My cairo-dock has gone awol.
As said previously, it looks like a cross between gnome-shell and Classic.

---

### Post by Harry33 on 2011-06-13
> **sparker256 said:**
> Does not seem to like my 270.41.06 Nvidia driver. Options?

Bill

The old nvidia-current versions (even though stable) do not accept highre kernel versions than 2.6.xx.
But you can download the latest beta (270.09.04) from the great xorg-edgers PPA.
That nvidia-current version works well with 3.0 series kernels too.

---

### Post by sparker256 on 2011-06-13
> **Harry33 said:**
> The old nvidia-current versions (even though stable) do not accept highre kernel versions than 2.6.xx.
But you can download the latest beta (270.09.04) from the great xorg-edgers PPA.
That nvidia-current version works well with 3.0 series kernels too.
Does latest beta (270.09.04) work with the 2.6.xx kernel? If so will go get it.

Thanks Bill

---

### Post by Quackers on 2011-06-13
An update.
It seems that whether I log in to GNOME, Ubuntu or classic I get exactly the same desktop and panels, with the same icons (or lack of) and headings.

---

### Post by PaulW2U on 2011-06-13
Not working too well with Kubuntu. :(

If I don't log in within a few seconds the kdm log-in screen disappears to reveal boot-up text. Ctrl-Alt-F7 brings the log-in screen back. I can then log-in and all seems well until I try to shutdown or reboot. The Kubuntu screen is displayed as it should but it doesn't clear within a few seconds as it should. I've reverted to 2.6.39-3 awaiting further updates or information to clarify what to report the bug against.

***Edit: kernel bug, obviously I'm in the minority at the moment. :(***

---

### Post by nm_geo on 2011-06-13
All seems to be working here with the new kernel.  Tried GNOME, Ubuntu & Ubuntu 2D logins all loaded as anticipated.  Of course the GNOME awaits the Gnome 3.0 additions and engine. However, I have been experimenting with Fedora 15 (don't tell anyone) just to see how Gnome 3.0 works. I like it pretty well after finding and applying some tweaks.

---

### Post by Maheriano on 2011-06-13
So they made the jump from 2.6 to 3?

---

### Post by sparker256 on 2011-06-13
> **Harry33 said:**
> The old nvidia-current versions (even though stable) do not accept highre kernel versions than 2.6.xx.
But you can download the latest beta (270.09.04) from the great xorg-edgers PPA.
That nvidia-current version works well with 3.0 series kernels too.

Have updated to the latest beta (275.09.04) from the xorg-edgers PPA and all is well. The latest driver worked on 2.6.xx and 3.0. Thanks for the info Harry.

Bill

---

### Post by Quackers on 2011-06-13
Should that xorg-edgers driver be 275.09.04?
Just to confirm, that is.

---

### Post by Quackers on 2011-06-13
I enabled the xorg-edgers.ppa and installed everything they had to offer :-)
Everything is fixed now! 
Bottom panel is now gone in gnome-shell desktop.
All icons are now back to normal in the top panel
Dash starts again
Window controls are back on the right
Excellent :-)
Thanks again, Harry33

---

### Post by sparker256 on 2011-06-13
> **Quackers said:**
> Should that xorg-edgers driver be 275.09.04?
Just to confirm, that is.
Correct should be and is on my machine 275.09.04
Bill

---

### Post by coffeecat on 2011-06-13
Well -since I started this, I'd better report.

Oneiric 1 - Sony Vaio laptop with Intel graphics and Intel wireless. Seems to be working (mostly) fine. The brighntess Fn keys are working, which is nice because they were broken with the Maverick kernel. The Fn volume up and down keys take me to max volume and mute respectively with just one tap, so that's not right. So far nothing's crashed, and I get Unity 3d.

Oneiric 2 - virtual VirtualBox machine in Natty host. It works; I get Unity 3d; and it's pole-axed itself no more often nor less often than it did with the 2.6.39 kernel.

All rather boringly reliable really! Relatively speaking. :wink:

---

### Post by Harry33 on 2011-06-13
> **sparker256 said:**
> Does latest beta (270.09.04) work with the 2.6.xx kernel? If so will go get it.

Thanks Bill

Yes it is fully backwords compatible.

---

### Post by Harry33 on 2011-06-13
> **Quackers said:**
> Should that xorg-edgers driver be 275.09.04?
Just to confirm, that is.

Yes you got the right one:
v. 275.09.04-0ubuntu1~edgers

---

### Post by inportb on 2011-06-13
... works just fine with Kubuntu  + Intel IGP. I am pleased.

---

### Post by 3vi1 on 2011-06-13
Not very happy with it on my system (i980x & SSD). 

[LIST=1][*]Seems like some kind of race condition is hanging it during mountall.  I assume it's in mountall, as when it hangs it last mentions mounting the NFS shares.  It's only booted successfully without hanging 2 out of 30 times I tried.
[*]HDA Intel sound is broken.  I can hear via my headphones, but the speakers do not work in 3.0.0.  Rebooting to 2.6.39-3 fixes the sound.
[*]Had to install the edgers nvidia drivers, since the current std repo version won't build for 3.0.0.
[/LIST]

---

### Post by teh603 on 2011-06-13
> **3vi1 said:**
> Seems like some kind of race condition is hanging it during mountall.  I assume it's in mountall, as when it hangs it last mentions mounting the NFS shares.  It's only booted successfully without hanging 2 out of 30 times I tried.
You didn't try uninstalling plymouth, did you? Supposedly, mountall is hard-coded to crash or something if plymouth isn't installed and running at boot. Either that or ureadahead.

Its been a while since we had plymouth foisted on us, but I remember that one of those two was partially rewritten to stop people from fixing a couple of bugs that made their systems unbootable, by removing plymouth.

---

### Post by Hedgehog1 on 2011-06-14
Thanks for this thread everyone (especially **coffecat**).

Armed with this knowledge, I was able to update to the new kernel and then also updated the new NVidia drivers before the reboot and was able to reboot with sound-over-HDMI still working and everything.

**You folks are awesome!**


***The Hedge***

:KS

---

### Post by donniezazen on 2011-06-14
Have you guys notices any improvements in power management. 2.6.38/39 is a power sucker. Any easy way to install this in Natty

---

### Post by jfernyhough on 2011-06-14
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)  3.0-rc2 is there for Oneiric but it works fine on Natty (for me, with edgers nvidia).  On my Oneiric laptop everything works very nicely once the system boots - however it takes two or three hard resets to get it to boot to a desktop; otherwise it just hangs when logging in (no keyboard response at all, not even to magic keys). SSH works but I can't force a logout (tried gnome-session-quit --display=:0 --force --[something else]).

---

### Post by TenPlus1 on 2011-06-14
3.0.0 installs and works well on Lubuntu 11.04 although my nvidia 6600gt wont kick in with binary drivers so using nouveau for now which works well also :)

---

### Post by 23dornot23d on 2011-06-14
Works well for me too and the gtk-recordmydesktop issues seem to have gone too ....
in Gnome-Shell ....

Finally got a running version of [Gnome Shell in OO .... 11.10]("http://img18.imageshack.us/img18/4801/screenshot10wa.jpg") ....... kernel generic 3.0.0
as of today .... and .... [**compiz replace works**]("http://img232.imageshack.us/img232/3197/screenshot15k.jpg") ....

no blues flashes ....

The ***[video problems no longer exist]("http://www.youtube.com/watch?v=d4W1nr2vEi8")*** .... this is quickly done basic video using Gtk-Recordmydesktop

Its been done on dual monitor and one is bigger than the other ..... thats why its so wide .... and a split
in the display 2/3rds across - but it is working well now.

---

### Post by paul_in_london on 2011-06-14
RC3 has turned up:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc3-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc3-oneiric/)

---

### Post by 3vi1 on 2011-06-14
> **teh603 said:**
> You didn't try uninstalling plymouth, did you?...

No.

And an additional item as noted in another thread:

4.  NFS mounts are broken.

---

### Post by jerrylamos on 2011-06-14
14 June daily build calls itself 3.0-0-generic:

Linux version 3.0-0-generic (buildd@roseapple) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.0-11ubuntu2) ) #1-Ubuntu SMP Thu Jun 9 16:32:23 UTC 2011

Seems to have the same lightdm crashes and nm applet crashes with wireless and date-time crashes as the previous level.  

This is Acer Aspire one netbook running 2D.  It will run 3D but I don't need Compiz overhead since I'm running full screen and don't see the 3D eye candy anyway.

Jerry

---

