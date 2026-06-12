---
title: "copying access denied"
date: 2013-07-14
forum: New to Ubuntu
---

### Post by bonbonjai on 2013-07-14
I record tv documentries on humax hd-fox--t2 on a small hard disk and transfer to an external 3tb hard disk.

i keep getting access denied.


There was an error copying the file into /media/44ab7280-dc57-43ab-be6b-3da7f0144543.

Error opening file '/media/44ab7280-dc57-43ab-be6b-3da7f0144543/epgsavedata': Permission denied

I formatted the external hard drive on gpartred 

help

---

### Post by sffvba[e0rt on 2013-07-14
> **bonbonjai said:**
> I record tv documentries on humax hd-fox--t2 on a small hard disk and transfer to an external 3tb hard disk.

i keep getting access denied.


There was an error copying the file into /media/44ab7280-dc57-43ab-be6b-3da7f0144543.

Error opening file '/media/44ab7280-dc57-43ab-be6b-3da7f0144543/epgsavedata': Permission denied

I formatted the external hard drive on gpartred 

help

As their is a question about copying shows off of a DVR type device to other external media this thread is closed for review.


404

---

### Post by cariboo on 2013-07-14
Thread reopened, as we don't care what type of file it is. @bonbonjai, it sounds like a permissions problem, who is the owner of the file, and who is the owner of the drive you want to copy the file to?

---

### Post by 3rdalbum on 2013-07-15
It specifically sounds like the DVR hard disk is mounted with the wrong permissions. Try this:

```
sudo chmod /media/44ab (press tab here) a+r
```

Or it could be filesystem corruption that has corrupted the permissions.

---

### Post by leunam12 on 2013-07-15
Has this external hard drive been connected to a Windows computer? if so, try re-connecting to windows again a do a proper "safe removal" procedure there (don't just simply pull the USB plug).

Sorry for being too obvious but here is the procedure for safety removal. [USB safe removal.]("http://etc.usf.edu/techease/win/hardware/how-do-i-safely-remove-a-usb-device-from-my-computer/")

---

### Post by ricardoeureka on 2013-07-15
Hi!

Please provide the output of the following commands:

# sudo df -h
# sudo ls -ltrd [COLOR=#000000][I]/media/44ab7280-dc57-43ab-be6b-3da7f0144543

And please provide information on how are you trying to copy the file (from a command line? from the desktop? which user? etc.)[/I][/COLOR]

---

### Post by CinTUX on 2013-07-16
Hey,

You could try mounting the HDD to another location with:
$ mount -t /dev/[NAME] [LOCATION]

---

