---
title: "Shutdown graphical user interface in order to use more GPU ram"
date: 2019-11-12
forum: Programming Talk
---

### Post by farhad-bat on 2019-11-12
[FONT=Helvetica]I wrote a program in PyTorch but unfortunately I need one more GB of GPU ram. My GPU is 1080 Ti and my OS is Ubuntu 18.04.[/FONT]
[FONT=Helvetica]In other to solve my problem I need to shutdown the Graphical User Interface of Ubuntu 18.04. However I don’t know how do that.[/FONT]

---

### Post by Bashing-om on 2019-11-12
farhad-bat; Hello. Welcome to the forum.

Boot to terminal from grub:
At grub's boot menu 'e' key for edit mode (with the desired kernel highlighted)
that gives you a screen for the kernel's boot directives. Here arrow down to the line starting with linux, remove "quiet splash" and insert the term:
systemd.unit=multi-user.target

Key conbo ctl+x to continue the boot process - to terminal.
Log in here with user name and pass word - when the password is entered there will be no response to the screen, enter password blindly and hit the enter key.

see: from terminal:
```

man bootup

```
for full documentation

And
[https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode](https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode)
for some other options.

[INDENT]it's ubuntu
[INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT]

---

