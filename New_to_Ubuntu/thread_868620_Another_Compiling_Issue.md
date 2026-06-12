---
title: "Another Compiling Issue"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by HieroPosche on 2008-07-24
I'm attempting to install gnome-hideseek.0.6.0 (compiling from source) and have run into a few issues along the way.

The initial attempt went as follows.

```
clay@Boris:~/Downloads/gnome-hideseek-0.6.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

After finding out that I needed libc6-dev and installing that via synaptic, I got it to go this far.

```
clay@Boris:~/Downloads/gnome-hideseek-0.6.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GHIDESEEK... configure: error: Package requirements (		  gtk+-2.0 >= 2.6.0			  gconf-2.0 >= 2.6.0			  ) were not met:

No package 'gtk+-2.0' found
No package 'gconf-2.0' found

```

I was able to discern that gtk+-2.0 was labeled libgtk2.0-dev and got that installed, but I'm unable to figure out how to get gconf-2.0.

Any help would be greatly appreciated.

This is a lot of effort to go through just to make the desktop on a cube have 4 different backgrounds so they animate when I spin it lol. (Even if there's an easier way to do that, I have to beat this problem to make me feel special)

---

### Post by iaculallad on 2008-07-24
On the terminal:

```
sudo apt-get install libgconf2-dev
```

---

### Post by SNuxoll on 2008-07-24
apt-cache is your friend

apt-cache search gconf | grep dev
libgconf2-dev - GNOME configuration database system (development)

That should be what you need.

---

### Post by HieroPosche on 2008-07-24
Worked like a charm, thanks :)

---

