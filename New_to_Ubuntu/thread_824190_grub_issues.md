---
title: "grub issues"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by ntrgc89 on 2008-06-09
After performing some updates in ubuntu, I now have 7 different versions of ubnutu available at the bootloader screen!

One is the memtest, and the other 6  are regular and recovery mode version of what appears to be various versions of the kernel, seeing as they end in 16, 17, and then 18. Why is this happening? And is it OK to remove them (how do you do that, by the way)? Thanks for all your help!

---

### Post by unutbu on 2008-06-09
```
gksu gedit /boot/grub/menu.lst
```

About 60% of the way through the document you'll find stanzas like this:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

The title line is what you see in the GRUB menu at boot time. Simply remove the stanzas that you don't want.

---

### Post by ntrgc89 on 2008-06-09
ok, thanks for the info.

I'm just wondering tho, why did this happen in the first place? And are those headers possibly linking to anything that won't be removed by taking out the stanzas as you recommend?

---

### Post by drs305 on 2008-06-09
StartUp-Manager is the safe way to edit grub and gives you a variety of options. Each time a kernel is introduced the default is to add it to the menu display. You can make changes through StartUp-Manager.

Check out this link that pretty much explains what you need/want to know about kernel displays in the grub menu:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by kansasnoob on 2008-06-09
Using startupmanager is definitely the safest way to deal with the situation.

---

### Post by ntrgc89 on 2008-06-09
I don't mind editing the grub list through terminal; I've done things like that before...

But I'm still really confused as to why this happened? Any ideas? Has it happened to anyone else?

---

### Post by Oldsoldier2003 on 2008-06-09
> **kansasnoob said:**
> Using startupmanager is definitely the safest way to deal with the situation.

actally the best way to deal with the situation is decide what kernel versions you no longer wish to have installed on your computer, then do a search in synaptic for linux-image. Mark the "extra kernels" for complete removal.

Synaptic will remove the kernels and update your menu.lst automagically.

edit : it is not a bad idea to keep at least one older kernel around in case you have a problem with your current kernel.

---

### Post by Oldsoldier2003 on 2008-06-09
> **ntrgc89 said:**
> I don't mind editing the grub list through terminal; I've done things like that before...
[B]
But I'm still really confused as to why this happened? Any ideas? Has it happened to anyone else?[/B]

When you install a kernel update through update manager it does not remove older kernel versions. when update-grub is called by the installation script, it just adds the new kernel to the top of the list making it the default kernel. This is by design, since it would be pretentious to assume that someone wanted kernels removed, and could also render a system unusable if the only remaining kernel proved to be inoperative for that system after updating.

---

### Post by unutbu on 2008-06-09
Every time you update your linux-image-* package, new files kernels and assistant files are added to your /boot directory, and your menu.lst is updated so you can boot the new kernel. 

To remove the files associated with a kernel you don't want to use, you'll want to remove the appropriate package. 

Suppose you want to remove the file /boot/vmlinuz-2.6.22-14-generic. (I don't have Hardy, so my file names are a bit different than yours). 

Type
> dpkg -S /boot/vmlinuz-2.6.22-14-generic
Give it a few seconds and it should return the name of the package that installed that file. In my case,
it returns 
```

linux-image-2.6.22-14-generic: /boot/vmlinuz-2.6.22-14-generic
```

Then to remove the package:
```

sudo apt-get remove linux-image-2.6.22-14-generic
```

I haven't tried this before, so I'm not entirely sure if Ubuntu will allow you to do this, though my guess is it will. If it can't it will complain about what dependencies would break. Either way, it should be safe to try.

---

### Post by Oldsoldier2003 on 2008-06-09
> **unutbu said:**
> Every time you update your linux-image-* package, new files kernels and assistant files are added to your /boot directory, and your menu.lst is updated so you can boot the new kernel. 

To remove the files associated with a kernel you don't want to use, you'll want to remove the appropriate package. 

Suppose you want to remove the file /boot/vmlinuz-2.6.22-14-generic. (I don't have Hardy, so my file names are a bit different than yours). 

Type

Give it a few seconds and it should return the name of the package that installed that file. In my case,
it returns 
```

linux-image-2.6.22-14-generic: /boot/vmlinuz-2.6.22-14-generic
```

Then to remove the package:
```

sudo apt-get remove linux-image-2.6.22-14-generic
```

I haven't tried this before, so I'm not entirely sure if Ubuntu will allow you to do this, though my guess is it will. If it can't it will complain about what dependencies would break. Either way, it should be safe to try.

In my opinion it is better to use synaptic than apt-get. Though i usually prefer the command line solution to almost any problem, using synaptic makes it a "no brainer" and cleans up after itself.

---

### Post by unutbu on 2008-06-09
I'm a complete APT newbie (having used RedHat for many years). Please explain. 

1) What does "cleans up after itself" mean?
2) Can Synaptic tell me what package provides a certain file?

---

