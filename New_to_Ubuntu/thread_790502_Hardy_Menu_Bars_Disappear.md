---
title: "Hardy Menu Bars Disappear"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by hello_emo_boy on 2008-05-11
Ok so I FINALLY just got Hardy to work and wouldn't you know it, after I restarted the computer, I've got a big problem.

Both my top and bottom menu bars have vanished. Now before anybody has any ideas about what the problem is, let me explain:

+No, they are not hiding
+No, Alt+F2 does not work
+Yes, this happened the restart after I did an update
+Yes, Ctrl+Alt+F1 does work
+No, I can't right click it back into exsistance
+No, I can't seem to gain access into Terminal

So that being said, any ideas folks?

---

### Post by ChrisBieda on 2008-05-12
No advice to offer, but misery is said to love company, so "Hello!  Same problem here."

---

### Post by Het Irv on 2008-05-12
One thing you didn't try
Recovery Mode?  (crosses fingers)

---

### Post by ShodanjoDM on 2008-05-12
Try this from the console (Ctrl+Alt+F1)

```
killall metacity
```

In my case that will restart the metacity and bring back the panels. It's a good idea to have a keyboard shortcut for the terminal, since keyboard inputs are unaffected - or so it seems.

---

### Post by N.N. on 2008-05-12
Try deleting the following hidden folders which are located in your home directory, i.e. in /home/your_username:
[LIST]
[*].gnome
[*].gnome2
[*].gconf
[*].gconfd
[*].metacity
[/LIST]
Then restart X by pressing CTRL+ALT+BACKSPACE. Doing this should reset your GNOME settings. With luck, that's all you will need to fix your problem. If it doesn't, however, you might have a serious problem which I don't know how to solve.

---

### Post by brydong on 2008-05-13
I'm experiencing this as well and the suggested fix did NOT work for me. Other things I've tried...

- created an entirely new user acct on machine and logged in. No menus there either.
- tried logging in with safe gnome, no menus there either.

I'm working in fluxbox currently otherwise I'd be completely hung up. Suggestions welcome please...

thanks,
brydon

---

### Post by Het Irv on 2008-05-13
While you are in Flux, can you access your Ubuntu install?
If so try going into your Ubuntu file and going to your /home and deleting the afore mentioned files (see N.N.'s post)

This should also work from the Live CD.

---

### Post by brydong on 2008-05-13
I did already try deleting those dir's. I believe I know how I messed up and caused this though...Based on advice here, [http://ubuntuforums.org/showthread.php?t=688687&highlight=menu+bars+disappear+gnome](http://ubuntuforums.org/showthread.php?t=688687&highlight=menu+bars+disappear+gnome)

I put those dirs back in place and I'm reinstalling ubuntu-desktop. Based on the packages I'm seeing pulled down, I'm pretty sure I caused this when I removed some evolution packages. I didn't realize they were required for gnome and panel menus. Once this is done I'll try gnome again and hopefully I'm back in business.

---

### Post by twentypercentlycra on 2008-08-06
> **brydong said:**
> Based on the packages I'm seeing pulled down, I'm pretty sure I caused this when I removed some evolution packages. I didn't realize they were required for gnome and panel menus.

Same problem here, still trying to find a solution.
I don't need Evolution, so today I removed packages... and well, here I am without the menu bars.

---

### Post by dnozner on 2008-08-26
Hi, same problem here after removing evolution..
To fix the problem reinstall evolution and update the ubuntu-desktop package:

```
sudo apt-get install evolution
sudo apt-get install -f ubuntu-desktop
```

Then restart X by pressing CTRL+ALT+BACKSPACE.

---

