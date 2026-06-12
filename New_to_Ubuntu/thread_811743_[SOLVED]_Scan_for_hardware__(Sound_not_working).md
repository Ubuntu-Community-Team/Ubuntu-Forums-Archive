---
title: "[SOLVED] Scan for hardware?  (Sound not working)"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by timandjulz on 2008-05-29
Hi all,

I removed a package that somehow killed the sound.  I cannot find a way to check what the problem is.  Windows lets you scan for hardware.  So if you remove a driver, you can scan and re-install the driver.

So three questions:
1) Does Ubuntu have a way to show me the list of hardware that doesn't have a driver associated?
2) Does Ubuntu have a way to say "Install the driver for this hardware" without having to go through a manual process?  i.e. without having to lspci, figure out what driver works with the hardware, install the package, troubleshoot, rinse and repeat.
3) Finally... how can I get my sound working?  Intel 82801I (ICH9 Family)

Thanks,
Tim

---

### Post by cmnorton on 2008-05-29
lsmod

and cat /proc/devices 

will provide you some information.

What package did you remove?

---

### Post by Xerp on 2008-05-29
lshw - list hardware :)

Drivers work a little differently in Linux than in Windows. For example, the Windows kernel itself doesn't support very much at all - hence having to download a driver from the device manufacturer. The Linux kernel handles thousands of devices, automatically loading the required module (meaning you don't have to download a driver). Nice.

As you had sound working, removed software and then sound stopped, your easiest way back is to re-install the package you removed. For sound, it might have been something like Pulse Audio.

---

### Post by drs305 on 2008-05-29
To tag on to what Xerp posted, you can get a nice html file with your hardware listing using the following command. It has a few drivers listed but not version numbers or probably what you are looking for in this particular thread:

```
sudo lshw -html > **~/Desktop/hardwarelist.html**
```

Of course, you can select any location and name for the output.

---

### Post by timandjulz on 2008-05-29
I have no idea what the package was I removed.  I was following instructions on a web page and can't find it.  Thanks to Linux being so stable, I didn't have to reboot for a week.  :-)

Xerp, lshw is great.  Thanks for the tip.

        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0

I searched Synaptic for "82801I" and "ICH9" and couldn't find anything.  What the heck?  :confused:

Tim

---

### Post by Nepherte on 2008-05-29
Ok, your card is already recognized by ubuntu.That's a start for sure :)

Since you said you removed a package that broke your sound, see if the following package, alsa-base, is installed.
```
aptitude search alsa-base
```
Alsa is typically the package that handles sound. An 'i' as first character denotes it is installed, 'p' means that the package is not installed. Other flags are possible as well, so if it is something else, be sure to post it here.

---

### Post by timandjulz on 2008-05-29
alsa-base is installed.  For grins I reinstalled but no good.

More information: When I run sound properties (gnome-sound-properties) it gives me the following error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.


AGGG!!! I hope to get more than just a solution.  How the heck do you troubleshoot this type of problem?

Thanks,
Tim

---

### Post by Xerp on 2008-05-29
Just a quick test - can you reboot and test sound again? (as it sounds like the audio device is maybe locked? Tricky as I've never had a problem with sound :)

Also, under System->Sound check "Device," and see if your sound card is selected. Try chaning "Sound playback" (eg. OSS / ALSA).

---

### Post by BDNiner on 2008-05-29
I have not had good luck when hardware shows up as UNCLAIMED. Same thing happened to my network card and it turned out that the ROM chip burnt out and i had to replace it. this may not be the case for you. good luck.

---

### Post by timandjulz on 2008-05-29
> **Xerp said:**
> Just a quick test - can you reboot and test sound again? (as it sounds like the audio device is maybe locked? Tricky as I've never had a problem with sound :)

Also, under System->Sound check "Device," and see if your sound card is selected. Try chaning "Sound playback" (eg. OSS / ALSA).

I rebooted.  Same thing.

I tried different options in the sound configuration.  I get the same error reported previously.

Here are two interesting things.  First, there is no sound adapter listed for "Default mixer tracks" in the sound configuration.  And secondly, I tried forcing alsa to reload and got the following errors.

```
sudo alsa force-reload

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

```

---

### Post by timandjulz on 2008-05-29
BINGO!  I am close!

Just before I had these problems, I accepted Ubuntu updates for a new kernel.  I can only find snd-* modules in /lib/modules/2.6.24-16-generic.  They do NOT exist in /lib/modules/2.6.24-17-generic

How do I get the new modules and rebuild the modules list?

Getting close.  Thanks for everyone's help!
Tim

---

### Post by timandjulz on 2008-05-30
bump

---

### Post by kansasnoob on 2008-05-30
This may be an ignorant suggestion, but it's pretty easy and can't harm anything.

Open Synaptic and click on reload. When it's done running see if it shows any broken packages or upgrades.

---

### Post by timandjulz on 2008-05-30
Been there done that kansasnoob.

But I have a solution.  Don't use kernel 2.6.24-17.  I switched back to 2.6.24-16 and sound has returned.  :-)

THANKS TO EVERYONE FOR THEIR HELP!

---

