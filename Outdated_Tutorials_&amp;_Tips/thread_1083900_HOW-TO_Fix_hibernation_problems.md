---
title: "HOW-TO: Fix hibernation problems"
date: 2009-03-01
forum: Outdated Tutorials &amp; Tips
---

### Post by link178 on 2009-03-01
Hello:

I had problems with hibernation in my laptop (like lots of people) and I fixed it by downloading and installing uswsup, so type
   sudo apt-get install uswsusp

After that, you have to edit the /etc/uswsusp.conf file with this content:

```

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
resume device = /dev/sda5
splash = n
compress = y
early writeout = y
image size = 728237260
RSA key file = /etc/uswsusp.key
shutdown method = platform

```

The resume device matches the partition where your swap is ( and where the image will be saved and restored) . So you have to find your /dev/x partition that matches the swap. Gparted will tell you that.

And this is all . It worked for me and I have posted it in Launchpad bugs related to hibernation problems, with great results. But I don't know how to make it and sticky or something more visible, so I hope that it if really works for everyone, you will spread the word about it. I'll like to know your opinion about the solution too.

PD: I don't know if it fix suspend problems too, but it probably does.

---

