---
title: "Help Troubleshooting Graphics After Install -  11.10 64Bit"
date: 2011-10-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by outerspacerace on 2011-10-09
Hi all,

I need some help/advice on finding out what's up with my system.

As the title suggests I performed a clean install of 11.10 64Bit (a few days ago) on a machine which had was previously running 11.04 smoothly.

Here's a rundown of the general graphics errors I'm seeing:

When logged into Ubuntu dragging windows is slow and jerky. There is no difference if I use the default drivers or enable the ATI drivers. 

I wasn't actually able to even install those drivers right away, it just worked after a few updates/reboots. Curiously, I'm still unable to install post release updates from AMD. The error points me to jockey.log but on a quick read I was unable to make much sense of that.

Performance in Blender seems a little slower than under 11.04 also but surprisingly it's not terribly slow like the desktop is.

I've since installed Gnome Shell to test for such issues and it has a garbled display across the top bar and some text in the dash area is also garbled to varying degrees at times.

As above, these artifacts exist under either driver.

My card is an ATI Radeon HD 5770.

Is there something I can run to troubleshoot all this? 

Thanks in advance.

---

### Post by effenberg0x0 on 2011-10-09
Hi,
Not sure if that still is the case but, in the recent past, I remember ATI users had to disable "Sync to VBlank" in the OpenGL plugin, inside ccsm (CompizConfig-Settings-Manager) in order to have a usable desktop. Give it a try.

Regards,
Effenberg

---

### Post by P-I H on 2011-10-09
I have installed the latest fglrx driver, Catalyst 11.9, by use of the method described in [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)
That fixed the problem with the upper panel when using gnome-shell.
I have also unchecked "sync to vblank" in the opengl plugin, as suggested by efenberg0x0, and also enbled "Tear Free" in the Catalyst Control Center.
With these changes I am quite satisfied with the proprietary driver.
My graphic card is a AMD Radeon 6850.

---

### Post by outerspacerace on 2011-10-09
Thanks!

Setting sync to vblank and tear free within Catalyst instantly fixed the usability of the unity desktop. I'm no longer getting slow, shuddering window movements which is nice.

Nothing has changed in Gnome Shell however, so it looks like I'll either have to install the updated driver myself or wait. I think I recall reading somewhere the drivers are updated shortly after release, is that right?

PI-H, I'm wondering did you follow the instructions for natty to get it working?

---

### Post by outerspacerace on 2011-10-09
Ah, stupid me. 

I've only just realized the post- release updates are probably referring to ubuntu releases -  not major AMD releases.

Seeing as Oneiric isn't officially released yet that would be why I couldn't install them...

---

### Post by P-I H on 2011-10-09
Yes, I followed the instructions for Natty but I change "natty" to "oneiric" in the command "$ sh ./ati-driver-installer-[11-9]("http://wiki.cchtml.com/index.php/11-9")-x86.x86_64.run --buildpkg Ubuntu/natty".
It is also important to follow the instruction "Removing Catalyst/fglrx" before the installation of the new Catalyst driver.

---

### Post by outerspacerace on 2011-10-10
Well I got the updated drivers installed without a hitch, which was a pleasant surprise considering the lengthy process involved. So thanks for the help there.

The panel in Gnome Shell and the garbled text is fixed, so I'm happy with that.

The window movements are still jittery in Gnome Shell, regardless of how I set things up. Unity is working fine though.

P-I H do you see this problem under Gnome Shell?

---

### Post by effenberg0x0 on 2011-10-10
Good to know it went well. Look, again, I'm not a specialist in ATI (don't have the hardware), but maybe I can help.

There are reports that gnome-shell on ATI can have a better performance if you:

```
sudo gedit /etc/environment

```Add this line to the end of the file:
```
CLUTTER_VBLANK="none"

```Save the file, exit gedit, reboot.

Back at a Gui Session, at a console, run this to make sure the environment variable was exported:

```
env | grep -i clutter

```It *should* help with performance lags of ATI under Gnome-Shell.
Specially if you have log messages about vertical sync / vblank issues.

At any point you can revert by excluding the mentioned line from /etc/environment and rebooting again. So its safe to give it a try.

Regards,
Effenberg

---

### Post by outerspacerace on 2011-10-12
Thanks, that did help the jittery nature of things.

Unfortunately it also makes the windows tear upon being moved.

There's also a bunch of weird things going on with Catalyst switching on and off enabling tear free, seemingly after having logging into gnome or unity/vice versa.

I've even had catalyst report that it was out of memory and had the options greyed out a few times.

I think I'll just stick to unity which is working okay for now and wait for driver improvements I guess.

A shame, I liked the look of Gnome Shell.

---

### Post by P-I H on 2011-10-12
I mostly use the Ubuntu login and when I checked today windows move more smoothly on Ubuntu compared to Gnome.
I also have problems to run CIV V under Steam in Gnome. It's unplayable because of all rendering problems. In the Ubuntu login it runs fine.

---

