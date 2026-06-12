---
title: "using Gnuplot"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by harish0508 on 2013-05-01
Hi...when I run gnuplot from terminal and give any command to plot, why dont I see the plot window ?

---

### Post by steeldriver on 2013-05-01
what is your gnuplot terminal type set to? e.g.

```
gnuplot> show terminal

   terminal type is wxt 0


```

---

### Post by harish0508 on 2013-05-01
it shows terminal type is unknown. and I tried changing into other few types like png, gif, latex etc, but I only get some scribbles in my terminal itself which resembles no plot..!! I'm simply typing plot sin(x)

---

### Post by steeldriver on 2013-05-01
How did you install gnuplot? it sounds like you only have gnuplot-nox, afaik you need gnuplot-x11 in order to get the functionality you are expecting

```

$ dpkg -l | grep gnuplot
ii  gnuplot                                         4.4.3-0ubuntu3                                      A command-line driven interactive plotting program
ii  gnuplot-nox                                     4.4.3-0ubuntu3                                      A command-line driven interactive plotting program
[B]ii  gnuplot-x11                                     4.4.3-0ubuntu3                                      A command-line driven interactive plotting program
[/B]
```

You can install the package with

```

sudo apt-get update
sudo apt-get install gnuplot-x11

```

Once gnuplot-x11 is installed the terminal type will probably default to wxt - if not you can manually set it using the 'set terminal' command

---

### Post by harish0508 on 2013-05-04
Thank you very much...that was the problem, and now I can finally plot..!!!

Thank you once again..!!

---

