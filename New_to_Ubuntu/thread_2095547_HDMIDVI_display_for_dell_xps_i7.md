---
title: "HDMI/DVI display for dell xps i7"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by babar2141 on 2012-12-17
I have Dell XPS 15 i7 laptop.I try everything to connect my laptop to a DELL monitor through  HDMI/DVI cable but it is not working.I have a black screen.Also i  have installed disper.
The output of disper -l is
display default: default
 resolutions: 1024x768, 800x600
Can anybody help me to fix the issue.Like how i can connect my monitor to my laptop.
Thanks in advance

---

### Post by audiomick on 2012-12-17
I think it would assist people to help you if you mention which video card the Laptop has, and if you have installed a proprietary driver for it.

If you are not sure of the name of the video card, open a terminal and do

```
sudo lshw -C video
```

You will be asked for your password, which you will not see as you type it. Just enter the password and hit enter.

The command lshw generates a list of your hardware. Without the option, you get everything. The option -C tells it to restrict itself to whichever class of hardware you then name, in this case video.

---

