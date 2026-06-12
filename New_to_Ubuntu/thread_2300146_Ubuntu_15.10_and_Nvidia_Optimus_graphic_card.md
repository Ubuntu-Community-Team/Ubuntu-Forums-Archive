---
title: "Ubuntu 15.10 and Nvidia Optimus graphic card"
date: 2015-10-23
forum: New to Ubuntu
---

### Post by test.kram on 2015-10-23
[FONT=verdana]I have a Laptop with a Nvidia GT540M. Is there a way to get to work like with Windows? So I can use the Intel chip in normal mode and the Nvidia card when I play games.[/FONT]

---

### Post by grahammechanical on 2015-10-23
Have you installed the Nvidia driver? If you have then you can use the Nvidia settings utility that was installed with that driver to switch between Intel and Nvidia video adapters. That is as good as it gets. The Nvidia driver for Linux does not do automatic switching as the Nvidia Windows driver does.

This may also work. Although I am not sure if the PPA is set up for 15.10 (wily). After installing the PPA You may need to go into Software & Updates>Other Software tab and edit the PPA URL and change "wily" for "vivid" to download the indicator.

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

Regards.

---

### Post by test.kram on 2015-10-23
Thanks, not a very good way, but I think it'll do.

---

### Post by test.kram on 2015-10-23
Ok, I thought it works, but it doesn't. I have the Nvidia indicator in the top, but when I change the graphics mode it always stays in the Intel card mode. My Laptop on the other side is loud and hot as if he would be still using the Nvidia card. Any ideas??

---

