---
title: "How do I run the menu.lst update?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by nowhere@cox.net on 2008-10-16
Hi, 

I just ran the system update tools which updated the kernel tonight. It asked in a seperate program to allow it modify the menu.lst file. I wasn't prepared and kernel updates almost alway goof up my desktop's booting due to mixed SATA and PATA drives in the box. So I said no and backed up my menu.lst file.

Now I don't know what command to run to make that nice configuration pgm to launch. Should I uninstall the latest kernel installed (21 I think. I am currently booted in 19).

Help!
Thanks!

---

### Post by taqkavar on 2008-10-17
Donnu the answer to your question, but you could alway do:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.backup2.lst
sudo /boot/grub/menu.lst
```

Then go to the line that says: 
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fc503a7e-dc3e-4f9f-b532-66448ba0822a ro
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

Or something like the above, Copy and paste it right below itself. then edit one of them and repace all the 19 s in 2.6.24-19-generic with 21s.
Should work, if this breaks your system, boot in 19 kernel and resotore your old menu.lst:

```
sudo cp /boot/grub/menu.backup2.lst /boot/grub/menu.lst
```

---

### Post by nowhere@cox.net on 2008-10-17
Actually, I tried that first but when I did, it did boot but it wasn't very clean and the graphic drivers loaded up in very low res. I'm guessing the nvidia drivers weren't loaded properly?

So Im staying with 19 for now but would like to know what's wrong. Im thinking about uninstalling everything .21 and re-running the system update...

Any other ideas?
Thanks!

---

### Post by kansasnoob on 2008-10-17
Why not just install startupmanager from synaptic or:

```
sudo apt-get install startupmanager
```

It'll then show up in System > Administration >

Then you can select which kernel to boot by default, but you can always hit 'esc' during boot and choose to boot the new kernel so you can play with the settings and get it right?

Maybe a dumb idea:confused:

---

### Post by Ptero-4 on 2008-10-17
You need to re-run the configuration for the nvidia propietary drivers. That way it gets the module for the 2.6.24-21 kernel.

---

### Post by taqkavar on 2008-10-17
did you install the graphic drivers provided from their website or using Envy? If so you need to re-install them after each kernel update, hopefully 8.10 will save us from this hassle in near future.

---

### Post by bodhi.zazen on 2008-10-17
LOL

When you do kernel upgrades, if you are running the Nvidia driver, you will need to reinstall it.

Try :

```
sudo update-grub
```

---

