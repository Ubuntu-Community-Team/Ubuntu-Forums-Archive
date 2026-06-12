---
title: "How do I switch cntrl and capsoff automatically on startup"
date: 2011-11-14
forum: Programming Talk
---

### Post by frootstripe on 2011-11-14
Hi all,

How do I switch the cntrl and caps keys automatically on startup? Right now I have to pull up a shell to do it each time as an alias command that I've put in my .bashrc.

---

### Post by frootstripe on 2011-11-14
saw on another forum that this might do the trick

```
xmodmap -e "remove lock = Caps_Lock
```

but what file would I put this in so that it would run automatically at boot?

---

### Post by frootstripe on 2011-11-15
Ok, here's the solution to my problem which has worked for me and should probably work for you two :)

first, I create a file in my home directory.
```
echo setxkbmap -option ctrl:swapcaps >> capsoff 
```

Then Start menu > System > Preferences > Startup Applications

The selection box pops up and click the `add' button.
Then you can click the `browse' button and select the `capsoff' file from the list of files in your home directory. When you restart, your `control' and `cap-lock' keys should be switched. 

Great for emacs users, once you get used to it!

If you would like to still be able to switch back to use the caps-lock key for it, paste the following into the commandline:

echo alias capstoggle='setxkbmap -option ctrl:swapcaps' >> ~/.bashrc

This will now be a permanent alias.

Then you should be able to switch to between the two different keymaps at will by typing at the command line:

capstoggle

---

### Post by crdlb on 2011-11-15
You can do this from the keyboard layout settings in GNOME as well: 'Options' -> 'Ctrl key position'

---

