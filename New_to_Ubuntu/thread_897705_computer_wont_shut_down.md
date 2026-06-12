---
title: "computer wont shut down"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Sturatt on 2008-08-22
I just installed ubuntu again yesterday. It seems though that whenever I try to shut down my computer from ubuntu, it freezes. The progress bar gets all the way down, and just sits there forever. This also happened the last time I had ubuntu installed, but I thought it had something to do with my problems during install. This time around, there werent any problems, but this one is still there.

Thanks for any help,
Stuart

---

### Post by WRDN on 2008-08-22
In the Terminal, type:

```
gksudo gedit /boot/grub/menu.lst
```

Now, remove the words "quiet splash" for the kernel line for the Ubuntu entry you boot. It will look something like this:

> kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=90ea8561-1dc6-4bb6-86bf-4ec61513e6cc ro 

Now, shutdown the PC. Instead of the status bar appearing, text will appear so you will be able to see exactly what is hanging. After you have found that out, the community should be able to offer further advice.

---

### Post by Sturatt on 2008-08-22
the last thing that shows is [96.914347] Power Down

---

### Post by wpshooter on 2008-08-22
My suggestion would be that you go into the BIOS (and first record all of the present parameter settings for all parameters - in case you need to go back to the current setup on some or all of the parameters) and then reset the BIOS to the default/fail safe parameters and then try your shutdown of Ubuntu and see if that helps.

---

### Post by alienexplorers on 2008-08-22
Try adding > acpi=force to the end of the kernel line you removed quiet splash from.

---

