---
title: "Can't detect new CD inserted"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by alankon on 2012-07-24
Hi,

I'm new to Ubuntu so forgive me if this is a daft question, however it's been bugging me for hours, and I can't find an answer.

When I insert a CD into the drive as Ubuntu is loaded, it appears in my launcher bar, and I can open it. Happy days.

However, when I swap the CD for another one, the one on the launcher disappears, but no new icon appears for the new disc. I can't seem to detect the CD drive anywhere.

Can someone please explain what I'm doing wrong?

Thanks.

---

### Post by Bufeu on 2012-07-24
Remember to use the "Unmount" or "Eject"-option to eject a disc.
Otherwise, just mount it. Should work with:```
sudo -s
mkdir sr1
mount /dev/sr1 sr1
exit
```To unmount it, use:```
sudo -s
umount sr1
rmdir sr1
exit
```

---

### Post by alankon on 2012-07-25
That worked... thank you.

It's been so long since I've used any OS other than Windows, I'd got used to just opening the CD drive without ejecting the disk.

---

### Post by Bufeu on 2012-07-25
Just explaining the code, the *mkdir*-command creates a folder to mount the device (CD-player) on. If you feel so, you don't need to run the *rmdir sr1*-command (the command just deletes the folder sr1). To eject the cdrom via the terminal, you can use *eject -v*. Remember to unmount it first before ejecting!
If your problem is solved, please mark this topic as "Solved".

---

