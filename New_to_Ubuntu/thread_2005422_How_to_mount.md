---
title: "How to mount ?"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-17
Hey guys,

If I run this from terminal, it mounts my NAS shared directory with me.


```
sudo mount 192.168.1.102:/volume1/photo /mnt/NAS/photo
```


But in order to get that next time after a reboot, I did this:

```
sudo vi /etc/fstab

192.168.1.102:/volume1/photo /mnt/NAS/photo

```

Then just to test it, I do 

```
 sudo mount -a
```

Then I get an error message:

> [mntent]: line 14 in /etc/fstab is bad

1) :( Why?

2) Besides even after manual mount, I can see the pics in the terminal under /mnt/NAS/photo but in Nautilus there is nothing shown.  Its quite inconvenient, how to fix that?

Thank you :)

---

### Post by Houmie on 2012-06-17
wow I found a solution.

Just append ```
nfs
``` to the line and it works. :)

```
192.168.1.102:/volume1/photo /mnt/NAS/photo nfs
```

The link on desktop works now too, even though it still doesn't show up in Nautilus.  

I leave this still open, in case anyone has something more clever to add to it.

Thanks,

---

### Post by Paqman on 2012-06-17
You might want to take a look at [this page]("https://help.ubuntu.com/community/Fstab") to get an idea how to format fstab entries properly.

What you've got is the minimum that will work, but you could expand it to:
```
192.168.1.102:/volume1/photo /mnt/NAS/photo nfs defaults 0 0
```
...which does exactly the same thing, but you can see that there are a couple of other "slots" for options in there. In your case you can use the defaults just fine, but if you wanted to do something different (eg: mount the share with certain permissions) then you can see where they would go.

---

### Post by Houmie on 2012-06-18
Thanks Paqman,  Its good to know.

On another note, now that I start Ubuntu I always get the mounts and hence my NAS never goes to sleep mode as long as the pc is turned on, which is a waste.

I wonder if I could use a bash script to do the mount whenever I need it.

```
#!/bin/bash

sudo mount 192.168.1.102:/volume1/photo /mnt/NAS/photo nfs defaults 0 0
```

Could I just link the script on my desktop and double click would execute it? Ah probably not because of password though...darn

---

