---
title: "No sound output with Ubuntu 13.10 After changing Drivers"
date: 2014-01-21
forum: New to Ubuntu
---

### Post by boyshawn on 2014-01-21
I have previously get my sound to be working with this version after I follow the article [here]("http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/"). 
  But just after I change the driver at Software and updates->  Additional Drivers to a proprietary drivers, the sound driver stop  working. The problem persists even after I revert it back to the one  which Ubuntu recommend (open source, tested). I tried to follow some of  the help instructions given in other threads but they are not helpful. 
  The driver which I change is Advanced Micro Devices, Inc. [AMD/ATI]: Juniper XT [Radeon HD5770]

Edit 1: Attached my screen shot for Additional Drivers
[IMG]https://db.tt/ySE5OMRI[/IMG]

Edited 2: Problem solved!

---

### Post by QIII on 2014-01-22
Hi!

Assuming you had previously installed the proprietary ATI fglrx driver, how, exactly, did you uninstall it?

---

### Post by squakie on 2014-01-22
Are you talking about analog sound, or sound via HDMI?  If via HDMI, and if you have the video card you mentioned, then you need:

- remove your other video drivers
- install fglrx-updates from the repositoried
- add the following option to the grub boot options:

radeon.audio=1

---

### Post by boyshawn on 2014-02-08
> **QIII said:**
> Hi!

Assuming you had previously installed the proprietary ATI fglrx driver, how, exactly, did you uninstall it?

Sorry that I am newbie in this area. I don't think that I uninstall it. Instead I just did a switch in option under "Software And Updates" -> "Additional Updates"

---

### Post by boyshawn on 2014-02-08
> **squakie said:**
> Are you talking about analog sound, or sound via HDMI?  If via HDMI, and if you have the video card you mentioned, then you need:

- remove your other video drivers
- install fglrx-updates from the repositoried
- add the following option to the grub boot options:

radeon.audio=1

Yes, I am talking about sound via HDMI. 
Sorry but I am not to sure what you mean by remove my other video drivers? I try to reference to this [Q&A]("http://askubuntu.com/questions/109452/how-can-i-uninstall-graphics-driver") but I don't have ATI folder in my drive.

---

### Post by boyshawn on 2014-02-14
bump , waiting for answer/ assistance!

---

### Post by boyshawn on 2014-02-25
bump for assistance!

---

### Post by squakie on 2014-02-26
give me until the weekend and i'll try to post something back for you.

---

### Post by squakie on 2014-02-26
Open a terminal window via cntrl/alt/F!

log in with your normal userid and normal password - the password is not echoed to the screen

type:

cd /etc/default <press enter >

sudo cp grub grub-original < press enter >  This creates a copy of the file before you modify it

sudo gedit grub < press enter>

This will start up the editor and open the grub file for editing.  You want to look for a line like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it to look like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

Then click on save, wait for it to save, then exit the editor to return back to the terminal window.

Type:

sudo update-grub < press enter >

sudo shutdown -r now < press enter >

These last 2 steps will regenerate a file used at boot time, then shutdown with a reboot (-r) so your PC will reboot.

After reboot, click on the sound icon on the top bar, click on "Sound Settings", and hopefully you will see the option now for HDMI sound output.  You'll have to click on it to make it the default, then just close out of it.

Try something now to see if the sound is active via HDMI now.

I have a Radeon HD 6450 and I have to use this to get sound via my HDMI link.

---

### Post by boyshawn on 2014-03-08
> **squakie said:**
> 
...This will start up the editor and open the grub file for editing.  You want to look for a line like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it to look like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

...

Yes, it works! Only that there is missing volume indicator! But still, thank you a lot!

---

### Post by raul-serrano512-x on 2014-03-28
Well it did not let me post this question. but am having same problem. only difference i can see the hdmi option i can toggle the increase volume and stuff.. also i already edited the lines. and still have no sound. My system Amd 6800k apu using propietary drivers

---

