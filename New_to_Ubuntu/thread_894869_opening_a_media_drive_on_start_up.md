---
title: "opening a media drive on start up?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by soviet911 on 2008-08-19
HI. I have a question, I use Ubunto 8.04 and i have 2 hdd's one main hdd (it has 500gigs) and then a 250 gig with  all my music on it, I have Ubuntu running on my 500 gig drive and when i start it up i have to go and manualy load up the media drive or otherwise Amarok doesnt see it, and thus it doesn't play music, wich is a minor annoyance but i would like to figure out how to fix, is there a way to make ubunto automatically open up the 250 gig drive on start up, and if so how would i go about doing it? :confused: Thanks in advance.

---

### Post by drs305 on 2008-08-19
> **soviet911 said:**
> HI. I have a question, I use Ubunto 8.04 and i have 2 hdd's one main hdd (it has 500gigs) and then a 250 gig with  all my music on it, I have Ubuntu running on my 500 gig drive and when i start it up i have to go and manualy load up the media drive or otherwise Amarok doesnt see it, and thus it doesn't play music, wich is a minor annoyance but i would like to figure out how to fix, is there a way to make ubunto automatically open up the 250 gig drive on start up, and if so how would i go about doing it? :confused: Thanks in advance.

You can put an entry in fstab. Is one a removable drive?

Please post the results of:
```

cat etc/fstab
sudo blkid
fdisk -l

```

If you are adventurous you can do it yourself via a gui fstab editor. See the link in my signature line for SDM - it will take you to the tutorial which includes a "5 Minute Guide".

---

### Post by soviet911 on 2008-08-19
its not a removable drive, but just a standard HDD that sits in my PC, I will try the link you gave me.

---

