---
title: "help in using virtualbox USB support"
date: 2011-10-23
forum: Philippine Team
---

### Post by gerryb23 on 2011-10-23
I recently installed ubuntu 11.10 and also tried installing virtualbox from the ubuntu repository.I downloaded the usb support of the same release of virtualbox 4.1.something...(limutan ko) hehe.but still virtualbox doesnt recognize my flashdisks?nakalagay parati sa USB--no usb something something...ayun.patulong lang po :)

---

### Post by haqking on 2011-10-23
> **gerryb23 said:**
> I recently installed ubuntu 11.10 and also tried installing virtualbox from the ubuntu repository.I downloaded the usb support of the same release of virtualbox 4.1.something...(limutan ko) hehe.but still virtualbox doesnt recognize my flashdisks?nakalagay parati sa USB--no usb something something...ayun.patulong lang po :)

First of all the repo version is out of date, download the latest which is 4.1.4

add the extensions pack also for best USB support.

You also need to check your user account is in the vboxusers group, if not then 
```

sudo usermod -a -G vboxusers username
```

The when you add your USB device, you also need to choose it from the devices menu in Virtual Box

You also need to log out and back in for the vboxusers info to take effect

---

### Post by jepong on 2011-10-25
+1 haqking

---

### Post by zeroseven0183 on 2011-10-25
Hi Gerry, were you able to use the one from Virtualbox.org? I suggest you install the PUEL version instead of the one in the repositories. If I'm not mistaken, once you plug the USB drive, the host OS mounts it automatically. So you have to unmount it so the VM can detect it.

---

### Post by jepong on 2011-10-25
no no no... you need to register the device first before it get detected.

---

### Post by JCyberinux on 2011-10-28
hmm.. in my case i haven't arrived any concern on usb with virtual box, i just let it detected by the vbox. :D choose what usb to used. or just did the old trick unplug and plug it. :D

---

### Post by vhinz on 2011-10-28
hi..not sure on 11.10 but used PUEL version on 10.04 (+1 zeroseven0183).  By default, the 10.04 repo uses the OSE.  Try installing the PUEL version which is free for personal and/or evaluation.

---

### Post by gerryb23 on 2011-11-05
> **haqking said:**
> First of all the repo version is out of date, download the latest which is 4.1.4

add the extensions pack also for best USB support.

You also need to check your user account is in the vboxusers group, if not then 
```

sudo usermod -a -G vboxusers username
```

The when you add your USB device, you also need to choose it from the devices menu in Virtual Box

You also need to log out and back in for the vboxusers info to take effect

Sir, how do i log in and out of the vboxusers? I tried to do this by typing sudo usermod -a -G vboxusers username in the terminal window, but when i tried running virtual box this message appears:

Failed to access the USB subsystem

VirtualBos is not currently allowed to access USB devices. You can change this by adding your user to the 'vboxusers' group...

I already installed the extension pack too. Thanks.

---

### Post by haqking on 2011-11-05
> **gerryb23 said:**
> Sir, how do i log in and out of the vboxusers? I tried to do this by typing sudo usermod -a -G vboxusers username in the terminal window, but when i tried running virtual box this message appears:

Failed to access the USB subsystem

VirtualBos is not currently allowed to access USB devices. You can change this by adding your user to the 'vboxusers' group...

I already installed the extension pack too. Thanks.

i take it you replaced username with your actual login name right ?

example

```
sudo usermod -a -G vboxusers gerryb23
```

or whatever your computer login name is

all this command does is add your user account to that group (you dont log in with it) once you login as you the system will know you are in that group

and once you have done that you need to log out and back in

---

