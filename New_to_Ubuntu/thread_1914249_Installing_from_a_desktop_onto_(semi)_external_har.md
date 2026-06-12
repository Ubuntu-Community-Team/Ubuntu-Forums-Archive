---
title: "Installing from a desktop onto (semi) external harddrive."
date: 2012-01-24
forum: New to Ubuntu
---

### Post by blucalculatr on 2012-01-24
Okay, so, i have ubuntu properly installed on my desktop, and i had a version on my laptop which i accidentally screwed up. but cant be bothered fixing, backed up files, now i just want to reinstall. i dont have any blank CD's or USB's i can use, so i have my laptop's harddrive plugged into my desktop as an external harddrive. is it possible to install linux on the harddrive in such a way it'll just work when i put it back into the laptop?

---

### Post by carl4926 on 2012-01-24
I never tried this
But the hardware on your desktop is completely different to your laptop, so my guess is the laptop will 'spit dummy' when you try booting it.
But it would be nice to try it.

FYI: I would only have the laptop drive connected for the install

---

### Post by blucalculatr on 2012-01-24
okay, well could i put some files on the harddrive that can just make it boot, to reinstall itself? like, a liveUSB kind of thing on the harddrive?

---

### Post by carl4926 on 2012-01-24
> **blucalculatr said:**
> okay, well could i put some files on the harddrive that can just make it boot, to reinstall itself? like, a liveUSB kind of thing on the harddrive?
I'm not aware that there is anything like this that could be done.

I'm thinking out of the box now, so don't shoot me down if this sounds crazy.

You know how usb booting works?
So, could it be possible, if you made a say 2GB partition at the start of the laptop HD and then somehow try and create like a usb boot device on sda1.

You might find some sage advice in the IRC and it's generally much quicker too

---

### Post by blucalculatr on 2012-01-24
yeah, thats what i was thinking.

next question: how do i get onto IRC?

---

### Post by carl4926 on 2012-01-24
[http://www.ubuntu.com/support/community/chat](http://www.ubuntu.com/support/community/chat)
[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

Start xchat
connect to the freenode network
You can choose any username actually but xchat should open with you user login name
then join the channel #ubuntu

---

### Post by Fernhill Linux Project on 2012-01-24
One possible solution could be to create an extra 1gb bootable partition on the HDD, and use Unetbootin to install the live disc/iso in that partition. 
You should then be able to boot the laptop from the live partition and install Ubuntu to the another partition on the HDD.

---

### Post by Cheesemill on 2012-01-24
Just install Ubuntu as normal with your laptop drive as the only drive plugged into your PC.

Then just put it in your Laptop and boot. Simple.

I have moved an installed Ubuntu between several different hardware platforms before without any issues, just make sure you don't have any restricted drivers installed before you switch the hardware.

---

### Post by carl4926 on 2012-01-24
> **Cheesemill said:**
> Just install Ubuntu as normal with your laptop drive as the only drive plugged into your PC.

Then just put it in your Laptop and boot. Simple.

I have moved an installed Ubuntu between several different hardware platforms before without any issues, hust make sure you dont have any restricted drivers installed before you switch the hardware.

That's interesting

---

### Post by Cheesemill on 2012-01-24
> **carl4926 said:**
> That's interesting

Yep.

Unlike Windows which sets up a fixed hardware profile when you first install it, the Linux kernel automatically probes for hardware on each boot.

Obviously you cant boot a 64 bit install on 32 bit hardware, but apart from that there should be no problems.
If you are moving from Nvidia graphics to ATI or vice versa just make sure you uninstall the restricted drivers first.

---

