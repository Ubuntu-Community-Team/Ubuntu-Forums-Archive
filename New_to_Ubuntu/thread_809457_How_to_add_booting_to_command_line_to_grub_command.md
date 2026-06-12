---
title: "How to add booting to command line to grub command line options"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by osnewbie on 2008-05-27
Hi,

I jus got into the Ubuntu world, recently installed Hardy Heron (server edition 8.04). 
I also installed the desktop so i could have gui access (windows has handicapped me). All this on an already existing Windows XP installation.

So what I have when i boot up the system is a list to select an OS which has 3 Options
1. boot to ubuntu - which boots to the gui
2. boot to ubuntu-recovery
3. boot to windows xp 

What I will like to achieve is to add a 4th option

boot to command line. to allow me some quick and dirty command line access for running commands as root..etc.

Thanks y'all

P.S i searched all the forums but didn't find a solution,(even ran that "check if already posted thingy")

---

### Post by philinux on 2008-05-27
That would be the recovery option for serious problems.

However All you really need is, Application >Accessories> Terminal after you boot up normally

---

### Post by osnewbie on 2008-05-27
I need to reiterate what i want to achieve is to add a 4th option
when my machine boots up that allows me to from the boot up menu list
select boot to command line.

---

### Post by philinux on 2008-05-27
Thats what I said.

2. boot to ubuntu-recovery

Try it.

---

### Post by tramir on 2008-05-27
I think what you want is to boot into a different runlevel. Maybe [this thread]("http://ubuntuforums.org/showthread.php?t=201130") can help.

---

### Post by Amstell on 2008-05-27
Well as mentioned above, if you boot into recovery mode, that will bring you into the CLI
 
but if you want to edit the boot menu just 

vi /boot/grub/menu.lst

edit it, save, and reboot

Good luck

---

### Post by Majorix on 2008-05-27
Perhaps you want to see GDM removed? GDM forces a graphical login screen. Remove it using Synaptic.

---

### Post by osnewbie on 2008-05-29
> **Majorix said:**
> Perhaps you want to see GDM removed? GDM forces a graphical login screen. Remove it using Synaptic.

no.
just want to have an option to boot to CLI which is not the recovery mode

---

### Post by osnewbie on 2008-05-29
> **Amstell said:**
> Well as mentioned above, if you boot into recovery mode, that will bring you into the CLI
 
but if you want to edit the boot menu just 

vi /boot/grub/menu.lst

edit it, save, and reboot

Good luck


spot on my man..seen some posts on this, but i opened mine..and its no mean feat..
the instructions are sketchy then I look at the earlier config for the existing options and for example i can't replicate a Command line boot.

---

### Post by osnewbie on 2008-05-29
> **philinux said:**
> Thats what I said.

2. boot to ubuntu-recovery

Try it.

I tried it and it's not what I want.
1. Its a recovery mode, i want a regulare mode that is just command line, like what you get when you install the server version of hardy heron.

2. i don't know if it defaults to that but the ubuntu-recovery mode logs you in as root without requesting for a password, that can't be good (read security risk!)

so does this explain what i desire better?

appreciate your/any help

---

### Post by bodhi.zazen on 2008-05-29
In Ubuntu all run levles 2-5 are all the same, default is run level 2

Select a run level to modify so as to boot to a comand line, say run level 3

Now lets make a small modification and then add a stanza in grub.

1. Edit run level:

```
sudo mv /etc/rc3.d/S30gdm /etc/rc3.d/s30gdm
```

2. Edit /boot/grub/menu.lst, copy your current stanza for Ubuntu , add to the end of the kernel line, like this :

> title           Ubuntu, Command line
root            (hdx,y)
kernel          /boot/vmlinuz-xyz root=/dev/sdxy **3**splash quiet
 initrd          /boot/initrd.img.xyz
quiet
savedefault
boot


You just need to modify the x - y -z part to point to the proper partition / kernel / initrd


See also this bug report : [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014)


You may need to edit run level 2 and then start GDM if desired.


An alternate is to replace upstart :


```
sudo apt-get install sysvinit
```

---

