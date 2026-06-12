---
title: "windows xp on ubuntu"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by davarse on 2008-05-15
hi everyone,
hi just wandering, can i running windows xp on my gusty gibbon??
does anyone know how to do that...

---

### Post by AcidHawk on 2008-05-15
Try Virtualbox..
```

sudo apt-get install virtualbox

```

My virtual xp server runs quicker in virtualbox than if I had to boot it from a seperate partition.

---

### Post by sharks on 2008-05-15
This may help you:
[http://news.softpedia.com/news/Unite-Windows-and-Linux-With-a-Single-Mouse-Click-78535.shtml](http://news.softpedia.com/news/Unite-Windows-and-Linux-With-a-Single-Mouse-Click-78535.shtml)

---

### Post by shifty_powers on 2008-05-15
don't use the one in te repos. use the full version from the virtualbox site that will allow you to install the guest additions. gives you more functionality.

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by AcidHawk on 2008-05-15
You can download the VBoxGuestAdditions.iso then when you try to install the addons from VirtualBox you will be asked where the iso file is.

I had no problems installing Addons for WinXP or Mandrake 2007.1 so far.

---

### Post by lazyart on 2008-05-15
There is also VMWare, the grandaddy of virtualization products.

---

### Post by Robocoastie on 2008-05-15
I have WinMCE2005 and also WinVista upgrades available. Currently I'm dual booting WinMCE2006 (got tired of Vista's slowness and other problems) with Ubuntu Hardy.

My question is what is the best way to virtualize my windows install? The problem is that my WinXP is of course a Dell version which doesn't recognize Dell hardware in a virtual machine and requires activation which of course doesn't work even when the code from my computer is punched in.

Can the partition be imaged perhaps and installed in a virtual machine that way? Or should I just pick up (another) WinXP license and be done with it?

thanks,
Rob

---

### Post by Achetar on 2008-05-15
Yes, it could be imaged and then put on the virtual disk. I recommend VirtualBox over VMWare because VBox is totally free.

---

### Post by Robocoastie on 2008-05-15
what do I image it with to make this work?

---

### Post by Tatty on 2008-05-15
If you are dual booting, there is a way of booting your already-installed windows partition in a virtual machine.  

There was a question about this a week or two ago on here, and someone posted some links on how to do it. Im not sure where though, have a search.

---

### Post by davarse on 2008-05-21
hi everyone, i have one more question, do i actually can use the same open software program (skype,etc) both for xp and ubuntu if i'm install xp in use virtualbox. or do i have to intall different one for windows xp....

cheers'

---

