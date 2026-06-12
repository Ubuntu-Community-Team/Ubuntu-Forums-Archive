---
title: "Installing no cd crack on Ubuntu"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by ArnsteinK on 2008-10-16
I have a laptop, and I want to have Diablo and Starcraft on it. But since I'm gonna use it while traveling etc. I don't want to bring CDs, so how I can I no-cd-crack them? I have tried some that I found, but it didn't work! I use Play on Linux.

---

### Post by OffAxis on 2008-10-16
The latest official update of Starcraft: Brood War had a no-cd check added to it (about time). I *think* it's the version now sold in stores, but haven't actually checked.

Same with Diablo II. one of the last few patches removed the CD-check.

I'm not sure if the patches would update properly in wine, but it's worth a shot.

---

### Post by starcannon on 2008-10-16
another option on games that it is difficult, or impossible to no-cd crack them, is to just make an iso of the cd in question and leave it on your hdd, then when you want to play, just mount the iso first. This does have an obvious side effect of using up a lot of space if you have more than 1 or 2 games you like to play, but creating iso's is fairly fast and painless, so no reason to keep an entirel library on there, just put them on as needed, then delete when bored of the game and put a more interesting one on, rinse repeat as needed.

---

### Post by ArnsteinK on 2008-10-16
I tried choosing to play online(because then it will update automatically), but the game just exited when I pressed battle.net!

---

### Post by TCSnyder on 2008-10-16
this should work.

well when you put the cd in right click it's icon and click copy disk copy it to a file. 

to mount the disk go to a terminal and type ```
sudo mkdir /media/Disk
```

that will create a new place to mount the .iso image
then type

```
sudo mount -o loop -t iso9660 "path/to/iso/image" /media/Disk
```

that will mount it. you should be able to start and play it from there

---

### Post by TCSnyder on 2008-10-16
to umount it type

```
sudo umount /media/Disk
```

---

### Post by ArnsteinK on 2008-10-16
How do I make an ISO? And what program do you have to use on Ubuntu to mount them? It's only Starcraft and Diablo I want, so it's no problem using ISO's

---

### Post by TCSnyder on 2008-10-16
put the cd in your computer, the icon will show up on the desktop. right click it and click copy disk. there is an option to copy it to a file. after its done, use the terminal commands i told earlier to mount and unmount it

---

### Post by fred_miller on 2008-10-16
You can make an iso with K3b and you can mount it with Gmount-iso which are both in the repository.  They are both gui and easy to use.  Why does everybody want users to use the terminal.  Lets just all use DOS too.

---

### Post by ArnsteinK on 2008-10-16
I found out that Play on Linux can get the patch, the problem is that it doesnt work!

---

### Post by TCSnyder on 2008-10-17
well if you use the terminal and learn it, then it doesn't matter what linux distro you use you can always get the job done.

P.S.  when i learned it there wasn't a GUI

---

### Post by LowSky on 2008-10-17
I Run Diablo 2 with Wine with No issues at all, StarCraft should be very simular. By the way Blizzard has the newest patches availible on the websites. I can even play online.

---

