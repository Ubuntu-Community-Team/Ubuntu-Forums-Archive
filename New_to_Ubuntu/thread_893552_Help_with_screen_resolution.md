---
title: "Help with screen resolution"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by aagavin on 2008-08-18
How do I increase the screen resolution???

when I go to the screen resolution menu it doesnt have anything bigger that 800 * 600

I want it to be 1024 * 768

How would i do this 

thx

---

### Post by SuperSonic4 on 2008-08-18
Have you installed the proprietory graphics card drivers using System -> Admin -> Hardware?

---

### Post by cdtech on 2008-08-18
Is this a new install?

What video card are you using?

---

### Post by nkri on 2008-08-18
```
gksu displayconfig-gtk
```

A window will pop up asking for your password; type it in and hit enter.  There will then be a box for the resolution.  Change it to 1024x768 and click OK.

Reboot.  At this point, it should be the right resolution.  If not, post the output of
```
lspci
```

Good luck!
-nkri

---

### Post by aagavin on 2008-08-18
```

gksu displayconfig-gtk

lspci

```

????

sorry I am new to ubuntu where do I enter that code???

thx

---

### Post by Ryadt on 2008-08-18
> **aagavin said:**
> ```

gksu displayconfig-gtk

lspci

```

????

sorry I am new to ubuntu where do I enter that code???

thx
Enter the command in the terminal. Applications > Accessories > Terminal

---

### Post by nitro_n2o on 2008-08-18
You might want to try this in the terminal as well 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I'm sure once you answer all the questions asked your problem will be solved

---

### Post by aagavin on 2008-08-20
> **nkri said:**
> ```
gksu displayconfig-gtk
```

A window will pop up asking for your password; type it in and hit enter.  There will then be a box for the resolution.  Change it to 1024x768 and click OK.

Reboot.  At this point, it should be the right resolution.  If not, post the output of
```
lspci
```

Good luck!
-nkri
Thanks that solved the problem

---

### Post by Nylo on 2008-09-03
> **nkri said:**
> ```
gksu displayconfig-gtk
```

A window will pop up asking for your password; type it in and hit enter.  There will then be a box for the resolution.  Change it to 1024x768 and click OK.

Reboot.  At this point, it should be the right resolution.  If not, post the output of
```
lspci
```

Good luck!
-nkri

I tried it and it didn't work. I did go from 60 to 61 mhz.  I did the ispci and it showed my card but no higher res than 800 x 600. My card is Intel 82815, ie. Intel 815.

---

### Post by Nylo on 2008-09-03
> **Nylo said:**
> I tried it and it didn't work. I did go from 60 to 61 mhz.  I did the ispci and it showed my card but no higher res than 800 x 600. My card is Intel 82815, ie. Intel 815.

Any other ideas?

---

