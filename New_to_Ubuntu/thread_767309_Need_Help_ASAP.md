---
title: "Need Help ASAP"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by kclemens on 2008-04-25
**SOLVED- Solution in Post**

Ok, so I installed compiz-fusion and it completely screwed up my network settings.  i ended up uninstalling network-manager.

Now I want to do a clean install, and I have burned the new Ubuntu release onto a CD.

It will not let me boot from a CD.  How do I completely remove or re-install linux??

Kclemens

---

### Post by nrmerritt on 2008-04-25
I'll try to help.. When say that you can't boot from the CD do you mean your computer is not able to boot from a CD or do you mean when you select your boot option from the CD's boot menu the live Cd (only a guess) hangs?

---

### Post by kclemens on 2008-04-25
when I hit f12 and select to boot from the CD, it hangs for 5 seconds and then boots up my installed version of Kubuntu.

I want to run the cd that I have ubuntu on. the latest version I just downloaded.

---

### Post by nickpaton on 2008-04-25
I assume you burnt the release onto CD as a .iso file and not as a data file.

Make sure that you have set your computer BIOS settings to CD as the first boot device.

If you've done all that, go back to the downloaded release and check the md5sum is correct - i.e. that what you've downloaded is 100% correct with no corrupt files.

When you install the new release, it will overwrite the old distro, so you don't need to remove the old one.

Welcome to the forums and Ubuntu!

---

### Post by kclemens on 2008-04-25
I unzipped the .iso and installed the unzipped files onto the CD.

---

### Post by nrmerritt on 2008-04-25
I agree with nickpaton. Check your install media. At worst you may have to re-download the image.

---

### Post by nrmerritt on 2008-04-25
You need to burn the image to the disk without unzipping the files. What program do you have available for burning disks?

---

### Post by qamelian on 2008-04-25
> **kclemens said:**
> I unzipped the .iso and installed the unzipped files onto the CD.
That is the wrong way to create a bootable CD from an ISO image. Most burning software has a "Burn/Record from image" feature that will burn the image correctly. Simply extracting files from the image does not allow you to make a bootable disc.

---

### Post by nickpaton on 2008-04-25
> **kclemens said:**
> I unzipped the .iso and installed the unzipped files onto the CD.

When you download the .iso file, don't subsequently unzip it, leave it as a single large .iso file.

In Windows, a great program to burn .iso files in a couple of clicks is [http://isorecorder.alexfeinman.com/isorecorder.htm]("http://isorecorder.alexfeinman.com/isorecorder.htm")

Should now work!

---

### Post by rjs987 on 2008-04-25
There would be your problem.
Use K3b and go to Tools>Burn CD Image and then select the ISO file you downloaded.
You need to burn the ISO image as-is to a CDR or CDRW. Do not unzip.
What you did was to only burn files as data.
Hope this helps.

edit: I guess I'm just not as fast as some posters :)

I also forgot to mention that the Burn CD Image dialog does an MD5sum check for you when you select the ISO file. Then all you need to do is compare with the published MD5sum given at the download site. I always copy and paste the published MD5sum to a text file while I am waiting for the download to complete so I have it handy.

---

### Post by nickpaton on 2008-04-25
Sorry forgot Ubu burning software!!!!

I use gnomebaker which is also good!

<EDIT> Double oops - just seen it's a Kubuntu post, so stick with K3b

---

### Post by kclemens on 2008-04-25
Thanks everyone.

The way I burned it would be my error.

Thanks to you all!

---

### Post by kclemens on 2008-04-25
Thanks everyone.

The way I burned it would be my error.

Thanks to you all!

---

