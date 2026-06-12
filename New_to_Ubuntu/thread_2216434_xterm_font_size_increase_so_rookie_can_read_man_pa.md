---
title: "xterm font size increase so rookie can read man page"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by firefoxm54a2 on 2014-04-11
Hey guys, I managed to get an lubunto image up on a usb stick and it appears to work on my ancient system. I pulled up an xterm but I am old and my eyes can't handle the small type.  can you please give me some simple step by step instructions to increase the font size by at least a factor of three. Once I can read things I can dive into the man pages and hopefully I wont have to bother people too much at least with the simple stuff. Thanks a bunch for any help!

---

### Post by 23dornot23d on 2014-04-11
Edit then Preferences .......... in Lxterminal ..... then the font is as shown below ....... 

>>>>>>>>>>>>>>>>>>>>>>>>>>                     Monospace on mine and size 10

[IMG]http://i.minus.com/iVGwYtr3mjQvh.png[/IMG]


__________________

But .......

sudo apt-get install gnome-terminal

I tend to install gnome-terminal though as it is better ,,,,, starts off bigger too ....... as default ......

That is in Edit - then Profile Preferences  -   ........

___________________

xterm is tiny on mine and but am in KDE ..... cannot see how to alter it ..... unless its a config file somewhere.

---

### Post by r_avital on 2014-04-11
Hi,

It's weird and I don't claim to understand it, but you can try this on the command-line:```
xterm -fn -misc-fixed-*-*-*-*-18-*-*-*-*-*-*-*
```

This should open up another xterm window with a font of whatever it considers to be sie 18.  You can replace that with a different size, if it's too small.

A fair warning however, this is ugly.  Is xterm the only thing you can use?

I admit this may not be the best for your situation, but I would try to install "konsole" -- no quotes, of course.  Being part of the KDE desktop, installing konsole will also drag a host of additional files, but if you do install it, you'll have a lot of leeway for configuring fonts, sizes and colors.

---

### Post by SeijiSensei on 2014-04-11
Some terminal clients like konsole let you increase or decrease the font size by holding down Ctrl and scrolling the mouse wheel.  This also works in programs like Firefox.  I haven't used LXTerminal for a while, but I seem to recall it worked there as well.

---

### Post by firefoxm54a2 on 2014-04-11
Thanks guys, I give these a shot.

---

### Post by ibjsb4 on 2014-04-11
Konsole is a 228M download on a Lubuntu system, is this really a good idea?  I think not.

Be careful about what you install on lubuntu so not to bloat it with gnome or kde dependencies.

---

### Post by walterorlin on 2014-04-12
Yes sakura would be a lighter terminal if you wanted something different but still lightweight on lubuntu and you can get to all settings by rightclicking. There is also the prefrences in lxterminal.

---

### Post by andrew.46 on 2014-04-12
> **walterorlin said:**
> Yes sakura would be a lighter terminal if you wanted something different but still lightweight on lubuntu and you can get to all settings by rightclicking. 

Or by directly editing *~/.config/sakura/sakura.conf* where key bindings can also be set. Great little terminal emulator that I have been using for some time now...

---

### Post by sudodus on 2014-04-12
If you really want ***xterm***, and not any of the other terminals, like lxterminal (default in Lubuntu), or sakura, you can use this command to launch it with a nice font (at least I think it is nice)

```
xterm -fa default -fs 14
```

and you can change the font size from 14 to any other size, 20 or even more if you want it really big.

*Edit*: See also 'freetype support' at this link

[http://wiki.netbsd.org/tutorials/how_to_use_ttf_fonts_in_xterm/](http://wiki.netbsd.org/tutorials/how_to_use_ttf_fonts_in_xterm/)

---

### Post by Rob Sayer on 2014-04-12
> **ibjsb4 said:**
> Konsole is a 228M download on a Lubuntu system, is this really a good idea?  I think not.

Be careful about what you install on lubuntu so not to bloat it with gnome or kde dependencies.

If you're talking about a really old system with less than 1Gb I'd agree with you, but I use dolphin and konsole on my 1Gb netbook, no problem.

It's true that kde apps introduce a ton of dependencies, worse than gnome.  But if the app has a lot more features & power it's worth it to me.

Try LXterminal if you don't want to install konsole and all those dependencies.  For some silly reason LXterninal is under menu->accessoriies instead of menu->system tools so you may miss it.

---

### Post by 23dornot23d on 2014-04-12
Post #9 ......... I do like that one .........

> 
xterm -fa default -fs 14


Nice and clear ........

[IMG]http://i.minus.com/iOFF27WX2Ya3T.png[/IMG]

---

