---
title: "Help installing emacs, getting a &quot;C compiler cannot create executables&quot; error"
date: 2008-09-13
forum: Programming Talk
---

### Post by tuffguy45 on 2008-09-13
I did some google work and couldn't really come up with anything. Whenever I type ./configure this is what I get:

sam@sam-laptop:~/Desktop/emacs-22.3$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by unutbu on 2008-09-13
To compile stuff, you need to install the build-essential package. 

Having said that, I think you would be better off installing emacs either from the official repository or from Vassalotti's ppa repo: [http://peadrop.com/blog/2007/09/17/pretty-emacs-reloaded/](http://peadrop.com/blog/2007/09/17/pretty-emacs-reloaded/)

The advantage of using Vassalotti's version is the fonts will look significantly better. 
(You'll be able to use ttf fonts).

By the way, Vassalotti's emacs-snapshot is version 23.0.60.1, which is newer than the source you seem to be compiling.

The page that referenced above seems to not be updated for Hardy. However, his ppa has hard packages available: 

[http://ppa.launchpad.net/avassalotti/ubuntu/pool/main/e/emacs-snapshot/](http://ppa.launchpad.net/avassalotti/ubuntu/pool/main/e/emacs-snapshot/)

Therefore, if you wish to try emacs-snapshot instead of the official repo version, follow his instructions except replace gutsy with hardy:
```

deb     http://ppa.launchpad.net/avassalotti/ubuntu hardy main
deb-src http://ppa.launchpad.net/avassalotti/ubuntu hardy main
```

---

### Post by bettlebrox on 2008-09-13
Do U have gcc installed (the GNU C compiler)? Is there a reason your installing Emacs yourself and not installing the Ubuntu packages?

---

### Post by tuffguy45 on 2008-09-13
I haven't downloaded the gnu c compiler so if it wasn't part of an update then no I don't have it. The reason why I'm not installing an ubuntu package is due to ignorrance and to answer the other guys question thats the link supplied by the emacs website...

---

### Post by dwhitney67 on 2008-09-13
Surely there must be a better way to install emacs.  Have you tried getting it from the repos:
```
sudo apt-get install emacs
```

If you want to do C s/w development, also get the GCC compiler:
```
sudo apt-get install build-essential
```

P.S.  There are many sub-packages available for emacs.  You can find a list of them (and many others) here:
[http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages)

---

### Post by tuffguy45 on 2008-09-13
I got it from the repo, I didn't realize I could do that. *nub alert*

now I just have to figure out the steep learning curve of emacs...

---

### Post by dwhitney67 on 2008-09-14
What is your compelling reason to use emacs?

You can pretty much accomplish the same s/w development task using gedit and the command-line to compile/link your application.

Emacs, though still be used by some, it not en-vogue as it once was.  Some swear by Eclipse, others like myself, prefer vim and the command-line (and Makefiles when dealing with larger projects).

---

