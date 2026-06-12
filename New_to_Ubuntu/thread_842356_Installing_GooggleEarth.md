---
title: "Installing GooggleEarth"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by jaygrice on 2008-06-27
Hi y'all,
I've gotten rid of Windows after many years, now have an exclusive Ubuntu box and am feeling very good about the change, even with the learning curve. So far everything has worked out of the box, no problems that weren't answered in this forum. My question now---I did the googleearth install following threads posted here and it seems the installation did what it's supposed to do, however when I try to run it, either from terminal or by clicking it in Applications, all that happens is the google splash screen shows for a few seconds, then it reboots the computer. Any ideas why?  Thanks
BTW--I tried to attach the code I copied and pasted for the installation but that didn't work :(

---

### Post by Canis familiaris on 2008-06-27
This thread will help:

[http://ubuntuforums.org/showthread.php?t=841352](http://ubuntuforums.org/showthread.php?t=841352)

EDIT: Sorry I didnt read your post carefully. So you have problems in Google Earth.

You can ignore this post

---

### Post by drs305 on 2008-06-27
Did you install it via synaptic or manually install it? There have been numerous threads on both recently.

If you didn't do it via synaptic, that is the method I recommend. Uninstall if possible and then run these steps: 
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Install Google Earth (this is a metapackage, no version number required. current version 4.3):
```
sudo apt-get install googleearth
```

If it was a synaptic install or it still doesn't work, let us know.

---

### Post by jaygrice on 2008-06-27
Ok, I uninstalled via Synaptic, re installed with the code in above reply, rebooted, clicked on the icon in applications, the same thing happened(was kicked back to log in screen).  Synaptic shows the package is there, but it doesn't want to cooperate.:(

Maybe I'm leaving out a step somewhere?

---

### Post by sydbat on 2008-06-27
Might be a video driver issue. What video card are you using?

---

### Post by jaygrice on 2008-06-27
Maybe you are right, however that app ran wonderfully when I was an XP user, same 'puter and hardware. So you'd think it would run in Ubuntu.  Computer is a Vio laptop, 5 years old, i gig ram, nVideo Go?--(not sure).  Thanks

---

### Post by Canis familiaris on 2008-06-27
You first need to install the nvidia drivers.

Go to System->Administration->Hardware Drivers and install the nVidia drivers. 

After this try running Google Earth again. Does this help.

EDIT: First what is the output of the following:
```
glxinfo | grep Direct
``````

```

---

### Post by tubbygweilo on 2008-06-27
System > Appearance >  Visual Effects will show if any are in use, if so then turn them off as I find this has helped me when running GoogleEarth and it may even help you.

---

### Post by drs305 on 2008-06-27
The windows drivers and linux drivers are not identical and may not perform the same.

The nvidia drivers installed via envyng-gtk are more recent than the restricted drivers, at least in my case. You may want to try to install them via:
Install envyng-gtk:
```
sudo aptitude install envyng-gtk
```
Once installed, it's in the System Tools menu. There is also an Nvidia X Server Settings wizard in System, Admin - I think that is installed with the nvidia-settings package.

---

### Post by jaygrice on 2008-06-27
OK,1st off the command "glxinfo" gives back nothing.  2nd I'm not using visual effects. Here are specs on vid card:
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV17 [GeForce4 420 Go]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=248 maxlatency=1 mingnt=5

This is so fun! Later

---

### Post by gandaran on 2008-06-27
> **jaygrice said:**
> Maybe you are right, however that app ran wonderfully when I was an XP user, same 'puter and hardware. So you'd think it would run in Ubuntu.  Computer is a Vio laptop, 5 years old, i gig ram, nVideo Go?--(not sure).  Thanks

in windows xp, google earth can be run in two ways, you got a 3d video card, it runs in gl mode, no 3d video card, it runs in directx mode, now in ubuntu you only can run google earth with a 3d video card.

---

### Post by jaygrice on 2008-06-28
OK, now I have a whole new problem--went to sys-admin-drivers and ticked the box to download the nVidia driver, after the install and reboot all I have now is a black screen. I got the boot option screen and can get the terminal--so how do I undo the driver install from there.  If Google will only run in Ubuntu with 3D card, I'm probably SOL, but no great loss.:)  Thanks for all the responses, it's impressive the amount of knowledge available and shared here!

---

### Post by drs305 on 2008-06-28
> **jaygrice said:**
> OK, now I have a whole new problem--went to sys-admin-drivers and ticked the box to download the nVidia driver, after the install and reboot all I have now is a black screen. I got the boot option screen and can get the terminal--so how do I undo the driver install from there.  If Google will only run in Ubuntu with 3D card, I'm probably SOL, but no great loss.:)  Thanks for all the responses, it's impressive the amount of knowledge available and shared here!

I don't know if the envyng-gtk package will run with your situation but you can do the install and see if it will launch some sort of gui or text mode that you can use.

```
sudo aptitude install envyng-gtk
```

---

### Post by jaygrice on 2008-06-28
From recovery screen, terminal shell puts me at root. Do I want to try things from root or should I change dir to a safer place?

---

### Post by Vadi on 2008-06-28
I believe some people should use the 4.2 version instead of 4.3 because 4.3 has some video driver issues. That's why medibuntu carries both

(hope you get your video problem solved soon)

---

### Post by bhadotia on 2008-06-28
By default you will log in as root in recovery mode . And because your working with pakage manager you will need the root (superuser) privilages.
So stay like that. BTW, how are you browsing the net ( if you are in recovery mode, some other PC, I think you said you were completely into ubuntu).

---

### Post by diablo75 on 2008-06-28
> **Vadi said:**
> I believe some people should use the 4.2 version instead of 4.3 because 4.3 has some video driver issues. That's why medibuntu carries both

(hope you get your video problem solved soon)

I can vouch for this too.

As for your "it's throwing me to a root terminal" problem, try running this from the command line:

```
dpkg-reconfigure xserver-xorg
```

It's pretty easy.... Though I would recommend you NOT use the kernel buffer when it asks you, as well as makeing sure you are using the driver called "nvidia".

Here's some more info if you need help:
[http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

---

### Post by bhadotia on 2008-06-28
If you did:
```
sudo apt-get install googleearth
```
Then , by default the 4..2 version was installed (atleast that was the case with me). The package googleearth picks up the version 4.2 as a dependency .

---

### Post by jaygrice on 2008-06-28
WOW! Finally got my desktop back,thanks to all the help (one problem solved). That brings me back to the orig.-getting goggleearth to load. If my video card isn't 3D it's a moot point anyway,correct? Here it is: NV17(GeForce4 420 Go)agp-2.0 vga. Nothing there about 3D tho.

---

### Post by Vadi on 2008-06-28
Oi, yeah... that is a very old card.

---

### Post by jaygrice on 2008-06-29
Finally got GoogleEarth to work, video display problems fixed and I'm happy as clam at high tide.  Here's what worked for me-----I had called on my son(who has been a Linuxhead for years)to help, but he was camping in the mountains all week,out of touch.  When he returned my calls he said he had faced the same problem and would try what worked for him. He did,it did! This is the fix:

sudo gedit [or use nano on the commandline] /etc/X11/xorg.conf
--under the “Device” section, add the following line:

Option “UseDisplayDevice”   “DFP"

Reboot, cross fingers :)

 That’s after enabling the Restricted Hardware Drivers for the Nvidia display, and before rebooting.

I hope this will help some other new user facing problems with older nVidia cards. And many thanks to all you people who offered help and support.):P

---

