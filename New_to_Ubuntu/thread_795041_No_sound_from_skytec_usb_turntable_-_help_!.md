---
title: "No sound from skytec usb turntable - help !"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by philinux on 2008-05-15
Got sound from all other sources.

Got audacity seems set ok.

Birthday present from my kids.

---

### Post by nicedude on 2008-05-15
Hey phil I know nothing about USB turntables but my first thought is what is the result of lsusb command with the device plugged in? You can also update your USB device list with command below. I also included the PCI update command as I just found them the other day so I don't know if you know you can do this. You might update your USB lists and then run lsusb and post back here.
 

Update your PCI known device list 

sudo update-pciids

Update for USB known device list

sudo update-usbids

If armed with that knowledge I can't help solve it I am sure someone can :-)

---

### Post by philinux on 2008-05-15
Ok progress as such. I selected my usb turntable from the recording selection list. Use my onboard soundcard for the playback, choose start monitoring. I get gibberish noise. vu meters are working though.

---

### Post by nicedude on 2008-05-15
Phil is the device in question a CITRONIC AC-1 USB. If so then this device works with Ubuntu here is a link to a post from a guy who got his working

[http://ubuntuforums.org/showthread.php?t=497649](http://ubuntuforums.org/showthread.php?t=497649)

If you have a diferent model please state it and I will try to help you more. and in a terminal you might run the command lsusb ( lists your USB devices that are currently detected in your PC ) and see if citronic anything shows up, since that would mean its being detected and will probably work.

---

### Post by philinux on 2008-05-15
It's a tec-3100. Shows up as usb audio codec in audacity

like I said i can get some sound but its very garbled.

Bus 006 Device 004: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec

---

### Post by nicedude on 2008-05-15
Try running the command I gave you in post #2 that will update your USB device lists and then run lsusb again and see if it changes. If not and it isn't correctly recognized then it may spell bad news. I see no tec-3100 ubuntu google links claiming fixes or working setups, I also don't see any claiming its a no go either so ? You might try reading the link above as well since that guy told what he set to get his to work with audacity and maybe it will work for you as well.

Good luck Phil

---

### Post by philinux on 2008-05-15
Ok update, I've got recording device set to usb codec as my manual tell me. If I choose my audio card playback and select start monitoring I get garbled noise. If i choose alsa front or usb codec as playback device it works but only in record mode with no sound If I then change my playback to my sound card and hit play it plays the recoding perfectly.

There must be a problem with pulse audio or alsa.

Audacity keeps crashing and needs a full system reboot to work again

---

