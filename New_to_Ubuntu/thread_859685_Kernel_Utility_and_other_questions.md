---
title: "Kernel Utility and other questions"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Mobidoy on 2008-07-14
Hello all, in my quest of knowledge, i am starting to learn tweaking and optimization.

I want to look at the kernel options and slowly create a custom one. Is there an utility (could not find one) to create and save a kernel profile which i could edit as i go ? 

Also, is there somewhere to learn the options for keyboard, mouse, video, network, sound etc... How to edit/what are the options for files like xorg.conf, rc.conf (i think) and any other files that can be edit to have a custom configuration ? 

I have Kernelcheck installed and, i got to the point of setting the options for my kernel but, i want to go thru it slowly, to understand what they are and what is needed on my system :) 

Thanx again

---

### Post by Mobidoy on 2008-07-14
Anyone ?

---

### Post by weirdfox on 2008-07-14
Well if you want to reconfigure your kernel you need to rebuild it.
So here's a quick howto (from my memory).

[INDENT][COLOR="DarkRed"]WARNING[/COLOR]: playing with your kernel might cause some big problem on your computer, always be careful of what you change !!![/INDENT]

Get the sources:
```
sudo apt-get install linux-source
```

This will download the current kernel's code (tarball) in /usr/src.  

(From here you might want to get root, be carful of your actions as it may have an impact on your PC)

Extract it.
Go in the newly created folder
Copy your current configuration from "/boot/config-<your current kernel version>" to ".config"

You will be able to modify the kernel's config with:
```
make xconfig
```

When your kernel is configured,  you need to compile it:
```
make && make modules
```

To install it:
```
make install modules_install
```

To try your newly compiled kernel, you will need to configure your grub to boot it.


**I strongly recomand to read thes as they will provide more info on the kernel :**
[INDENT][http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html)
[http://www.linuxdocs.org/HOWTOs/Kernel-HOWTO.html](http://www.linuxdocs.org/HOWTOs/Kernel-HOWTO.html)[/INDENT]


I hope this helps, have fun !

---

### Post by Mobidoy on 2008-07-15
Nice thanx, sure i will read those.

Still looking for the utility to create a kernel profile tho, when i started kernelcheck , it started something called qconf or something like that, i have looked in the menus and found out that i could load and save a kernel profile.

But sadly, i dont have the right name or this is not in synaptic packages :( 

I did not had time to do it earlier and, i want to take my time to build the profile for my computer so, i need to look at all ticks, see what they do, look up the web if i am not sure etc... That way, i should have the optimum config for my notebook and would only need to apply that profile when a new kernel is released :)

---

### Post by sdennie on 2008-07-15
If you know where kernelcheck installed the kernel source code, you can go into that directory and type either:

```

make xconfig

```

or

```

make menuconfig

```

Then you can use the normal Save/Load for your config as many times as you like.

---

### Post by Sef on 2008-07-15
Don't bump your thread unless 24 hours has gone by.  If you do, you could get an infraction.  You will not get one this time, but please be patient in the future.  Everyone here is a volunteer, so at times, it does take to get a response.

---

### Post by Mobidoy on 2008-07-15
> **Sef said:**
> Don't bump your thread unless 24 hours has gone by.  If you do, you could get an infraction.  You will not get one this time, but please be patient in the future.  Everyone here is a volunteer, so at times, it does take to get a response.

Oups, sorry, promise i wont do it again :)

---

