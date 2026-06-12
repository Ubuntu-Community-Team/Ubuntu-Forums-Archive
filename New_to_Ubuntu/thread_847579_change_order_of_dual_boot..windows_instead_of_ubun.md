---
title: "change order of dual boot..windows instead of ubuntu.."
date: 2008-07-02
forum: New to Ubuntu
---

### Post by katzpiketailes on 2008-07-02
hi, i wanted to change the boot order so that it opens up windows first instead of ubuntu..

i opened the terminal in ubuntu and typed in sudo gedit /boot/grub/menu.lst

afterwards, it asked for the password and an editor with a tab that says "menu.1st" opened up...
however, there was NOTHING written in it.. so i can't edit anything 

is this normal? and what can i do to change the boot order?

thank you.. pls help me ASAP.:(

oh and btw.. i have ubuntu 8.04

---

### Post by ibutho on 2008-07-02
The file should not be blank. Run ALT-F2 and enter "gksudo nautilus" and navigate to /boot/grub and then open the menu.lst file with gedit. Is it blank?

---

### Post by flaggh on 2008-07-02
> **katzpiketailes said:**
> 
i opened the terminal in ubuntu and typed in sudo gedit /boot/grub/menu.lst


It looks like you typed menu.1st (1st as in first) not menu.lst (as in lowercase LST)

This could explain why the file did not exist.

---

### Post by unutbu on 2008-07-02
```
gksudo gedit /boot/grub/menu.lst
```

Make sure you type menu.lst with an "ell", not a one.

Also, use gksudo when running graphical applications as root.

---

### Post by drs305 on 2008-07-02
You probably mistyped the address or are doing it from the livecd. In any case, I'd recommend installing and using StartUp-Manager. It is safer than editing menu.lst and it a very easy gui-based app. You can set Windows or any linux kernel to be your default. You can also set a variety of other boot options such as displays, menu display time, number of kernels to boot, etc.

To Install:
```
sudo aptitude install startupmanager
```

To run:
gksudo startupmanager
or 
System, Administration, StartUp-Manager

On the main page you can set the default OS.

[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by katzpiketailes on 2008-07-02
ok i mispelled it and type (first) --1st instead of lowercase LST...:D:lolflag:

now the menu is up.. what do i do next?

---

### Post by Sealbhach on 2008-07-02
> **katzpiketailes said:**
> hi, i wanted to change the boot order so that it opens up windows first instead of ubuntu..



Do you mean that you want Windows to appear first on the list, with Ubuntu in "Other Operating Systems" ?



.

---

### Post by katzpiketailes on 2008-07-02
yeah i wanted to change the order of the list so that windows is on top...

could i just rearrange thelist?

also, if i just change the number in the line:

default 0

would the list of operating systems will still show up when i start my comp? or will it automatically go straight to the operating system i set it to?

thank you soo much!!!:KS

---

### Post by logos34 on 2008-07-02
yes, you'll still see the list.

If you want windows on top AND as default OS, leave it '0' and do this:

> ...

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

[COLOR=Blue]**[put windows stanza here]**[/COLOR]

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

...

---

### Post by katzpiketailes on 2008-07-02
THANK YOU SOOO MUCH GUYS!!!!

everything worked out perfect!:KS:KS

---

