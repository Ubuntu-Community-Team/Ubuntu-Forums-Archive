---
title: "[SOLVED] ERROR: There is no default action associated with this location"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by huxinda on 2008-06-27
Hi, I'm new to linux.

I've got a problem: I can't open any folders in the "Places" Menu.

When I click on Places->Home folder or Desktop or ... , I got errors.

" Could not open location ********"
There is no default action associated with this location

This problem happens just today. I think I didn't do anything.

btw, accessing those locations using terminal are fine.

Thanks.

---

### Post by Vivaldi Gloria on 2008-06-27
Try this. Press Alt+F2 and start

```
gksudo gedit /etc/gnome/defaults.list
```

Make sure that the following lines are as follows:

```
inode/directory=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop
```

If not, change and save.

---

### Post by huxinda on 2008-06-27
Thank you. BUT,

Probably not this problem.

The codes are correct.

---

### Post by huxinda on 2008-06-27
OK. I got it. I accidentally uninstalled the ubuntu-desktop.

now it is fine.

Thanks.

---

### Post by Vivaldi Gloria on 2008-06-27
What happens when you write

```
nautilus ~
```

in a terminal? Can you open your home folder that way? If not, does it give any error messages?

Edit: Nevermind, I didn't see your last message.

---

### Post by Duff_Beer on 2008-06-28
I get that same error and following Vivaldi Glorias advice everything seems to work. I.E. typing "nautilus ~" in the application launcher launches the file browser just fine.

Using the Places menu everything bombs.

---

