---
title: "GNUPlot Installation Problem"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by xptional on 2011-11-30
Hello :)

I am trying to install GNUPlot 4.4.4 on Ubuntu 10.04 LTS version. 

1) I have downlaoded from sourceforge and then extract it

2) Did as same as on written on the site [http://www.gnuplot.info/announce.4.4.4]("http://www.gnuplot.info/announce.4.4.4"), Other Notes Installation

Everything run fine except

```
make install
```

Output 

[HTML]khan@khan:~/gnuplot-4.4.4$ make install
Making install in config
make[1]: Entering directory `/home/khan/gnuplot-4.4.4/config'
make[2]: Entering directory `/home/khan/gnuplot-4.4.4/config'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/khan/gnuplot-4.4.4/config'
make[1]: Leaving directory `/home/khan/gnuplot-4.4.4/config'
Making install in m4
make[1]: Entering directory `/home/khan/gnuplot-4.4.4/m4'
make[2]: Entering directory `/home/khan/gnuplot-4.4.4/m4'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/khan/gnuplot-4.4.4/m4'
make[1]: Leaving directory `/home/khan/gnuplot-4.4.4/m4'
Making install in term
make[1]: Entering directory `/home/khan/gnuplot-4.4.4/term'
make[2]: Entering directory `/home/khan/gnuplot-4.4.4/term'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/gnuplot/4.4/js" || /bin/mkdir -p "/usr/local/share/gnuplot/4.4/js"
/bin/mkdir: cannot create directory `/usr/local/share/gnuplot': Permission denied
make[2]: *** [install-jsDATA] Error 1
make[2]: Leaving directory `/home/khan/gnuplot-4.4.4/term'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/khan/gnuplot-4.4.4/term'
make: *** [install-recursive] Error 1
khan@khan:~/gnuplot-4.4.4$[/HTML]

Please does somebody know about it ? Help me out , Thanks in advance !

---

### Post by searchfgold6789 on 2011-11-30
```
sudo make install
```Should fix it.

---

### Post by searchfgold6789 on 2011-11-30
By the way, it's available from the Software Center.

---

### Post by xptional on 2011-11-30
Thank you so much for your help, 

It works now with command ```
sudo make install
```

It works ! Thanks again

---

### Post by cholericfun on 2011-11-30
just as a note,
using the software centre is generally a good idea, not just for ease of installation but mainly for the simple automated update mechanisms and watching out over dependencies (otherwise an uninstall of some other program might remove files that are needed by some other manually installed program.

---

### Post by MG&amp;TL on 2011-11-30
It's less of a pain, it uses less disk space in the end, and removing stuff is much less of a pain. Go for the software center version.

---

### Post by xptional on 2011-12-01
OK. Thanks for your suggestions. 

Infact, I like to work on terminal for better understanding how things passed in Linux particular Ubuntu. Software center gives interface like windows, but I am already tired of these things. Anyhow, I utilize it when I badly need it. :)

---

### Post by horvathd on 2011-12-01
And when can we expect to update gnuplot in software center to 4.4.4? The 4.4.3 version has a bug which makes it unusable for me and I had to downgrade 4.4.2 in ubuntu 11.10.

---

### Post by MG&amp;TL on 2011-12-01
> **horvathd said:**
> And when can we expect to update gnuplot in software center to 4.4.4? The 4.4.3 version has a bug which makes it unusable for me and I had to downgrade 4.4.2 in ubuntu 11.10.

Go pester the guy who does the GNUPlot packaging. :)

You don't have to use software-center to install stuff, you can still have all the benefits of a package manager with:

```
sudo apt-get install <package>
```

---

