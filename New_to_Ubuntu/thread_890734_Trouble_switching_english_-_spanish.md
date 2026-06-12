---
title: "Trouble switching english - spanish"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by pp_bomb on 2008-08-15
Hi everybody, I hope someone can help me with this little problem I got.

I'm using Ubuntu 8.04 - Hardy Heron. I like using the spanish versions, since I like to use my OS in my native language. However, my brother couldn't find some stuffs (just because they are named differently in spanish) and so we decided to switch to english. Everything worked fine, files were renamed and all option's names changed to the english versions.

The problem is, when I switched back to spanish, I couldn't find anything on the desktop. I did find the folder "Escritorio" with everything I had on my desktop, but the system still belives that I have english version and tries to find the Desktop folder rather than the Escritorio one.

Can anybody help me to solve this trouble? 

I am thinking about creating a new folder called Desktop, but I belive it wouldn't be the optimal solution, if the desktop file was renamed to escritorio it should read the escritorio one rather than desktop.

---

### Post by Pro-reason on 2008-08-16
Do this:

```

nano ~/.config/user-dirs.dirs

```

Change "Desktop" to "Escritorio" or vice versa.  Hit *Ctrl + X*, then *y* to save and exit.

I haven't tested it, but I imagine it will change the location in which Ubuntu searches for your desktop.

Another thing you can do is create a symbolic link.  For example, if your stuff is currently located at ~/Escritorio and you want to be able to access it at ~/Desktop, then do the following command:

```

ln -sT ~/Escritorio ~/Desktop

```

It will then be accessible from both locations, regardless of your latest linguistic preferences.


P.S. Both "~" and "$HOME" are abbreviations for the current user's home folder, e.g. "/home/pablo".

---

### Post by Pro-reason on 2008-08-17
Did that work for you?  If so, please use the menu to mark this thread as solved.

---

### Post by Pro-reason on 2008-08-19
I believe that the command *xdg-user-dirs-gtk-update* will automatically fix such things after locale changes.

I've just found that command because it is listed in the Session Manager as one of the commands that are run when I log into my GNOME desktop. Perhaps you disabled it on your box.

---

