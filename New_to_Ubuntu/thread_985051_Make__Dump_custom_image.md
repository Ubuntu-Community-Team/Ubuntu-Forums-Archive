---
title: "Make / Dump custom image"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by vdb on 2008-11-17
Hello there,

I'm pretty new with ubuntu / xubuntu in specific.
I've got a question containing the making and dumping of a custom image.

I've installed the 8.10 version of Xubuntu, tweaked it for business use. Now I want to make an image of this specific configuration which I can use for more computers. I want to create 10 computers with that same configuration.
Is there a simple way to make this possible?

Thanks alot for your help!

---

### Post by rampageoberon on 2008-11-17
I remember reading up on this a while ago and found various tools, unfortunately can't remember them all.

Here are some tools that could do what you want.
PartImage - [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
CloneZilla - [http://www.clonezilla.org/](http://www.clonezilla.org/) ([http://www.linux.com/feature/115208](http://www.linux.com/feature/115208))

Hope that helps

---

### Post by magnus0 on 2008-11-17
You can clone your hard drive:

```
dd if=/dev/sda of=/dev/sdb
```

"if" is the input drive, "of" is the output drive.

---

### Post by vdb on 2008-11-17
Thanks for these quick answers!

Are there also ways to create a bootable ISO (or .gho) of the particular disk including the set configuration?

---

### Post by rampageoberon on 2008-11-17
PartImage should create an ISO i believe. Never used any of these before so not absolutely sure.

---

### Post by magnus0 on 2008-11-17
You can make an iso with the same command:

```
dd if=/dev/sda of=/home/somebody/image.iso
```

Just replaced the output drive with an iso file.

---

### Post by solitaire on 2008-11-17
I'd use "remastersys" (in the repo's)
it basically can turn your current desktop install into a "liveCD", a full backup DVD or a recovery DVD.

I find it easy to use.

---

