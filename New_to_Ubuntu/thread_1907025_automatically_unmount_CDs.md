---
title: "automatically unmount CDs?"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by JohnDillinger43 on 2012-01-10
Unless I'm misremembering, when I first installed Ubuntu (11.10) on my computer, I could simply hit the eject button on my optical drives (2x HP DVD-RW drives) and the disc would eject.  Now I'm finding that I can't do that.  Instead I have to manually unmount the volume, using, e.g., ```
sudo umount /dev/sr1
```, and then I can eject the disc with no problem.  Is there a way I can get it to unmount the disc automatically when I press the eject button?

---

### Post by androssofer on 2012-01-10
> **JohnDillinger43 said:**
> Unless I'm misremembering, when I first installed Ubuntu (11.10) on my computer, I could simply hit the eject button on my optical drives (2x HP DVD-RW drives) and the disc would eject.  Now I'm finding that I can't do that.  Instead I have to manually unmount the volume, using, e.g., ```
sudo umount /dev/sr1
```, and then I can eject the disc with no problem.  Is there a way I can get it to unmount the disc automatically when I press the eject button?

not sure you could.. at least i have no idea how.

what i would do is make a desktop shortcut you can click on that does it for you?

make the shortcut and in the command part of it do:

```
umount /dev/sr1 && eject
```

---

### Post by androssofer on 2012-01-10
my original plan didnt work... got a new 1 though... 

so open a terminal and do:

```
gedit cdEjector
```

then in the file put:

```
#!/bin/sh

umount /dev/sr1
eject
```

then save it and exit, then do these one at a time:

```
sudo mv cdEjector /usr/bin

cd /usr/bin

sudo chmod +x cdEjector
```

then create a launcher on your desktop and in the command part do:

```
cdEjector
```

now when you double click it, it will unmount the cd and eject it for you :-)

---

### Post by Paqman on 2012-01-10
> **JohnDillinger43 said:**
> Is there a way I can get it to unmount the disc automatically when I press the eject button?

That is the normal behaviour, sounds like you've got a bug there.

Do you know for certain that the eject button on your drive works?

---

