---
title: "How do I install a Philips SPC520NC Webcam"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Healey on 2008-06-22
Hi

I recently purchased a Philips SPC520NC Webcam

The reason I I bought this one, was because according to this wiki
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

It should "Works nice out of the box" with Hardy and Skype - So I thought I could not go wrong with this webcam as it has already been tested.

After connecting the webcam to my PC and running skype I find that the video works on the  > Video Devices > Test 

However after selecting "USB Video Camera" from the Sound devices menu - It fails the "Make a test call"  ie I cannot hear my voice played back.

So I am able to get video but not sound in Skype ver 2

I tried Ekiga and it hangs on the sound test and Video is green

I tried Easycam2 and it says Webcam is not compatible

I tried Easycam and it finds the camera on a list but fails to install

I tried Cheese and am able to take a picture of myself

I tried it in win XP and skype and it works well ( I hated that test  !)

I pasted lsusb into a terminal and got:-

Bus 002 Device 002: ID 0471:0334 Philips 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

I have tried Google but cannot find any infomation that helps me

Is the above wiki wrong ???

Does anybody know how to get this webcam working

Thanks in advance
Healey

---

### Post by TeoBigusGeekus on 2008-06-22
Type 
```
alsamixer
``` 
in a terminal and press the right button (->) until you go to the mic bar. See if the mic level is high - if not, raise it pressing the up button and then redo the skype test.

---

### Post by Healey on 2008-06-22
Hi 
Thanks for the reply

I forgot to mention that I have tried alsamixer already and it did not help

I have just tried it again   -  and again it did not help

Any other ideas

Thanks
Healey

---

### Post by Healey on 2008-06-23
Hi

Is there really no way to get this webcam working ????

The Philips SPC520NC is supposed to work "Out of the box" according to this page

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

Please can someone help with this problem

Thanks

Healey

---

### Post by Healey on 2008-06-24
Hi 
OK so nobody knows !

I have googled and googled and have found some info about another cam which uses the same driver and gives the same fault (Video ok but no sound in skype)

This is the interesting bit from a page I found:

"Starting at version 2.6.22, the Linux kernel includes a USB audio bug fix which triggers a bug in first and second generation Logitech Webcams. Fortunately this one seems to have a workaround, although not a pretty one. 

The webcam audio interface must be initialised before the video interface. Linux will by default initialise the video interface first, so you need to remove the uvcvideo.ko module from the /lib/modules subdirectory where it gets loaded automatically, and load it manually after plugging the webcam. 

A more convenient workaround on openSUSE (and maybe other distros too)
Just add the following line to your /etc/modprobe.conf.local : 

  uvcvideo install / sbin / modprobe snd_usb_audio; / sbin / modprobe - ignore-install uvcvideo

    * If you have to reset you cam for any reason, do:
         1. unplug your cam unplug your cam
         2. modprobe -r uvcvideo modprobe-r uvcvideo
         3. modprobe -r snd_usb_audio modprobe-r snd_usb_audio
         4. replug your cam replug your cam 
          o (not sure if step 1 and 4 are really necessary, or if 2 and 3 would be sufficient) (not sure if step 1 and 4 are really necessary, or if 2 and 3 would be sufficient) "

I am not sure if this would help in my situation but I would like to try!!

The problem is that the instructions are written for openSUSE and I am using Ubuntu Hardy.

So can anybody translate the above instructions into an easily unsderstood text for Ubuntu ???  I have already looked into it, but stoppped when I realised that Ubunto does not have a modprobe.conf.local   !!!!!!

OR is there a simpler way to change the order that the video and audio is loaded

I would really like to get this cam working as it SHOULD work out of the box, according to somebody who has not come forward yet !!
Ref [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

Just as a little extra info I have tried this cam on another machine running Hardy which has different hardware and it shows the same fault

Please help !!

Thanks

Healey

---

### Post by Healey on 2008-06-25
Hi

OK then I guess I have no choice but to give up on this camera

At best I suppose I have to say that the following site has some unreliable info
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

Be careful if you are using it to buy equipment - Do more searches first !!

Regards

Healey

---

### Post by Pottedmeat on 2008-07-08
Based on the advice on the list you mentioned, I also bought this camera. I have exactly the same problem you do. Video, no sound. Grrrh. I now have to purchase a mic too, but with no guarantee that it will work either.

With Ubuntu becoming more popular, it would be marvellous if there was some kind of licensing standard for hardware that would run on Ubuntu systems.

---

### Post by Healey on 2008-07-18
Hi Pottedmeat

Yes - Its a great shame that this has happened - When I read the list of cameras that work, I was very confident that I was reading accurate infomation - How wrong I was - I have tried everything I can to get it to work but I have failed !!

It also makes you wonder about the next list of hardware you read !!!

Maybe if the author of that list sees this thread, then he/she will reply

If you do find a solution to this - PLEASE post the solution - I will of course do the same.

I am sorry you did not see this thread in time before you bought that camera !!

Regards

Healey

---

### Post by GangOfOne on 2008-07-23
Hi Healey

I had the same problem with you and Pottedmeat but also Cheese refused to work at all with this camera.  I spent the best part of two days fiddling with different things according to suggestions here and in other forums.  I finally noticed two things: 1) my microphone's volume on alsamixer was zero, although the mic was not muted and 2) the gspca driver wasn't being loaded (*lsmod | grep gspca*). 

I fixed (1) by making sure my mic's volume control icon is maxed-up each time I boot-up and (2) by adding the line 'gspca' at the end of the modules file (*sudo gedit /etc/modules*).  Now both video and sound on Skype works a treat, even better than on my Win XP boot (get fuzzy audio when video comes on).  Cheese still refuses to work but that's no great loss to me, to be honest.

I don't know if these two things were the sole culprits for the sound not working or if there was a cumulative effect from all the other stuff I tried but it might be worth a try if you downloaded and built the gspca driver, added it to your modules file and made sure your mic channel was unmuted and at full volume.

---

### Post by Healey on 2008-07-30
Hi GangOfOne

Many thanks for your reply - Sorry for my late reply I have been busy

I wonder if you could explain how to download and install the gspca driver ??

Also how can I check that its not installed already ??

Thanks in advance

Healey

---

### Post by GangOfOne on 2008-08-04
You can check if the gspca driver is loaded by starting a terminal as root (*$ sudo bash*) and type:
[I]
# lsmod | grep gspca.[/I]

If the text 'gspca' doesn't appear on the left column then:

1) download the source code:   [from here]("http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz") ( assuming your kernel is 2.6.11 and above - if you're running Ubuntu 7.10 or higher you're fine)
2) Extract the archive folder
3) Still on the root terminal, go to gspcav1 directory and run:

*# ./gspca_build *

if all goes well the module should be compiled and loaded in memory. For some reason mine didn't, so I had to add the line 'gspca' at the end of the modules file (*sudo gedit /etc/modules*) and reboot.

Good luck, let us know how it goes.

---

### Post by Healey on 2008-08-05
Hi

Thanks for the reply - This is the result of 
lsmod | grep gspca

gspca                 643920  0 
videodev               29440  2 gspca,uvcvideo
usbcore               146028  8 gspca,uvcvideo,usblp,snd_usb_audio,snd_usb_lib,ehci_hcd,ohci_hcd


So I assume that gspca is already installed - would that be correct?

Thanks 

Healey

---

### Post by GangOfOne on 2008-08-05
> **Healey said:**
> Hi

Thanks for the reply - This is the result of 
lsmod | grep gspca

gspca                 643920  0 
videodev               29440  2 gspca,uvcvideo
usbcore               146028  8 gspca,uvcvideo,usblp,snd_usb_audio,snd_usb_lib,ehci_hcd,ohci_hcd


So I assume that gspca is already installed - would that be correct?

Thanks 

Healey
yes that 's fine, looks remarkably like my own listing, it means gspca is already loaded.

Make sure your mic is not muted and maxed-up (alsamixer) and try Skype again.

---

### Post by Healey on 2008-08-07
Hi

Thanks for the reply

Well I have tried skype a few times and I still get the same result - Video ok but no sound

The mic is not muted - I have checked and double checked

Looks like it just wont work - Except in windows of course !!!

Thanks for your help

Healey

---

### Post by GangOfOne on 2008-08-07
Sorry to hear you didn't get a result, don't know what else to suggest (other than buy a different webcam perhaps).  I don't know why mine works and yours doesn't. I'm a Ubuntu noobie so it was probably beginner's luck I guess.

---

### Post by Healey on 2008-08-08
Hi

Hey no problem - I will give it another try when the next ubuntu version comes out

Thanks for your help

Healey

---

