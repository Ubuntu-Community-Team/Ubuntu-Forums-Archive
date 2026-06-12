---
title: "Wrong Keyboard..."
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Eagle6395 on 2008-05-30
Hi

I have started using Ubuntu recently and have noticed that when I start Linux, my keyboard types letters different to what they should be. For example, '/' appears as '-'. I have to go to System -> Preferences -> Keyboard -> Layout and then create a new layout for the UK for it to work. The old layouts are still there, but don't work.

Please Help!

---

### Post by aysiu on 2008-06-04
Can you try pasting these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working
sudo dpkg-reconfigure xserver-xorg
``` Even though there are some questions about screen resolution and video stuff, there should also be a chance for you to change your system-wide keyboard identification.

If, for some reason, your screen resolution gets messed up after that, you can type ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.not.working
sudo cp /etc/X11/xorg.conf.working /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

---

