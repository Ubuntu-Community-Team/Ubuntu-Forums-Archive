---
title: "restricted drivers"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by jerzydirtracer on 2008-04-22
Hello, I have a restricted driver for my video, my laptop is a Toshiba Satellite 1415-S173 with Toshiba vid card, now I am using the basic driver from Ubuntu, I tried to load the driver on my 1st Ubuntu try, the screen went a multicolor prism or blocky screen, and the laptop seemed to lock up, I would like to load the driver for the 3D, if I get the screen of death and my computer locks up again, how do I recover my old working settings? I am using Ubuntu for a couple of months now and it is working great, including the wireless. How can I safely get my vid card working?

Thanks
Bob

---

### Post by mikeyphi on 2008-04-23
If you have the same problem again (after a reboot) then boot into the recovery option (usually second choice on boot page), when asked - select the shell option and enter the following at the command prompt:
dpkg-reconfigure -phigh xserver-xorg

you will see a lot of text with a question at the end of each section - accept the default answer unless you know otherwise!
when finished, reboot into the normal mode and all should be as it was!

---

