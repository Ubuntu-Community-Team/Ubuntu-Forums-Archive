---
title: "Adjusting screen resolution in virtual terminals?"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by 3strandchords on 2008-11-10
Hi all.

Running 8.04, fully-patched.

I do a fair amount of work in the terminal, and so I typically have used the Cntrl-Alt-F1/2/3/etc keystroke to open a naked terminal session.  That gives me maximum screen real estate for my work.

The trick is that I built 8.04 on a new desktop machine with a relatively hi-res TFT panel.  The resolution within GNOME is fine, but if I shift to one of those other ttys, the text overruns the screen boundaries.  

Everything works, but my prompt looks like this:
```
1@sandbox:~$ ls -al
l 204
r-xr-x 37 user1 user1 4096 2008-11-10 09:12 .
r-xr-x  3 root  root  4096 2008-11-04 12:21 ..
------  3 user1 user1 4096 2008-11-06 11:19 .adobe
------  1 user1 user1 1492 2008-11-06 09:47 .bash_history
r--r--  1 user1 user1  220 2008-11-04 12:21 .bash_logout
r--r--  1 user1 user1 2940 2008-11-04 12:21 .bashrc
```

It's annoying losing 4 characters over to the left.  Is there something I can hack so I can see the terminal window better?

Thanks,  3strand

---

### Post by eldragon on 2008-11-10
i dont know if this is what you are looking for, but you could set the console terminal resoultion to 1024x768 which will give you more than just 4 characters...

download and install startup-manager from the repositories, and run it with admin privileges...

---

### Post by prshah on 2008-11-10
> **3strandchords said:**
> 
Everything works, but my prompt looks like this:
```
1@sandbox:~$ ls -al
l 204
r-xr-x 37 user1 user1 4096 2008-11-10 09:12 .
r-xr-x  3 root  root  4096 2008-11-04 12:21 ..
------  3 user1 user1 4096 2008-11-06 11:19 .adobe
------  1 user1 user1 1492 2008-11-06 09:47 .bash_history
r--r--  1 user1 user1  220 2008-11-04 12:21 .bash_logout
r--r--  1 user1 user1 2940 2008-11-04 12:21 .bashrc
```

It's annoying losing 4 characters over to the left.

You need to use the monitor's auto-adjust feature; it will subsequently remember it for the future, for the given resolution.

Each TFT monitor will maintain a table of optimal settings for each resolution and refresh rates. So when you switch back to Ctrl+Alt+F7, it will load the optimal settings for that mode, and when you switch back to Ctrl+Alt+F1, the optimal settings for that mode. But every mode must be auto-adjusted at least once to populate the table of settings.

---

### Post by 16777216 on 2008-11-10
Like eldragon said you can install startupmanager to easly adjust the boot splash resolution which will also set the tty ( text mode ) terminals resolution.

```
sudo apt-get install satrtupmanager
```**System > Administration > StartUp-Manager**

In StartUp-Manager change the display resolution to something more to your likeing.

There are other ways to do this but, this is one of the easiest.

---

### Post by 3strandchords on 2008-11-10
Thanks, everyone... I took **prshah's** advice first, and he was right.  The auto-adjust seems to have fixed the issue.


Thanks,   3strand

---

