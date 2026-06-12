---
title: "Compiz Fusion on Hardy"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by akimatsu123 on 2008-04-26
Hi,

I installed a fresh install of hardy yesterday. I have an ATI video driver.  Previously, i had Gutsy, and my compiz fusin worked fine with xgl. 

Hearing that xgl is no long required in Hardy, and that the suspend feature is better (which it indeed is i can suspend my T60p now :D) i decided to switch to hardy and get a fresh start. 

but whenever i try to start compiz from the appearance menu, i get a dialog saying "Desktop effects could not be started"

I also tried "compiz --replace" from the terminal, and it gave me 
```

Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

```

So i thought okay, let me install xgl then. but when i did that, compiz fusion did indeed work, but at an unbelievably slow and glitch way that made my computer basically unusable. so i had to uninstall that. 

now i am compiz-fusion less. how do i get it back? i find it very difficult to not be able to switch between desktops with my keyboard, zoom into text, etc. 

how should i fix this problem? thanks in advance.

---

### Post by Thingymebob on 2008-05-12
First I would recommend you have a good read of [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

if you type fglrxinfo in a terminal you should get something like
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.1.7412 Release
```
While you have xgl installed the OpenGL vendor string will probably read Mesa.

remove xgl, check your xorg.conf you probably have a section that reads
```

Section
   Option "AIGLX" "off"
End Section

```
If you do back up your xorg.conf and remove it.

This was a line that needed to be added a while back to get ATI cards to work with compiz.

As the latest drivers are compatible xgl and the AIGLX option are no longer needed.

---

