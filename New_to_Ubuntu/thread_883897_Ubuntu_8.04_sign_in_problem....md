---
title: "Ubuntu 8.04 sign in problem..."
date: 2008-08-08
forum: New to Ubuntu
---

### Post by droopsta915 on 2008-08-08
I type in the username and password, hit enter, then it goes back to the login screen?? The only way I can get in is through the failsafe mode, but thats not fun. Anyone got any suggestions,( the username is correct and the pass word is correct, I know the number lock deal and all that good stuff. I also reinstalled twice.

---

### Post by Het Irv on 2008-08-08
No error messages or anything?  Does the login screen accept your password, and then fail?  Did you use the same disk for the reinstalls?

One other thing.  Is the partition that Ubuntu is installed in full?

---

### Post by markjensen on 2008-08-08
I think X puts any errors it runs into into its error log: /var/log/Xorg.0.log

Alternatively, you can use CTRL+ALT+F1 to get to a TTY (text mode) login and make sure you can log in there.  If you can't, then we have BIG issues.  If you can, try the following:
**sudo init 3** (this will shut down X)
**startx** (to start X back up, I don't think it requires sudo)
Doing it this way, it should also report errors right to your console.

Best of luck!

---

### Post by droopsta915 on 2008-08-08
Yes, the login screen does accept the password, I installed the full install. I can get in failsafe mode by using the username and password. I looked at the logs in Xorg.0.1..LOL. I guess that was a problem i'll try the /var/log/Xorg.0.log and see what I can find out. thank for the help everyone. I don't feel like down grading back to gutsy but if I can't solve he problem I guess a downgrade wont hurt.  :(

---

