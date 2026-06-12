---
title: "Logitec USB headset"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-04-27
Hi
I have a Logitec USB headset and I having issues using it with Ubuntu.  Are there any drivers that I can install?

---

### Post by Nero_Flint on 2009-06-27
From what I understand USB headsets have their own drivers. I don't use a USB headset so I can't help to fix the problem but hopefully someone else can help out.

---

### Post by ncc1701e on 2009-07-02
I've also got a Logitech USB headset which is detected upon connect but I can't seem to declare it as the device to use. I'll investigate further and see if I can put up my error messages for further analysis.

---

### Post by khelben1979 on 2009-07-02
> **saskatchewan said:**
> Hi
I have a Logitec USB headset and I having issues using it with Ubuntu.  Are there any drivers that I can install?

What exact model is it?

---

### Post by austinpsycho on 2009-07-02
Does it show up in Isusb? if so my solution was to uninstall pulse audio(which commonly breaks alsa) and if that helps *but only marginally, like some programs can use the headset while others still use the speakers, and i suspect this is the case, update your alsa driver to 1.0.20

---

### Post by ncc1701e on 2009-07-02
I do not know my exactly model but it is a USB Logitech headset with microphone. Here is 
the output of the system log when I plug it into my computer.

___________________________________________________________
Jul  2 15:38:21 GamingPCUbuntu kernel: [20737.443447] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.3/input/input8
Jul  2 15:38:21 GamingPCUbuntu kernel: [20737.468603] generic-usb 0003:046D:0A02.0003: input,hidraw1: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:0b.0-6/input3
Jul  2 15:38:21 GamingPCUbuntu pulseaudio[3255]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Jul  2 15:38:21 GamingPCUbuntu pulseaudio[3255]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Jul  2 15:38:36 GamingPCUbuntu kernel: [20752.928010] usb 2-5: new full speed USB device using ohci_hcd and address 9
Jul  2 15:38:37 GamingPCUbuntu kernel: [20753.149293] usb 2-5: configuration #1 chosen from 1 choice
______________________________________________________

Any ideas what this means?

---

### Post by austinpsycho on 2009-07-04
if you go into sound options *under system;preferences; sound* can you select your usb under any of the options? where it says default you should beable to select a device. it should say usb headset(alsa) or something of the sort.  If you can select it; then go into your synaptic package manager (in system;administration;synaptic package manager)
and search for pulseaudio.  click it and hit complete removal. then accept *it will tell you its going to uninstall ubuntu desktop; that's ok.. don't get too worried ;)*  
Reset and this should make your headset operate in most programs..  Then go to terminal and type *asoundconf list* and post the results here

---

### Post by earthpigg on 2009-07-04
im going to suggest something simple, if you havent already tried it. it will either work or it will at least remove one possibility and narrow down the problem a bit:

click on the volume thingie in the upper right, and select volume control. play around with those settings a bit. make sure you click 'preferences' and add some of that stuff.

a lot of these sound inputs are muted or turned all the way down by default.

---

### Post by kostkon on 2009-07-04
Install the *PulseAudio Device Chooser* utility (using *Synaptic*).

For more info you can check [here]("http://ubuntuforums.org/showthread.php?t=1130384"), for example.

---

