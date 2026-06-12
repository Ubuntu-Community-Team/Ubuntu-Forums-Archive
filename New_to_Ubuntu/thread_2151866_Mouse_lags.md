---
title: "Mouse lags"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by FERFA on 2013-06-06
Alright so I'm new to Ubuntu. I just switched entirely over from Snow Leopard. I'm now 100% commited to be frustrated for months learning a new OS but I'm excited. Anyways I've started off on a really really excruciatingly bad note. I use my Macbook track pad and it lags like a banshee on this. I went into settings and fiddled, nothing. So I took to the Internet and found this post...

[http://ubuntuforums.org/showthread.php?t=1343689&highlight=mouse](http://ubuntuforums.org/showthread.php?t=1343689&highlight=mouse)

My problem though is I can't open the Xorg file. Says something about needing an application that can open shared libraries. I'd be searching for this on my own but it's so painfully slow for me I need to just ask and get this solved so I can truly begin learning and experiencing Ubuntu. I also can't figure out how to use a right click. On Leopard it was control + click on the track pad. 

Computer: Macbook
My driver is... Intel® 965GM x86/MMX/SSE2 

If there's anything else you need to know I'll be happy to fill you in and thanks for your patience.

---

### Post by Isamu715 on 2013-06-06
*/etc/X11/xorg.conf* doesn't exist in Ubuntu by default, you need to create it.

---

### Post by sandyd on 2013-06-06
moved to absolute beginners section

---

### Post by FERFA on 2013-06-06
Okay I'd love to be able to create the file but I have no idea how. I tried right clicking (I figured out how to set that up in some compacity) but there was nothing. So I know where to add it, but how do I go about creating it? Do I go into some program like textedit or something?

---

### Post by Isamu715 on 2013-06-06
First, your text editing program on Ubuntu is called gedit(shows up as "Text editor" in the Dash), you can use it to create text files either by opening the editor directly and saving the file in your desired location or by right-clicking and selecting *Create New Document > Empty Document* from the menu.

Secondly, system configuration files(like those located in */etc*) need to be created/edited with administrative provileges(as root), to open gedit as root press Alt+F2 and type:
```
gksudo gedit
```
enter your password and you'll be able to create the file you need. Just enter or paste the contents and save it as *xorg.conf* in the */etc/X11* folder.

---

### Post by FERFA on 2013-06-06
Thanks. Your suggestion worked kind of. It's still not smooth though like Mac OSX was. Wonder if there's some program or something.

---

### Post by Cvxcvgg on 2013-06-06
There's always the option of checking your drivers. It's always a good idea to update those, in my opinion.

---

