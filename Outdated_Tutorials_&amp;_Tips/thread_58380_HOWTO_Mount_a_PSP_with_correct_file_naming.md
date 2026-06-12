---
title: "HOWTO Mount a PSP with correct file naming"
date: 2005-08-19
forum: Outdated Tutorials &amp; Tips
---

### Post by daigorobr on 2005-08-19
Well, I almost killed myself trying to mount the Playstation Portable in my Kubuntu so I could use the wonderful homebrews it offers.
Well, case matters in PSP file naming so the correct /etc/fstab entry should be something like this:

```
/dev/sda1 /mnt/psp vfat user,shortname=winnt 0 0  
``` 

I don't need to mention that the paths must be individualized according to user's preferences and needs.

Hope it helps someone.

---

### Post by kpaul_nyc on 2006-06-27
i'm a newbie to ubuntu can you go into detail on how to do this?

---

### Post by Khannie on 2006-08-02
I've had to refer to this a few times now, as my 5.10 installation has stopped auto-mounting my psp for some reason. 

If you don't want to edit fstab, the one-time command to mount the PSP is:

```
sudo mount /dev/sda1 *<insert mount directory here>* -t vfat -o user,shortname=winnt
```

---

