---
title: "HOWTO: Restore default TTY resolution (for roguelike games)"
date: 2011-03-27
forum: Outdated Tutorials &amp; Tips
---

### Post by goldaryn on 2011-03-27
Hello,

Started using Ubuntu 10.10 and I have been trying to restore the resolution in the virtual consoles to the default low resolution as I want to play roguelike games such as ADOM in low resolution fullscreen.

For anyone who's not seen this before, you get a virtual console up by typing Ctrl-Alt-F1 to Ctrl-Alt-F6. You can get X (the graphical interface) back by pressing Ctrl-Alt-F7.

I finally found a blog post which has helped me to get these back to the resolution I want and so I am repeating the instructions here in order to help anyone else with the same issue. **Warning**: a side effect of these instructions is that the hi-res splash screen on startup will be replaced - you will get a text "Ubuntu 10.10" instead.

Open /etc/default/grub, by typing this in console:

```
sudo gedit /etc/default/grub
```

change 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

change

```
#GRUB_TERMINAL=console
```
to 
```
GRUB_TERMINAL=console
```


then save and exit

in console type

```
sudo update-grub2
```

and then reboot. Thanks to [http://kosiara87.blogspot.com/2011/03/change-main-tty-resolution-to-vga-in.html](http://kosiara87.blogspot.com/2011/03/change-main-tty-resolution-to-vga-in.html)

---

