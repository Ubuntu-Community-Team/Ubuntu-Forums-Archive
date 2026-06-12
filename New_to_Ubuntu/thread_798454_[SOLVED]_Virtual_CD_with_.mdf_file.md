---
title: "[SOLVED] Virtual CD with .mdf file"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by neur0 on 2008-05-18
I need to mount an old game I have in .mdf format. I use fuseiso to mount .mdf files and it works. However, this game is asking me for a CD after I begin setup.exe with Wine. (it obviously needs the CD in the drive)
Someone mentioned I could mount .mdf files simply with mount -o loopback, but i get "mount: can't find /mnt/cd/ in /etc/fstab or /etc/mtab" error when I try that with .mdf.

Is there any way I can get a (temporary) virtual CD drive like with Daemon Tools or Alcohol 120%?
I'm gonna try converting it to ISO and see if it helps, in the meantime, does anyone know a better solution?

Update: The iso I get from the mdf using mdf2iso doesn't seem to be mountable or accessible in the archive manager, it says it not a iso9660. though all is fine with the mdf (I can see its contents with fuseiso) Darn, its getting from bad to worse...

---

### Post by Monicker on 2008-05-18
Have you tried mounting it from the console?  You could also try gmountiso or kiso to mount it.

---

### Post by neur0 on 2008-05-18
Thanks for the reply,

OK, It seems that the MDF file is somewhat corrupted as Kiso also couldn't recognize/open the ISO file it made from the MDF file, and it could do that with the second MDF file (its a game on 4 CDs)
So, I copied the files from the MDF I mounted via fuseiso (kudos to fuseiso makers) to a different folder and then after deleting some unnecessary files (like DXSETUP) I made a custom ISO file out of it. I still couldn't fool the application into thinking that the CD is in the drive (mount -o loop) but at least I managed to burn that custom made ISO on the real CD and start the Install from it.
Now if you are wondering why didn't I just burn the MDF file on  a CD, its just over 700MB large and couldn't fit on a CD, and besides, it seems corrupted somehow as I explained and probably wouldn't even work. 
So, this is solved I guess, though I didn't emulate a CD drive like with Daemon Tools or Alcohol 120%

---

