---
title: "Help! Sound Not Working"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Pasty-Flawss on 2008-07-14
Hi,

My sound is not working. i think its something to do with my sound drivers. I have tried many tutorials and all failed and now im confused and have no idea what problem is.

Ubuntu can detect my sound driver however its not working..

when i load alsa mixer i get this:
ALSA lib conf.c:1588: (snd_config_load1) /home/pasty-flawss/.asoundrc.asoundconf:8:20:Unexpected char
ALSA lib conf.c:2849:(snd_config_hook_load) /home/pasty-flawss/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2713: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3076: (snd_config_update_r) hooks failed, removing configuration

alsamixer: function snd_ctl_open failed for default: Invalid argument


when i load gnome alsamixer it says:
ALSA lib conf.c:1588:(snd_config_load1) /home/pasty-flawss/.asoundrc.asoundconf:8:20:Unexpected char
ALSA lib conf.c:2849:(snd_config_hook_load) /home/pasty-flawss/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2713:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3076:(snd_config_update_r) hooks failed, removing configuration

and launches a program with blank screen and when i go into Edit > Sound Card properties it says in terminal:
ALSA lib conf.c:2849:(snd_config_hook_load) /home/pasty-flawss/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2713:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3076:(snd_config_update_r) hooks failed, removing configuration


PLEASE HELP! THANKS FOR ANY HELP IN ADVANCE!

---

### Post by Pasty-Flawss on 2008-07-14
has it got anything to do with alsamixer?

---

### Post by Pasty-Flawss on 2008-07-14
i think i need to "load my alsa modules" how do i do this?

---

### Post by philinux on 2008-07-14
Whats the sound card.

lspci 

in a terminal will show it.

Also system>prefs>sound try the alsa and pulse audio and test a couple.

I assume you're using Hardy.

---

### Post by Pasty-Flawss on 2008-07-14
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
06:00.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
06:00.1 Generic system peripheral [0805]: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
06:00.2 FLASH memory: ENE Technology Inc Unknown device 0720
06:00.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller

---

### Post by ChildOfMana on 2008-07-14
Just out of curiosity, what kernel are you using?

I only ask because I recently lost all sound after installing a kernel module when trying to get VirtualBox working.

Turns out it'd replaced the default kernel in my Grub menu with the new one - which, for whatever reason, didn't support sound (the offending kernel was 2.6.24-18-386).

All I had to do was edit my Grub menu to boot into the original kernel (which was 2.6.24-18-generic at the time) and all was fine again.

This may have no bearing at all on your particular problem but I thought it was worth a mention just in case. And anyway, you'll at least get a bump out of it :)

---

### Post by Pasty-Flawss on 2008-07-14
im a complete noob at linux i dont even know what kernel is.. i think its gutsy if that makes sense? isnt there a command to check your kernal?

---

### Post by BGFG on 2008-07-14
Hey have you checked to make sure all your devices are turned up full ? I know it sounds simple but it's actually important.
Open your volume control and check...

---

### Post by Pasty-Flawss on 2008-07-14
thats my problem alsamixer isnt working

---

### Post by BGFG on 2008-07-14
Alsa mixer was a package i also installed. but try the regular volume control. you know, from the panel....(not trying to sound sarcastic or anything :) )
Was your sound working before ?

---

### Post by ChildOfMana on 2008-07-14
[QUOTE="Pasty-Flawss"]im a complete noob at linux i dont even know what kernel is.. i think its gutsy if that makes sense? isnt there a command to check your kernal?[/QUOTE]

To find out what kernel version you're using type:

> uname -r

in to a terminal.

But to be honest I don't think this is your problem now that I've read the above posts.

Sorry for any confusion.

---

### Post by Pasty-Flawss on 2008-07-14
no it wasnt and by the normal volume one  do you mean System > prefrences > sound? because that doesnt work

---

### Post by Pasty-Flawss on 2008-07-14
my kernel is 2.6.22-15-generic

---

### Post by kansasnoob on 2008-07-14
Well I pretty much spilled everything I know about sound in this thread:

[http://ubuntuforums.org/showthread.php?t=855544](http://ubuntuforums.org/showthread.php?t=855544)

I really do prefer Gnome Alsa Mixer.

---

### Post by kansasnoob on 2008-07-14
> **Pasty-Flawss said:**
> my kernel is 2.6.22-15-generic

Is that Gutsy?

My Hardy is 2.6.24-19-generic.

If so ignore all the Pulse Audio stuff in my previous post.

---

### Post by Pasty-Flawss on 2008-07-14
yeah it is gutsy and there is no pulse audio :P

---

### Post by BGFG on 2008-07-14
Sorry, I've been in a hardy frame of mind also...
Purge and Re-install :) ?

---

### Post by Pasty-Flawss on 2008-07-14
> **BGFG said:**
> Sorry, I've been in a hardy frame of mind also...
Purge and Re-install :) ?

what does that mean and how do i do that? (sorry im a newbie)

---

### Post by BGFG on 2008-07-14
Just to be sure, you're using gutsy gibbon and not hardy heron right ?

basically

```
sudo apt-get purge '*package*'
``` completely removes a package

so that you may then reinstall it and hopefully fix your situation. 

But i hope kansasnoob and ChildOfMana have better alternatives

---

### Post by Pasty-Flawss on 2008-07-14
i purged and reinstalled gnome-aslamixer and it is now working however i toggled volumes but sound is still not working  im not sure what im doing what should gnome alsamixer settings bet set to?

---

### Post by Pasty-Flawss on 2008-07-14
also now when i open alsamixer it comes up with error:

alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by BGFG on 2008-07-14
I basically have everything in ALSAMIXER turned up to the max (tried to post a screenshot but it's taking forever). Sorry if you posted this already but What is your sound hardware ? onboard or card ?

---

### Post by Pasty-Flawss on 2008-07-14
well i restarted computer and its completely screwed now. i think i did something or uninstalled something and on reboot it completely got rid of it because now it cant detect any sound drivers and i cant even turn the volune up or down. (i could before even though there was no sound) any idea what to do now or have i screwed it completely?

---

### Post by Pasty-Flawss on 2008-07-14
im using gutsy at the moment do you think if i upgrade to the latest ubuntu do you think sound might work? and is it a lot better than gutsy?

---

### Post by BGFG on 2008-07-14
I'd definitely recommend upgrade. but before you do i went back in the thread and noticed you have intel sound.
You could check this:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Also, if you do end up upgrading remember to do you research, so your transition is smooth. Hope the link helps man....

---

