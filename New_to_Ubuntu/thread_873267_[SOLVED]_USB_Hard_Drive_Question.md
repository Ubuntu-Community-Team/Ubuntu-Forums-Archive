---
title: "[SOLVED] USB Hard Drive Question"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by anachronon on 2008-07-28
Hey all,

I am using Ubuntu Hardy on a desktop machine.  I also have a laptop that uses Windows.  I have a USB hard drive that is formatted in FAT 32, which I use to back-up files from the laptop.

My question is: Can I also plug the USB drive into my Ubuntu machine, without damaging the file system?  Can I use the USB drive as backup for both machines?

According to the Linux book I have, I can.  But first, I wanted to post this question here, to find out if anyone has had any issues with this.

---

### Post by kansasnoob on 2008-07-28
If it's purely a data storage drive you should have no problems. Especially since it's FAT32.

If you have trouble "mounting" the drive try either using "pmount" (which depends on hal), or usbmount for "hot-plugging".

They're both available in synaptic.

---

### Post by halitech on 2008-07-28
I have a 200gig external that is formatted NTFS that I use on a daily basis with Ubuntu and never have a problem with it. One of these days I plan on moving everything off it so I can format it in FAT32 so I can use it when I go to my parents place and on mine at home

---

### Post by laffinet on 2008-07-28
You certainly can. That's exactly what I do all the time with my external HDs.

---

### Post by anachronon on 2008-07-29
Thanks everyone. I figured that it would be OK. But, I just wanted to double-check first. I guess, better safe than sorry.

---

### Post by aheckler on 2008-07-29
If you want to be fancy, you can create two equally-sized partitions and format those using seperate file systems. Just a thought... :)

---

### Post by anachronon on 2008-07-30
> **aheckler said:**
> If you want to be fancy, you can create two equally-sized partitions and format those using seperate file systems. Just a thought... :)
Hmmmm, sounds interesting.  But, I really just use the USB HDD for quick backup storage of documents, photos, stuff like that.  Mostly, just things that aren't ready for more permanent storage on CD.

---

