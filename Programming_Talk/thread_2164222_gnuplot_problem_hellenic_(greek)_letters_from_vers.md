---
title: "gnuplot problem: hellenic (greek) letters from version &gt;4.4"
date: 2013-07-30
forum: Programming Talk
---

### Post by Claus7 on 2013-07-30
Hello,

the other day I wanted to use gnuplot as the [old days]("http://ubuntuforums.org/showthread.php?t=763753&highlight=gnuplot"), yet I was not able to type any hellenic letters, after the command prompt of gnuplot: gnuplot> 

Initially, I thought that my old maverick box was the case, so I tried to install newest versions of gnuplot. This was not possible since most of them require as a dependency libc6>2.15 and maverick with 2.12 cannot afford such an installation.

Using saucy alpha version under virtual box, I was able to install one of the latest gnuplot versions (4.6), yet still even then I was not able to type hellenic letters.

In order to solve the problem I installed:
First the gnuplot-nox 4.2.0-3 (amd64 binary) in [ubuntu gutsy]("https://launchpad.net/ubuntu/gutsy/amd64/gnuplot-nox/4.2.0-3")
and then the gnuplot-x11 4.2.0-3 (amd64 binary) in [ubuntu gutsy]("https://launchpad.net/ubuntu/gutsy/amd64/gnuplot-x11/4.2.0-3")
and I can work with gnuplot as usual.

EDIT: do not forget to uninstall the original corresponding libraries from your ubu box first, before you attempt the installation of the gutsy packages

Regards!

---

