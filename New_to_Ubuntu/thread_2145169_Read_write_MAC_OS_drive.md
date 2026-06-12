---
title: "Read write MAC OS drive"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by jpaulb on 2013-05-14
Not sure which topic this falls under
I have the use of a MAC OS external HDD which I can read it is there an app that can write to it?
Paul

---

### Post by stevesy on 2013-05-14
> **jpaulb said:**
> Not sure which topic this falls under
I have the use of a MAC OS external HDD which I can read it is there an app that can write to it?
Paul

Can you give some more details about the problem Paul? Thanks

---

### Post by jpaulb on 2013-05-14
I have a external HDD that is being use on a Mac Pro OS X 10 something. I brought the HDD home to transfer some files to my box running Ubuntu 12.04, transfer went perfect. I wanted to copy some file into another directory on the external HDD, copy was allowed but paste was disabled. Is there an app that can R/W to the mac file system. Don´t ask me too many questions about the Mac, I never used one until last month. That chewed on Apple logo turned me off yeas ago.:)

---

### Post by Kopkins on 2013-05-14
The hfs+ filesystem is not writeable by default in linux. It is usually read only. If you go in through Mac OS X you should be able to turn of journaling and then you should be able to write to it from linux. The other option is to back up the data and use a filesystem that both mac OSX and Linux can recognize (fat32 for example)

Try google-ing hfs+ linux write

Good luck,

Kopkins

---

### Post by jpaulb on 2013-05-15
> **Kopkins said:**
> The hfs+ filesystem is not writeable by default in linux. It is usually read only. If you go in through Mac OS X you should be able to turn of journaling and then you should be able to write to it from linux. The other option is to back up the data and use a filesystem that both mac OSX and Linux can recognize (fat32 for example)

Try google-ing hfs+ linux write

Good luck,

Kopkins

Turning the journaling off is not an option the Mac is not mine; fat32 is not an option, some of the 109 file are as large as 30GB, the Mac, at least this one can not R/W NTFS nor ext3 - 4. The final 1 hour HD video will many hundred GBs.

Paul

---

### Post by Kopkins on 2013-05-15
Well, those are your options.

Look into other filesystem types that they both can recognise.

Good luck.

EDIT: I think you would just have to turn off journaling for your external HDD. Isn't that yours? Then it would be read write. You just need a Mac to do it. Don't have to do anything to the Mac.

---

### Post by sandyd on 2013-05-15
You can probably use NTFS as well
most macs already have NTFS installed (ntfs3g) via FUSE

---

### Post by Kopkins on 2013-05-15
> **sandyd said:**
> You can probably use NTFS as well
most macs already have NTFS installed (ntfs3g) via FUSE

I was going to suggest, but OP said that mac doesn't r/w ntfs. And it's not their Mac so they won't change anything.

---

### Post by jpaulb on 2013-05-15
> **sandyd said:**
> You can probably use NTFS as well
most macs already have NTFS installed (ntfs3g) via FUSE

Thanks I'll get someone to look into that.

---

