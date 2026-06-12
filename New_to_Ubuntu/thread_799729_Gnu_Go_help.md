---
title: "Gnu Go help"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Sheneron on 2008-05-19
I am trying to play the game Gnu Go.  So in the terminal I open up the program by typing glGo, however when I click the button on the interface that comes up I get an error.  Here is what it says.

*** glibc detected *** glGo: munmap_chunk(): invalid pointer: 0x08fc09b0 ***

then a huge list comes up and it ends like this.

b6dfb000-b6dfd000 r--s 00000000 03:01 5113803    /var/cache/fontconfig/e13b20fdb0Aborted

It will also sometimes come up with a Segmentation error.

I really do not know what to do because this used to work fine.  Im not sure if anymore info is needed to help me, but if so let me know and I will get it to you.  Thanks.

---

### Post by Sheneron on 2008-05-19
I am not sure if this makes a difference but I do not have libpython2.4 installed, and I can't figure out how.

---

### Post by Sheneron on 2008-05-19
bump

---

### Post by Majorix on 2008-05-19
You are mixing up GnuGo with some other program I think. Because gnugo doesn't have any buttons (it is in text mode) and it is launched by typing "gnugo" into your terminal or by adding a shortcut to it to your Gnome menu.

---

### Post by Sheneron on 2008-05-19
yes but there is an interface you can put gnugo to.  GlGo.  So if you use glGo in conjunction with gnugo it won't be text based.  Something has messed up with my glGo though, maybe because I am missing something I need.  Online works fine but when I click preferences or gnugo it comes up with those errors.  I know this must be very confusing unless anyone has dealt with Go; please tell me if I need to explain more.  Also I am sure it doesn't help that I have no idea what I am doing with linux yet.

---

### Post by billgoldberg on 2008-05-19
> **Sheneron said:**
> I am not sure if this makes a difference but I do not have libpython2.4 installed, and I can't figure out how.

I don't know the programs you are describing, but if they need libpython2.4, then go to

"system -> administration -> synaptic package manager"

and download it (use the search button).

---

### Post by Sheneron on 2008-05-19
> **Sheneron said:**
> I am not sure if this makes a difference but I do not have libpython2.4 installed, and I can't figure out how.

> **billgoldberg said:**
> I don't know the programs you are describing, but if they need libpython2.4, then go to

"system -> administration -> synaptic package manager"

and download it (use the search button).

I do not see it there.  I have libpythonize installed but I don't know if that is the same thing.

I am going by this page. [http://www.pandanet.co.jp/English/glgo/Install.txt](http://www.pandanet.co.jp/English/glgo/Install.txt)
I do not think I have all of those "lib" things which may be why its not working.  I only assume this because I have installed it correctly and it seems to be the only reason it isn't working.

---

### Post by Majorix on 2008-05-19
I see what you mean.

Does it matter for you if you were to use some other gui tool for your gnugo?

If it doesn't, do this:
[php]sudo apt-get install gnugo qgo
#and once the install is done, without leaving the terminal, do this:
qgo[/php]
and you will hopefully have an interface this time.

---

### Post by Sheneron on 2008-05-19
haha I am not sure why I didn't even think of just using a different interface.  It works.  Thanks alot everyone.

---

