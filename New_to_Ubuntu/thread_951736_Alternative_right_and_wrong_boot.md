---
title: "Alternative right and wrong boot"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by belier on 2008-10-18
Hello.

Before exposing my problem just say hello to all the Ubuntu community on my first thread/post here... ):P

I come from installing for first time Kubuntu.
It's mounted on a machine with Windows installed. Kubuntu it's on his own disk.
Everything is fine, just a little big annoyance:

I start the machine, select Kubuntu with grub and it boots well. Everything works fine.
Next time I boot, when I open Konqueror or Firefox, they don't have title bar. I can't move them, close or do anything. In addition other applications are not opening. 
I must go to kMenu, and restart Kubuntu. Changing user or so has no effect.

I have no Compiz, Emerald or so installed (at least not knowingly... :roll:)

I had two desktops but changed it to only one because I noticed that when the issue happens, KDE starts with only one desktop with no name on desktop one and two.
The only special thing that I have done is to enable hardware acceleration on the NVidia driver.

Any suggestion?

Thanks in advance

---

### Post by Zzl1xndd on 2008-10-18
Compiz is installed by defualt on the latest versions of Ubuntu. It is likely the cause of your problem. I would try disabling it first to see if it fixes your issue.

---

### Post by belier on 2008-10-18
Thx for the fast answer.

When I write "compiz --replace" on the Alt+F2 screen I get an error of Compiz not installed.

---

### Post by reg4c on 2008-10-18
Hey, 

welcome to the wonderful world of [K]Ubuntu.

What you might want to do is install fusion-icon 

sudo apt-get install fusion-icon

and then just add it to the start up: System > Preferences > Session > Add
and type fusion-icon

It will make the compiz reload, and will give you an easy way to reload it should that happen again: right click > reload window manager.

Cheerio

---

### Post by reg4c on 2008-10-18
Pfft, accidentally double posted.
Any way to delete one of these?

---

### Post by belier on 2008-10-18
Thx a lot. Now I have Compiz installed... I see menu for Window Manager. I'll wait or next boot in order to check if it works.

=D>

---

