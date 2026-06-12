---
title: "Wireless USB 11.10 Not Recognising"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by BaftDrush on 2011-11-07
Hello all, thanks for having a wee look.

I'm pretty much a Linux virgin and having installed Ubuntu 11.10 from USB stick to a new build machine with no OS everything's working aside from the USB wireless dongle.

I've attached the machine to a wired network and downloaded all updates.

I've ran lsusb and there's nothing there, it's as if the PC doesn't know it's there.

I do have Linux drivers on the CD that comes with the wireless USB but I've no idea how to install drivers for a device I cannot locate!

How do I install the Linux drivers from the installation CD?

Thanks,

Rob.

---

### Post by Ricx94 on 2011-11-07
it should see the wireless dongle no matter what...i think that may mean the wireless usb is broken...not sure, but i think so

---

### Post by grahammechanical on 2011-11-07
You say it a new build. I also built my own machine. You may need to set things up in the BIOS. Under the BIOS Main tab I had Legacy Diskette A enabled. When I disabled that I then got USB configuration options in the Advanced tab.

I was testing a newly created Live Ubuntu USB memory stick and I could not get the boot order changed to boot from USB until I played around the USB settings in the BIOS.

You are trying to do something different but you may also need to play around with the USB settings in the BIOS.

Regards.

---

### Post by BaftDrush on 2011-11-07
Here's what I get from lsusb:

robert@robert-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. 
Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 002: ID 1ea7:0002

I think the Ralink is it - wonder how I install driver to it then?

I installed Ubuntu using USB so I reckon the BIOS USB settings are ok?

Any help is greatly appreciated.

Rob

---

### Post by gandaran on 2011-11-07
> Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. 
this is the adapter, I'll try to find out which chipset it has
but paste the output of
```
lsmod
```
just to check if any ralink driver is loaded.

---

### Post by BaftDrush on 2011-11-07
Thanks, here's the output:

robert@robert-PC:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
vesafb                 13489  1 
snd_hda_codec_hdmi     31426  1 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
snd_hda_codec_realtek   254125  1 
binfmt_misc            17292  1 
ppdev                  12849  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hda_intel          24262  3 
fglrx                2595570  149 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
k10temp                12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  2 snd_seq,snd_pcm
parport_pc             32114  1 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  1 
uas                    17699  0 
floppy                 60310  0 
forcedeth              58103  0 
pata_amd               13753  0 
sata_nv                23379  3

---

### Post by anewguy on 2011-11-07
Please read through the following post carefully.  Forget the device name specified - it's the usb manufacturer and device id (the xxxx:yyyy) that are important in this instance.  Please note you may need to follow a link from there to another post to fix some small errors.


[http://ubuntuforums.org/archive/index.php/t-1800178.html]("http://ubuntuforums.org/archive/index.php/t-1800178.html")

Post back after you've gone through that with any questions you may have.

Dave ;)

---

### Post by wildmanne39 on 2011-11-07
Hi anewguy, I researched this earlier and if you read to the bottom of that link you posted chili555 ended up telling him to take it back and get another one. The usb adapters that use the 5390 are not hard to get to work but I have not seen this adapter working yet.
Thank you

---

### Post by anewguy on 2011-11-08
> **wildmanne39 said:**
> Hi anewguy, I researched this earlier and if you read to the bottom of that link you posted chili555 ended up telling him to take it back and get another one. The usb adapters that use the 5390 are not hard to get to work but I have not seen this adapter working yet.
Thank you

I think you misread it: > It beats the answer you get on other forums and IRC: "Take it back and get a supported device." 

Didn't know there was a problem - I've gotten these to work before and I thought it was following that thread plus the info pointed to in the 8th post down -> changing a couple of names in the source files. There is a link there but it wasn't created as a link in the post so the "http://....." info is imbedded in the post.  Maybe I'm remembering wrong, but I thought this was the procedure used before.  And it is a 5370 according to the device id.

Oh well - doesn't make much difference to me as long as someone can get it working for the OP.

Thanks for the info.

Dave ;)

---

### Post by BaftDrush on 2011-11-08
Hi guys, thanks again for the assistance, I'll try it out when I get home tonight.

I've also now got in my possession a PCI Tenda Wireless N adaptor with Ralink RT3062F chipset by looks of it - wonder if this would be more "friendly"?

Rob.

---

### Post by BaftDrush on 2011-11-08
> **anewguy said:**
> Please read through the following post carefully.  Forget the device name specified - it's the usb manufacturer and device id (the xxxx:yyyy) that are important in this instance.  Please note you may need to follow a link from there to another post to fix some small errors.


[http://ubuntuforums.org/archive/index.php/t-1800178.html]("http://ubuntuforums.org/archive/index.php/t-1800178.html")

Post back after you've gone through that with any questions you may have.

Dave ;)

Nevermind. This is gay. <----- LOL, nice to be so appreciative :D

---

### Post by wildmanne39 on 2011-11-08
Hi, this is the link that anewguy was referring to and it has directions for making it work but I was not sure that it did or not because as you saw the guy working with it quit.
[http://ubuntuforums.org/showthread.php?t=1800178](http://ubuntuforums.org/showthread.php?t=1800178)

Directions are in post 4.
I am going to let anewguy help with this since he started here first and I was never sure about it working.
Thank you

---

### Post by BaftDrush on 2011-11-08
Everything ok until 

cd Desktop/2011

root@robert-PC:/home/robert/Desktop# cd Desktop/2011
bash: cd: Desktop/2011: No such file or directory

I've got a new PCI wireless card:

01:08.0 Network controller: Ralink corp. Device 3062

I think I'd rather try and install that as it's not USB and is 300M opposed to 150M. 

Any ideas?

---

### Post by BaftDrush on 2011-11-08
I followed Chilli's advice in this post: [http://ubuntuforums.org/showthread.php?t=1674202](http://ubuntuforums.org/showthread.php?t=1674202)

for the wireless PCI card and hey presto, I'm wireless at 130Mbps!

Thanks for all the help guys.

---

### Post by wildmanne39 on 2011-11-08
Hi, I am glad you have wireless working.

---

