---
title: "Failed to load session &quot;Gnome&quot;, Checking Battery State"
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kiwited on 2011-07-15
I have upgraded my 11.04 to 11.10. Normal boot stops at "Checking Battery State" - machine hangs but responds to alt-ctrl-del and reboots.
Booting into recovery mode gets to selection box, but continuing into normal boot brings up an error message box "Failed to load session "Gnome"" with one option - Logout. This drops back to a command line interface.
The recovery mode no longer offers the low graphics mode.
AMD64 X6, ATI Radeon HD 3870

---

### Post by Peter09 on 2011-07-16
Yes - I have this problem as well, it seems to be intermittent, and sometimes will boot correctly. However, since an update last night, when I had to do an Update-grub to get it to boot at all, its running like a dog, really clunky and slow.

---

### Post by kiwited on 2011-07-16
I have registered this as a possible bug.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/811355](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/811355)

---

### Post by cariboo on 2011-07-16
You're probably getting the can't start gnome error, because you don't have gnome-shell installed. I haven't taken the time yet to check where the session is set, but starting using startx always  starts gnome-shell on my system.

Your bug will probably be marked invalid, as there aren't any details included

---

### Post by mc4man on 2011-07-16
Do you have 3d support on your hardware? If not and unity-2d or gnome-session-fallback   aren't available/installed then you won't be able to load up
(I believe session 'Gnome" is unity 3d, the others are named specifically like gnome-shell, unity-2d, ect.

---

### Post by cariboo on 2011-07-16
At one point last week, I was also getting can't start Unity errors along with the Gnome error, mind you this was choosing the session from lightdm.

---

### Post by kiwited on 2011-07-16
Thanks for the help Caribou.

I did try to follow the preferred method of sending in a possible bug. The problem is that there is a need for online access, the use of Apport, and a knowledge of the offending package, none of which is available when you cannot get past the command prompt unless you have a better knowledge that I do of command line computing!

I just figured that if anyone was interested they could ask whatever they needed to know and perhaps tell me how to find what is needed this info.

---

### Post by cariboo on 2011-07-16
Once you get the system up and running, you could check apport.log and Xorg.0.log, to see if there is anything significant to add to the bug report.

If your system still isn't up and running, I'd suggest installing gnome-shell in recovery mode, then trying startx again.

---

### Post by Peter09 on 2011-07-17
I am getting this on a standard unity install, so its nothing to do with gnome-shell. When it does boot I go into Unity 3D.

---

### Post by garvinrick4 on 2011-07-17
> I have upgraded my 11.04 to 11.10. Normal boot stops at "Checking  Battery State" - machine hangs but responds to alt-ctrl-del and reboots. About a week ago had two installs 11.10 this was happening and had to install
lightdm and a lightdm theme. 
Ctrl/alt/F1
login
sudo apt-get install lightdm
sudo apt-get install lightdm-greeter-example-gtk
sudo stop gdm
sudo start lightdm
Ctrl/alt/F7
She went to login screen in using lightdm 

Here are the two packages I used .
```
rick@rick-HP:~$ aptitude show lightdm
Package: lightdm                         
New: yes
State: installed
Automatically installed: no
Version: 0.4.3-0ubuntu1
Priority: optional
Section: x11
Maintainer: Robert Ancell <robert.ancell@ubuntu.com>
Uncompressed Size: 307 k
Depends: debconf (>= 0.5) | debconf-2.0, upstart-job, libc6 (>= 2.4),
         libglib2.0-0 (>= 2.28.0), libpam0g (>= 0.99.7.1), libxcb1, libxdmcp6,
         libpam-runtime (>= 0.76-14), libpam-modules, adduser
PreDepends: dpkg (>= 1.15.7.2)
Recommends: xserver-xorg, lightdm-greeter
Provides: x-display-manager
Description: Display Manager
 LightDM is a X display manager that: 
 * Has a lightweight codebase 
 * Is standards compliant (PAM, ConsoleKit, etc) 
 * Has a well defined interface between the server and user interface 
 * Cross-desktop (greeters can be written in any toolkit)
Homepage: https://launchpad.net/lightdm

rick@rick-HP:~$ 




rick@rick-HP:~$ aptitude show lightdm-greeter-example-gtk
Package: lightdm-greeter-example-gtk     
New: yes
State: installed
Automatically installed: no
Version: 0.4.3-0ubuntu1
Priority: optional
Section: x11
Maintainer: Robert Ancell <robert.ancell@ubuntu.com>
Uncompressed Size: 311 k
Depends: libc6 (>= 2.2.5), libcairo2 (>= 1.2.4), libgdk-pixbuf2.0-0 (>= 2.22.0),
         libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.23.90),
         liblightdm-gobject-0-0
Recommends: lightdm
Provides: lightdm-greeter
Description: LightDM GTK+ Greeter
 A LightDM greeter that uses the GTK+ toolkit.
Homepage: https://launchpad.net/lightdm

```

---

### Post by wildmanne39 on 2011-07-18
Hi, I have the same problem right now.

---

### Post by argument on 2011-07-21
Same here. What seems to be wise? Wait for an update or go back to 11.04? Did not find any solution to the problem yet.

---

### Post by garvinrick4 on 2011-07-21
> Same here. What seems to be wise? Wait for an update or go back to 11.04? Did not find any solution to the problem yet.
I do not believe it has lightdm or gdm to open the GUI.
If you ctrl/alt/F1
what do you have running
sudo start lightdm (does it say it is running.)
sudo start gdm (does it say it is running)if so
sudo stop gdm
sudo start lightdm (if that fails try below.)
sudo dpkg-reconfigure lightdm (does it get it going)
sudo session lightdm restart (how about now)
If not:
sudo apt-get install aptitude
aptitude show lightdm (is it installed)
# I was on upgrade and did not use login screen and when lightdm
became default I was in same position as you. If above works fine  good,if not need to install lightdm and lightdm theme. Be forwarned that 11.10 is in Alpha and not stable will have a few of these problems to go through.

---

### Post by Peter09 on 2011-07-21
I have no keyboard when it is in the 'battery wait' state.

---

### Post by garvinrick4 on 2011-07-21
> I have no keyboard when it is in the 'battery wait' state.I believe we had that issue not to far back in oneiric, lets look back and see
what the fix was.
edit: Thread about a week or so old, should be more.
[http://ubuntuforums.org/showthread.php?t=1802114](http://ubuntuforums.org/showthread.php?t=1802114)

---

### Post by cariboo on 2011-07-21
I just got the same error after installing the latest kernel (3.0.0.6-7), after trying to start using startx I got the no screens error message. I had to re-install nvidia-current to get past the checking battery state message.

---

### Post by Harry33 on 2011-07-22
> **cariboo907 said:**
> I just got the same error after installing the latest kernel (3.0.0.6-7), after trying to start using startx I got the no screens error message. I had to re-install nvidia-current to get past the checking battery state message.

This is because the latest kernel installation does nor start dkms rebuild.
The new installation is left without the file (/lib/modules/3.0.0-6-generic/updates/dkms/nvidia-current.ko).
Re-installation corrects the issue.

---

### Post by Quackers on 2011-07-22
Re-installing nvidia-current worked for me :-)

---

### Post by David Tomic on 2011-07-22
> **Quackers said:**
> Re-installing nvidia-current worked for me :-)

+1

I was worried that this was going to be a much more painful problem. ;)

---

### Post by zeus.jay on 2011-07-23
> **Harry33 said:**
> This is because the latest kernel installation does nor start dkms rebuild.
The new installation is left without the file (/lib/modules/3.0.0-6-generic/updates/dkms/nvidia-current.ko).
Re-installation corrects the issue.


Thanks guys this does indeed fix the issue.

---

### Post by kiwited on 2011-07-25
The solutions that have been arrived at seem to refer to nvidia graphics. I have an ATI Radeon card.
For me the problem persists. I have not yet been able to start the desktop.
"Normal" boot halts after "Checking battery state"
Booting into recovery mode, then into normal boot achieves a couple of screen flickers, a long wait then:

xinit: giving up
xinit: unable to connect to xserver: Connection refused
waiting for x server to shut down ddxSigGiveUp: Closing log
xinit: server error
xauth: error in locking authority file /home/theo/.Xauthority

---

### Post by Peter09 on 2011-07-26
I have an intel card - so no change there for me.

---

### Post by halloweenx8 on 2011-07-26
I have an INTEL 945 on a netbook EEE 1500ha, what do I do?

---

### Post by halloweenx8 on 2011-07-26
More update, when i boot in termal mode, and i start gnome-session
i get this
 
gnome-session-is-accelerated: No hardware 3D support
gnome-session-check-accelerated: helper exited with code 256
gnome-session [2330]: WARNING: Session 'gnome' runnable check failed; Exited with code 1
 
Any ideas?

---

### Post by godhika on 2011-07-26
Ok guys as I encountered the same error message after the latest update (which brought in a new lightdm version) i tried to change the display manager to GDM - and it works! 
Sorry if this workaround has been mentioned here before, I didn't dig through the whole thread ;)

---

### Post by cecilpierce on 2011-07-26
How did you change it?
I have to go to tty1 and type startx and then im in ubuntu classic 2d or something, when I logout im back to tty1 :confused:

---

### Post by godhika on 2011-07-26
if you have a fairly recent install GDM wasn't installed by default. So simply sudo apt-get install gdm and when asked choose GDM.
If your install is from early in this cycle or an updated narwhal I think the command is > sudo dpkg-reconfigure gdm

---

### Post by drs305 on 2011-07-26
> **godhika said:**
> Ok guys as I encountered the same error message after the latest update (which brought in a new lightdm version) i tried to change the display manager to GDM - and it works! 
Sorry if this workaround has been mentioned here before, I didn't dig through the whole thread ;)

The previous update failed for me until I reinstalled the nvidia driver. 

Reinstalling nvidia-current did not work for me this time, but installing/reinstalling gdm from the Recovery mode root prompt did.

Update: I then uninstalled lightdm 0.4X and installed the 0.9.2 version of lightdm, lightdm-gtk-greeter and lightdm-gobject-1-0. Ran 'sudo dpkg-reconfigure lightdm", rebooted, and things were back to normal.

---

### Post by lsrg on 2011-07-27
In my case I solved it doing:

sudo apt-get remove lightdm
sudo apt-get install ubuntu-desktop

and reboot

---

### Post by MadCow108 on 2011-07-27
installing lightdm-gtk-greeter should solve the problem:
[https://lists.ubuntu.com/archives/ubuntu-devel/2011-July/033772.html](https://lists.ubuntu.com/archives/ubuntu-devel/2011-July/033772.html)

---

### Post by yaddoshi on 2011-07-27
> **lsrg said:**
> In my case I solved it doing:

sudo apt-get remove lightdm
sudo apt-get install ubuntu-desktop

and reboot

Same here, although instead of rebooting I did
```
sudo stop lightdm
sudo start lightdm
```
and then it continued booting normally.

---

### Post by JRV on 2011-07-27
Thank you lsrg and yaddoshi, that worked for me.

---

### Post by margu on 2011-07-29
> **MadCow108 said:**
> installing lightdm-gtk-greeter should solve the problem:
[https://lists.ubuntu.com/archives/ubuntu-devel/2011-July/033772.html](https://lists.ubuntu.com/archives/ubuntu-devel/2011-July/033772.html)


Thank you MadCow108. It worked for me.

---

### Post by kiwited on 2011-07-29
Having reinstalled lightdm-gtk-greeter I have made some progress (I think!).
The desktop still does not start in the "normal" boot mode. In recovery mode I can start lightdm but the computer hangs at the login screen.
I cannot login from the recovery mode and start the desktop - the computer hangs with a blank screen.
I CAN run startx as root from the recovery mode and the desktop starts as user root.

So, my present position is that I still cannot start the desktop as user.

---

### Post by VinDSL on 2011-07-30
LoL!  Just got home from holiday, and...

Turned on the PC and got an error saying my "Floppy" wasn't working.  Hello!?!?!  Don't have a floppy!  Date was Mar-something-2003, also.

Seen this one before - dead CR2032 button cell on the mobo.  After going through a storage bin of half-dead replacement batteries, I found one that actually measured 3V - and I was off to the races, no pun intended.

Booted into Ubu 11.10 and was greeted by 100's of updates.  Fine!

By the time all the updates were completed - with nothing being held back - I was stuck @ "Checking Battery State" @ boot.  Seen that one before too...

In my experience, 99% of the time, this indicates having to reinstall the nVidia drivers, but I tried fiddling around with LightDM (as described above).  No soap!

When I was done playing around, I did a wash, rinse, and restyle of "nvidia-current".  This got me to the desktop, but...

Somewhere along the line, Libcairo2 got updated, and it was using 75% of my (1GB) RAM, sitting idle at the desktop.  Seen that too!

Sooo... Lastly, I downgraded Libcairo2 from "1.10.2.**[COLOR="Red"]6[/COLOR]**ubuntu2" to "1.10.2.**[COLOR="Red"]2[/COLOR]**ubuntu2" and...

Life is good now!

So nice to be home...  :D

---

### Post by aquarius18 on 2011-07-31
This issue is going back to June 8th, 2010 (Ubuntu 10.04) - see thread [http://ubuntuforums.org/showthread.php?t=1504531](http://ubuntuforums.org/showthread.php?t=1504531) ... so the bootup freeze at "Checking Battery State" is not that new at all

I have 11.04 running perfectly (so far) on one machine but on a new install (alongside Win7) on a machine I am trying to get running for my wife the same error keeps happening.

---

### Post by cariboo on 2011-07-31
@aquarius18

This is the Oneric testing and discussion sub-forum, the problem here is different from the problem you are suffering from. Most of the people having the problem here, either have to re-install the nvidia driver with the latest kernel (3.0.0-7.9) or stop and restart lightdm.

---

### Post by aquarius18 on 2011-08-07
> **cariboo907 said:**
> @aquarius18

This is the Oneric testing and discussion sub-forum, .......

oops, didn't realize that I am in the wrong forum - obviously too late in the day. Sorry about that folks.

---

### Post by seattle vic on 2011-09-02
I'm upgraded to 11.10 to a VM guest I have running under Ubuntu (also upgraded to 11.10).  The host boots up fine, but the guest halts at the battery check.  I'm not always able to ssh in to the guest, but when I could I had some success with lightdm when I stopped and started it and it booted into the ubuntu desktop (which I don't care for).  The greeter app did nothing.

So I'm reading that upgrading to a newer NVIDIA (which I do use) driver may help; I'll try that next.

BTW, is this a kernel issue?  What software is doing this battery check and what is it checking or think it's checking?

---

### Post by cariboo on 2011-09-02
You didn't say what virtual machine you are using, but virtualbox doesn't use nvidia drivers, if you are getting to the battery check, it usually means that lightdm isn't starting automatically. If you can start in recovery mode, you should be able to get to a command line login prompt, once logged in type the following command:

```
sudo service lightdm start
```

this should take you to a graphical login screen, once there you should be able to fix the problem of lightdm not starting automatically.

---

### Post by tricky76 on 2011-09-05
Beginner ubuntu user here. I had the same issue.  I am running Ubuntu on a 2008 imac and just upgraded to 11.10.  I uninstalled and reinstalled lightdm.  I also reinstalled ubuntu-desktop (removed when I removed lightdm) and uninstalled and reinstalled the nvidia-current drivers.  

The log in screen finally comes up, however after a minute or so (whether or not I log in), my system freezes and mouse and keyboard are unresponsive.  Does anyone have any ideas on how I can fix this?  

thanks!
-t

---

### Post by ventrical on 2011-09-06
> **cariboo907 said:**
> I just got the same error after installing the latest kernel (3.0.0.6-7), after trying to start using startx I got the no screens error message. I had to re-install nvidia-current to get past the checking battery state message.


I got the same thing.. the no screens error. I tired all the codes  that have been posted, but to no avail.

How to I check for/and install a video driver?

---

