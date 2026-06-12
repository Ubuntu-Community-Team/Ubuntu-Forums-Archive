---
title: "removing windows vista"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by cabz on 2012-04-27
I am running a toshiba laptop dual booting with windows vista and xubuntu. I have decided to go with xubuntu all the way and was wondering what I have to do to remove windows vista and recover the HD space to xubuntu. would I have to do a new install and choose not to dual boot?. massive newb here so spell it out for me:lolflag: please

---

### Post by carl4926 on 2012-04-27
Open a terminal in Xubuntu
Post result of

```
sudo fdisk -l
```

Normally, to keep it pretty. A fresh install is best. But to simply use the space as it is, without trying to integrate it to Xubuntu, all you need do is use GParted to format it to ext4 and then use that space as storage.

---

### Post by fantab on 2012-04-28
Go to DISK UTILITY and format the vista partiton to ext4. It will be plain linux partiton you can use it to save your Data. You may have to mount it evertime after a restart to use it... or you can configure it to automount.

Then update GRUB: *sudo update-grub*

Next time when you do a clean Install Xubuntu you can use [GPARTED LiveCD]("http://gparted.sourceforge.net/livecd.php") to partiton space to your liking...

---

### Post by mobisallen on 2012-04-28
yeah a fresh installation is the best way to recover the space from HD and it also helps to increase the performance of the PC or Lap top. but try to avoid this practice of installation it also damages the clusters of HD

---

### Post by Mark Phelps on 2012-04-28
> **mobisallen said:**
> yeah a fresh installation is the best way to recover the space from HD and it also helps to increase the performance of the PC or Lap top. 
Unless the Ubuntu installation is a year old or older, I seriously doubt a fresh install (of the same version) is going to result in any observable performance gain.
> but try to avoid this practice of installation it also damages the clusters of HD
This is sheer nonsense!!

---

### Post by Bartender on 2012-04-28
cabz -

I'd suggest downloading a 12.04 Xubuntu .iso first, then making the bootable CD.

For a 'massive newb' the most straightforward path would probly be to save your music, docs, etc. to some external device, then boot from your new Xubuntu 12.04 disc and install fresh to the entire drive.

That's what I'd do.  And I'm probly not a massive newb anymore although I do make dumb mistakes on a regular basis

Since you're dual-booting, simply wiping out the Windows install creates complications.  Your boot loader will think Windows is still there.  It's not a huge deal to fix the boot loader, but not really fun either.  I don't know about you but for me it's a little nerve-racking to try and fix something like that.

Plus, with 12.04 out, you can take care of two big jobs at once...

---

### Post by cabz on 2012-04-30
I had allready done the 12.04 upgrade , I think for now I am just gonna leave well enough alone. This PC works so well right now I dont want to mess with it . I will in he future be removing windows from it becasue in windows the PC gets so hot the cpu overheats and the PC shuts off. ( this model toshibas gremlin) but with linux it will run for weeks with no issues.

---

