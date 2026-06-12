---
title: "Lacie external usb drive"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by bjurcina on 2008-07-13
I'm trying to use my Lacie external usb drive on my Hardy system at home but it doesn't seem to see it at all. The drive works fine on my Windows system and I assume it has NTFS format. From what I've been reading it should auto detect without any problem and mount but when I plug it in I can hear it run and nothing happens. Any ideas or am I such a nube that I missed something? Thanks.

---

### Post by tuxxy on 2008-07-13
do "lsusb" in terminal, is it detected?

---

### Post by tiltus on 2008-07-14
I too have a LaCie external drive, and have the same problem.
Mine's in NTFS. 
it can find it when I use the lsusb command, and i can see it in file browser, but i cannot mount it, and get the error 

**Cannot mount volume.** 
Invalid mount option when attemping to mount the volume 'External_HDD'.

the same went for my thumb stick. I've tried the NTFS-3G method but no luck

I've played around with it, and I can now fully access the HDD or the thumb drive, but only if they're the second usb mounted. Any ideas about this?

---

### Post by sayakb on 2008-07-14
Have you tried mounting it from the terminal?
```
sudo mkdir /media/disk
sudo mount /dev/sdb1 /media/disk
```

Where /dev/sdb1 is the device link for your USB HDD.

---

### Post by tiltus on 2008-07-15
personally my dilemma has become alot stranger.
For some reason whenever i plug a single usb hdd or stick, i am unable to mount it, but if i have a second one in at the same time, the second one mounts fine! if i swap the devices around it works for the second device only.

---

### Post by wariskampar on 2008-07-15
I also use this external HD. Follow linuxisinovation (create mount point), add entry in fstab, then, everytime I want to mount; mount /dev/sdb1. Auto-mount is not working in my case. I don't know why and how to do it.
ps: I'm mediocre user so hope my post can give at least very rough idea

---

### Post by peakshysteria on 2008-07-15
If the LaCie wasn't removed properly from windows via safe removing it may not mount properly. Boot windows and mount the disc as usual then remove it via safe removing of hardware. Then boot Ubuntu and it should pop up. Usually this is the case when problems like this occur (been there myself a few times).

---

### Post by wariskampar on 2008-07-15
peakshysteria; do you mind to share your fstab entry for this USB HD. After do as you said (safely disconnect in XP which is running in VirtuaBox), I no longer can write to my HD. I still need to manually mount it instead of it will automatically pop up

---

### Post by wariskampar on 2008-07-18
My problem started and end with this thread. At first Hardy manually detected my ext. HD (Lacie). After following one suggestion to safely disconnect it in XP, Hardy refuse to detect it at all. Found that all the data were corrupted. GO back to XP to run chkdsk. Upon completion (whole night!), safely disconnect it and it was the solution. Hardy automatically detect my HD when I plug it in.
ps: along the process I found 2 + 1 great programs; testdisk and photorec and chkdsk

---

