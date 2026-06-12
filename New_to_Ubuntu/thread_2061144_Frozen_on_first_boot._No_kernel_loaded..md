---
title: "Frozen on first boot. No kernel loaded."
date: 2012-09-21
forum: New to Ubuntu
---

### Post by MerlynMagdalen on 2012-09-21
I recently loaded Ubuntu 12.04 on an old laptop that barely worked and after I fixed the wireless adapter problem I decided I loved it, so I attempted to dual boot it on my Asus A52F. It performs the entire Wubi install and asks me to reboot. When I reboot it freezes on the first load page, forcing me to improperly shut down. When I boot again it brings up the grub, I entered boot and it tells me there is no kernel loaded. I've uninstalled and reinstalled 4 times, including running disk checks. How can I fix this? I would love to have Ubuntu on my Asus. Any help is appreciated.

---

### Post by NikTh on 2012-09-21
Hi , 
you must clarify something 

you said > **MerlynMagdalen said:**
> It performs the entire Wubi install 

and then you said > **MerlynMagdalen said:**
> When I boot again it brings up the grub

Wubi install (from withing Windows) has no grub at all. Windows boot-loader remains.

Did you install Ubuntu through wubi installer , or you did a regular dual-boot from a LiveCD/Usb ? 

Thanks

---

### Post by critin on 2012-09-21
> **NikTh said:**
> Hi , 
you must clarify something 

you said 

and then you said 

Wubi install (from withing Windows) has no grub at all. Windows boot-loader remains.

Did you install Ubuntu through wubi installer , or you did a regular dual-boot from a LiveCD/Usb ? 

Thanks

I think he means the screen to choose which os to enter.  Both should be there just like a regular dual boot.

---

### Post by MerlynMagdalen on 2012-09-21
It's Wubi. The screen after rebooting says GNU GRUB version 1.99-21ubuntu3.1
Then has  a message   Minimal BASH-like line editing is supported. For th first word, TAB etc;   I hit tab and it gives me a list of commands, one of which is boot, which I typed and then it said no loaded kernel.

---

### Post by critin on 2012-09-21
> **MerlynMagdalen said:**
> I recently loaded Ubuntu 12.04 on an old laptop that barely worked .

You probably should use a live cd to make sure it works on this machine before installing.  Ubuntu won't actually 'fix' *a barely working* laptop or a faulty Windows os.

---

### Post by MerlynMagdalen on 2012-09-21
This is after selecting Ubuntu in the OS menu.

---

### Post by MerlynMagdalen on 2012-09-21
Actually that PC is having no problems with Ubuntu, it is my Asus - which works great - that I am having trouble with. Would like to go Wubi if possible, since I don't want to risk losing any data.

---

### Post by critin on 2012-09-21
Did you try to boot windows yet?  Does it work?

---

### Post by critin on 2012-09-21
> **MerlynMagdalen said:**
> Actually that PC is having no problems with Ubuntu, it is my Asus - which works great - that I am having trouble with. Would like to go Wubi if possible, since I don't want to risk losing any data.

Aw, okay.  You're talking of two separate computers.  Got it now.

---

### Post by MerlynMagdalen on 2012-09-21
Yes windows works, although once in a previous install it asked me to do a disk check before booting.

---

### Post by jerrrys on 2012-09-21
Your Asus A52F seems to be compatible with ubuntu.  Maybe you should just create some free space on your HDD and dual boot.

 [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Asus+A52F&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Asus+A52F&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dual+boot+windows+7&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dual+boot+windows+7&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by MerlynMagdalen on 2012-09-21
I read that there was a risk of losing data this way, and I have information for work and school on this PC. Thought Wubi was the best option. Is loading a dual boot safe?

---

### Post by Old_Grey_Wolf on 2012-09-21
> **MerlynMagdalen said:**
> I read that there was a risk of losing data this way, and I have information for work and school on this PC. Thought Wubi was the best option. Is loading a dual boot safe?

You should have a backup of your important data before making changes to your computer's operating system or partitions.

I recommend a backup no matter how the operating system is installed. I have seen catastrophic results for people installing using any method.

It is easy to make a mistake, and sometimes trying to fix  the mistake when you haven't had experience can make things worse.

---

### Post by MerlynMagdalen on 2012-09-21
I guess that's what I will have to do. Thanks for the help

---

