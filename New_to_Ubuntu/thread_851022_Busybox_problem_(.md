---
title: "Busybox problem :("
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Rioku on 2008-07-06
Ok guys I'm getting sick now... I'v used ubuntu quite abit now... but every time iv used it after a while I always end up getting some issue which I cant be resolved and results in wiping out the installation.

Ubuntu was working fine on my laptop yesterday... and now today I turn it on and go into ubuntu the load screen shows then straight after I get some "busybox" thing which I have no idea about...

I have tried searching but have been unable to fix this issue 


can anyone help me out please?

btw its 8.04 and I have installed using wubi

---

### Post by PmDematagoda on 2008-07-06
Did you update Ubuntu or more specifically, update the kernel before this started happening?

---

### Post by Rioku on 2008-07-06
Nope I didnt do anything..

Altho I did go into vista late during the night and I defragged. But I dont believe that could have anything to do with it could it?

---

### Post by damis648 on 2008-07-06
Try this: At you GRUB (boot) menu, press "e" on the Ubuntu option you normally boot. Go down to the second line and press "e" again. You should find yourself able to edit a line with "quiet" and "splash" at the end. Remove ONLY those two words. Now, press enter and then press "b". Wait until you see the busybox, and tell us the error messages that appeared right before that.

---

### Post by Totto90 on 2008-07-06
It happened with me. Open Windows and run a disk check on the drive where ubuntu is installed. that should fix it if your computer didn't shut down normally. try it.

---

### Post by Rioku on 2008-07-06
I didnt get an error and the busybox thing didnt appear after deleting those that you mentioned. It went straight onto the desktop gui and worked fine.

So thanks allot! :D Great help from a great comunity.

I do however now have a boot time problem.. after deleting those It seems to take about a minute longer to boot... But I can deal with that.

once again thanks!

The reason I defragged was to see and test if battery performance would increase. And... It did! I gained an extra 25 - 30 minutes in vista and I havnt checked ubuntu yet.. waiting to discharge the battery and give it a full charge again... but when I just checked before when it was at 80% I had 2 hours 15 minutes (in ubuntu) and I believe thats allot more than it was before I defragged the HDD

---

### Post by damis648 on 2008-07-06
> **Rioku said:**
> I didnt get an error and the busybox thing didnt appear after deleting those that you mentioned. It went straight onto the desktop gui and worked fine.

So thanks allot! :D Great help from a great comunity.

I do however now have a boot time problem.. after deleting those It seems to take about a minute longer to boot... But I can deal with that.

once again thanks!

Wierd... all that does it stop the splash from appearing and shows terminal output. I guess it was just a coincidence?

---

### Post by Rioku on 2008-07-06
Thats strange :S... Well it seems to have done the trick. I must have tried re booting like 6 or 7 times before I came here to post about it.

Soon as I did what you mentioned it seems to have solved this issue :D

---

### Post by exchequer on 2008-07-07
> **Rioku said:**
> I didnt get an error and the busybox thing didnt appear after deleting those that you mentioned. It went straight onto the desktop gui and worked fine.

So thanks allot! :D Great help from a great comunity.

I do however now have a boot time problem.. after deleting those It seems to take about a minute longer to boot... But I can deal with that.

once again thanks!



I had the same problem and the same result after following the instructions damis648 gave. Thanks! :KS

---

