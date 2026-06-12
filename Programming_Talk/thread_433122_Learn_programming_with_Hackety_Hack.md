---
title: "Learn programming with Hackety Hack"
date: 2007-05-04
forum: Programming Talk
---

### Post by jhnthn on 2007-05-04
I thought this was pretty cool, so I wanted to share it.

The same guy that made [Why's (Poignant) Guide to Ruby](http://www.poignantguide.net/ruby/) and [Try Ruby](http://tryruby.hobix.com/), has started a project called [Hackety Hack](http://hacketyhack.net). It's basically a fun way to introduce people to programming, using ruby. It has interactive lessons and it's written in the same style as his book. 

It's based on Mozilla's XUL (I think) and at the moment is only for windows. But, there should be a linux and mac osx version out in June!

---

### Post by buzz_ on 2007-07-24
Hi there.
I've been trying to install Hackety Hack 1.0 on Ubuntu 7.04 AMD64, but it just won't work:

> buzz@amethyst:~/Desktop/hacketyhack-0.L$ ./hacketyhack
./hacketyhack: error while loading shared libraries: libwx_gtk2u_aui-2.8.so.0: cannot open shared object file: No such file or directory

---

### Post by Note360 on 2007-07-24
this might not be it but is camping installed?

---

### Post by ButteBlues on 2007-07-24
> **buzz_ said:**
> Hi there.
I've been trying to install Hackety Hack 1.0 on Ubuntu 7.04 AMD64, but it just won't work:
Read the thread linked on the H-ety Hack download page. You need a preload added to that command. ;)

---

### Post by buzz_ on 2007-07-25
[QUOTE="_why"]To get Hackety Hack working on Ubuntu Feisty, download 0.L. And then:
```
sudo apt-get install libwxgtk2.8-0
cd hacketyhack-0.L                                                                                                  
LD_LIBRARY_PATH=/usr/lib/firefox:. ./hacketyhack
```[/QUOTE]

I've already posted this error ( and im not the only one ) at the [Hackety Hack Forums]("http://talkety.hacketyhack.net/thread/130/hackety-hack-for-linux?page=2"), but no answers yet.

My error:
```
buzz@amethyst:~/hacketyhack$ LD_LIBRARY_PATH=/usr/lib/firefox:. ./hacketyhack
./hacketyhack: error while loading shared libraries: libwx_gtk2u_aui-2.8.so.0: cannot open shared object file: No such file or directory
```

---

### Post by ButteBlues on 2007-07-25
> **buzz_ said:**
> I've already posted this error ( and im not the only one ) at the [Hackety Hack Forums]("http://talkety.hacketyhack.net/thread/130/hackety-hack-for-linux?page=2"), but no answers yet.

My error:
```
buzz@amethyst:~/hacketyhack$ LD_LIBRARY_PATH=/usr/lib/firefox:. ./hacketyhack
./hacketyhack: error while loading shared libraries: libwx_gtk2u_aui-2.8.so.0: cannot open shared object file: No such file or directory
```
What version of Ubuntu are you running?

---

### Post by buzz_ on 2007-07-25
[quote="buzz_"]Ubuntu 7.04 AMD64[/quote] ;)

---

### Post by buzz_ on 2007-07-26
Hey, I'd really like to use this program on Ubuntu, so please help someone!

---

### Post by unixhead on 2007-07-26
Why don't you just email _why (the author of Hackety Hack)? Seems that Linux version is coming up next, not sure whether he released it at all.

---

### Post by jyba on 2007-07-26
Strange, it works on my machine.
Does it work if you cd to the hacketyhack-0.L directory and type...
```
LD_LIBRARY_PATH=/usr/lib/firefox:. ./hacketyhack
```
...?
(it takes 6 or 7 seconds to start up).

---

### Post by buzz_ on 2007-07-26
No success! 

```

[buzz@amethyst ~]$ cd Desktop
[buzz@amethyst Desktop]$ cd hacketyhack-0.L
[buzz@amethyst hacketyhack-0.L]$ LD_LIBRARY_PATH=/usr/lib/firefox:. ./hacketyhack
./hacketyhack: error while loading shared libraries: libwx_gtk2u_aui-2.8.so.0: cannot open shared object file: No such file or directory
[buzz@amethyst hacketyhack-0.L]$ 
```

---

### Post by AnoJ on 2007-07-31
hey, I am needing help getting hackety to run as well. I am totally new to Linux so probably made a noob mistake.
I installed it following these instructions...

[http://wfarr.wordpress.com/2007/06/01/hackety-hack-meet-linux/](http://wfarr.wordpress.com/2007/06/01/hackety-hack-meet-linux/)

Now when in enter LD_LIBRARY_PATH=/usr/lib/firefox:. ./hacketyhack

I get 
bash: ./hacketyhack: No such file or directory

I untarred the tarball to my desktop if this info helps shed any light.
would be grateful for any help.

---

### Post by buzz_ on 2007-08-03
Still won't work with Ubuntu 64 Bit ;)

---

### Post by GNUlancer on 2007-11-24
> **AnoJ said:**
> hey, I am needing help getting hackety to run as well. I am totally new to Linux so probably made a noob mistake.
I installed it following these instructions...

[http://wfarr.wordpress.com/2007/06/01/hackety-hack-meet-linux/](http://wfarr.wordpress.com/2007/06/01/hackety-hack-meet-linux/)

Now when in enter LD_LIBRARY_PATH=/usr/lib/firefox:. ./hacketyhack

I get 
bash: ./hacketyhack: No such file or directory

I untarred the tarball to my desktop if this info helps shed any light.
would be grateful for any help.


The dot in './hacketyhack' means current directory. When you typed this your current directory wasn't that where you untarred hacketyhack. You need to change directory first, like this:

```
cd ~/Desktop/hacketyhack-0.L
```
or you can just replace './hacketyhack' with this file's full path (drag&drop file into the terminal)

---

### Post by Kadrus on 2007-11-24
It's very good and nice :)..
Nice Project..Didn't download..but read about it though..

---

### Post by ThinkBuntu on 2007-11-24
Maybe a Mac version will be released some day. For now, this is spectacular: [http://rubylearning.com/satishtalim/tutorial.html](http://rubylearning.com/satishtalim/tutorial.html)

---

### Post by cgarza on 2008-10-29
> **buzz_ said:**
> Hi there.
I've been trying to install Hackety Hack 1.0 on Ubuntu 7.04 AMD64, but it just won't work:

to resolve the libwx_gtk2u_aui-2.8.so.0
issue run 
sudo apt-get install libwxgtk2.8-0
(this works on hardy)

---

### Post by Ferrat on 2008-10-29
> **cgarza said:**
> to resolve the libwx_gtk2u_aui-2.8.so.0
issue run 
sudo apt-get install libwxgtk2.8-0
(this works on hardy)

I got libwxgtk2.8-0 installed but still it wont find libwx_gtk2u_aui-2.8.so.0, guessing a link or path error but don't know which

---

### Post by cgarza on 2008-10-29
> **Ferrat said:**
> I got libwxgtk2.8-0 installed but still it wont find libwx_gtk2u_aui-2.8.so.0, guessing a link or path error but don't know which

Please be sure its version 2.8 since thats what hackety is looking for.
Not 2.4 or 2.6 but 2.8


crc@bork$ dpkg -S /usr/lib/libwx_gtk2u_aui-2.8.so.0
libwxgtk2.8-0: /usr/lib/libwx_gtk2u_aui-2.8.so.0

the above command shows the file is owned by libwxgtk2.8-0
/usr/lib/libwx_gtk2u_aui-2.8.so.0

do you have this in your /usr/lib?

---

### Post by Ferrat on 2008-10-29
did

```
icebreaker@iceblock:~$ dpkg -S /usr/lib/libwx_gtk2u_aui-2.8.so.0
libwxgtk2.8-0: /usr/lib/libwx_gtk2u_aui-2.8.so.0
```

but I still get the message that it can't find it =/

---

### Post by timClicks on 2009-02-14
I have a similar error to those above:

```

~/hacketyhack-0.L$ LD_LIBRARY_PATH=/usr/lib/firefox:. ./hacketyhack
./hacketyhack: error while loading shared libraries: libxpcom.so: cannot open shared object file: No such file or directory

```

---

