---
title: "nVidia XServer display config in Oneiric"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by volkerbradley on 2011-09-27
My system is 64-bit with a Nvidia GeForce GTX 285M Graphics card with 1GB GDDR3 Video Memory.  I have a Dell monitor attached to my laptop via a DVI connector.
In Natty, the nVidia XServer display configuration lists my monitor and allows me to configure it and use it.
In Oneiric, the nVidia XServer display configuration does not list the monitor and I cannot configure the monitor or use it.
Screenshots are enclosed.
Do you have any suggestions?

---

### Post by BicyclerBoy on 2011-09-27
Backup/Delete /etc/X11/xorg.conf
This file is not needed anyway..

run from terminal:
nvidia-xconfig
could need sudo but I think that just causes more problems.

There are many other possible configuration files in use now with the later Xorg. I don't know where/what they are.

---

### Post by cariboo on 2011-09-28
> **BicyclerBoy said:**
> Backup/Delete /etc/X11/xorg.conf
This file is not needed anyway..

run from terminal:
nvidia-xconfig
could need sudo but I think that just causes more problems.

There are many other possible configuration files in use now with the later Xorg. I don't know where/what they are.

You need to run:

```
sudo nvidia-xconfig
```

as the command writes a new /etc/X11/xorg.conf, which means you need to escalate privileges.

---

### Post by volkerbradley on 2011-09-28
> **cariboo907 said:**
> You need to run:

```
sudo nvidia-xconfig
```

as the command writes a new /etc/X11/xorg.conf, which means you need to escalate privileges.
Thank you for your responses.
I gave the command you suggested.  It did not fix the problem.
Perhaps it is related to a bug that I have experienced and others have reported. The bug is gnome-settings-daemon crashed with SIGSEGV
What do you think?

---

### Post by BicyclerBoy on 2011-09-28
Was there any std-out messages from nvidia-xconfig ?

Run from a terminal:
nvidia-settings
(no sudo)

Any error messages ?

post the /var/log/Xorg.0.log files.

---

### Post by volkerbradley on 2011-09-30
> **BicyclerBoy said:**
> Was there any std-out messages from nvidia-xconfig ?

Run from a terminal:
nvidia-settings
(no sudo)

Any error messages ?

post the /var/log/Xorg.0.log files.
Here is what I tried in the meantime:
While I was in Natty on this machine, copied the xorg.conf file to a USB drive
Then installed the Oneiric image which I am running now.  Made a backup of the original xorg.conf file and then installed the xorg.conf file from Natty in my Orneiric installation.
Logged out and logged back in.
The Dell monitor now functions.  Did sudo nvidia-xconfig  --no error messages
Did nvidia-settings  --no error messages
The only problem is that the monitor is set at 640x480 which is intolerable.  Wished I know how to fix this.
I have included my present xorg.conf file and the /var/log/Xorg.0.log file.
If you could suggest how to change the resolution to 1400x1050, I would be most grateful.

---

### Post by BicyclerBoy on 2011-10-01
There is an error about EDID read failure..on the DFP-2.
That's a common nVidia problem.

How have you managed to get a nVidia driver so old ? (173)..
Surely 11.10 would be using 275 or 280 ?
Was this driver included with 11.10 install or a left over from previous ubuntu distro ?
Check with synaptic pack manager what nvidia* packages you have installed.
Maybe the update is blocked by 173.xx.xx ..

---

### Post by volkerbradley on 2011-10-01
> **BicyclerBoy said:**
> There is an error about EDID read failure..on the DFP-2.
That's a common nVidia problem.

How have you managed to get a nVidia driver so old ? (173)..
Surely 11.10 would be using 275 or 280 ?
Was this driver included with 11.10 install or a left over from previous ubuntu distro ?

Thanks again for taking time to respond. 
After I had performed a fresh install of 11.10, a message popped up stating that a commercial driver was available.  I clicked on this message and then this nVidia driver was installed.
Would you say that following the advice at [http://www.multimediaboom.com/install-nvidia-driver-ubuntu-1-04-11-10-ppa/](http://www.multimediaboom.com/install-nvidia-driver-ubuntu-1-04-11-10-ppa/) is what I should do to install the latest driver?  Think that it might resolve the EDID read failure?

---

### Post by BicyclerBoy on 2011-10-01
It's just setting up to use the x-swat ppa.
This blog,like most of the web, just rehashes/repeats info from elsewhere.

That's fairly safe & reversable procedure.

You could just check you have the nvidia-current package installed now.

Another more risky ppa is xorg-edgers launchpad ppa.

---

### Post by effenberg0x0 on 2011-10-01
I have posted some detailed instructions on how to get and install the NVidia Official (proprietary) drivers for Ubuntu 32-bit and 64-bit here: [http://ubuntuforums.org/showthread.php?p=11293922#post11293922](http://ubuntuforums.org/showthread.php?p=11293922#post11293922)

Also in that thread, I have posted a link from NVidia website where you can see what is the correct driver for your card.

You'll get more information there but, to summarize, some cards only support version 173. The most recent is 280.13 and 275 is actually beta (you'll find it in NVidia Linux Drivers website only if you click on Beta and Legacy drivers, which are separate from the stable ones).

The official driver installation performs some steps to find and fix potentially conflicting files from other drivers. It's a fairly easy process (just answer yes to all questions). 

Maybe it can help.

Regards,
Effenberg

---

### Post by MAFoElffen on 2011-10-01
Just info on the driver:
For some (at least in Natty) rolling back to nvidia-173 is a workaround for poor video playback, jagged graphics and video tearing in some problem between compiz and nvidia's drivers.  Launchpad says it's an nVidia driver problem, but it only seems to happen (to rare individuals) with compiz and especially in Ubuntu.  They lose quality and speed in that fix.

On the EDID...
If you can get output from 
```

sudo hwinfo --monitor

```Then the nVidia driver and nvidia-settings can usually see your monitor's EDID data.

If not, but you can still get output from
```
[FONT=monospace]
[/FONT]xrandr --prop

```Then I have a way to get your EDID data, even if nvidia-settings cannot.

---

### Post by volkerbradley on 2011-10-02
> **effenberg0x0 said:**
> I have posted some detailed instructions on how to get and install the NVidia Official (proprietary) drivers for Ubuntu 32-bit and 64-bit here: [http://ubuntuforums.org/showthread.php?p=11293922#post11293922](http://ubuntuforums.org/showthread.php?p=11293922#post11293922)

Also in that thread, I have posted a link from NVidia website where you can see what is the correct driver for your card.

You'll get more information there but, to summarize, some cards only support version 173. The most recent is 280.13 and 275 is actually beta (you'll find it in NVidia Linux Drivers website only if you click on Beta and Legacy drivers, which are separate from the stable ones).

The official driver installation performs some steps to find and fix potentially conflicting files from other drivers. It's a fairly easy process (just answer yes to all questions). 

Maybe it can help.

Regards,
Effenberg
I downloaded the driver for my card which is a Nvidia GeForce GTX 285M Graphics with 1GB GDDR3 Video Memory.  Then I did CTRL+ALT+F1
This turned my screen black and nothing else happened.  No login prompt.
I got back to X with CTRL+ALT+F7
Per another suggestion I tried sudo hwinfo --monitor.  This gave me no information.  Then I tried xrandr --prop  .  Here is the output:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0*    51.0     52.0     53.0  
   576x432        54.0     55.0     56.0     57.0  
   512x384        58.0     59.0     60.0  
   416x312        61.0  
   400x300        62.0     63.0     64.0     65.0  
   320x240        66.0     67.0     68.0
It's interesting that it does not show the resolutions that are possible for the monitor.  The maximum is certainly not 640x480
Can you tell me what I am doing wrong?  How can I get out to the VT so I can try to install the new driver?

---

### Post by volkerbradley on 2011-10-02
> **BicyclerBoy said:**
> There is an error about EDID read failure..on the DFP-2.
That's a common nVidia problem.
etc...

Problem solved.  As I mentioned before, while I was in Natty, I copied my xorg.conf file. 
Then I followed the instructions at [http://analogbit.com/fix_nvidia_edid](http://analogbit.com/fix_nvidia_edid) by doing the following:
Ran nvidia-settings, clicked on DFP-2, then clicked "Acquire EDID..." and saved the binary file. Copied this file to a USB memorystick as well.
Reinstalled the Oneiric image
Made a backup of the /etc/X11/xorg.conf file
Copied the xorg.conf file from the memorystick to /etc/X11/
Then copied the edid file to /etc/X11/dell.edid
Edited the xorg.conf file as suggested at [http://analogbit.com/fix_nvidia_edid](http://analogbit.com/fix_nvidia_edid)
Rebooted.
Now my attached monitor works perfectly.

---

### Post by MAFoElffen on 2011-10-02
Sidenote to this topic--

You know... Previous to the last 2 1/2 weeks ago, an EDID read problem was rare in these forums.  It sure seems to have been a lot of EDID problems in 11.10 and 11.04 in the past 2 weeks!  (Not just in Oneiric.) Most of these had monitors that were fine in previous versions of Ubuntu.

Was there any updates to xorg-xserver in the last two weeks?

EDIT--
Yes there was.

In progress:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/712075](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/712075)
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/538600](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/538600)
and a few other duplicates.

---

