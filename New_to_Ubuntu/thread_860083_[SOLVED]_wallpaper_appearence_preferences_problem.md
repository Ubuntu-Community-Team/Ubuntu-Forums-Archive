---
title: "[SOLVED] wallpaper/ appearence preferences problem"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-07-15
hi everyone,
I have a probelm that I cannot solve by searching for an answer
when I goto change the desktop background in appearence preferences there seems to be a bug where one of 3 things happens:
1, works fine (rarely)
2, when I goto 'add' the pictures file is blank
3, the whole appearence preferences box in blank

I tried this in the terminal:

richard@richard-laptop:~$ gnome-appearance-properties
sh: kde-config: not found
sh: kde-config: not found
richard@richard-laptop:~$ 

any ideas?

---

### Post by benfindlay on 2008-07-15
> **LTFC2020 said:**
> richard@richard-laptop:~$ gnome-appearance-properties
sh: kde-config: not found
sh: kde-config: not found
richard@richard-laptop:~$ 


Are you running gnome or kde?

---

### Post by LTFC2020 on 2008-07-15
gnome which kind of confused me
but I did try the KDE desktop a while back but did not like it and uninstalled it

---

### Post by benfindlay on 2008-07-15
Not too sure, but it looks to me like you set KDE to control the desktop environment, and its still trying to do that! You can set gnome back to control your desktop by running ```
sudo dpkg-reconfigure gdm
```and following any prompts onscreen. Then try to relaunch the gnome appearance config

Hope this helps!

---

### Post by LTFC2020 on 2008-07-15
I tried removing KDE and restarted but the problem is still there

---

### Post by benfindlay on 2008-07-15
Did you try the gdm-reconfigure I suggested? What did that show you on screen?

---

### Post by LTFC2020 on 2008-07-15
this in the terminal

richard@richard-laptop:~$ sudo dpkg-reconfigure gdm
[sudo] password for richard:
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
richard@richard-laptop:~$ 

nothing else on screen

---

### Post by benfindlay on 2008-07-15
Ok, on the login screen, try choosing "session" and picking gnome. When prompted choose to make it the default session. You may need to reboot after this

Hope this helps!

---

### Post by LTFC2020 on 2008-07-16
ben
yeah I did that too (choose gnome for default session) but no change I'm afraid

---

### Post by benfindlay on 2008-07-16
Ok, open an terminal and try```
sudo apt-get remove kdm
```

Failing that try the following:
```
sudo su
```followed by
```
gnome-appearance-properties
```

Any joy?

---

### Post by LTFC2020 on 2008-07-27
ben
thanks for the help
still no joy I'm afraid
sorry it took me so long to get back to you but I've been in the wilderness camping:)

---

### Post by durand on 2008-07-27
Maybe you could take screenshots of your problem? Press the Print Screen button on your keyboard (top right) or go to Applications > Accesories > Take Screenshot, then post them here.

---

### Post by LTFC2020 on 2008-07-28
ok
here they are...

---

### Post by durand on 2008-08-06
Sorry, I was away for a week...The problem you have there is that gnome-settings-daemon seems to have uninstalled itself..
Type this in a terminal:
```
sudo aptitude install gnome-settings-daemon
```

---

### Post by LTFC2020 on 2008-08-10
I tried that too
still no joy I'm afraid

---

### Post by LTFC2020 on 2008-08-10
hi everyone
I found that if I open my wallpaper pictures file and then the change desktop background window I can drag the image I want across between the windows
This makes the appearence preferences window halfly cut out but if I close it then reopen it the image I want is there
Hasn't solved the under lying issue but at least it works to do what I originally wanted to
Thanks to everyone for their help with trying to find a solution

---

