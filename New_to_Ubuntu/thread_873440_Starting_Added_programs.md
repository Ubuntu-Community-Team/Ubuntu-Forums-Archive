---
title: "Starting Added programs"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by ntu on 2008-07-29
I wonder how to start using programs that have been installed via Applications>Add/Remove?

I have just installed gparted by this method, but now do not know how to find/start it.

I am using Ubuntu Feisty.

Help appreciated.

---

### Post by ConMan318 on 2008-07-29
GParted is in System > Administration > Partition Editor.

In general though, you can hit Alt+F2 and type the name of the program, or even better, run it from the command line.  If you need to know where a program is located (useful for making a launcher) you can always type "which programName" in the terminal.

```

connor@connor-desktop:~$ which gparted
/usr/bin/gparted

```

---

### Post by ntu on 2008-07-29
Thank you for your informative post ConMan.

Just for your info, Gparted is not at System > Administration > Partition Editor in my Feisty Ubuntu 7.04. There is no "Partition Editor" in the "Administration" menu

---

### Post by SunnyRabbiera on 2008-07-29
it may not be there then, check around the other menus and if it isnt there we can tell you how to manually add it to the menu's

---

### Post by ntu on 2008-07-29
NO, it isn't in any of the menus.How to add it please?

---

### Post by ConMan318 on 2008-07-29
Hm, try to right-click on System, then go to 'edit menus'.  On the left, go down and click 'System'.  Then, on the corresponding list on the right, see if there is an unchecked 'partition manager' item.  If so, check it.  I don't know if those instructions will work in Feisty; if they don't, then I can't help you.  Sorry.

---

### Post by ntu on 2008-07-29
Thanks ConMan - your directions got me to the right place so that I was able to add Gparted to the menu (with its command). Now I have System > Administaration > Gparted and it works :)

And thank you Sunny Rabbiera for the suggestion that it could be added.

---

### Post by Bucky Ball on 2008-07-29
In the words of the gparted program itself;

> Gparted can only be run under root as it can be used as an instrument of mass destruction

... or words to that effect. Namely, you can wipe your drives if you don't have a handle on what your up to (like your nephew goofing around playing games or some such). Therefore, in a terminal type ...

> sudo gparted

and there's the gui. You will find most other programs install a link in the applications menu as per normal, this one not, for obvious reasons. :)

---

### Post by kdb424 on 2008-07-29
If you want to see programs, just find the menuedit under settings, and check in the little box.

---

### Post by Bucky Ball on 2008-07-29
Not showing in my edit menu section, but oddly enough, my wife's machine allows you to do it. Only difference I can think is that one is Ubuntu 8.04 i386 install and my laptop is amd64 version. Curious. About to install UbuntuStudio on my workstation later so might check that out,too. Looks like my advice was half right! :P

---

### Post by kdb424 on 2008-07-29
As long as you get your problems fixed. That's why we are here.

---

### Post by ConMan318 on 2008-07-29
Mine added to the menu automatically in 64-bit Hardy, curious that yours didn't.  You do have the program installed on that comp, right?  It isn't there by default.

And I don't know about your theory that programs that must be run as superuser won't add to the menus, as nearly everything in 'Administration' is run as root.  They still prompt for your password to be run as root; running 'sudo gparted' is the same as Sys > Admin > GParted.

---

### Post by ntu on 2008-07-29
> **kdb424 said:**
> If you want to see programs, just find the menuedit under settings, and check in the little box.

Can't find "Settings". Where is it please?

---

### Post by kdb424 on 2008-07-29
It's at the top of the screen, and the menu all the way to the right. I forget what it's called. I think system. Then the top thing will bring out another menu to the right, and it's in there.

---

### Post by Bucky Ball on 2008-07-30
The theory may be wrong, here to learn, but this is fact and I have no idea why (plus not bothered, comfy running from terminal considering how often it is used); I have gparted installed on this laptop and nothing anywhere on any menu that links to partition manager (gparted). Installed on wife's machine and it is right there. Odd, but not fussed either way.

---

