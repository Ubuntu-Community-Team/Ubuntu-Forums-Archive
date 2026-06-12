---
title: "[SOLVED] Strange mouse scroll wheel behaviour"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by ubername on 2008-06-29
Hi

I have a Logitech MX3000 wireless keyboard and mouse. All was well until a couple of days ago when I tried to play with the settings to get more of the keyboard and mouse functioning (or at least understand how it was functioning). So I went into the Keyboard option from Preferences and instead of using the 105 key generic keyboard I picked a Logitech key board (LX-300, which looked the closest match!).

Having done that my mouse scroll wheel works to scroll down but not to scroll up. Instead it seems to try to slightly increase the size of the window. If I hold down one of the other mouse buttons and roll the wheel  it will scroll up! I have a number of other user profiles on the same box which are unaffected by this change (i.e. scroll wheel works in both directions) so I don't think it's an xorg.conf problem (because as far as I can tell I only have one xorg.conf in /etc which I presume all users share). Even when I change back to the original keyboard layout this behaviour persists.

Can anyone help? It's not a train smash but it's weird that it works on other profiles and not this one.

TIA

---

### Post by unutbu on 2008-06-29
Boy, that is strange!

I think you are right in your diagnosis -- there is only one xorg.conf, and if the problem was there, it would affect all users.

So, I believe the problem is in one of the following gnome configuration directories which reside in your home directory: .gconf, .config, .gnome, .gnome2, .gnome2_private, .gnome_private

My guess is it is .gconf, and perhaps in particular 
.gconf/desktop/gnome/peripherals/keyboard/general/%gconf.xml
or .gconf/desktop/gnome/peripherals/mouse/%gconf.xml

One way you can test this is to log out (so gnome is not running), press Ctrl-Alt-F2. Log in at the text terminal. Then run
```

mv ~/.gconf ~/.gconf-broken
exit
Ctrl-Alt-F7

```
Log back in and see if your mouse scroll wheel is better. If so, at least we'll have isolated the problem to that directory. If you get your scroll wheel functioning again, then we can puzzle over how to transfer the good settings and leave the bad. 

If it doesn't work, then open a terminal and run
```

rm -rf ~/.gconf
mv ~/.gconf-broken ~/.gconf
```
This should restore you to your present state.

---

### Post by ubername on 2008-06-29
> **unutbu said:**
> Boy, that is strange!

I think you are right in your diagnosis -- there is only one xorg.conf, and if the problem was there, it would affect all users.

So, I believe the problem is in one of the following gnome configuration directories which reside in your home directory: .gconf, .config, .gnome, .gnome2, .gnome2_private, .gnome_private

My guess is it is .gconf, and perhaps in particular 
.gconf/desktop/gnome/peripherals/keyboard/general/%gconf.xml
or .gconf/desktop/gnome/peripherals/mouse/%gconf.xml

One way you can test this is to log out (so gnome is not running), press Ctrl-Alt-F2. Log in at the text terminal. Then run
```

mv ~/.gconf ~/.gconf-broken
exit
Ctrl-Alt-F7

```
Log back in and see if your mouse scroll wheel is better. If so, at least we'll have isolated the problem to that directory. If you get your scroll wheel functioning again, then we can puzzle over how to transfer the good settings and leave the bad. 

If it doesn't work, then open a terminal and run
```

rm -rf ~/.gconf
mv ~/.gconf-broken ~/.gconf
```
This should restore you to your present state.

Thanks so much.

Option one worked, but perhaps I wasn't clever enough to follow the instructions to the letter so ended up restarting the system after the 'exit' command.  I may have pressed Alt Ctl F2 again.  Either way it has worked, so thanks a bunch. I don't have any particular other probelms so having isolated and solved this, I am very happy. I may have to come back after a reboot etc. but I doubt it. Thanks again.

---

### Post by ubername on 2008-06-29
Just getting a bit weirder. Now my compiz won't allow four Horizontal Virtual size desktops. I can increase it to three, or 5 or 6 or more (19 works!), but it don't like four. When I enter that, it reverts to 2. This is fun!

---

### Post by unutbu on 2008-06-29
I'm not sure this is necessary, but to be safe, log out. Press Ctrl-Alt-F2. Log in at the text terminal.

First, let's save a copy of your current semi-working .gconf:
```

cp -a ~/.gconf ~/.gconf-mouse-yes-compiz-no
```

And now copy your old apps settings to your current .gconf:
```
cp -a ~/.gconf-broken/apps/* ~/.gconf/apps 
```

Logout by typing 
```
exit
```

Press Ctrl-Alt-F7, log in.
Is compiz and the mouse wheel both working now?

I've noticed that if I log in and out, some apps do not behave quite right. (For me, emacs fonts become un-antialiased). I don't know for sure, but your problem with compiz acting strangely might have to do with the logging in and out I've asked you to do. If the problem persists, perhaps try rebooting.

---

### Post by ubername on 2008-06-30
> **unutbu said:**
> I'm not sure this is necessary, but to be safe, log out. Press Ctrl-Alt-F2. Log in at the text terminal.

First, let's save a copy of your current semi-working .gconf:
```

cp -a ~/.gconf ~/.gconf-mouse-yes-compiz-no
```

And now copy your old apps settings to your current .gconf:
```
cp -a ~/.gconf-broken/apps/* ~/.gconf/apps 
```

Logout by typing 
```
exit
```

Press Ctrl-Alt-F7, log in.
Is compiz and the mouse wheel both working now?

I've noticed that if I log in and out, some apps do not behave quite right. (For me, emacs fonts become un-antialiased). I don't know for sure, but your problem with compiz acting strangely might have to do with the logging in and out I've asked you to do. If the problem persists, perhaps try rebooting.

Thanks again for the assistance, but sadly your suggestions have not worked. I have also tried copying the contents of my other users' ~/.gconf to my own ~/.gconf to no avail. I am not bothered however. If I can have 5 desktops rather than 4 well, what's the loss? It is so strange, but I may well upgrade the machine to ubuntu 8.10 (intrepid ibex)  which may well solve the problem or introduce a whole lot more! Thanks again for you help

---

### Post by ubername on 2008-07-16
> **ubername said:**
> Thanks again for the assistance, but sadly your suggestions have not worked. I have also tried copying the contents of my other users' ~/.gconf to my own ~/.gconf to no avail. I am not bothered however. If I can have 5 desktops rather than 4 well, what's the loss? It is so strange, but I may well upgrade the machine to ubuntu 8.10 (intrepid ibex)  which may well solve the problem or introduce a whole lot more! Thanks again for you help


Have done the upgrade and indeed having lot's more fun, but the mouse wheel works!

---

