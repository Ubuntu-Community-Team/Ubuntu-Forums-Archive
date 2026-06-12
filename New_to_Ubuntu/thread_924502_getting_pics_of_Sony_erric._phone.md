---
title: "getting pics of Sony erric. phone"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by driscom59 on 2008-09-19
How can I get some pics and a video of my sony erricson phone and onto the computer?  In the old days (windows) I just went into "right click then explore" and went from there. Is there a way to do the same in Ubuntu?

---

### Post by Delirium_Trigger on 2008-09-19
It doesn't show up under Places on your panel?
If so you can just click on it and it'll mount itself.

---

### Post by bobnutfield on 2008-09-19
Not familiar with the phone, but if it connects via USB, Ubuntu usually treats it as mass storage and you can just drag and drop.  Or, you could connect via Bluetooth to transfer the files if the phone and computer support it.

---

### Post by driscom59 on 2008-09-19
Thanks. It connects via USB although when I plug it in and turn it on nothing happens.  I am guessing that the computer is not recognizing it as a mass storage device, as with other things that I plug in. Where to from here? I don't have bluetooth installed on the computer

---

### Post by Gost-Taras on 2008-09-19
On linux you can only send files from your phone to you pc or visa versa trhough bluetooth, usb doesnt work, becouse it doenst recognise it *** storage device,

u need bluetothe

u can stop trying to send or recive files with usb on ubuntu it wouldnt work

sorry

---

### Post by acidsolution on 2008-09-19
before it used to recognise as mass storage for me 
but once i installed ubuntu desktop theme it dont automatically mount it.
 :( any help ??
i have sony ericsson k510i

---

### Post by bobnutfield on 2008-09-19
> **Gost-Taras said:**
> On linux you can only send files from your phone to you pc or visa versa trhough bluetooth, usb doesnt work, becouse it doenst recognise it *** storage device,

u need bluetothe

u can stop trying to send or recive files with usb on ubuntu it wouldnt work

sorry

Sorry, but it works just fine on my Nokia N95 via USB.  It does treat it as mass storage and I just drag and drop.

to the OP:  With the phone pluggin in via USB, open a terminal and type:

> lsusb

The output will tell you if Ubuntu is recognizing the phone.

---

### Post by Gost-Taras on 2008-09-19
U lucky then couse i have Motorola Razor V8 and it doesnt recongise anything

---

### Post by driscom59 on 2008-09-19
Thanks - I'm really new to this, but it recognizes my camera and ipod as a mass storage device????  Why not the phone???

---

### Post by bobnutfield on 2008-09-19
One further note.  Ubuntu will have trouble with recognizing your SIM card, but if you have a storage card in the phone, move your photos to it and it should be recognized.

---

### Post by driscom59 on 2008-09-19
Thanks Bob - don't know what happened but I just plugged it inand it went to FSpot and opened eveything up.  Had not worked on the previous 2 attempts. I'll see how it goes in the future.

---

