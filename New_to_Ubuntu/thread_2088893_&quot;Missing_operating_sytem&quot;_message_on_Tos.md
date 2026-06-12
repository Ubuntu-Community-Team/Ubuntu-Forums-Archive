---
title: "&quot;Missing operating sytem&quot; message on Toshiba Satellite"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by mtds on 2012-11-27
I've been using Ubuntu on an old Dell for 3 or 4 years and I am very happy with it, but I am still in the absolute beginner category. I'm just a user, not a technical person.

I just inherited a Toshiba Satellite U405-S2826. It has Vista on it now... 

I have used the Satellite to download 12.04 to a flash drive and used setup to make the flash drive the first boot location. When I turn on the laptop, I get a one line message: "Missing operating system."

From Vista I can open the flash drive and see that it contains a "disk image file", so I think Ubuntu is on the flash drive, but I can't get past that error message.

Any suggestions?

---

### Post by Monotoko on 2012-11-27
What did you create the flash drive with? Does it have an MBR? When you say you see the disk image on the drive, do you mean you just copied and pasted it? If so... have a look at unetbootin, it creates a USB bootable drive for you :)

Edit: Inside unetbootin, it will give you options at the top for a lot of distributions... ignore that, just hit the second option down (Disk Image) then find the image on your hard drive. Remember to format the drive first, unetbootin doesn't do this for you...

---

### Post by mtds on 2012-11-27
> **Monotoko said:**
> What did you create the flash drive with? Does it have an MBR? When you say you see the disk image on the drive, do you mean you just copied and pasted it? If so... have a look at unetbootin, it creates a USB bootable drive for you :)

Edit: Inside unetbootin, it will give you options at the top for a lot of distributions... ignore that, just hit the second option down (Disk Image) then find the image on your hard drive. Remember to format the drive first, unetbootin doesn't do this for you...

Thanks for trying to help me.

1. I formatted the flash drive with the Satellite and then used the Satellite to download 12.04 to the flash drive.

2. MBR... I just googled this and now know that MBR means Master Boot Record. I don't know how to tell whether the flash drive has an MBR or not.

3. No, I didn't copy and paste 12.04.

4. I just googled unetbootin and will try and use it. Wish me luck; I'm "all thumbs" in this field. Thanks again.

---

### Post by mtds on 2012-11-28
Thanks to Monotoko and UNetbootin, I am up and running on my new/used laptop!

---

