---
title: "How Do I Get to Command Line"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Flirtilizer on 2008-09-12
How do I get to the command line.  Not that I'll know what to do when I get there.  :)

---

### Post by SunnyRabbiera on 2008-09-12
Easy, in your menu's under applications go to "accessories"
then go to "terminal".
With any luck you may barely even have to touch the command line, as Ubuntu has many graphic tools built in for most functions.

---

### Post by chris062689 on 2008-09-12
Applications > Accessories > Terminal

---

### Post by Vivaldi Gloria on 2008-09-12
To open a Terminal do as follow:

    *      Choose Applications &#8594; Accessories &#8594; Terminal;

    *      Or press Alt+F2 and type gnome-terminal.

See 

[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

---

### Post by iaculallad on 2008-09-12
Or press Alt+F2 and input "gnome-terminal" (w/o quote) and press Enter key.

EDIT: Or if you like, you could integrate the Terminal on your mouse right-click. So you could just perform a right-click when inside a folder, automatically, the terminal path would reflect your current folder location.

```
sudo apt-get install nautilus-open-terminal
```

---

### Post by Flirtilizer on 2008-09-12
Thanks all, I saw that but thought it was a way to log in to another system so I didn't click on it.  :)

---

### Post by SunnyRabbiera on 2008-09-12
> **Flirtilizer said:**
> thought it was a way to log in to another system so I didn't click on it.  :)

well it can be, the terminal is quite versatile.
From starting up applications to shutting down the OS the terminal can do it all.

---

### Post by crazypenguin2008 on 2008-09-12
i love using terminal to do tasks. if you can learn the commands it makes life simple. ive got tons of commands and what they do saved to a usb drive. all i do is mount the flashdrive and copy paste and it does its thing....


Jas'

---

### Post by SunnyRabbiera on 2008-09-12
> **crazypenguin2008 said:**
> i love using terminal to do tasks. if you can learn the commands it makes life simple. ive got tons of commands and what they do saved to a usb drive. all i do is mount the flashdrive and copy paste and it does its thing....


Jas'

for the beginner though the terminal is scary, luckily the terminal is becoming less of a hassle since I started, in just 4 years I have seen Linux progress better then windows could in 10.

---

### Post by eentonig on 2008-09-12
Another way (and sometimes usefull is you're GUI seems frozen) is the key combinaten > <Ctrl>+<Alt>+<F1...6,8...12> 
(Thats one of these function keys on top of your keyboard, except F7)

This switches from your current terminal (the GDM session everybody calls the desktop)to on of the other available TTYs. They're all CLI based and you'll need to login again. But you get a full screen cli at your disposal to remediate or verify if you experience issues under Gnome.

To get back to your GUI, just issue the same command with <F7>

---

### Post by crazypenguin2008 on 2008-09-12
i agree. i started using linux in collage,about 4years ago and it has improved and progressed imensly. 

but im kinda oldschool and i rember using terminal in DOS to play leisure suit larry on my first pc when i was in gradeschool

oh the way times have changed

---

### Post by iaculallad on 2008-09-12
> **eentonig said:**
> Another way (and sometimes usefull is you're GUI seems frozen) is the key combinaten  
(Thats one of these function keys on top of your keyboard, except F7)

This switches from your current terminal (the GDM session everybody calls the desktop)to on of the other available TTYs. They're all CLI based and you'll need to login again. But you get a full screen cli at your disposal to remediate or verify if you experience issues under Gnome.

To get back to your GUI, just issue the same command with <F7>

Doing the above suggestion will bring you to what we call the "Virtual Terminal" (VT), this emulates the Terminal (gnome-terminal). This is the terminal that you often see on Server builds (no desktop environment).

---

