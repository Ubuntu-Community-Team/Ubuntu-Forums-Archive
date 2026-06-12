---
title: "firefox shortcut issues"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by simon303 on 2008-05-20
Hi,
Recently upgraded to 8.04 and everything seems to be working, apart from one of my shortcut keys.
I have manually assigned a shortcut for firefox through system-->preferences-->keyboard shortcuts and it used to work just fine.
But now i have upgraded when i press the shortcut i get an error message saying
> 
Couldn't execute command: /usr/lib/firefox/firefox ""
Verify this is a valid command.

Any ideas??
Thanks

---

### Post by Canis familiaris on 2008-05-20
Try changing the command assigned to the shortcut.
Open terminal:
```
which firefox
```
Use its output as a command for keyboard shortcut.

---

### Post by Zularan on 2008-05-20
Hardy 8.04 comes with Firefox 3 beta 5 IIRC, I'm pretty sure you need to address is as /usr/bin/firefox3 or similar depending where you have it. (As opposed to just 'firefox'.)

One way to make sure you're pointing to the correct target would be to rightclick on the 'Applications' -> 'Edit Menus' and see where Firefox points to in the Internet folder by rightclicking on its entry.

I don't know the exact notation as I reverted back to Firefox2 until version3 stabilises a bit.

Hope this helps.

---

### Post by simon303 on 2008-05-20
the location for firefox given by "which" is
```

/usr/bin/firefox

```
how do i change the command executed when the shortcut is pressed as the keyboard shortcuts dialog has no such option??

---

