---
title: "Can I permanently mount a flash drive for backup?"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by jbuczek on 2012-02-14
I'm worried about my financial records including scans of every financial and ID document I have.  I'm sync'ing everything else to both Dropbox and UbuntuOne but the former had a major security flaw that opened EVERYTHING on it to the web for a while and the latter has no "in Cloud" encryption at all.

I'd like to put the documents in TrueCrypt and auto sync that container to a 16GB flash drive but remembering to plug in the flash each day cancels the benefits of "automatic" sync.  OTOH flash drives have a finite number of writes so if Ubuntu is logging, journaling or whatever frequently the drive is not going to last long.

So does Ubuntu do that?

Using Ubuntu 11.04 with Gnome and about to convert to Lubuntu 11.10.

To eliminate "why don't you just buy a USB HDD?" replies, I'm already doing a weekly sync of other stuff to the same Flash Drive. KISS, you know!

---

### Post by jailbait on 2012-02-14
> **jbuczek said:**
> I'm worried about my financial records including scans of every financial and ID document I have.  I'm sync'ing everything else to both Dropbox and UbuntuOne but the former had a major security flaw that opened EVERYTHING on it to the web for a while and the latter has no "in Cloud" encryption at all.

I'd like to put the documents in TrueCrypt and auto sync that container to a 16GB flash drive but remembering to plug in the flash each day cancels the benefits of "automatic" sync.  OTOH flash drives have a finite number of writes so if Ubuntu is logging, journaling or whatever frequently the drive is not going to last long.

So does Ubuntu do that?

Using Ubuntu 11.04 with Gnome and about to convert to Lubuntu 11.10.

To eliminate "why don't you just buy a USB HDD?" replies, I'm already doing a weekly sync of other stuff to the same Flash Drive. KISS, you know!
a) There are services such as bqbackup and rsync.net that offer secure encrypted backups. Their normally used for server backups and stuff, but they should be secure enough anyways.

b) If your so worried, why don't you encrypt the documents with gnupg?

c) You can use a UDEV rule to run a script when it is plugged in. [https://help.ubuntu.com/community/UsbDriveDoSomethingHowto](https://help.ubuntu.com/community/UsbDriveDoSomethingHowto)

---

### Post by jbuczek on 2012-02-16
Yes, I know I can set up scripts, etc. To give myself cross platform access to my info, I'm playing with TrueCrypt at the moment.

But that wasn't my question.

Maybe I got too wordy but my real question was:

   "Can I leave the pen drive plugged in 24/7 without Ubuntu beating the heck out of it with housekeeping writes?"

---

### Post by jailbait on 2012-02-17
> **jbuczek said:**
> Yes, I know I can set up scripts, etc. To give myself cross platform access to my info, I'm playing with TrueCrypt at the moment.

But that wasn't my question.

Maybe I got too wordy but my real question was:

   "Can I leave the pen drive plugged in 24/7 without Ubuntu beating the heck out of it with housekeeping writes?"
just use a cronjob to mount and unmount it.
when its unmounted, ubuntu won't touch it.

---

### Post by jbuczek on 2012-02-17
Obviously that's the ticket.  Never thought of that.  Thanx.

---

