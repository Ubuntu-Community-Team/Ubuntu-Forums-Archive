---
title: "I messed up!  I acidentally dissabled my graphical interface"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Sorandal on 2008-04-22
I had this bright idea that if I disabled the graphical login that it wouldn't take quite as long to boot up linux.  What I didn't know is that by disabling the graphical login it also disables the graphal interface even after you have logged in...  

I'm using Xubuntu 7.04 on a Dell inspiron 8000.  Would anyone be kind enough to walk me through reactivating the graphical login through command line?  You would be me hero!
Thanks

---

### Post by Runny on 2008-04-22
I made the same mistake.

---

### Post by Joeb454 on 2008-04-22
After you log in from the command line, you could type ```
startx
```

If that doesn't work then just try hitting **Ctrl+Alt+F7** As I believe that should bring back a GUI (not 100% sure on the key combination though)

---

### Post by brennydoogles on 2008-04-22
You could also try typing in ```
xfce4-session
``` in the command line.

---

### Post by T-Virus on 2008-04-22
Yes it's **Ctrl + Alt + F7**. But if it doesn't bring you X after you log in, just run the command **startx** as stated below.

---

### Post by Sorandal on 2008-04-22
Thanks for the help everyone, startx is what worked, no response from Ctrl + Alt + F7.  Everything is normal and I'm typing from Ubuntu again!

---

