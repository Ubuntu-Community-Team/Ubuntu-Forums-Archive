---
title: "[Shell] Bash gurus?"
date: 2008-11-02
forum: Programming Talk
---

### Post by Maqz447 on 2008-11-02
Hi all. I posted this half a day ago in the genereal help forum but that may not be the right place, though this may not be either... 

It's not a big problem, more of an annoyance. I created a file ~/.xmodmap that swaps my caps lock and ctrl keys. This is convenient when using Emacs of course. I added the line "xmodmap ~/.xmodmap" to my .bashrc. This works as expected. The problem is, any time I open a shell (terminal instance or in emacs) .bashrc is of course read again and swap them back! So I have to type "xmodmap ~/.xmodmap" manually every time I open a shell instance. Does anyone know of a clever trick to avoid this?

---

### Post by jimi_hendrix on 2008-11-02
try making a variable and asigning it to 0...then do an if statement that will swap them only if the variable = 0 then after this make the variable = to 1

---

### Post by stylishpants on 2008-11-02
Instead of executing ~/.xmodmap from ~/.bashrc, do it from an init file that only gets called at login time, not at shell creation time.  You could try ~/.bash_profile or /etc/profile.

More info:
```
man bash | less -p '^FILES'
```

---

### Post by unutbu on 2008-11-02
Maqz447, if you are the only one using the machine, or if all users are happy swapping capslock and ctrl, then you can set this behavior on a system-wide level by editing /etc/X11/xorg.conf:
```

gksu gedit /etc/X11/xorg.conf
```

Search for the word "XkbLayout"
Add a line in this Section:
```

    Option 	   "XkbOptions" "ctrl:swapcaps"

```
or if you wish to make both the ctrl and the capslock keys behave as ctrl keys, add this instead:
```

    Option 	   "XkbOptions" "ctrl:nocaps"

```
Or, if you wish to swap those keys just for a single user, you could go to System>Preferences>Sessions (assuming you use GNOME) and add the "xmodmap ~/.xmodmap" command there.

---

### Post by Maqz447 on 2008-11-03
Great suggestions, all! I made a .bash_profile and the problem is gone.

---

