---
title: "Mount partition."
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Jerfo on 2008-11-24
I was wondering if there is way to make it so that my NTFS partition (which is basically where all my files are) is always mounted? I find it somewhat annoying that every time I open a program that looks for files in there (e. gr. the video player), I have to mount it again.

---

### Post by iaculallad on 2008-11-24
> **Jerfo said:**
> I was wondering if there is way to make it so that my NTFS partition (which is basically where all my files are) is always mounted? I find it somewhat annoying that every time I open a program that looks for files in there (e. gr. the video player), I have to mount it again.

Follow up with this previous [thread]("http://ubuntuforums.org/showthread.php?t=988862"). Try the solution I posted, it's post number 3.

---

### Post by __Ryan__ on 2008-11-24
You need to make sure there is an entry for it in /etc/fstab.

Make sure that it does not have the noauto option enabled as well so that it will be automatically mounted.

---

### Post by RiceMonster on 2008-11-24
You can add the drive to /etc/fstab

```
gksudo gedit /etc/fstab
```

Then, add this line:
```
/dev/**sda1** /PATH/TO/DIRECTORY/ ntfs-3g defaults 0 0
```

The part I bolded above is very likely different for you, it may be hda1 or sda3, or something along those lines. 

Please note that you must create the directory first. Once you've got the right information, it will mount on boot.

---

