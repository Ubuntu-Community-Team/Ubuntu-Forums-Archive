---
title: "where to change bash path info on hardy?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by jam1492 on 2008-07-01
I would like to automatically add to the bash path for all users.

Before using hardy, I did this by modifying /etc/profile

Now, on hardy, if I modify /etc/profile it only changes the path information outside of Xwindows (ie. when I use CTL+ALT+F2 to get command line) but it doesn't incorporate the new path information if I open a terminal inside Xwindows even after rebooting?  

So maybe there is a second file in /etc/ or elsewhere that I need to modify?

Anyone have any suggestions?

Alex

---

### Post by Fafnir on 2008-07-01
Hmm. After doing a bit of reading, /etc/profile is only executed by the shell on startup if it's a login shell - that is, if you just start an xterm from within the GUI, it will ignore /etc/profile, but it will read it if you log in via the terminal. (IIRC you have to log in again after CTRL-ALT-F2, which explains why it works in that case.) I'm guessing before Hardy changes from the initial login shell propagated to xterms, and now they don't for some reason.

As to what you should do, it so happens that there's a very similar file called /etc/bash.bashrc that's only executed by the shell on startup if it's a *non*-login shell - so it gets executed whenever you start an xterm, but not when you log in via the terminal. I think if you copy your PATH changes from /etc/profile to /etc/bash.bashrc everything should work. (Keep them in /etc/profile in case you need to leave X for some reason.)

My guess is the change was made to preserve the distinction between the two files - after all, if /etc/profile is applied to every shell regardless, /etc/bash.bashrc suddenly becomes a bit pointless...

---

### Post by bodhi.zazen on 2008-07-01
> **jam1492 said:**
> I would like to automatically add to the bash path for all users.

Before using hardy, I did this by modifying /etc/profile

Now, on hardy, if I modify /etc/profile it only changes the path information outside of Xwindows (ie. when I use CTL+ALT+F2 to get command line) but it doesn't incorporate the new path information if I open a terminal inside Xwindows even after rebooting?  

So maybe there is a second file in /etc/ or elsewhere that I need to modify?

Anyone have any suggestions?

Alex

Put it in ~/.bashrc

```
export PATH=$PATH:/additional/dir
```

---

### Post by bhadotia on 2008-07-01
I once pressed ctrl+alt+f2 got into the command line. I did (do) not know how to get back to gui so I had restart to get the gui. My question is what do we have to do to get out if we are in the command prompt like that?

---

### Post by bodhi.zazen on 2008-07-01
> **bhadotia said:**
> I once pressed ctrl+alt+f2 got into the command line. I did (do) not know how to get back to gui so I had restart to get the gui. My question is what do we have to do to get out if we are in the command prompt like that?

Ctrl-Alt-F7

---

### Post by bhadotia on 2008-07-01
Thanks again bodhi.

---

