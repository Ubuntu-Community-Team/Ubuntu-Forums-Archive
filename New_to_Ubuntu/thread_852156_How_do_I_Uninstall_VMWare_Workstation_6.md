---
title: "How do I Uninstall VMWare Workstation 6?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by oxsyn on 2008-07-07
I downloaded & installed VMWare Workstation 6, downloaded directly from vmware.com.  I was just trying it out.  I want to uninstall it now, but apparently I'm a complete noob and don't know how, since I didn't install it via my beloved synaptic package manager.  I can't seem to find an uninstall script (perhaps I just don't know where to look).

The vmware installer modifies quite a bit of the system, so I don't want to try to manually remove it and frick my system all up.

Please help!
Thanks.

---

### Post by bumanie on 2008-07-07
Usually > sudo aptitude remove <package name> will remove anything you have installed. Never tried with vmware, but that is a fairly standard uninstall procedure.

---

### Post by oxsyn on 2008-07-07
> **bumanie said:**
> Usually  will remove anything you have installed. Never tried with vmware, but that is a fairly standard uninstall procedure.

Just tried that, ran the command ```
sudo aptitude remove vmware
```.  It ran through an uninstaller, but I don't think it worked correctly (didn't throw any noticeable errors though).

In my applications menu, I still see the VMWare Player & Workstation.  In a terminal, if I type ifconfig, I still see all the vmware adapters.

Any ideas?  I tried restarting after the uninstaller, no difference.

---

### Post by oxsyn on 2008-07-08
For anyone else trying to find this answer:  The vmware installer creates a file /usr/bin/vmware-uninstall.pl.

The command: sudo ./usr/bin/vmware-uninstall.pl will remove vmware from your system.

---

### Post by Marcial Contreras on 2008-09-04
I had the same problem and 

```
me@mygraybox:/usr/bin$ sudo ./vmware-uninstall.pl
```

worked just fine :guitar:

---

### Post by Arminius on 2009-02-10
I tried all that? and all I'm getting is sudo: ./vmware-uninstall.pl: command not found

---

### Post by Tomyec on 2009-02-20
Browse /usr/bin/vmware-uninstall.pl and run in console with sudo, I do it

---

### Post by tombott on 2009-02-20
From the command you need to type the following:
```
sudo ./usr/bin/vmware-uninstall.pl
```

Or
```

cd /usr/bin
sudo ./usr/bin/vmware-uninstall.pl
```

Don't try to remove Vmware via apt-get!

---

### Post by alanchen8197 on 2009-10-07
for anyone still need to uninstall VMWare Workstation 6 here are the commands

> cd /usr/bin
sudo vmware-uninstall


That's it!!!

alan

---

### Post by johanneslandin on 2009-12-16
```
sudo su
vmware-installer -u vmware-workstation
```

---

### Post by sdoolman on 2010-02-21
> **johanneslandin said:**
> ```
sudo su
vmware-installer -u vmware-workstation
```

**Thanks! Worked though I didn't have the vmware-uninstall.pl**

---

### Post by thikidflyss on 2010-07-10
> **johanneslandin said:**
> ```
sudo su
vmware-installer -u vmware-workstation
```

This worked for me :)

Thank you. I've been trying for over an hour now to remove it since VirtualBox is much better and free!

---

### Post by xavierzhao on 2011-03-18
> **johanneslandin said:**
> ```
sudo su
vmware-installer -u vmware-workstation
```

Thanks it worked for me!

---

