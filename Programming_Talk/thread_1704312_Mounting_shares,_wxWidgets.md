---
title: "Mounting shares, wxWidgets"
date: 2011-03-10
forum: Programming Talk
---

### Post by rockoprem on 2011-03-10
Hi all,
I've been trying to mount my Novell share using a simple GUI coded in wxWidgets, C++. From the terminal, it is a simple one line code that includes the ip, username, password, etc. The problem is, to mount a share, one needs to be a su and when I try to pass on a char buffer to the terminal via System("blah blah commands...") command... nothing happens! I tried running the GUI as a su.. nothing different! Any ideas, help?

---

### Post by dwhitney67 on 2011-03-10
Have you tried using the mount() C library function, and also running your program as sudo?  Mounting a file system requires root permissions.


P.S.  The system() runs command in a separate shell; not the one in which your application is running.  Generally usage of system() should be avoided, especially when there is a better alternative, such as the C library.

---

### Post by rockoprem on 2011-03-10
I will try that.. however, for the Novell shares, one has to use the ncpmount and ncpumount. 
The command looks something like..

ncpmount -S <server> -A <fqdn> -U <username> ..... <mount location>

I tried running my program as sudo, doesn't help!

---

### Post by dwhitney67 on 2011-03-10
Ah... I was unaware that you required a non-standard command to mount the file system.  Thus, I guess it is back to using system().  :-)

Try prefacing the command you pass into the system() function with gksudo.  Something like the following, but obviously replacing the entries in <>:
```

system("gksudo ncpmount -S <server> -A <fqdn> -U <username> ..... <mount location>");

```
You should be able to run the application as a regular user, however that user will be prompted for their sudo password.  If they are not a sudoer, then they are out of luck.

---

