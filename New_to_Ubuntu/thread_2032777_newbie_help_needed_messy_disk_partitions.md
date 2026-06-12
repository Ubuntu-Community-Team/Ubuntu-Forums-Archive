---
title: "newbie help needed: messy disk partitions"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by Damsonjam on 2012-07-24
I've been using ubuntu for quite a while to revitalise an old Windows laptop.. but the hard disk has now got to be a bit of a mess, to the point where it was hard for me to find enough space to install the latest updates..
I've completely lost track of which versions are where...really want to use this laptop exclusively for 10.4, so I'm not worried about losing data/destroying previous installations..
Can anyone decipher the attached screenshot and suggest a way of adjusting things such that I can maximise the space available and be free apply updates?

---

### Post by ratcheer on 2012-07-24
First, you have several swap partitions. You only need one. Depending on your amount of RAM, it could be 2 times your RAM up to a maximum of, say, 4 GB. Try deleting all your swap partitions except one and showing us what you have after that.

However, the picture you posted does not seem to show your entire drive.

Tim

---

### Post by Bufeu on 2012-07-24
Can you paste a screenshot from GParted?

---

### Post by Damsonjam on 2012-07-24
many thanks for looking at this..
attached is the screenshot from gparted

---

### Post by westie457 on 2012-07-24
If you have no objection to completely wiping the hard drive and reinstalling from scratch is probably the easiest way to go.

In Gparted click on 'Device' in the menu bar and then click 'new'. This will write a new partition table destroying info about all of the others. Leave the drive unformatted. Reboot using your LiveCD/USB. Let the installer decide which partitions to create.

IMHO this will be quicker than trying to decide which partitions to keep and which to get rid of.


Edit.... Forgot to mention that you will need to click on 'Apply' and agree to the default suggestions in any pop up windows.

---

### Post by Bufeu on 2012-07-24
> **westie457 said:**
> If you have no objection to completely wiping the hard drive and reinstalling from scratch is probably the easiest way to go.

In Gparted click on 'Device' in the menu bar and then click 'new'. This will write a new partition table destroying info about all of the others. Leave the drive unformatted. Reboot using your LiveCD/USB. Let the installer decide which partitions to create.

IMHO this will be quicker than trying to decide which partitions to keep and which to get rid of.Needlessly, it's very easy to mount the partitions and backup the data before reformatting.

---

### Post by Ubun2to on 2012-07-24
> **Damsonjam said:**
> many thanks for looking at this..
attached is the screenshot from gparted

Four swap partitions? Might as well wipe the drive and start over to avoid confusion. Make sure you backup your data as well.

---

### Post by Damsonjam on 2012-07-25
> **Bufeu said:**
> Needlessly, it's very easy to mount the partitions and backup the data before reformatting.

Thanks for this

So this means I can mount each partition in turn, back it up then reformat that partition?

And I should do this for each of the following because they are no longer in use:
sda10
sda11
sda6
sda7
sda5

sda2, sda8, sda9 are the currently used partitions?

should I delete them and create a single (FAT?) partition?

I supposes my next question is whether I can (easily) take advantage of that partition until I get around to doing a rebuild?

(I appreciate the general sentiment that has been expressed to 'start again' and I probably will at some future point but I'm wondering what I can do in the meantime)

---

### Post by Bufeu on 2012-07-25
Backup all data, then do as westie457 said.

EDIT: To answer your question; yes, mount it and backup the data you want to keep.

---

### Post by techvish81 on 2012-07-25
backup important data and just run and boot the installation disk/usb  , if you don't  need different partitions,  just select ' erase disc and install ' option.  it will take care of everything.

it is the easiest way.

---

