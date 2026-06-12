---
title: "FOMUS 0.1.18 installation"
date: 2014-05-14
forum: Packaging and Compiling Programs
---

### Post by fr-andres on 2014-05-14
Hi everyone,

Based on my own problems with this issue I wanted to explain here the minor patches that I needed to do, in order to get FOMUS 0.1.18 gcc-compiling and working on my Ubuntu 14.04-64bit (it compiles fine with sbcl by the way, also tested on my system).
I refer here the most related post that I found, 2012 by Mr. López-Lezcano, 
[http://sourceforge.net/p/fomus/mailman/message/29471486/](http://sourceforge.net/p/fomus/mailman/message/29471486/) he got it working by getting another svn versions, and with Fedora.

So far I didn't find on the web a solution by tweaking these sources, so I hope that this post is by any means helpful.
II'll try to refer them precisely but if you follow them and still get some problems drop a comment, I will for sure then remember if I forgot something

First of all you need to download the FOMUS sources and the and put them anywhere, let's say /path/to/fomus
here the sources
[http://sourceforge.net/projects/fomus/files/fomus-0.1.18-alpha.tar.gz/download](http://sourceforge.net/projects/fomus/files/fomus-0.1.18-alpha.tar.gz/download)

The Boost libraries are required. Here how to get them:
[http://askubuntu.com/questions/168053/how-to-install-all-the-boost-development-libraries](http://askubuntu.com/questions/168053/how-to-install-all-the-boost-development-libraries)
Lilypond is also strongly suggested
```
sudo apt-get install lilypond
```

Now that we have the prerequisites, let's edit some files:

```
gedit /path/to/fomus/src/lib/mods.h
```
change line 217 for:
   ```
void* getdata(FOMUS f) const {return **this**->initerrwrap(T::newdata(f));}
```
save and exit

```
gedit /path/to/fomus/src/lib/vars.cc
```
make the following changes: lines 461 til 478, change the iterating value i for (for example) w. You can copy the following chunk:
```

      rat **w**(miv.isnull() ? std::numeric_limits<fint>::min() + 1 : numtorat(miv));
      rat o(ocv.isnull() ? std::numeric_limits<fint>::min() + 1 : numtorat(ocv));
      user.push_back(new userkeysigent(m, a, **w**, o));
      if (m.numerator() == std::numeric_limits<fint>::min() + 1) return false; 
      if (a.numerator() == std::numeric_limits<fint>::min() + 1) a = 0; // must have at least these two things
      if (**w**.numerator() == std::numeric_limits<fint>::min() + 1) **w** = 0; // must have at least these two things
      if (o.numerator() != std::numeric_limits<fint>::min() + 1) { // got an octave
    rat x0(o + m);
    if (x0.denominator() != 1 || isblack(x0.numerator())) continue; // better to skip it 
    assert(todiatonic(x0.numerator()) >= 0 && todiatonic(x0.numerator()) < 75);
    sig[todiatonic(x0.numerator())] = std::pair<rat, rat>(a, **w**);
      } else {
    if (m.denominator() != 1 || isblack(m.numerator())) continue; // better to skip it 
    for (int x = todiatonic(m.numerator()) % 7; x < 75; x += 7) sig[x] = std::pair<rat, rat>(a, **w**);
      }
    }
    return true;
  }
```

and then save and exit. So far with the patching. Now calling ./configure with the actual path of the c++ Boost libraries should work fine:
```

cd /path/to/fomus
./configure --prefix=/usr --with-boost-libdir=/usr/lib/x86_64-linux-gnu/

```
[I]
(EDIT: for 32-bit systems, the boost libs may be in /usr/lib/i386-linux-gnu[/I])

and then installing fomus in /usr/local, the libraries in /usr/share/fomus, and  the binary file as /usr/bin/fomus, should be a reality!
```
make
sudo make install
```

a little terminal testing can confirm it:
[http://fomus.sourceforge.net/doc.html/Input.html#Input](http://fomus.sourceforge.net/doc.html/Input.html#Input)

```
fomus -o /tmp/test.ly /usr/local/fomus/doc/ex001.fms 
lilypond /tmp/test.ly
gnome-open /tmp/test.pdf
```

If you can see the theme of your next fugue congratulations! fomus is working on your system
Now I only need to know (and that's not so off-topic as it seems)... how to make common music 3.9 find it! has anybody idea?
here is the thread
[http://ubuntuforums.org/showthread.php?t=2224099](http://ubuntuforums.org/showthread.php?t=2224099)
should I link the libraries or the installation path?
where and how should I refer the link?

Best regards,
Andres

---

### Post by fr-andres on 2014-05-23
So, my FOMUS 0.1.18-alpha is now running perfectly through Grace 3.9.
Here the solution, thanks to Rick Taube and steeldrive:
[http://ubuntuforums.org/showthread.php?t=2224099](http://ubuntuforums.org/showthread.php?t=2224099)

Cheers!!
Andres

---

### Post by halfshark-alligato on 2014-09-26
Thank you thank you thank you @Andres!

I have had enormous difficulties trying to get started with cm, fomus, lilypond and boost--especially trying to work with homebrew and compiling on a Mac.

I switched over to the Ubuntu side here and had similar problems, but following the steps you outlined here exactly (and digging into the links you also provided) got me to a working FOMUS/lilypond install.

Now I just have to build common music/grace from source, and I expect I will be taking a look at your other related posts about that!

Thanks again,
Cicero

---

### Post by halfshark-alligato on 2014-09-26
I still got the errors that Andres mentions here: [http://ubuntuforums.org/showthread.php?t=2224099&p=13023795#post13023795](http://ubuntuforums.org/showthread.php?t=2224099&p=13023795#post13023795)

```

/usr/bin/ld: cannot find -lsndlib
```

and 

```
/usr/bin/ld: cannot find -lgsl
/usr/bin/ld: cannot find -lgslcblas
```

The solutions he describes for all of these errors worked for me, on 14.04.

Thanks again, Andres!

---

### Post by fr-andres on 2014-09-26
Youre welcome!
Im happy that the thread worked to you. This kind of issues arise when compilling with different systems and working with alpha versions, but thats ok when you are on the bleeding edge :mrgreen::mrgreen::mrgreen: it is indeed an amazing software and its worth it definitely.
But remember that with great power comes great responsibility!! haha have fun

Cheers,
Andres

---

