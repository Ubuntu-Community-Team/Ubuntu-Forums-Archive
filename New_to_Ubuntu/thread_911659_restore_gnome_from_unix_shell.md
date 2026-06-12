---
title: "restore gnome from unix shell"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Incognito72 on 2008-09-05
hi all -

newcomer and loving ubuntu! im working through some unix self-study books and while ive managed to get to the shell from GNOME, I dont know how to restore it after I've completed my work. 

Whats the keystroke combination to restore the ubuntu GUI for login?

Thanks

---

### Post by unutbu on 2008-09-05
Hello Incognito72, welcome to the forums. 
There are many ways to reach a unix shell. When you boot up, and reach the GUI login window, you could press Ctrl-Alt-F2 (or Ctrl-Alt-Fn, for any n=1,..,6). This will take you to a text terminal. You can return to the GUI login window by pressing Ctrl-Alt-F7.

If you login through the GUI, then open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)), you can reach a shell that way without every leaving the graphical desktop environment.

---

### Post by knix on 2008-09-05
if you killed the x server, typ  gdm  as root

---

### Post by Nepherte on 2008-09-06
You can easily switch to a virtual terminal with ctrl + alt + F1 (to F6). If you want to restore the graphical session, just do ctrl + alt + F7

If you want to completely kill the graphical session, do:
```
sudo /etc/init.d/gdm stop
```

You can then start it up again from the shell with:
```
startx
```
or
```
/etc/init.d/gdm start
```

---

### Post by Incognito72 on 2008-09-06
thank you for the help everyone - I know I can easily use a terminal window, but I was trying to work with it from the command line only without a GUI loaded... now I know how to return once completed!

---

