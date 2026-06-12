---
title: "Ubuntu Server hosting drives: RAID or JBOD?"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by honeycombs_big_yahyahyah on 2012-08-01
Hi folks,

I want to use my old laptop with Ubuntu Server to act, among other things, as a NAS and media server on my home network.  Basically, I want to attach a big multi-drive external enclosure to my laptop, and serve media files, host backups, etc.

I don't want to have to manage 4 or 5 different logical drives on the laptop.  Rather, I'd like to manage all those drives as a single (or perhaps 2) logical drive.

I had been looking for a RAID enclosure (attachable via USB) to accomplish this.  But then I read that windows home server can handle things like folder duplication.  Can Ubuntu do a similar thing?  That is, can Ubuntu do in software basically what RAID can do in hardware (e.g. mount a bunch of drives as a single logical device, take care of files spanning multiple drives, redundancy, etc)?

I hope I'm making sense here...

Thanks in advance!

---

### Post by Cheesemill on 2012-08-01
Yes it can.

But the real question is how are you going to attach the drives to the laptop?
If it's an enclosure for multiple drives that is connected by a single USB port then it's likely that the enclosure already has a RAID controller built in.
To take advantage of Ubuntu's software RAID you need all of the drives connected separately, and IMHO performance from USB connected drives is likely to be terrible.

---

### Post by honeycombs_big_yahyahyah on 2012-08-01
thanks cheesemill - i'll attach them via USB (slow, but, that's what I got).  I was looking at something like this as an example: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817198047](http://www.newegg.com/Product/Product.aspx?Item=N82E16817198047)

So, when you say "yes it can", is software RAID what you're referring to ([https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)), or should I be reading about other options as well?

thanks!

---

### Post by Cheesemill on 2012-08-01
> **honeycombs_big_yahyahyah said:**
> So, when you say "yes it can", is software RAID what you're referring to ([https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID))

Yes, your best bet would be software RAID using mdadm.

As well as that link rubylaser has some great how-to guides on his site.
[http://zackreed.me/articles?tag_id=22](http://zackreed.me/articles?tag_id=22)

---

### Post by honeycombs_big_yahyahyah on 2012-08-01
great, thanks!  now off to find some cheap drive caddies.

one final followup: it seems that most RAID specifications require that the disks be the same size, and if they're not, they'll just 'downgrade' the rest of the disks to the size of the smallest one.  I assume that mdadm doesn't offer a nice way around this, such that different size disks can be added without suffering that penalty?  If not, is there any other disk configuration I should be considering, such as ZFS?  Drobo's BeyondRAID is proprietary, but I wonder if there's some sort of open-source equivalent...

---

