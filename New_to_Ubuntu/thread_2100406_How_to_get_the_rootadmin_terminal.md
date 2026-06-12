---
title: "How to get the root/admin terminal?"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by grish on 2013-01-01
I saw someone having an admin terminal where you are root from when you start it. I also have it on raspbian on my raspberry pi.

I wonder how to get it on ubuntu.

Using 12.04 and GNOME Classic.



_____________________________________________________________
Happy New Year to all of you :)

---

### Post by PinkFloyd102489 on 2013-01-01
Is there really a need to directly access the root terminal at boot? That is a huge security risk.

If you need access to root, just sudo -s.

---

### Post by JiuJitsu500 on 2013-01-01
Yeah, root terminal is not the best thing in the world to do... all that essentially does is make it so you don't need to ask for permission with 'su' in any way after you open it to give it root permission. In other words, take the 'sudo' or 'gksu' etc. out of every command you'd type anyway.

You can just type sudo -s or su to get into superuser in a normal terminal... but you can also I suppose just download a root terminal from the software center. Then, every time you open it, you'll type your password. Same as if you open a normal terminal and type 'su' or 'sudo -s'...

---

### Post by sisco311 on 2013-01-01
The preferred way to start a root shell is **sudo -i**. Please check out the community documentation:
[uhelp]community/RootSudo[/uhelp]

@OP: You can use gksu to run GUI applications as root. So you can create a new launcher with the following command:```
gksu gnome-terminal
```

Of course, if you use gksu the whole application will run with elevated privileges, which may be considered a security risk. 

It's probably a little bit safer to run sudo -i in the terminal window. You can create a custom launcher which will automate this for you:
```
gnome-terminal -x sudo -i
```

---

### Post by grish on 2013-01-01
Thanks for all your replies.:KS

---

