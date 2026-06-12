---
title: "Howto: Install and use Luminocity (eye candy)"
date: 2005-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2005-06-29
EDIT: because of the fact that I can't host the howto here without some of the lines adopting smiley faces, I posted it here:

[https://wiki.ubuntu.com/LuminocityHowTo](https://wiki.ubuntu.com/LuminocityHowTo)

If you are like me, you probably like to have some eye candy and the Luminocity demos enticed you. All those effect look great, but what good are they if we have to wait years for the effect to get into Gnome? 

I created this howto to help people like myself install Luminocity now in order to try out the new effects. It does alright on my Pentium 4 with an ATI card (newest fglrx drivers installed), but using a mouse wheel seems to make it crash (anyone got a work around?).

This is fun to play with (I really like the desktop switcher) but its not a functional window manager like Metacity. Its only to be looked at. So don't show this off to all your Window's buddies (unless you say "this is the future of Linux") because they will be disappointed when they switch to use it only to find out its basically a demo.

This howto was created by adding this Gentoo one to this wikipage:

[http://64.233.167.104/search?q=cache:2ai6TpucWhoJ:forums.gentoo.org/viewtopic-t-313926.html+install+luminocity&hl=en&lr=&client=firefox&strip=1](http://64.233.167.104/search?q=cache:2ai6TpucWhoJ:forums.gentoo.org/viewtopic-t-313926.html+install+luminocity&hl=en&lr=&client=firefox&strip=1)

---

### Post by N'Jal on 2005-06-29
Tempting, however will lumocity became the default window manager? If so i have to resist temptation since i need a roughly working system, and right now it's dying. Anything more coud kill it.

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=N'Jal]Tempting, however will lumocity became the default window manager? [/QUOTE]

No. It works within its own canvas...its more a cool tech demo that it is a new window manager.

---

### Post by poofyhairguy on 2005-06-29
Here is a screenshot of Luminocity running with Gxine playing a movie inside it while I move it around.

Neat stuff.

---

### Post by poofyhairguy on 2005-06-29
By... the way..I noticed that this makes the CPU on my Pentium 4 max out....so this might not be the thing for older systems.

A good link for it:

[http://fishsoup.net/blog/2004/11/01/](http://fishsoup.net/blog/2004/11/01/)

---

### Post by poofyhairguy on 2005-06-29
Can someone try this and see if it works for more than me?

---

### Post by keybreckaba on 2005-06-30
sorry stupid ? but what is the smily supposed to be?

i am looking to try to try this out but just can't think of what it is thanks

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=keybreckaba]sorry stupid ? but what is the smily supposed to be?

i am looking to try to try this out but just can't think of what it is thanks[/QUOTE]

Look at my edit for info.

---

### Post by codejunkie on 2005-06-30
[QUOTE=poofyhairguy]Can someone try this and see if it works for more than me?[/QUOTE]
im working on it i let you know my results ps: thanks  i've been wanting to try this for a while \\:D/

---

### Post by codejunkie on 2005-06-30
when i try and install jhbuild with this command 
```
cvs -d :pserver:[MAILTO] anonymous@anoncvs.gnome.org:/cvs/gnome get jhbuild cd jhbuild/ make make install

```
i get this error Unknown command: `anonymous@anoncvs.gnome.org:/cvs/gnome' i have never compiled from cvs before so could you tell a cvs newbie what he's doing wrong.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=codejunkie]when i try and install jhbuild with this command 
```
cvs -d :pserver:[MAILTO] anonymous@anoncvs.gnome.org:/cvs/gnome get jhbuild cd jhbuild/ make make install

```
i get this error Unknown command: `anonymous@anoncvs.gnome.org:/cvs/gnome' i have never compiled from cvs before so could you tell a cvs newbie what he's doing wrong.[/QUOTE]

take out that damn mailto that the wiki added.

---

### Post by codejunkie on 2005-06-30
i still can't seem to get it right now its giving me this 
```
cvs checkout: warning: failed to open /home/codejunkie/.cvspass for reading: No such file or directory
cvs server: cannot find module `cd' - ignored
cvs server: cannot find module `make' - ignored
cvs server: cannot find module `make' - ignored
cvs server: cannot find module `install' - ignored
cvs [checkout aborted]: cannot expand modules

```
i got it sorry for the aggravation.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=codejunkie]i still can't seem to get it right now its giving me this 
```
cvs checkout: warning: failed to open /home/codejunkie/.cvspass for reading: No such file or directory
cvs server: cannot find module `cd' - ignored
cvs server: cannot find module `make' - ignored
cvs server: cannot find module `make' - ignored
cvs server: cannot find module `install' - ignored
cvs [checkout aborted]: cannot expand modules

```[/QUOTE]


Did you install the build-essential package like I said to?

---

### Post by codejunkie on 2005-06-30
yeah i have build-essential installed  and i got jhbuild installed it was just a typo.

---

### Post by codejunkie on 2005-06-30
i hate to keep doing this but now when i do 
```
cvs -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome get luminocity/luminocity.modules
cp luminocity/luminocity.modules modulesets/
```
i now get this ```
cvs checkout: warning: failed to open /home/codejunkie/.cvspass for reading: No such file or directory
```

---

### Post by parktownprawn on 2005-06-30
[QUOTE=poofyhairguy]
Unfortunately the wiki automatically make @ links into mail tos....both suck for this howto. You'll have to compare the two to get the correct lines (anyone have a server space I can borrow for a good ole HTML howto?).

[/QUOTE]

hope you don't mind - i edited the wiki you posted so that @links don't appear as mailtos:

you can use tripple braces for verbatim code

{{{ Verbatim code blah blah}}}

rather than

''' Verbatim code blah blah blah ''' 

hopefully i didn't introduce anymistakes in the wikki

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=parktownprawn]hope you don't mind - i edited the wiki you posted so that @links don't appear as mailtos:

you can use tripple braces for verbatim code

{{{ Verbatim code blah blah}}}

rather than

''' Verbatim code blah blah blah ''' 

hopefully i didn't introduce anymistakes in the wikki[/QUOTE]


Good job...thanks.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=codejunkie]i hate to keep doing this but now when i do 
```
cvs -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome get luminocity/luminocity.modules
cp luminocity/luminocity.modules modulesets/
```
i now get this ```
cvs checkout: warning: failed to open /home/codejunkie/.cvspass for reading: No such file or directory
```[/QUOTE]


Try from the beginning from teh wiki. Its fixed.

---

### Post by codejunkie on 2005-06-30
it's compiling now i just hope it finishes without errors cause it seems like it's taking as long to compile this as it does to compile a kernel :) but it's worth the wait to try out some new i candy  O:) again thanks for all the help and thanks again for the how-to.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=codejunkie]it's compiling now i just hope it finishes without errors cause it seems like it's taking as long to compile this as it does to compile a kernel :) but it's worth the wait to try out some new i candy  O:) again thanks for all the help and thanks again for the how-to.[/QUOTE]

No problem. Please post if it works for you...and your hardware and how it performs.

---

### Post by codejunkie on 2005-06-30
[QUOTE=poofyhairguy]No problem. Please post if it works for you...and your hardware and how it performs.[/QUOTE]

it's working but it's a little slow moving stuff around inside luminocity
athlon xp 2100+
1gig ram
Nvidia GeForce 4 MX 4000 not great but it works :) 
2.6.12.1-custom-k7 kernel
it took about 45 minutes to compile and install
and im having the same issues about the scrollwheel crashing it on my computer also again thanks for all the help it's a little slow but i like it ;-).

---

### Post by jzke on 2005-06-30
[QUOTE=codejunkie]it's working but it's really slow on my system 
athlon xp 2100+
1gig ram
Nvidia GeForce 4 MX 4000 not great but it works :) 
2.6.12.1-custom-k7 kernel
it took about 45 minutes to install
and im having the same issue about the scrollwheel crashing it on my computer also again thanks for all the help it's slow but i like it ;-) .[/QUOTE]
 Hmm, not sure if I'll try it now, I have similar specs, and don't want to be slowed down... although I can usually never resist eye candy!

I did begin to install it and got this error though;

jake@ubuntu:~/luminocity$ cvs -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome get jhbuild

Unknown host anoncvs.gnome.org.


Any suggestions?

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=jzke]Hmm, not sure if I'll try it now, I have similar specs, and don't want to be slowed down... although I can usually never resist eye candy!

I did begin to install it and got this error though;

jake@ubuntu:~/luminocity$ cvs -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome get jhbuild

Unknown host anoncvs.gnome.org.


Any suggestions?[/QUOTE]

Are you connected to the internet?

---

### Post by codejunkie on 2005-06-30
[QUOTE=jzke]Hmm, not sure if I'll try it now, I have similar specs, and don't want to be slowed down... although I can usually never resist eye candy!

I did begin to install it and got this error though;

jake@ubuntu:~/luminocity$ cvs -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome get jhbuild

Unknown host anoncvs.gnome.org.


Any suggestions?[/QUOTE]

it won't slow the system down all the time it's just a little slow while it's running my cpu stayed around 40-85 percent load with about 5 apps running in it and about four firefox windows open and an xterm outside of luminocity. it's just a little slow moving stuff around in luminocity i think it's maybe video card related. i believe it's just a testbed application for thing's that may make it into gnome.  try it it's fun and and pretty exciting to see what things may be moving into gnome :). if it's to slow you can just shut it down and it won't slow the system down when your not using it. what i ment by slow is if you've ever used vnc software it's like using vnc with tons of eyecandy turned on i get some video lag when moving/opening  stuff in luminocity but when using stuff outside of luminocity it seems normal.

---

### Post by Paulus on 2005-06-30
hey, i thought i'd give this a go, i've run into a problem though...
within the ~/luminocity/jhbuild directory, once i have run make when i try to run "make install"  I get the following error:
> paulus@ubuntu:~/luminocity/jhbuild$ make install
Creating /home/paulus/bin/jhbuild
Creating /home/paulus/.gnome2/vfolders/applications/jhbuild.desktop
Don't forget to create ~/.jhbuildrc
install -m755 install-check /home/paulus/bin/install-check
paulus@ubuntu:~/luminocity/jhbuild$      

any ideas?   I'm using KDE btw :o

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=Paulus]hey, i thought i'd give this a go, i've run into a problem though...
within the ~/luminocity/jhbuild directory, once i have run make when i try to run "make install"  I get the following error:
 

any ideas?   I'm using KDE btw :o[/QUOTE]


Thats not an error. Continue.

---

### Post by Paulus on 2005-06-30
lol.
Building now... time for some breakfast :)

---

### Post by Paulus on 2005-06-30
cool!  It took about 12 mins to build.  Here is a screenie, a bit of windows action!

[[IMG]http://img148.imageshack.us/img148/2986/lol15ep.th.jpg[/IMG]](http://img148.imageshack.us/my.php?image=lol15ep.jpg)

it seems to run very smooth, but jerks every 5 odd seconds :/

My specs: Ath XP @ 2.3ghz Geforce FX 5950

EDIT: stuttering gone, it was the Kpager causing it!  Now it's smooth as butter.  thanks to poofyhairguy!

---

### Post by warptrosse on 2005-07-01
I have the next error:

```
*** Building luminocity *** [24/24]

make
make  all-recursive
make[1]: Entering directory `/home/warp/luminocity/src/luminocity/luminocity'
Making all in src
make[2]: Entering directory `/home/warp/luminocity/src/luminocity/luminocity/src'
glib-genmarshal --prefix=lmc_marshal lmc-marshal.list --header > lmc-marshal.h
glib-genmarshal --prefix=lmc_marshal lmc-marshal.list --body > lmc-marshal.c
make  all-am
make[3]: Entering directory `/home/warp/luminocity/src/luminocity/luminocity/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT async.o -MD -MP -MF ".deps/async.Tpo" \
  -c -o async.o `test -f 'async.c' || echo './'`async.c; \
then mv -f ".deps/async.Tpo" ".deps/async.Po"; \
else rm -f ".deps/async.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT bits.o -MD -MP -MF ".deps/bits.Tpo" \
  -c -o bits.o `test -f 'bits.c' || echo './'`bits.c; \
then mv -f ".deps/bits.Tpo" ".deps/bits.Po"; \
else rm -f ".deps/bits.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT decoration.o -MD -MP -MF ".deps/decoration.Tpo" \
  -c -o decoration.o `test -f 'decoration.c' || echo './'`decoration.c; \
then mv -f ".deps/decoration.Tpo" ".deps/decoration.Po"; \
else rm -f ".deps/decoration.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT display.o -MD -MP -MF ".deps/display.Tpo" \
  -c -o display.o `test -f 'display.c' || echo './'`display.c; \
then mv -f ".deps/display.Tpo" ".deps/display.Po"; \
else rm -f ".deps/display.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT events.o -MD -MP -MF ".deps/events.Tpo" \
  -c -o events.o `test -f 'events.c' || echo './'`events.c; \
then mv -f ".deps/events.Tpo" ".deps/events.Po"; \
else rm -f ".deps/events.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT gui.o -MD -MP -MF ".deps/gui.Tpo" \
  -c -o gui.o `test -f 'gui.c' || echo './'`gui.c; \
then mv -f ".deps/gui.Tpo" ".deps/gui.Po"; \
else rm -f ".deps/gui.Tpo"; exit 1; \
fi
gui.c: In function `gui_begin_move':
gui.c:821: warning: implicit declaration of function `lmc_toplevel_begin_move'
gui.c: In function `gui_update_move':
gui.c:831: warning: implicit declaration of function `lmc_toplevel_update_move'
gui.c: In function `gui_end_move':
gui.c:839: warning: implicit declaration of function `lmc_toplevel_end_move'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT lmc-marshal.o -MD -MP -MF ".deps/lmc-marshal.Tpo" \
  -c -o lmc-marshal.o `test -f 'lmc-marshal.c' || echo './'`lmc-marshal.c; \
then mv -f ".deps/lmc-marshal.Tpo" ".deps/lmc-marshal.Po"; \
else rm -f ".deps/lmc-marshal.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT main.o -MD -MP -MF ".deps/main.Tpo" \
  -c -o main.o `test -f 'main.c' || echo './'`main.c; \
then mv -f ".deps/main.Tpo" ".deps/main.Po"; \
else rm -f ".deps/main.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT output.o -MD -MP -MF ".deps/output.Tpo" \
  -c -o output.o `test -f 'output.c' || echo './'`output.c; \
then mv -f ".deps/output.Tpo" ".deps/output.Po"; \
else rm -f ".deps/output.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT root.o -MD -MP -MF ".deps/root.Tpo" \
  -c -o root.o `test -f 'root.c' || echo './'`root.c; \
then mv -f ".deps/root.Tpo" ".deps/root.Po"; \
else rm -f ".deps/root.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT texture.o -MD -MP -MF ".deps/texture.Tpo" \
  -c -o texture.o `test -f 'texture.c' || echo './'`texture.c; \
then mv -f ".deps/texture.Tpo" ".deps/texture.Po"; \
else rm -f ".deps/texture.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT toplevel.o -MD -MP -MF ".deps/toplevel.Tpo" \
  -c -o toplevel.o `test -f 'toplevel.c' || echo './'`toplevel.c; \
then mv -f ".deps/toplevel.Tpo" ".deps/toplevel.Po"; \
else rm -f ".deps/toplevel.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT utils.o -MD -MP -MF ".deps/utils.Tpo" \
  -c -o utils.o `test -f 'utils.c' || echo './'`utils.c; \
then mv -f ".deps/utils.Tpo" ".deps/utils.Po"; \
else rm -f ".deps/utils.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT window.o -MD -MP -MF ".deps/window.Tpo" \
  -c -o window.o `test -f 'window.c' || echo './'`window.c; \
then mv -f ".deps/window.Tpo" ".deps/window.Po"; \
else rm -f ".deps/window.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/warp/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/warp/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT spring-model.o -MD -MP -MF ".deps/spring-model.Tpo" \
  -c -o spring-model.o `test -f 'spring-model.c' || echo './'`spring-model.c; \
then mv -f ".deps/spring-model.Tpo" ".deps/spring-model.Po"; \
else rm -f ".deps/spring-model.Tpo"; exit 1; \
fi
gcc  -g -O2 -Wall   -o luminocity  async.o bits.o decoration.o display.o events.o gui.o lmc-marshal.o main.o output.o root.o texture.o toplevel.o utils.o window.o spring-model.o -pthread -L/home/warp/luminocity/opt/luminocity/lib -L/usr/local/kx/lib -lgthread-2.0 -lgdk_pixbuf-2.0 -lm -lpangoft2-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lXdamage -lXcomposite -lXfixes -lXtst -lXext -lXcursor -lXrender -lX11 -ldl   -L /usr/X11R6/lib -lGL -lGLU
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeQueryVersion'
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make[3]: *** [luminocity] Error 1
make[3]: Leaving directory `/home/warp/luminocity/src/luminocity/luminocity/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/warp/luminocity/src/luminocity/luminocity/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/warp/luminocity/src/luminocity/luminocity'
make: *** [all] Error 2
*** error during stage build of luminocity: could not build module *** [24/24]


  [1] rerun stage build
  [2] ignore error and continue to install
  [3] give up on module
  [4] start shell
  [5] go to stage force_checkout
  [6] go to stage configure
choice: 1

```

how can i fix it???

thanks...

---

### Post by keybreckaba on 2005-07-01
i have the same error 
anybody know whats wrong and how to fix it 
thanks

---

### Post by poofyhairguy on 2005-07-01
maybe install your kernel version's headers?

---

### Post by warptrosse on 2005-07-01
i have this kernel 2.6.10-5-k7....

---

### Post by WiLLiE on 2005-07-01
Exactly the same problem here.
No ideas?

Edit:
These two seemes to be the problem:
```

undefined reference to `XF86VidModeQueryVersion'
undefined reference to `XF86VidModeGetModeLine'
```
I found [this in an old Ubuntu thread:](http://ubuntuforums.org/showthread.php?t=3790&page=8&pp=10) (2nd & 3rd post)

> 
daniels 12-02-2004, 11:56 AM

For a quick hack, link with -lXxf86vm and -lpthread also (or maybe just -pthread?); I'll fix this in the next revision of the X.Org packages. Thanks.
And this```

xdpyinfo | grep XF86VidModeQueryVersion
xdpyinfo | grep XF86VidModeGetModeLine
```outputs nothing.

Perhaps a quick hack as Daniels suggested might be needed?


Edit2:
Hey, it worked!

I performed these steps:

1. nano -w ~/luminocity/src/luminocity/luminocity/Makefile

2. Locate the line
    DEP_LIBS = -pthread...
    add    -lXxf86vm     at the end of the line

3. Run 'make' in that directory

4. I ran the whole deal again: (to be sure)
    ~/bin/jhbuild -f ~/luminocity/jhbuildrc-luminocity build xserver luminocity
     (it doesnt build all the packages again)

5. **** Success ****

6. Continue the guide  :)

Edit3:

Well, I do get an error when launching gmplayer or Amarok:
(DISPLAY=:1 gmplayer &)

Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".

But i've tried gEdit and xmms so far, and both work fine.

---

### Post by m87 on 2005-07-04
[QUOTE=WiLLiE]Edit3:

Well, I do get an error when launching gmplayer or Amarok:
(DISPLAY=:1 gmplayer &)

Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".

But i've tried gEdit and xmms so far, and both work fine.[/QUOTE]

that's probably because they require an extension that Xephyr or Xfake or Xglx or Xbloodyhell that are you use to run luminocity currently miss. honestly I've tried it and I found it awesome
BUT
it's no use by now... we shall wait until metacity *absorbs* the luminocity and spiffifity features ~ and maybe we should wait until X11R7 :)

---

### Post by Tamir on 2005-07-05
hi, I have a problem too:
I am 64Bit user.

root@ubuntu:/home/tamir # ~/bin/jhbuild -f ~/luminocity/jhbuildrc-luminocity build 

```

Traceback (most recent call last):
  File "/root/bin/jhbuild", line 5, in ?
    import jhbuild.main
ImportError: No module named jhbuild.main
```

what should I do?

[COLOR=Red]Doesn't matter. SOLVED[/COLOR]

Another Problem  :-? :

[HTML]*** Building luminocity *** [24/24]

make
make  all-recursive
make[1]: Entering directory `/home/tamir/luminocity/src/luminocity/luminocity'
Making all in src
make[2]: Entering directory `/home/tamir/luminocity/src/luminocity/luminocity/src'
make  all-am
make[3]: Entering directory `/home/tamir/luminocity/src/luminocity/luminocity/src'
gcc  -g -O2 -Wall   -o luminocity  async.o bits.o decoration.o display.o events.o gui.o lmc-marshal.o main.o output.o root.o texture.o toplevel.o utils.o window.o spring-model.o -pthread -L/home/tamir/luminocity/opt/luminocity/lib64 -L/usr/local/kx/lib -lgthread-2.0 -lgdk_pixbuf-2.0 -lm -lpangoft2-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lXdamage -lXcomposite -lXfixes -lXtst -lXext -lXcursor -lXrender -lX11 -ldl   -L /usr/X11R6/lib -lGL -lGLU
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2fc1): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeQueryVersion'
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2ffd): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make[3]: *** [luminocity] Error 1
make[3]: Leaving directory `/home/tamir/luminocity/src/luminocity/luminocity/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tamir/luminocity/src/luminocity/luminocity/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tamir/luminocity/src/luminocity/luminocity'
make: *** [all] Error 2
*** error during stage build of luminocity: could not build module *** [24/24]


  [1] rerun stage build
  [2] ignore error and continue to install
  [3] give up on module
  [4] start shell
  [5] go to stage force_checkout
  [6] go to stage configure
choice:[/HTML]

I tried what somebody here said before be, it doesn't work.

---

### Post by papabean on 2005-07-05
I'm just popping in to say it did work for me.  Although the menus "wobbling" about takes a little getting used to.  Definitely not going to consider doing any real work in Luminocity, but it's a damned fine display of eye candy.

System Specs:
AMD Athlon XP 2400+
Asus A798X Deluxe Mobo
NVidia 5200 FX (Latest drivers from NVidia's website)

---

### Post by Dali on 2005-07-05
I am having the same problems as others have recently had.  The fix that worked for Willie provides me with no joy.  

I had tried to build luminocity a while ago and got to this stage with the same error...was hoping this HOWTO would shed further light on the issue, but I find myself staring at the same error.  

Any help?

Cheers,

dali

---

### Post by markmark on 2005-07-06
Okay, I had this problem and have managed to compile now (although I haven't had a chance to run it since I've being doing this remotely via ssh).

I found that even though I had added "-lXxf86vm" to DEP_LIBS in the Makefile as suggested by Willie it wasn't turning up in the gcc command line produced by make. So I cd'd to src then manually did the gcc command that make was trying to run with "-lXxf86vm" added to the end like:

cd src
gcc  -g -O2 -Wall   -o luminocity  async.o bits.o decoration.o display.o events.o gui.o lmc-marshal.o main.o output.o root.o texture.o toplevel.o utils.o window.o spring-model.o -pthread -L/home/tamir/luminocity/opt/luminocity/lib64 -L/usr/local/kx/lib -lgthread-2.0 -lgdk_pixbuf-2.0 -lm -lpangoft2-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lXdamage -lXcomposite -lXfixes -lXtst -lXext -lXcursor -lXrender -lX11 -ldl   -L /usr/X11R6/lib -lGL -lGLU -lXxf86vm

That worked. The other thing I had already done which may have helped is to update the X11_Xext_LIB variable to point to libXxf86vm as well. Not sure if this did anything, but can't hurt:

X11_Xext_LIB="/usr/X11R6/lib/libXext.so;/usr/X11R6/lib/libXxf86vm.so"

Anyway, hope that helps someone. Incidentally when I was googling around trying to see what was wrong it seemed all the people with this problem where running the nvidia drivers?

---

### Post by papabean on 2005-07-06
It would appear I was wrong in claiming success with Luminocity.  It worked once and has not worked since.

Now, when I run the exact same steps that showed off this crazy bit of eye candy, I get the following: ```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  118 (X_SetModifierMapping)
  Value in failed request:  0xcf
  Serial number of failed request:  87
  Current serial number in output stream:  87
Segmentation fault
```I've seen similar errors with other software that tries to fiddle with X (skippy, for example) but not sure what it means in regards to Luminocity.

---

### Post by Dali on 2005-07-06
[QUOTE=markmark]Okay, I had this problem and have managed to compile now (although I haven't had a chance to run it since I've being doing this remotely via ssh).

I found that even though I had added "-lXxf86vm" to DEP_LIBS in the Makefile as suggested by Willie it wasn't turning up in the gcc command line produced by make. So I cd'd to src then manually did the gcc command that make was trying to run with "-lXxf86vm" added to the end like:

cd src
gcc  -g -O2 -Wall   -o luminocity  async.o bits.o decoration.o display.o events.o gui.o lmc-marshal.o main.o output.o root.o texture.o toplevel.o utils.o window.o spring-model.o -pthread -L/home/tamir/luminocity/opt/luminocity/lib64 -L/usr/local/kx/lib -lgthread-2.0 -lgdk_pixbuf-2.0 -lm -lpangoft2-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lXdamage -lXcomposite -lXfixes -lXtst -lXext -lXcursor -lXrender -lX11 -ldl   -L /usr/X11R6/lib -lGL -lGLU -lXxf86vm

That worked. The other thing I had already done which may have helped is to update the X11_Xext_LIB variable to point to libXxf86vm as well. Not sure if this did anything, but can't hurt:

X11_Xext_LIB="/usr/X11R6/lib/libXext.so;/usr/X11R6/lib/libXxf86vm.so"

Anyway, hope that helps someone. Incidentally when I was googling around trying to see what was wrong it seemed all the people with this problem where running the nvidia drivers?[/QUOTE]
 I think you're right about the nvidia drivers being the common issue for those of us with that particular error...

Sigh.  

Thanks for the tips, will try that today and see if I get any love.

Dali

---

### Post by afonit on 2005-07-06
fyi

I had to use this
cvs -d :pserver:anonymous@anoncvs3.gnome.org:/cvs/gnome get jhbuild


note the "3" at the end of anoncvs

then it was able to get jhbuild

without the 3, I would get the error/message:  "no such user anonymous in CVSROOT/passwd"

---

### Post by gorth on 2005-07-07
The last step in the howto fails in my case with:

"Cannot open target display"

Anyone else experiencing the same problem?

---

### Post by One Quick Question on 2005-07-16
For anyone still having problems, make sure if you use the nvidia driver that you apt-get nvidia-glx-dev and libxxf86vm-dev.
After implementing WiLLiE's fix and I got those packages, everything worked fined.
So yay.

Luminocity crashes for me like a quadriplegia 16 year old driver late for the prom, but at least it compiles!

---

### Post by jzke on 2005-07-30
[QUOTE=Tamir]hi, I have a problem too:
I am 64Bit user.

root@ubuntu:/home/tamir # ~/bin/jhbuild -f ~/luminocity/jhbuildrc-luminocity build 

```

Traceback (most recent call last):
  File "/root/bin/jhbuild", line 5, in ?
    import jhbuild.main
ImportError: No module named jhbuild.main
```

what should I do?

[COLOR=Red]Doesn't matter. SOLVED[/COLOR]

Another Problem  :-? :

[HTML]*** Building luminocity *** [24/24]

make
make  all-recursive
make[1]: Entering directory `/home/tamir/luminocity/src/luminocity/luminocity'
Making all in src
make[2]: Entering directory `/home/tamir/luminocity/src/luminocity/luminocity/src'
make  all-am
make[3]: Entering directory `/home/tamir/luminocity/src/luminocity/luminocity/src'
gcc  -g -O2 -Wall   -o luminocity  async.o bits.o decoration.o display.o events.o gui.o lmc-marshal.o main.o output.o root.o texture.o toplevel.o utils.o window.o spring-model.o -pthread -L/home/tamir/luminocity/opt/luminocity/lib64 -L/usr/local/kx/lib -lgthread-2.0 -lgdk_pixbuf-2.0 -lm -lpangoft2-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lXdamage -lXcomposite -lXfixes -lXtst -lXext -lXcursor -lXrender -lX11 -ldl   -L /usr/X11R6/lib -lGL -lGLU
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2fc1): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeQueryVersion'
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2ffd): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make[3]: *** [luminocity] Error 1
make[3]: Leaving directory `/home/tamir/luminocity/src/luminocity/luminocity/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tamir/luminocity/src/luminocity/luminocity/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tamir/luminocity/src/luminocity/luminocity'
make: *** [all] Error 2
*** error during stage build of luminocity: could not build module *** [24/24]


  [1] rerun stage build
  [2] ignore error and continue to install
  [3] give up on module
  [4] start shell
  [5] go to stage force_checkout
  [6] go to stage configure
choice:[/HTML]

I tried what somebody here said before be, it doesn't work.[/QUOTE]
 I got this second error too... Is there a fix about by any chance?

---

### Post by Dali on 2005-07-31
Confirmed - apt-getting that dev package for the nvidia drivers and redoing the whole thing worked for me as well.  I didn't need to do Willie's fix though...had success right off, unlike the dozens of previous attempts.

Ok, so how do I stop playing with this bit of eye candy???  I think I've just spent the past 20 minutes moving windows around.

Not exactly productive, is it?  

Amazing, though...  Thanks to everyone who has helped people like myself with technical problems.
 
I love it!

Dali

---

### Post by poofyhairguy on 2005-07-31
[QUOTE=Dali]
Ok, so how do I stop playing with this bit of eye candy??? [/QUOTE]

Remember, its just a fun toy at this point.

---

### Post by Corrosionx on 2005-08-09
Well I've been trying for days to install Luminocity and all kinds of dependencies, but still get this error... anybody can tell me more?

Thanks


> *** Configuring xserver *** [17/24]

./autogen.sh --prefix /home/daverag/luminocity/opt/luminocity  --enable-maintainer-mode --disable-static
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal
/usr/share/aclocal/vorbis.m4:9: warning: underquoted definition of XIPH_PATH_VORBIS
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
/usr/share/aclocal/pkg.m4:5: warning: underquoted definition of PKG_CHECK_MODULES
/usr/share/aclocal/libraw1394.m4:6: warning: underquoted definition of AC_LIB_RAW1394_FLAGS
/usr/share/aclocal/libraw1394.m4:19: warning: underquoted definition of AC_LIB_RAW1394_HEADERS
/usr/share/aclocal/libraw1394.m4:41: warning: underquoted definition of AC_LIB_RAW1394_LIBVERSION
/usr/share/aclocal/libraw1394.m4:75: warning: underquoted definition of AC_LIB_RAW1394_RUNTEST
/usr/share/aclocal/libraw1394.m4:138: warning: underquoted definition of AC_LIB_RAW1394
/usr/share/aclocal/gtk.m4:7: warning: underquoted definition of AM_PATH_GTK
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
/usr/share/aclocal/avifile.m4:21: warning: underquoted definition of AM_PATH_AVIFILE
/usr/share/aclocal/aalib.m4:12: warning: underquoted definition of AM_PATH_AALIBautoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
/usr/share/aclocal/vorbis.m4:9: warning: underquoted definition of XIPH_PATH_VORBIS
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
/usr/share/aclocal/pkg.m4:5: warning: underquoted definition of PKG_CHECK_MODULES
/usr/share/aclocal/libraw1394.m4:6: warning: underquoted definition of AC_LIB_RAW1394_FLAGS
/usr/share/aclocal/libraw1394.m4:19: warning: underquoted definition of AC_LIB_RAW1394_HEADERS
/usr/share/aclocal/libraw1394.m4:41: warning: underquoted definition of AC_LIB_RAW1394_LIBVERSION
/usr/share/aclocal/libraw1394.m4:75: warning: underquoted definition of AC_LIB_RAW1394_RUNTEST
/usr/share/aclocal/libraw1394.m4:138: warning: underquoted definition of AC_LIB_RAW1394
/usr/share/aclocal/gtk.m4:7: warning: underquoted definition of AM_PATH_GTK
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
/usr/share/aclocal/avifile.m4:21: warning: underquoted definition of AM_PATH_AVIFILE
/usr/share/aclocal/aalib.m4:12: warning: underquoted definition of AM_PATH_AALIBautoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /home/daverag/bin/install-check
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /home/daverag/bin/install-check
checking whether ln -s works... yes
checking for bison... bison -y
checking for flex... flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking whether make sets $(MAKE)... (cached) yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking for vprintf... yes
checking for _doprnt... no
checking for geteuid... yes
checking for getuid... yes
checking for link... yes
checking for memmove... yes
checking for memset... yes
checking for mkstemp... yes
checking for strchr... yes
checking for strrchr... yes
checking for strtol... yes
checking for getopt... yes
checking for getopt_long... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for sqrt in -lm... yes
checking ndbm.h usability... no
checking ndbm.h presence... no
checking for ndbm.h... no
checking dbm.h usability... no
checking dbm.h presence... no
checking for dbm.h... no
checking rpcsvc/dbm.h usability... no
checking rpcsvc/dbm.h presence... no
checking for rpcsvc/dbm.h... no
checking sys/vm86.h usability... yes
checking sys/vm86.h presence... yes
checking for sys/vm86.h... yes
checking sys/io.h usability... yes
checking sys/io.h presence... yes
checking for sys/io.h... yes
checking linux/agpgart.h usability... yes
checking linux/agpgart.h presence... yes
checking for linux/agpgart.h... yes
checking sys/agpio.h usability... no
checking sys/agpio.h presence... no
checking for sys/agpio.h... no
checking linux/apm_bios.h usability... yes
checking linux/apm_bios.h presence... yes
checking for linux/apm_bios.h... yes
checking linux/fb.h usability... yes
checking linux/fb.h presence... yes
checking for linux/fb.h... yes
checking asm/mtrr.h usability... yes
checking asm/mtrr.h presence... yes
checking for asm/mtrr.h... yes
checking linux/h3600_ts.h usability... no
checking linux/h3600_ts.h presence... no
checking for linux/h3600_ts.h... no
checking tslib.h usability... no
checking tslib.h presence... no
checking for tslib.h... no
checking for pkg-config... /usr/bin/pkg-config
checking for xdmcp... yes
checking XDMCP_CFLAGS... -I/home/daverag/luminocity/opt/luminocity/include
checking XDMCP_LIBS... -L/home/daverag/luminocity/opt/luminocity/lib -lXdmcp
checking for XdmcpWrap in -lXdmcp... yes
checking for x11 xext... yes
checking XEPHYR_CFLAGS... -D_XOPEN_SOURCE=500 -I/home/daverag/luminocity/opt/luminocity/include
checking XEPHYR_LIBS... -L/home/daverag/luminocity/opt/luminocity/lib -lXext -lX11 -ldl
checking for randrproto renderproto fixesproto damageproto xextproto xfont xproto xtrans xau compositeproto resourceproto recordproto xdmcp xdmcp... Package randrproto was not found in the pkg-config search path.
Perhaps you should add the directory containing `randrproto.pc'
to the PKG_CONFIG_PATH environment variable
No package 'randrproto' found

configure: error: Library requirements (randrproto renderproto fixesproto damageproto xextproto xfont xproto xtrans xau compositeproto resourceproto recordproto xdmcp xdmcp) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
*** error during stage configure of xserver: could not configure module *** [17/24]


  [1] rerun stage configure
  [2] ignore error and continue to build
  [3] give up on module
  [4] start shell
  [5] go to stage force_checkout
choice:



---

### Post by tread on 2005-08-09
On the wiki page this:
```

cvs -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome get  
luminocity/luminocity.modules

```

needs to be on one line:
```

cvss -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome get luminocity/luminocity.modules

```

Thanks for the howto, I'm making my way through it!

---

### Post by Stallone on 2005-08-10
[QUOTE=Corrosionx]Well I've been trying for days to install Luminocity and all kinds of dependencies, but still get this error... anybody can tell me more?

Thanks[/QUOTE]

Me too! I need help with this problem - it always crashes on module 17/24.

---

### Post by Stallone on 2005-08-10
Errrr, any help with this error would be appreciated - thanks.

```
 *** Configuring xserver *** [17/24]

./autogen.sh --prefix /home/daverag/luminocity/opt/luminocity --enable-maintainer-mode --disable-static
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal
/usr/share/aclocal/vorbis.m4:9: warning: underquoted definition of XIPH_PATH_VORBIS
run info '(automake)Extending aclocal'
or see http://sources.redhat.com/automake/...tending-aclocal
/usr/share/aclocal/pkg.m4:5: warning: underquoted definition of PKG_CHECK_MODULES
/usr/share/aclocal/libraw1394.m4:6: warning: underquoted definition of AC_LIB_RAW1394_FLAGS
/usr/share/aclocal/libraw1394.m4:19: warning: underquoted definition of AC_LIB_RAW1394_HEADERS
/usr/share/aclocal/libraw1394.m4:41: warning: underquoted definition of AC_LIB_RAW1394_LIBVERSION
/usr/share/aclocal/libraw1394.m4:75: warning: underquoted definition of AC_LIB_RAW1394_RUNTEST
/usr/share/aclocal/libraw1394.m4:138: warning: underquoted definition of AC_LIB_RAW1394
/usr/share/aclocal/gtk.m4:7: warning: underquoted definition of AM_PATH_GTK
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
/usr/share/aclocal/avifile.m4:21: warning: underquoted definition of AM_PATH_AVIFILE
/usr/share/aclocal/aalib.m4:12: warning: underquoted definition of AM_PATH_AALIBautoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
/usr/share/aclocal/vorbis.m4:9: warning: underquoted definition of XIPH_PATH_VORBIS
run info '(automake)Extending aclocal'
or see http://sources.redhat.com/automake/...tending-aclocal
/usr/share/aclocal/pkg.m4:5: warning: underquoted definition of PKG_CHECK_MODULES
/usr/share/aclocal/libraw1394.m4:6: warning: underquoted definition of AC_LIB_RAW1394_FLAGS
/usr/share/aclocal/libraw1394.m4:19: warning: underquoted definition of AC_LIB_RAW1394_HEADERS
/usr/share/aclocal/libraw1394.m4:41: warning: underquoted definition of AC_LIB_RAW1394_LIBVERSION
/usr/share/aclocal/libraw1394.m4:75: warning: underquoted definition of AC_LIB_RAW1394_RUNTEST
/usr/share/aclocal/libraw1394.m4:138: warning: underquoted definition of AC_LIB_RAW1394
/usr/share/aclocal/gtk.m4:7: warning: underquoted definition of AM_PATH_GTK
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
/usr/share/aclocal/avifile.m4:21: warning: underquoted definition of AM_PATH_AVIFILE
/usr/share/aclocal/aalib.m4:12: warning: underquoted definition of AM_PATH_AALIBautoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /home/daverag/bin/install-check
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /home/daverag/bin/install-check
checking whether ln -s works... yes
checking for bison... bison -y
checking for flex... flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking whether make sets $(MAKE)... (cached) yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking for vprintf... yes
checking for _doprnt... no
checking for geteuid... yes
checking for getuid... yes
checking for link... yes
checking for memmove... yes
checking for memset... yes
checking for mkstemp... yes
checking for strchr... yes
checking for strrchr... yes
checking for strtol... yes
checking for getopt... yes
checking for getopt_long... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for sqrt in -lm... yes
checking ndbm.h usability... no
checking ndbm.h presence... no
checking for ndbm.h... no
checking dbm.h usability... no
checking dbm.h presence... no
checking for dbm.h... no
checking rpcsvc/dbm.h usability... no
checking rpcsvc/dbm.h presence... no
checking for rpcsvc/dbm.h... no
checking sys/vm86.h usability... yes
checking sys/vm86.h presence... yes
checking for sys/vm86.h... yes
checking sys/io.h usability... yes
checking sys/io.h presence... yes
checking for sys/io.h... yes
checking linux/agpgart.h usability... yes
checking linux/agpgart.h presence... yes
checking for linux/agpgart.h... yes
checking sys/agpio.h usability... no
checking sys/agpio.h presence... no
checking for sys/agpio.h... no
checking linux/apm_bios.h usability... yes
checking linux/apm_bios.h presence... yes
checking for linux/apm_bios.h... yes
checking linux/fb.h usability... yes
checking linux/fb.h presence... yes
checking for linux/fb.h... yes
checking asm/mtrr.h usability... yes
checking asm/mtrr.h presence... yes
checking for asm/mtrr.h... yes
checking linux/h3600_ts.h usability... no
checking linux/h3600_ts.h presence... no
checking for linux/h3600_ts.h... no
checking tslib.h usability... no
checking tslib.h presence... no
checking for tslib.h... no
checking for pkg-config... /usr/bin/pkg-config
checking for xdmcp... yes
checking XDMCP_CFLAGS... -I/home/daverag/luminocity/opt/luminocity/include
checking XDMCP_LIBS... -L/home/daverag/luminocity/opt/luminocity/lib -lXdmcp
checking for XdmcpWrap in -lXdmcp... yes
checking for x11 xext... yes
checking XEPHYR_CFLAGS... -D_XOPEN_SOURCE=500 -I/home/daverag/luminocity/opt/luminocity/include
checking XEPHYR_LIBS... -L/home/daverag/luminocity/opt/luminocity/lib -lXext -lX11 -ldl
checking for randrproto renderproto fixesproto damageproto xextproto xfont xproto xtrans xau compositeproto resourceproto recordproto xdmcp xdmcp... Package randrproto was not found in the pkg-config search path.
Perhaps you should add the directory containing `randrproto.pc'
to the PKG_CONFIG_PATH environment variable
No package 'randrproto' found

configure: error: Library requirements (randrproto renderproto fixesproto damageproto xextproto xfont xproto xtrans xau compositeproto resourceproto recordproto xdmcp xdmcp) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
*** error during stage configure of xserver: could not configure module *** [17/24]


[1] rerun stage configure
[2] ignore error and continue to build
[3] give up on module
[4] start shell
[5] go to stage force_checkout
choice: 
```

---

### Post by Stallone on 2005-08-10
I take it no one wants to help?  :-?

---

### Post by Sam on 2005-08-10
Try this
```
$ sudo apt-get install fort77 g77
```

---

### Post by mircea on 2005-09-08
[QUOTE=Sam]Try this
```
$ sudo apt-get install fort77 g77
```[/QUOTE]
try that but [-X  no efect
any other ideeas?

---

### Post by ouphe on 2005-09-12
very, very ugly:

go here:
[http://xorg.freedesktop.org/X11R7.0-RC0/proto/](http://xorg.freedesktop.org/X11R7.0-RC0/proto/) 

get all .tar.gz's for: randrproto renderproto fixesproto damageproto xextproto compositeproto resourceproto recordproto 

unpack them (I opened the files from within Firefox, created a folder on my desktop and extracted them in that folder, the archive will create a new folder)

when done, open every folder and doubleclick "autogen.sh", select "run in terminal" for each one

when done, open a terminal and do:
sudo su -

move into every folder and do:
cp *.pc /usr/lib/pkgconfig 

this will copy the necessary files to the correct folder

now, either resume the compile process or restart it

and results in: 
*** success *** [24/24]  :razz:

and works afterwards. runs fine on a r9500pro (latest fglrx). it's sweeeeeet!

---

### Post by mircea on 2005-09-12
reporting ...
SUCCESS !
I also needed to edit the file:
~/luminocity/src/luminocity/luminocity/src/Makefile
as sugested in this thread, post #33 [http://ubuntuforums.org/showpost.php?p=237657&postcount=33](http://ubuntuforums.org/showpost.php?p=237657&postcount=33)

maybe someone will update the wiki page with the info cumulated here... :)

---

### Post by akb on 2005-10-23
hi there,

i've got a problem with stage 27 too, but its an other one:

```

checking for XSERVER... configure: error: Package requirements (randrproto renderproto fixesproto damageproto xextproto xfont xproto xtrans xau compositeproto resourceproto recordproto xdmcp xdmcp) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the XSERVER_CFLAGS and XSERVER_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
*** error during stage configure of xserver: could not configure module *** [17/24] 

```

any ideas? :-/

---

### Post by stran on 2005-11-09
Yes, I have the same problem. There's no specific failure, just "package (....) not met." I verify that all these files exist in pkgconfig.... not to mention the fact these same files are dependencies for earlier modules.


any ideas??

---

### Post by akb on 2005-11-09
somewhere within this thread i found the following:

> 
go here:
[http://xorg.freedesktop.org/X11R7.0-RC0/proto/](http://xorg.freedesktop.org/X11R7.0-RC0/proto/)

get all .tar.gz's for: randrproto renderproto fixesproto damageproto xextproto compositeproto resourceproto recordproto

unpack them (I opened the files from within Firefox, created a folder on my desktop and extracted them in that folder, the archive will create a new folder)

when done, open every folder and doubleclick "autogen.sh", select "run in terminal" for each one

when done, open a terminal and do:
sudo su -

move into every folder and do:
cp *.pc /usr/lib/pkgconfig

this will copy the necessary files to the correct folder

now, either resume the compile process or restart it

and results in:
*** success *** [24/24] 

this helped in my case too.

---

### Post by senning on 2005-11-20
I've created a shell script for downloading and installing all the xorg.freedesktop.org files;  You'll have to remove the .txt extension.  I haven't actually tested the cp section, as I didn't really want it to overwrite things already there, but it should work.  Let me know if it doesn't (possible problems: 
1. I used sudo on every line instead of su.  It should only prompt once, but I don't actually know
2. the cp commands are wrong.  Though they shouldn't be.  The script does exactly what I did in terminal)

The second last line deletes the temporary folder I created to store the tars and their folders.  remove it if you don't want it to do that (I just like tidying up :KS )

P.S. I've got a P4 2.6 and a Radeon 9200SE and luminocity runs like a like a dying lemur (in theory.  I've never seen a dying lemur...) twitchy and slow.  Nonetheless, I had a very very good time doing it.  Do I need to do anything special to get it to run with GLitz, and should it matter?

---

### Post by vtechstu on 2005-12-08
I followed the steps, I'm pretty sure, and I get this error.  Could you please suggest a fix?  Thanks

```
chase@ubuntu:~/luminocity$ ~/bin/jhbuild -f ~/luminocity/jhbuildrc-luminocity build xserver luminocity
Logging in to :pserver:anonymous@anoncvs.gnome.org:2401/cvs/gnome
CVS password:
cvs login: warning: failed to open /home/chase/.cvspass for reading: No such file or directory
*** Checking out XExtensions *** [1/24]

cvs -z3 -q -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xlibs checkout -P -A XExtensions
U XExtensions/.cvsignore
U XExtensions/AUTHORS
U XExtensions/COPYING
U XExtensions/ChangeLog
U XExtensions/INSTALL
U XExtensions/MITMisc.h
U XExtensions/Makefile.am
U XExtensions/NEWS
U XExtensions/README
U XExtensions/XEVI.h
U XExtensions/XEVIstr.h
U XExtensions/XI.h
U XExtensions/XInput.h
U XExtensions/XIproto.h
U XExtensions/XKB.h
U XExtensions/XKBgeom.h
U XExtensions/XKBproto.h
U XExtensions/XKBsrv.h
U XExtensions/XKBstr.h
U XExtensions/XLbx.h
U XExtensions/XShm.h
U XExtensions/XTest.h
U XExtensions/Xag.h
U XExtensions/Xagsrv.h
U XExtensions/Xagstr.h
U XExtensions/Xcup.h
U XExtensions/Xcupstr.h
U XExtensions/Xdbe.h
U XExtensions/Xdbeproto.h
U XExtensions/Xext.h
U XExtensions/Xv.h
U XExtensions/XvMC.h
U XExtensions/XvMCproto.h
U XExtensions/Xvproto.h
U XExtensions/autogen.sh
U XExtensions/bigreqstr.h
U XExtensions/configure.ac
U XExtensions/dpms.h
U XExtensions/dpmsstr.h
U XExtensions/extutil.h
U XExtensions/lbxbuf.h
U XExtensions/lbxbufstr.h
U XExtensions/lbxdeltastr.h
U XExtensions/lbximage.h
U XExtensions/lbxopts.h
U XExtensions/lbxstr.h
U XExtensions/lbxzlib.h
U XExtensions/mitmiscstr.h
U XExtensions/multibuf.h
U XExtensions/multibufst.h
U XExtensions/saver.h
U XExtensions/saverproto.h
U XExtensions/security.h
U XExtensions/securstr.h
U XExtensions/shape.h
U XExtensions/shapestr.h
U XExtensions/shmstr.h
U XExtensions/sync.h
U XExtensions/syncstr.h
U XExtensions/xcmiscstr.h
U XExtensions/xextensions.pc.in
U XExtensions/xtestext1.h
U XExtensions/xteststr.h
*** Configuring XExtensions *** [1/24]

./autogen.sh --prefix /home/chase/luminocity/opt/luminocity  --enable-maintainer-mode --disable-static
./autogen.sh: line 9: autoreconf: command not found
*** error during stage configure of XExtensions: could not configure module *** [1/24]


  [1] rerun stage configure
  [2] ignore error and continue to build
  [3] give up on module
  [4] start shell
  [5] go to stage force_checkout
choice: Interrupted
chase@ubuntu:~/luminocity$

```

---

### Post by vtechstu on 2005-12-09
Ok, so I installed autoconf2.13 or something like that, and it switched to a different error when i ran the last command:

```

chase@ubuntu:~$ ~/bin/jhbuild -f ~/luminocity/jhbuildrc-luminocity build xserver luminocity
*** Checking out XExtensions *** [1/24]

cvs -z3 -q -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xlibs update -dP -A .
*** Configuring XExtensions *** [1/24]

./autogen.sh --prefix /home/chase/luminocity/opt/luminocity  --enable-maintainer-mode --disable-static
Can't exec "aclocal": No such file or directory at /usr/bin/autoreconf2.50 line 176.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf2.50 line 176.
Can't exec "automake": No such file or directory at /usr/bin/autoreconf2.50 line 177.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf2.50 line 177.
autoreconf2.50: Entering directory `.'
autoreconf2.50: configure.ac: not using Gettext
autoreconf2.50: running: aclocal  --output=aclocal.m4t
Can't exec "aclocal": No such file or directory at /usr/share/autoconf/Autom4te/FileUtils.pm line 288.
autoreconf2.50: failed to run aclocal: No such file or directory
*** error during stage configure of XExtensions: could not configure module *** [1/24]


  [1] rerun stage configure
  [2] ignore error and continue to build
  [3] give up on module
  [4] start shell
  [5] go to stage force_checkout
choice:

```

---

### Post by joce on 2005-12-16
hello,
i have a problem about  Luminocity.
it is an error.
who can teach me how to fix it?

```

.
.
.
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEP... configure: error: luminocity dependencies not satisfied

Now type 'make' to compile luminocity.
*** Building luminocity *** [24/24]

make
make: *** No targets specified and no makefile found.  Stop.
*** error during stage build of luminocity: could not build module *** [24/24]


  [1] rerun stage build
  [2] ignore error and continue to install
  [3] give up on module
  [4] start shell
  [5] go to stage force_checkout
  [6] go to stage configure
choice:

```

thank you.

---

### Post by LifeIsAFractal on 2006-01-04
[QUOTE=ouphe]very, very ugly:

go here:
[http://xorg.freedesktop.org/X11R7.0-RC0/proto/](http://xorg.freedesktop.org/X11R7.0-RC0/proto/) 

get all .tar.gz's for: randrproto renderproto fixesproto damageproto xextproto compositeproto resourceproto recordproto 

unpack them (I opened the files from within Firefox, created a folder on my desktop and extracted them in that folder, the archive will create a new folder)

when done, open every folder and doubleclick "autogen.sh", select "run in terminal" for each one

when done, open a terminal and do:
sudo su -

move into every folder and do:
cp *.pc /usr/lib/pkgconfig 

this will copy the necessary files to the correct folder

now, either resume the compile process or restart it

and results in: 
*** success *** [24/24]  :razz:

and works afterwards. runs fine on a r9500pro (latest fglrx). it's sweeeeeet![/QUOTE]

I've never been a fan of the ugly solution, thats why I use ubuntu.  All of the missing files are availbe in the ubuntu repositories.

the needed files are:
randrproto renderproto fixesproto damageproto xextproto compositeproto resourceproto recordproto

the packages are named: x11-(name of proto)-dev

install the missing packages and continue your build to success.

cheers to my first post too :p .

---

### Post by Iandefor on 2006-02-04
Interesting. It looks okay. Runs fine on an AMD Sempron 64 2600+ that's been overclocked to about 1.8 ghz and a GeForce 6100. I really like some of the effects, but it's overdone in Luminocity.

---

### Post by kanapee on 2006-10-29
Why not just use Beryl??? Isn't Beryl or Compiz pretty much the same thing?:???:

---

### Post by KingArthur10 on 2006-10-29
The origional howto was out before Beryl.  Beryl/Compiz is pretty darned new.

---

