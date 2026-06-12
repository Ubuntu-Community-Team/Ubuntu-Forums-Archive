---
title: "Grub theme does not change"
date: 2023-08-31
forum: New to Ubuntu
---

### Post by lovedlx on 2023-08-31
I have a pc with two hard drives
the main one has ubuntu 23.04 and the secondary windows 10
I followed several tutorials to theme grub with grub customizer (I had even done it a long time ago with another pc)
but when doing everything the tutorials say and ending with the command:
*$ sudo update-grub*
when restarting nothing happens, grub continues with the same black theme as always
even using the *sudo $ update-grub* command outputs:
```
Found theme: /boot/grub/themes/crt-amber-theme/theme.txt
```
so it's supposed to show up
even in grub customizer the theme appears with all its corresponding images but I don't know what I can do to solve this and I would really appreciate it if you could help me

---

### Post by Dennis N on 2023-08-31
You need to enable the theme in /etc/default/grub.

Add a line similar to this example with the path to your theme.txt file. Then run sudo update-grub.

```
GRUB_THEME=/usr/share/grub/themes/breeze/theme.txt
```

---

### Post by lovedlx on 2023-08-31
ok add the line that you put editing it so that it is the theme that I want to use and then I put  *sudo update-grub*  and restart the pc
but still nothing happens, I used the  *sudo update-grub*  command and this time the message of *Found theme: /boot/grub/themes/crt-amber-theme/theme.txt* did not appear

---

### Post by Dennis N on 2023-08-31
O.K, I looked at your theme, and managed to get it to install. A tricky business.
You need to create a new text file:
```
/etc/default/grub.d/init-select.cfg
```
It's a dummy file to workaround a bug. The contents apparently doesn't matter! My file's contents:
```
# Work around file needed for grub themes
```
Also, the resolution of the result can be wrong. Add a line to /etc/default/grub: 
```
GRUB_GFXMODE=1920x1080,auto

```
Change 1920x1080 to fit your screen resolution if necessary.

Also, the path to the theme may need to be in quotes!
```
GRUB_THEME="/usr/share/grub/themes/crt-amber-theme/theme.txt"
```
When done, run sudo update-grub and reboot.

---

### Post by lovedlx on 2023-08-31
I did everything you said and still nothing
Isn't it a conflict with my two hard drives? since in the first drive I have two partitions, one of 5 GIB has FreeDOS installed (it is to boot windows 98) and the other that is 69.53 GIB has Ubuntu 23.04 installed and the second drive only has Windows 10
in the bios the drive with ubuntu is the main one but I don't know why there is something that tells me that what doesn't let me change the theme is related to what was mentioned

---

### Post by Dennis N on 2023-08-31
I don't see how having two drives would have anything to do with it. I have two drives too. Put the grub theme folder where I have it instead of in /boot/grub/themes. 
Because, if you install a grub theme from Ubuntu repository, /usr/share/grub/themes  is where they get installed by the package manager (as in post #2). It's apparently the preferred location now. 

I got  the crt-amber theme from gnome-look.org. 

You might try one with an install script included. Like Vimix - I downloaded the **Vimix-1080p.tar.xz** file which contains a script to install everything correctly. I like how Vimix looks.

---

### Post by lovedlx on 2023-08-31
I don't know why Grub refuses to change the theme
but i have tried everything
put the theme in /boot/grub/themes
try the themes in /usr/share/grub/themes
change the resolution
use grub customizer
use sudo nano /etc/default/grub and edit it
I tried using vimix as you told me with the installer script but neither
The only thing I have left is to try to put a fallout theme that I found as a second option but I doubt it will work and I don't even know why grub doesn't want to do it
And I had already done this changing the theme at the beginning of the year with two laptops (and in fact I used the same crt amber theme) and it worked
The only thing that occurs to me is that since I am now using ubuntu 23 instead of ubuntu 22 but nothing else
It's very weird

---

### Post by Dennis N on 2023-08-31
Well, it **could** be related to using grub customizer. I'm surprised the script did not work. I haven't used grub customizer myself, so I only know what I have read over time. You can find pros and cons about its effects on grub, but among our frequent Ubuntu forum users, my impression is the majority would not recommend it.    

Some negative articles:

[https://forum.endeavouros.com/t/faq-why-you-should-not-use-grub-customizer/37844](https://forum.endeavouros.com/t/faq-why-you-should-not-use-grub-customizer/37844)
[https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html](https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html)

Of course, you can also find some positive articles with Google search. So there's that.

You could post your **/etc/default/grub** file as it appears after using the install script, and we can take a look at it.

---

