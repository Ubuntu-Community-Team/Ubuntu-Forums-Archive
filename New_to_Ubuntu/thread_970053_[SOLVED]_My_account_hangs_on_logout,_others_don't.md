---
title: "[SOLVED] My account hangs on logout, others don't?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Virtualboxbuntu on 2008-11-03
I'm using Ubuntu Hardy x64 and restricted NVidia drivers. Whenever I log out of my account, it hangs and displays only my wallpaper. I have to use CTRL ALT BACKSPACE to get back to the login screen. Other accounts do not do this. 

I've deleted my account and home directory and re-made my account, but after logging in/out about 20 times, it started hanging on logout again. I hadn't made any changes at all between the last successful logout and the first failed logout, all I did was answer about two dozen Yahoo! Answers questions.

---

### Post by cmnorton on 2008-11-07
For starters, look in /var/logs

Also, consider having a second account logged in and poke around when your first account does not log out. Look at the output of top, and ps.

---

### Post by Virtualboxbuntu on 2008-11-07
Unless I misunderstood, that won't work. When it hangs, I can't do anything except CTRL ALT BACKSPACE. That would more or less logout every account that's logged in.

It seems to be a problem with the x64 edition. I'll just use the x86 edition. Thanks anyway!

---

