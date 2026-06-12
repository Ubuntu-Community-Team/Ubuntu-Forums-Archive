---
title: "A couple of useful tips for Nvidia owners..."
date: 2009-08-23
forum: Outdated Tutorials &amp; Tips
---

### Post by nomnomnom on 2009-08-23
I have always found these really useful, so hopefully someone else will too.

Tip 1 - Autostart Nvidia color settings.

I use an old CRT monitor for my desktop that has kind of died slightly, and is *really* dark, and has to be countered with gamma, so I find that having the Nvidia color settings autostarting to be really useful.

The way I do it is like this;

1 - Goto, **System >> Preferences >> Startup Applications**, click **Add**, and **copy & paste** this into the **Command** box

```
nvidia-settings -l
```And name it something like Nvidia Color Autostart. Then click **Add**, and then **Close** and that's it. Next time you restart your PC and log in, the Nvidia Color settings will autostart themselves.

[SIZE=2]_I will finish this tomorrow probably as I can't be bothered now._[/SIZE]

---

### Post by GoodPanos on 2009-12-14
God...I was looking for that setting!  Every time I upgrade Ubuntu I forget to copy this setting and then I have to go looking for it.

Thank you for posting this.  This is a great tip to know.

---

### Post by Linuxforall on 2009-12-15
All you have to do is gksudo nvidia-settings and set your gamma and it will stick next time you reboot.

---

