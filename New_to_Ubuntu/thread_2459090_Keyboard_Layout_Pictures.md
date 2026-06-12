---
title: "Keyboard Layout Pictures"
date: 2021-03-10
forum: New to Ubuntu
---

### Post by boomerang63 on 2021-03-10
Hello everybody

I'm pretty new to ubuntu, and to linux in general. But I do have a lot of expierience with various computers since the 80s, including commandline systems like Novell in the 90s.

If I connect from windows via putty the keyboard layout is correct. If I connect my ubuntu (which is running in virtual station on my QNAP NAS) by clicking on the running virtual machine, then the keyboard layout is english. This second access is comparable with sitting directly at the running station - i think it is called the console. Running sudo dpkg-reconfigure keyboard-configuration doesnt change anything.

Maybe you can help me: how can I determine on which tty i am sitting now
And how can i reconfigure keyboerd layout on the console ?

By the way, this is my first port and I want to check if I am able to post after registerung
Thanks

PS: Are there any libraries of different leyboard layout pictures within this forum or wiki ?

---

### Post by TheFu on 2021-03-15
> **boomerang63 said:**
>  
I'm pretty new to ubuntu, and to linux in general. But I do have a lot of expierience with various computers since the 80s, including commandline systems like Novell in the 90s.
Good news.  Linux is  90% like every other Unix system you've used. Only the admin stuff is different, if you ignore the GUI, which changes every 2-3 yrs because "new" has been deemed to be better than "working."

> **boomerang63 said:**
> This second access is comparable with sitting directly at the running station - i think it is called the console. Running sudo dpkg-reconfigure keyboard-configuration doesnt change anything.
Console settings are for the "console", not for remote connections.

> **boomerang63 said:**
> Maybe you can help me: how can I determine on which tty i am sitting now
And how can i reconfigure keyboerd layout on the console ?
There are multiple consoles in Linux.  <cntl><alt>-F1 thru <cntl><alt>-F8, I think.  The exact tty is shown on the top line when you change consoles. May need to hit enter to get some text output on each.

> **boomerang63 said:**
> PS: Are there any libraries of different leyboard layout pictures within this forum or wiki ?
No.  Keyboard layouts are logical, but that depends on the exact keyboard hardware. Some keys don't allow switching around - like some French or UK keys - most almost all can be remapped.  I remap the "CapsLock" to be the "Super" key, for example.
If I wanted to see examples of different keyboards, I'd use google and search for images.

There is also a pre-login virtual keyboard that can be used to enter passwords on the graphical console.  On my system, the graphical console is on tty7.

Some Linux systems have stopped using real ttys and use pttys instead.  I don't know what this really means - think it is for pseudo-ttys, which makes them virtual. Sorry.  I'm seeing 65 ttys on a few of my systems. I didn't check them all.

---

### Post by mastablasta on 2021-03-15
i think you need to add keyboard, then you configure it. i use i have a couple of keyboard where i switch form US to local or from local to UK but this is all on deskotp not on server.

[https://askubuntu.com/questions/434849/change-keyboard-layout-english-uk-on-command-line-to-english-us](https://askubuntu.com/questions/434849/change-keyboard-layout-english-uk-on-command-line-to-english-us)

---

