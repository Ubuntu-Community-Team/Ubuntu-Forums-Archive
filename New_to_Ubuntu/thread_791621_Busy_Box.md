---
title: "Busy Box ???"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by bainesmg on 2008-05-12
I've been running Ubuntu (Wubi install) as a dual boot with Windows XP for about a week. I'm a new user and was initially impressed. When I try to boot up Ubuntu now i'm getting the message below. Presumably i've got to use one of the commands but i'm unsure which one. I tried reset but nothing seemed to happen. Can any guru out there help me get Ubuntu back ? Thanks in advance. PS Try and keep it simple.

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

:confused:

---

### Post by Venality on 2008-05-12
i had the same problem and reinstalling didn't work the first time, but the second time i reinstalled i changed the wubi set amount from 15 to 30,and instead of starting Ubuntu after it wanted to restart i let windows start up one more time just to use the proper "Shut Down" method and it worked like a charm. if you dont want to reinstall my way i understand cause it could have been a fluke that it started working haha.

---

### Post by Pap3r on 2008-05-12
Huh.  Busy Box is usually a very small kernel used on routers (mostly) and I was unaware it came with the Wubi.

If you have a prompt, try ```
startx
```

That will start the xserver.

---

### Post by P373 on 2008-05-12
I have the exact same problem ... startx doesn't do anything when I type it in . ?

---

### Post by Pap3r on 2008-05-13
What screen are you on?  Are you on a prompt that says login?  Or are you at a bash prompt? ( $ )

Try hitting ctrl+alt+f2, this will bring you to another screen, where you will most likely have to login.  After login type ```
startx
```If that doesn't work, try ```
init3
startx
```

Don't startx from root, log in as a user.

---

### Post by bainesmg on 2008-05-15
Thanks for the help. As it was a relatively new install I removed it from XP. Then I re-installed it under Wubi. Voila, its now working again though it sometimes still won't boot up (just a black screen after the Ubuntu logo). I've found that switching the power off and starting again usually works. Its not an ideal situation, however, once in the system I find I prefer it to XP. I'm keeping XP because I like the AceHTML program. Unfortunately its not available for Linux and I prefer it to the Linux equivalents i've tried.

---

