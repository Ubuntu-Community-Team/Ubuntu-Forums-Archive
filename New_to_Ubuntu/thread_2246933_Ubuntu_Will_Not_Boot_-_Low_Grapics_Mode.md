---
title: "Ubuntu Will Not Boot - Low Grapics Mode"
date: 2014-10-04
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-10-04
I'm trying (unsuccessfully) to help a friend with his 12.04 laptop over the phone.  It will not boot at all - so I suggested he chooses the recovery option at the grub screen.  I have tried failsafex and he gets to a screen saying he is in low graphics mode - I get him to choose the option to start in low graphics for this session only but clicking on OK seems to have no effect.  Some web sites suggest pressing Crtl, Alt, F1 at this stage but this key strokes have no effect.  No matter what options he chooses in failsafex he gets in a loop.  I can get him to a command prompt via recovery mode but do not have the skills/knowledge to know what to do to hep recover 12.04 from the prompt.  Is there anything I can do at the command prompt to help him recover his machine?

---

### Post by XDevHald on 2014-10-04
Hi Quarkrad,

If you have eth0 or wlan running during the X session, use another computer and view this link I am providing you and be sure to follow them correctly to ensure it meets all requirements to ensure this works. Please let us know the results of the process. Good luck!

[http://simpledeveloper.com/system-running-in-low-graphics-mode/](http://simpledeveloper.com/system-running-in-low-graphics-mode/)

---

### Post by grahammechanical on 2014-10-04
That link refers to re-installing, purging and installing GDM but Ubuntu has not used GDM (Gnome Display Manager) for years. Ubuntu uses LightDM.

In my opinion, failsafeX mode is broken. Even on a fully functional system I am unable to use failsafeX to get to any further than your friend has got.

My advice is to use to use Recovery Mode>Resume. On 12.04 that should load to a desktop using VGA video mode instead of the proprietary video driver. Then at the desktop use Additional Drivers to change the video driver. Reboot and see what happens.

Of course, the words "will not boot at all." Do not give us enough information to determine where the boot process is failing. The machine is not booting into failsafeX mode of its own accord but because you are telling your friend to select it. The failure of failsafeX is a distraction.

Is there a Grub Boot menu? What happens when Ubuntu is selected? What appears on the screen? Can the loading process get to a login screen? Do you understand the kind of information that would help eliminate possible causes? 

We know that there is a Grub boot menu. We know that the machine will load as far as the Recovery menu but what happens when Resume normal boot process is selected?

Regards.

---

### Post by Quarkrad on 2014-10-05
I've tried a few things and they haven't worked.  We have a 12.04 (32bit) machine that is running kernel 3.2.0-69 - when you power up you get to the grub screen and then into the boot process.  When the Ubuntu white text appears in the centre of the screen the white dots beneath are static in stead of 'moving/blinking' &#8211; it is as if the whole boot process is frozen.   There is an option at the grub screen to boot to the previous version 3.2.0-68 but the same thing happens.  I have booted into recovery mode and tried failsafex but that does not help.  After some reading and trying several commands at the root prompt I kept getting:

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write /var/cache/apt/
E: The package lists or status file could not be parsed or opened

After further reading I tried:

mount -o remount,rw /
mount &#8211;all

and then tries of:

sudo apt-get install --reinstall xorg-xserver*
sudo apt-get install --reinstall lightdm
sudo apt-get install --reinstall unity
sudo apt-get install --reinstall ubuntu-desktop


Before I tried the above commands I tried the Resume option in the recovery menu as well as (some time after) dpkg but all result in the frozen screen, after grub, with the Ubuntu text and the static white dots.

---

### Post by Quarkrad on 2014-10-08
Crunch day today - I have to do something or do a remote re build.  Most web searches on ubuntu recovery using the live cd is about restoring grub - but my grub is OK.  The problem (I think) is something during Ubuntu's boot process.  Is there anything I can try using a live CD that 'recovery mode' does not fix?

---

