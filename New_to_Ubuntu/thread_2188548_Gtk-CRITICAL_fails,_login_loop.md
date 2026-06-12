---
title: "Gtk-CRITICAL fails, login loop"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by Crossbow on 2013-11-17
What is Gtk and how do you fix it?

Yesterday my browser suddenly stopped allowing input. (I was trying to update my credit card information on a website I use a lot.) That was the only sign of trouble. I rebooted and got a black screen with a blinking cursor. Unistalled, purged, and reinstalled Nvidia, reinstalled lightdm, reinstalled xserver-xorg, did updates between everything, ran repair broken packages, etc. Unable to reconfigure Nvidia. Unable to customize grub. Nothing has worked. Now I've got it where it tries to boot in low graphics mode but it actually won't even do that. I've browsing the forums all day looking for an answer but there are too many variables with "blank screen." One user said it could be due to the system not detecting the keyboard but not how to fix it.  

Boot-repair, which had no errors the first time I ran it, is now giving me a string of fails beginning with "Gtk-CRITICAL." 

I'm running Ubuntu 13.10 on a Dell 530. 
Intel(R) Pentium(R) Dual CPU E2160 @ 1.80GHz
Nvidia GeForce 8300 GS 
I tried this with Nvidia-common and -173, which is the last one that worked for me. 

Thanks!

---

### Post by MG&amp;TL on 2013-11-19
I have no idea why your graphics aren't working, but repairing the boot sector won't help.

However, in layman's terms, GTK+ is a tool GNOME application programmers use to make windows and buttons and things. Can you post the exact errors you get?

---

### Post by Crossbow on 2013-11-24
> **MG&TL said:**
> I have no idea why your graphics aren't working, but repairing the boot sector won't help.

However, in layman's terms, GTK+ is a tool GNOME application programmers use to make windows and buttons and things. Can you post the exact errors you get?

Hi - Thank you for replying! 

The error I get updating is: 

**failed to fetch [http://ppa.launchpad.net](http://ppa.launchpad.net) ubuntu-x-swat/x-updates/ubuntu/dist/saucy/main/binaru-i386/Packages 404 not found.**

And here are the errors I get with boot-repair:

[IMG]http://img.photobucket.com/albums/v97/Crossbow/Mobile%20Uploads/1385309975_zps59bc3607.jpg[/IMG]

So I guess this gtk stuff is in this repository that I can't connect to?

---

### Post by Crossbow on 2013-11-24
I found this old thread with the same question but I don't understand the answer. I guess I have to remove that "swat" one, but what do I need to enter instead?

[http://askubuntu.com/questions/360560/404-errors-in-ubuntu-13-10](http://askubuntu.com/questions/360560/404-errors-in-ubuntu-13-10)

---

### Post by MG&amp;TL on 2013-11-24
First of all, remove the *x-swat* PPA, then update, unless you have to reason to believe things will be broken otherwise. I can't think that's helping matters (from the X-swat page):

> If you are upgrading from one release to another with this PPA  activated, please install the ppa-purge package and use it to downgrade  everything in here beforehand. sudo ppa-purge ppa:ubuntu-x-swat/x-updates will do it.



From the screenshot you've posted, I think I understand what's happening now: GTK+ is a red herring. Graphical applications require the display server (currently *X.org*) to be started, which in turn requires the graphics card drivers to be working. If the display server is not started, various parts of the GTK+ stack fail (noisily) and give you the errors you're seeing. Can you also post the contents of the file */var/log/Xorg.0.log* and the results of the command

```
sudo service lightdm restart
```

please? Thanks. :-)

---

### Post by Crossbow on 2013-11-24
```
ppa-purge ppa:ubuntu-x-swat/x-updates
```

Returned that same 404 message and gave me a warning that "apt-get update failed for some reason." 

```
service lightdm restart
```

returned thisr:

```
usage: /etc/init.d/lightdm {start|stop|restart|force-reload}
```

I tried restarting then, and it still says it's starting in low graphics mode but then won't even really do that. 

> Can you also post the contents of the file /var/log/Xorg.0.log

I am not sure how to do that.

---

### Post by MG&amp;TL on 2013-11-25
> ```
ppa-purge ppa:ubuntu-x-swat/x-updates
```

Returned that same 404 message and gave me a warning that "apt-get update failed for some reason." 

Ah right. I hoped *ppa-purge* did something smarter than that, but I guess not. In that case, I think you need to remove the source manually: look for and delete any entries relating to *x-swat* in */etc/apt/sources.list* and delete any *x-swat* related files in */etc/apt/sources.list.d/*, then run

```
sudo apt-get update
```

again.

> ```
service lightdm restart
```

returned this:

```
usage: /etc/init.d/lightdm {start|stop|restart|force-reload}
```

I tried restarting then, and it still says it's starting in low graphics mode but then won't even really do that. 


Ah.

> I am not sure how to do that.

Well, since you cannot access a graphical browser from your desktop, copy the file onto whichever machine you're posting from. If you don't know how to do that from the command-line, the easiest way is probably to boot a live CD and drag-drop files onto a USB.

As a side-note, how much time are you willing to spend fixing this? Fixing problems of this nature is often time-consuming, but educational. If you need the machine for work or something (or you're just fed up), the easy solution would be to back up your files and reinstall (or possibly upgrade).

---

### Post by Crossbow on 2013-11-30
> 
As a side-note, how much time are you willing to spend fixing this? Fixing problems of this nature is often time-consuming, but educational. If you need the machine for work or something (or you're just fed up), the easy solution would be to back up your files and reinstall (or possibly upgrade). 

If there is a way to do that from the command line in recovery mode, I would. 

I'm sure the x-swat is not the problem as I only added it in after the problem started. It had worked for someone else. I don't know why.

Edit: I was just reading this: [http://www.webupd8.org/2013/09/how-to-install-gnome-310-in-ubuntu-1310.html](http://www.webupd8.org/2013/09/how-to-install-gnome-310-in-ubuntu-1310.html)

I don't really understand it but maybe this is my problem.

---

### Post by Crossbow on 2013-12-01
>  Can you also post the contents of the file /var/log/Xorg.0.log and the results of the command

I got "permission denied."

---

### Post by Iowan on 2013-12-01
> **Crossbow said:**
> I got "permission denied."

Try it with **sudo**?

---

### Post by Crossbow on 2013-12-01
Even though I'm in root? Can you tell me exactly what command I should enter please? I am doing something wrong.

---

### Post by Crossbow on 2013-12-01
I tried this: [http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver](http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver)
and this: [http://ubuntuforums.org/showthread.php?t=1744248](http://ubuntuforums.org/showthread.php?t=1744248)
But nothing is working yet. I got this error:

ERROR: (dkms apport): binary packages for nvidia: 310.40 not found
Error! Bad return status for module build on kernel 3.11.0-13-generic

Tried all this with Nvidia-current and nvidia-173, which is the only one that has worked for me before. When I tried installing fglrx, I got a message that the video mode could not be displayed at that resolution or something. At the moment, when I try to boot up normally I get a blank screen with a blinking cursor.

---

### Post by Crossbow on 2013-12-02
I think maybe I found something. I've been searching the "cannot open display" error, and it looks like almost everyone who gets it refers to SSH. I don't know what SSH is. It sounds like a networking thing? I only have this one home computer, not networked, but maybe something in there is set up for networking and/or SSH and shouldn't be?

---

### Post by Crossbow on 2013-12-08
The "unable to fetch" error I was getting disappeared with the last upgrade, so I was hopeful, but I still have no GUI. Have now read dozens and dozens of threads on this. I can't do anything in gedit because of the "unable to open display" error. Everyone recommended deleting .Xauthority but that did nothing. I've purged and reinstalled NVIDIA at least three times now.

---

### Post by MG&amp;TL on 2013-12-08
Sorry I've been away for a while, I hadn't noticed that the thread had started up again. :-)

As for your problems, I'm a little clueless. Quite a few of the commands I posted *should* have done something (rather than give the errors they did), but they appear not to have done.

> **Crossbow said:**
> If there is a way to do that from the command line in recovery mode, I would. 

You *can* do this from the command-line, but I wouldn't recommend that unless you know exactly what you're doing. The easy way is to boot a live CD, mount your hard disk from there and copy your files onto external media or another partition, unmount the disk, then reinstall as normal.

---

### Post by Crossbow on 2013-12-15
There have been two updates to the kernel since I started. The first one got rid of those "unable to fetch" errors but still no gui. Will try everything again today. I'm doing all this in root:

**service lightdm restart** gave me the low graphics mode message. Unable to do anything form there, had to shut off computer.

Did **apt-get remove --purge** on Nvidia-common, -current, -settings, -current-updates, -173, -173-updates. (The 173 stuff was not actually installed. Just checking.) Trying to remove nvidia* gave me an error message that there was no bug report???

Re-installing nvidia-common and -current now...

No go. Installs went fine. Updated and Rebooted after purging and again after reinstalling. Still got the "low graphics mode" which won't even run in low graphics mode.

> Can you also post the contents of the file /var/log/Xorg.0.log

I don't know how to open that. When I just type in the file name I get "permission denied."

**dpkg-reconfigure nvidia-current** returned nothing. 

**nvidia-reconfig** gave me a message that it had backed up the file. Is that what it should do?

"Fix broken packages" begins with two "cannot remove..." errors but they go by too fast to read.

---

### Post by Crossbow on 2013-12-15
**Nautilus** returns:

**(nautilus:2366): GtK-WARNING **: cannot open display**

Which is also what I get when I try anything with gedit. I did reinstall gedit. Didn't help.

---

### Post by MG&amp;TL on 2013-12-16
> **Crossbow said:**
> There have been two updates to the kernel since I started. The first one got rid of those "unable to fetch" errors but still no gui. Will try everything again today. I'm doing all this in root:

**service lightdm restart** gave me the low graphics mode message. Unable to do anything form there, had to shut off computer.

Did **apt-get remove --purge** on Nvidia-common, -current, -settings, -current-updates, -173, -173-updates. (The 173 stuff was not actually installed. Just checking.) Trying to remove nvidia* gave me an error message that there was no bug report???

Re-installing nvidia-common and -current now...

No go. Installs went fine. Updated and Rebooted after purging and again after reinstalling. Still got the "low graphics mode" which won't even run in low graphics mode.



I don't know how to open that. When I just type in the file name I get "permission denied."

**dpkg-reconfigure nvidia-current** returned nothing. 

**nvidia-reconfig** gave me a message that it had backed up the file. Is that what it should do?

"Fix broken packages" begins with two "cannot remove..." errors but they go by too fast to read.

What happens if you remove nvidia, then reboot? Theoretically the open-source drivers should come back into play, and you should get a usable system, while we figure out what's wrong with the drivers.

To view files from the command-line use:

```
cat <filename>
```

to get all the output at once, or

```
less <filename>
```

to get it 'paged' (i.e, you can scroll by pressing return).

And yup, if you try and run graphical apps without the display server working, they're going to fail with a message like that.

---

### Post by Crossbow on 2013-12-21
Hmm. I removed nvidia, rebooted, got a login loop, which I guess is progress? Last time I had that, I fixed it by changing "normal" to "nomodeset" on the grub screen, but it was already at nomodeset. I found a thread where someone had solved the login loop by removing compiz, so I tried that and it enabled me to log in as guest, only I can't do anything there. I only have a blank desktop.

---

### Post by MG&amp;TL on 2013-12-21
> **Crossbow said:**
> Hmm. I removed nvidia, rebooted, got a login loop, which I guess is progress? Last time I had that, I fixed it by changing "normal" to "nomodeset" on the grub screen, but it was already at nomodeset. I found a thread where someone had solved the login loop by removing compiz, so I tried that and it enabled me to log in as guest, only I can't do anything there. I only have a blank desktop.

Can you open a terminal on the desktop? If so, you should be able to launch applications to backup files and use sudo to run commands as required.

---

### Post by Crossbow on 2013-12-21
No, I was not able to open a terminal on the Guest desktop. The only thing I can access is the root through grub. Whatever I do has to be done that way.

>  The easy way is to boot a live CD, mount your hard disk from there and copy your files onto external media or another partition, unmount the disk, then reinstall as normal. 

Can you break that down for me more please? How do I mount my hard disk after I boot up with the live CD?

---

### Post by Crossbow on 2013-12-21
OK, I did a bunch of sh*t and now I can at least open a terminal in Guest and then log in as myself. I went in there and re-installed nvidia-current. I thought then maybe I could get to a GUI, but **startx** just brought up a blank black screen, first with a cursor, then nothing. CTRL+ALT=f1 back to terminal gave me a repeating: 

```
NO PROTOCOL SPECIFIED
...
```

That repeated for several hundred lines, then 

```
xinit giving up
xinit unable to connect to xserver
```

and later, 

```
xinit: server error
xauth:  timout in locking authority file /home/anna/.Xauthority
```

I tried removing .Xauthority because that's what everyone always says to do. Updated and tried startx again. Black screen again. Back in terminal, it appears to be stuck on 

```
Loading extension for GLX
```

What's that?

ETA: Progress, I think! I did [these steps to clean it up]("http://ubuntuforums.org/showthread.php?t=1586633&p=9916841#post9916841"), and then I was able to log in normally but got an error that there were no settings for my monitor, or words to that effect. Purging Nvidia... again.

ETA: OK. I'm up and running. I have huge distorted graphics but it's working. Going to work on backing up my files in case I have to reinstall but I REALLY don't want to! Please tell me what to run to see what the deal is.

---

### Post by Crossbow on 2013-12-21
So, it looks like I now have something called Vesa instead of Nvidia, and it does not have an option for the correct resolution for my screen, which I believe is 1440x900. Apparently Vesa doesn't support this at all. I have no idea what I need to install now, as clearly NVIDIA isn't cutting it. PLEASE HELP!

My driver is, apparently, Vesa:g86 Board-p413h01.

---

### Post by MG&amp;TL on 2013-12-22
> **Crossbow said:**
> No, I was not able to open a terminal on the Guest desktop. The only thing I can access is the root through grub. Whatever I do has to be done that way.


Did you try Ctrl + Alt + T? That usually works, even if the hardware-accelerated parts of the desktop fail to load. By the looks of the rest of your posts though, this is irrelevant now.

> OK, I did a bunch of sh*t and now I can at least open a terminal in Guest and then log in as myself. I went in there and re-installed nvidia-current. I thought then maybe I could get to a GUI, but **startx** just brought up a blank black screen, first with a cursor, then nothing. CTRL+ALT=f1 back to terminal gave me a repeating: 

```
NO PROTOCOL SPECIFIED
...
```

That repeated for several hundred lines, then 

```
xinit giving up
xinit unable to connect to xserver
```

and later, 

```
xinit: server error
xauth:  timout in locking authority file /home/anna/.Xauthority
```

The X server is not an area I know a lot about (I just don't like it: it's ancient and broken in [several]("http://wayland.freedesktop.org/architecture.html") [ways]("http://wayland.freedesktop.org/faq.html#heading_toc_j_6"). Its two (competing) replacements, Wayland and Mir, both fix many of X's problems); but from this it appears that the X server started, but did not finish loading for some reason (likely driver issues).

> I tried removing .Xauthority because that's what everyone always says to do. Updated and tried startx again. Black screen again. Back in terminal, it appears to be stuck on 

```
Loading extension for GLX
```

What's that?

GLX is the X server extension that allows for hardware acceleration of applications via OpenGL in the X server (OpenGL for X -> GL-for-X -> GL-X -> GLX, is my guess). If your driver is broken in some way, the X server will hang while it tries to load the extension. I have no idea why it's doing this, but likely your nvidia driver is/was broken.

> ETA: Progress, I think! I did [these steps to clean it up]("http://ubuntuforums.org/showthread.php?t=1586633&p=9916841#post9916841"), and then I was able to log in normally but got an error that there were no settings for my monitor, or words to that effect. Purging Nvidia... again.

ETA: OK. I'm up and running. I have huge distorted graphics but it's working. Going to work on backing up my files in case I have to reinstall but I REALLY don't want to! Please tell me what to run to see what the deal is.


Right, it looks like you have succeeded in getting rid of the broken Nvidia driver. My understanding is if no driver is loaded, the system loads the default driver, which is Vesa. Vesa isn't designed for any particular graphics cards, so it's horrible to use, but it does work reliably.

> **Crossbow said:**
> So, it looks like I now have something called Vesa instead of Nvidia, and it does not have an option for the correct resolution for my screen, which I believe is 1440x900. Apparently Vesa doesn't support this at all. I have no idea what I need to install now, as clearly NVIDIA isn't cutting it. PLEASE HELP!

My driver is, apparently, Vesa:g86 Board-p413h01.

If you have the desktop environment 'working', run the 'software sources' application and click on the 'Additional Drivers' tab. Here you'll see several options. For now, I'd recommend installing the *nouveau* driver - this is the community driver for Nvidia cards, but in my experience it's a lot more reliable than the Nvidia-made drivers. It gives reasonable performance, but nothing special.

As for the CD rescue option: once you've booted the CD, start up the file manager. You'll see your drives down the left-hand side (from memory), and you should be able to click on them and browse for your files. They're under /home/<your name> in the file layout. Sorry about using the word 'mounting': this is what the file manager does internally when you browse a disk that isn't the one the operating system is running on.

HTH. :-)

---

### Post by Crossbow on 2013-12-22
OK, thanks. Say, I just noticed during boot up that "Nvidia persistence daemon" failed. Do I  need to do something about that?

Edit: Oh, NOW what? I hadn't even got to changing anything, but now the GUI won't load again, and it's hanging on **"(EE) module ABI major version (6) doesn't match the servre's version (7)".** What, do pixies come in and mess with this thing while I'm asleep?

---

### Post by MG&amp;TL on 2013-12-23
> **Crossbow said:**
> OK, thanks. Say, I just noticed during boot up that "Nvidia persistence daemon" failed. Do I  need to do something about that?

Edit: Oh, NOW what? I hadn't even got to changing anything, but now the GUI won't load again, and it's hanging on **"module ABI major version (6) doesn't match the serve's version (7)".** What, do pixies come in and mess with this thing while I'm asleep?

Ugh... apparently the *nvidia-persistenced* software:

> Loads the NVIDIA kernel driver and creates device files 
nvidia-persistenced is a simple setuid root utility which loads the NVIDIA kenel 
module and creates the NVIDIA device files, to allow usage of the NVIDIA 
driver by client applications that would otherwise not have sufficient 
permission to load the module or create the device files on their own.

I imagine that is a bad idea when you have another graphics driver working. No idea how to get rid of it though, it should be part of the nvidia driver package which should have been removed. Can you run:

```
dpkg --get-selections | grep -i nvidia
```

As for the server mismatch... no idea. Absolutely none. :mad: Apparently this happens when you have old modules lying around. Can you post relevant output from

```
grep EE /var/log/Xorg.0.log
```

---

### Post by steeldriver on 2013-12-23
VESA is the generic fallback driver AFAIK - nothing to worry about (except that it only supports unaccelerated VGA modes)

Several people appear have had issues with a recent upgrade bumping their nvidia proprietary driver up to an incompatible one - if you can get to a GUI interface (even with the VESA driver) then probably the easiest way forward is to go to the 'Additional Drivers' utility and pick a known good driver from there. If you can't get to a GUI desktop but you're on 12.04 then you can use jockey-text from the command line.

---

### Post by Crossbow on 2013-12-23
> **MG&TL said:**
> Ugh... apparently the *nvidia-persistenced* software:



I imagine that is a bad idea when you have another graphics driver working. No idea how to get rid of it though, it should be part of the nvidia driver package which should have been removed. Can you run:

```
dpkg --get-selections | grep -i nvidia
```

As for the server mismatch... no idea. Absolutely none. :mad: Apparently this happens when you have old modules lying around. Can you post relevant output from

```
grep EE /var/log/Xorg.0.log
```

Neither of those returned anything, but I did do another nvidia-purge last night and there were somehow some remnants of 319 in there even though I'd purged before. 

>  If you can't get to a GUI desktop but you're on 12.04 then you can use jockey-text from the command line. 

I can no longer get to a GUI. I'm in 3.10. Can I still do that?

I read that I should reset unity and compiz. I installed dconf-tools but **apt-get dconf reset -f /org/compiz/** only gave me an error that it had to be a path or a key and apparently it's not valid either way. Also tried reinstalling compiz and unity. **unity --reset** did nothing. **Setsid unity** returns: 

**Compiz (decor_ warn: requested a pixmap type decoration when compositing isn't available. **

Oh, I forgot, I don't know if this matters, but since the last upgrade, my login screen has a "remote login" option that was not there before.

---

### Post by MG&amp;TL on 2013-12-23
> Neither of those returned anything, but I did do another nvidia-purge last night and there were somehow some remnants of 319 in there even though I'd purged before.


Nvidia drivers are ridiculously persistent at times. :-(

>  I can no longer get to a GUI. I'm in 3.10. Can I still do that?

Yes, but you'll need to

> sudo apt-get install jockey-common

first, I suspect.

>  Oh, I forgot, I don't know if this matters, but since the last upgrade, my login screen has a "remote login" option that was not there before.

No, that's a new feature for remote desktop login on recent releases. Nothing to worry about. :-)

---

### Post by Crossbow on 2013-12-26
Well, I still have the GtK errors, but apparently the ACTUAL problem is that my graphics card is dead. I'm not sure if I should mark this "solved" or not. 

If anyone needs to know: What I had to do was uninstall and reinstall both **xserver-xorg** and **xserver-xorg-core**, which is something I'd never heard of. That makes me able to use the resolution 1024x768. My monitor is actually 1440x900 but good enough I guess. 

This morning when I logged in I was back to 600x800 and my "graphics" were "**Gallium 0.4 on llvmpipe**." I have no earthly idea what that is. I found some threads where people had had the same problem but no solutions, or at least none that I could understand. I uninstalled and reinstalled **xserver-xorg** and **xserver-xorg-core again**, and that brought back Vesa.

---

### Post by MG&amp;TL on 2013-12-26
> **Crossbow said:**
> Well, I still have the GtK errors, but apparently the ACTUAL problem is that my graphics card is dead. I'm not sure if I should mark this "solved" or not. 

If anyone needs to know: What I had to do was uninstall and reinstall both **xserver-xorg** and **xserver-xorg-core**, which is something I'd never heard of. That makes me able to use the resolution 1024x768. My monitor is actually 1440x900 but good enough I guess. 

This morning when I logged in I was back to 600x800 and my "graphics" were "**Gallium 0.4 on llvmpipe**." I have no earthly idea what that is. I found some threads where people had had the same problem but no solutions, or at least none that I could understand. I uninstalled and reinstalled **xserver-xorg** and **xserver-xorg-core again**, and that brought back Vesa.

Well, if your situation is no longer attached to the problem in the thread, I usually mark it as solved. Bit of a grey area, that.

...so...if your graphics card is dead, a) how do you know? and b) what are you using now?

---

### Post by Crossbow on 2013-12-26
> **MG&TL said:**
> 

...so...if your graphics card is dead, a) how do you know? and b) what are you using now?

a) I don't, actually, I just know my system can't see it. I don't know how to tell, otherwise. 
b) Apparently, just Vesa. I don't really understand.

---

### Post by MG&amp;TL on 2013-12-26
> **Crossbow said:**
> a) I don't, actually, I just know my system can't see it. I don't know how to tell, otherwise. 
b) Apparently, just Vesa. I don't really understand.

Oh. Well, if you have no card-specific drivers, the card is probably alive and well (yay!), but the software isn't able to see it (boo...). You should be able to see it, however, in the output from

```
lspci
```

I would (tentatively) suggest firing up the additional drivers utility again and seeing if the nouveau install works correctly this time (without the Nvidia driver remains)

---

### Post by Crossbow on 2013-12-26
> **MG&TL said:**
> Oh. Well, if you have no card-specific drivers, the card is probably alive and well (yay!), but the software isn't able to see it (boo...). You should be able to see it, however, in the output from

```
lspci
```

I would (tentatively) suggest firing up the additional drivers utility again and seeing if the nouveau install works correctly this time (without the Nvidia driver remains)

Huh. Okay, it looks like the GeForce 8300 is is still there, if I understand this, which I may not. I don't actually have the additional drivers utility, or it's not where it used to be. It's not in system settings.  The software center says Additional Drivers *IS* installed. Where, I don't know. 

```

anna@anna-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8300 GS] (rev a1)
anna@anna-desktop:~$ 

```

---

### Post by Crossbow on 2013-12-26
PS. [http://www.geforce.com/drivers]("http://www.geforce.com/drivers") is unable to detect it, but apparently only scans Windows.

---

### Post by MG&amp;TL on 2013-12-27
> **Crossbow said:**
> Huh. Okay, it looks like the GeForce 8300 is is still there, if I understand this, which I may not. I don't actually have the additional drivers utility, or it's not where it used to be. It's not in system settings.  The software center says Additional Drivers *IS* installed. Where, I don't know. 

```

anna@anna-desktop:~$ lspci
<blah>
**01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8300 GS] (rev a1)**
anna@anna-desktop:~$ 

```

Yup, your card is still there. :-)

It's not in system settings anymore (I've no idea why; for some reason they moved it), it's now under 'software sources', under the 'additional drivers' tab.

---

### Post by Crossbow on 2013-12-27
I found it in Synaptic Package Manager. It says I'm already using Nouveau, though. And it does see my driver, although today I'm stuck with this Gallium thing again.

Applying Nvidia-173, as that was the last one that actually worked for me.  

ETA: Well, that didn't work. Nvidia-xconfig worked. Restarted X and was back to blank screen after login. X was hanging at "LOADING EXTENSION NV-CONTROL." I removed and reinstalled xserver-xorg and xserver-xorg-core because I didn't have any better ideas. So I'm back with Vesa, the Nvidia settings utility is gone, and I have the wrong resolution. I feel like maybe I'm missing part of X. I'm not messing with this anymore today. Having this working at all is a huge step up! I don't like having to remove and reinstall xserver-xorg and -core every time but it's better than nothing.

---

### Post by MG&amp;TL on 2013-12-28
I'm afraid you've got to the end of what I know about this part of Ubuntu; sorry what I do know hasn't helped. Why you have a gallium driver is beyond me; I was under the impression that gallium was for AMD cards.

---

### Post by steeldriver on 2013-12-28
I *think* that nouveau uses Gallium/llvmpipe as a software renderer for GeForce cards where hardware acceleration is not enabled/supported

---

