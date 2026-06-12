---
title: "[SOLVED] ATI Radeon 7000 IGP - Change brightness??"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Tom--d on 2008-05-17
I need to change the brightness of a laptop screen.

I cannot change it by, the function key. nor by the brightness applet for the gnome panel.

**How can I change the brightness?!**


I do not think that I have the proper driver installed for it. 
How do I find out? 
How do i install the correct one and get the right. I do not mind if compiz doesnt work. As its only for a laptop which is for internet, email etc. 

Just want brightness dimmed!! Thats really what I want. Compiz is a bonus :D

Thanks,
Tom

---

### Post by Tom--d on 2008-05-17
Anyone?

---

### Post by mitar on 2008-05-17
You can run this command to change the brightness

sudo -s
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness
exit

You can replace the 50 with:
37 12 25 37 50 62 75 87 100

100 is full brightness 50 is half brightness ect.

---

### Post by Tom--d on 2008-05-17
It does not work :(

the output was:

```
kevin@laptopk:~$ sudo -s
root@laptopk:~# echo -n 50 > /proc/acpi/video/VGA/LCD/brightness
bash: /proc/acpi/video/VGA/LCD/brightness: No such file or directory
```

:(

---

### Post by Tom--d on 2008-05-17
I can ajust the gamma, but not the brightness.

---

### Post by mitar on 2008-05-17
I don't know. Try looking for existing threds. There have been several issues about this. For instance, try [http://ubuntuforums.org/showthread.php?t=743329](http://ubuntuforums.org/showthread.php?t=743329)  It's long but maybe you ll find the answer.

---

### Post by Tom--d on 2008-05-17
Nothing :(

How do I enable the ATI driver foo 7000?

---

### Post by Tom--d on 2008-05-17
I can only do it through BIOS
It is a acpi problem

---

### Post by krash182 on 2008-05-28
> **Tom--d said:**
> Nothing :(

How do I enable the ATI driver foo 7000?

It seems you can't  I've gotten nowhere with the forum posts and support. EnvyNg wothless, termanal commands worthless, Ubuntu 8.04 worthless

---

### Post by tunznath on 2008-05-30
OK I am trying to find drivers for Mobility radeon 7000IGP as well - everything seems to work OK except the graphics card on my machine - is there anyone who knows or can help???

---

### Post by tunznath on 2008-06-03
I just got an downloaded update for fglrx or flgrx whatever it is called todayand now 3D with my radeon 7000 works  THANKS TO WHOEVER WROTE THE UPDATE - now i just need to figure out how to get it to work really well - are there settings thatcan be used for 3D??

---

