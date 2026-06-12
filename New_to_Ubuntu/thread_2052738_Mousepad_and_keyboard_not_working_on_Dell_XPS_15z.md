---
title: "Mousepad and keyboard not working on Dell XPS 15z"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by sinistershades on 2012-09-03
Hi. I recently installed Ubuntu, but ran into the issue that my mousepad and keyboard are not responding when I run Ubuntu.

I do have a USB mouse and that is working. Though, whenever I click on something (like the power button or anything at the top) it will automatically select what ever my mouse scrolls over. I don't even have to click. It also opens 20 or so windows if I click on something once.

Please help, as I do want this OS. Thanks!

---

### Post by MyVitalRemains on 2012-09-03
Have you tried using the mouse to access the "Additional Drivers" application, so as to check whether you need any additional proprietary drivers. 

Also what kind of keyboard do you have?

---

### Post by sinistershades on 2012-09-03
> **MyVitalRemains said:**
> Have you tried using the mouse to access the "Additional Drivers" application, so as to check whether you need any additional proprietary drivers. 

Also what kind of keyboard do you have?
No.
I have an internal laptop keyboard. It isn't USB.

---

### Post by Bashing-om on 2012-09-04
--shades... 

Here is a solution... try and advise us:
**Boot options**

 Add  to the grub boot line the following options by pressing [e] when on the  grub loading page, and add the following just before *quiet splash* : 
   acpi=noirq 
  
To keep these option edit the grub command. Execute this in a terminal : 

```

gksudo gedit /etc/default/grub


```and modify the line :    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
  
 to obtain this line : 
   GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq quiet splash" 
  
Then, save, close, and back in the terminal, execute :
```

sudo update-grub


```Now, when you will restart, it should be great. 

The use of gksudo & sudo requires your pass word, will get no echo to the screen (security reasons).

[INDENT]HTH <==BDQ
[/INDENT]

---

### Post by MyVitalRemains on 2012-09-04
Did it work on the LiveCD?

---

