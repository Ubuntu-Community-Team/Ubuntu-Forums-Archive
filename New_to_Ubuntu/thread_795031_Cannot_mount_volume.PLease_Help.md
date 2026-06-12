---
title: "Cannot mount volume.PLease Help"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-15
Hello all,

can anyone help me on this please. i attached my external HDD but i forgot to unmount it on windows so i tried to follow the command as per mention on details but it say that i only root can do that. whats does that mean? and how to do it?

edward@Vlad:~$ mount -t ntfs-3g/dev/sde1 /media/New Volume-o force
mount: only root can do that
edward@Vlad:~$ mount -t ntfs-3g/dev/sde1 /media/New Volume -o force
mount: only root can do that

---

### Post by kpkeerthi on 2008-05-15
I suggest you boot into windows, connect the external HDD and simply use "Safely Remove Hardware" option from system tray and then try with Ubuntu.

Of course, you may force mount the device but thats risky. To force mount run this command after connecting the drive
```
**[COLOR="Red"]sudo[/COLOR]** mount -t ntfs-3g /dev/sde1 /media/New Volume -o force
```

---

### Post by exile on 2008-05-15
See: [http://ubuntuforums.org/showthread.php?t=666920]("http://ubuntuforums.org/showthread.php?t=666920")

---

### Post by appoloin on 2008-05-15
i tried adding sudo but now it gave me this error

mount: mount point Volume does not exist what does this mean?

---

### Post by kpkeerthi on 2008-05-15
You need to create the mount point if not done already.
```

sudo mkdir **/media/Windows**
sudo mount -t ntfs-3g /dev/sde1 **/media/Windows** -o force

```

But again, force mounting a volume is risky.

---

### Post by exile on 2008-05-15
If possible, the safest option is to just "Safely Remove" the disk from windows. It worked for me. Use force after you've tried the simple stuff.

---

### Post by appoloin on 2008-05-15
i know its risky but i have no choice at this  point.. thanx guys that work. 

just to make sure i have this clear i always to make directory when i do anything? is this right?

---

