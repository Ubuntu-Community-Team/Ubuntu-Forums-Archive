---
title: "[SOLVED] the CD wont eject!"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by hammeraxe on 2008-06-26
i just installed xubuntu on a bit obsolete table computer (667MHz, 256RAM) ... it runs fine

when i insert a CD/DVD it is detected and mounted, yet no desktop icon is shown but that is a minor inconvenience... the real problem is that i cannot eject the CD... when i press the eject button there is no reaction... the only thing i can do is 
```

sudo umount /media/cdrom0

```
and then push the button... obviously that is not very comfortable

could you please suggest any causes/solutions for this problem?

---

### Post by wootah on 2008-06-26
> **hammeraxe said:**
> i just installed xubuntu on a bit obsolete table computer (667MHz, 256RAM) ... it runs fine

when i insert a CD/DVD it is detected and mounted, yet no desktop icon is shown but that is a minor inconvenience... the real problem is that i cannot eject the CD... when i press the eject button there is no reaction... the only thing i can do is 
```

sudo umount /media/cdrom0

```and then push the button... obviously that is not very comfortable

could you please suggest any causes/solutions for this problem?

Is it a burned CD? Do you know if the drive reads all types of cds/dvds?

---

### Post by hammeraxe on 2008-06-26
as far as i know the drive reads all types of CDs/DVDs... ive never had problems with it

i tried different disks, both burned and original... its the same thing

EDIT: waitt, the problem persists only when using DVDs, CDs can be ejected :D

---

### Post by wootah on 2008-06-26
Maybe it's a problem with the hardware ? It seems like a very strange problem... Hopefully someone with more experience can help out here.

---

### Post by rburkartjo on 2008-06-26
ham, try this open terminal and type eject and then kit the enter key on your keyboard/cheesemaker

---

### Post by |{urse on 2008-06-26
try 

> eject /dev/scd0
eject /dev/sr0


too.

If that doesnt work try 

> 
sudo apt-get install cdrecord
cdrecord -scanbus

to help identify your device.

or you can look through fstab or mtab.

wait a minute... are you using a livecd? lol j/k all you really need to know is its /dev/ designation

---

### Post by |{urse on 2008-06-26
or.. make a script

```

#!/bin/bash
sudo umount /media/cdrom0
sleep 2
eject

```

that should do the trick. paste that into an empty document and save. then right click and select "properties" put a check in the Make this Executable option and apply. now you have to double click it to eject your tray but hey.. thats a few less keystrokes.

---

### Post by hammeraxe on 2008-06-27
gah.. it now works after ive restarted a couple of times.. probably some update fixed it...
anyway i tested the things you guys suggested and they all work!
thanks

---

### Post by wootah on 2008-06-27
> **hammeraxe said:**
> gah.. it now works after ive restarted a couple of times.. probably some update fixed it...
anyway i tested the things you guys suggested and they all work!
thanks
Don't forget to mark this thread as solved :) (Thread tools -> Mark as solved)

---

