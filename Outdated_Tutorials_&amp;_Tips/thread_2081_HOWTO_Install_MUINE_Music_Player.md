---
title: "HOWTO: Install MUINE Music Player"
date: 2004-10-25
forum: Outdated Tutorials &amp; Tips
---

### Post by oddabe19 on 2004-10-25
Muine is an incredible music player (though lacks some features) that uses Mono, and is very versitle, quick and has great sound. I prefer Xmms and Beep, however, I'm starting to use Muine more and more and finding it much cleaner and simpler.

The first thing you want to do is uncomment universe in /etc/apt/sources.list and add the following lines ```
#Mono
deb http://www.getsweaaa.com/~tseng/ubuntu/debs/ ./
deb-src http://www.getsweaaa.com/~tseng/ubuntu/debs/ ./
``` (sudo gedit /etc/apt/sources.list) and save and exit.

then do a ```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install muine
``` The apt-get upgrade shouldn't be necessary, however, I ran into broken pakage situations if I didn't do that. When it is all done, you should have Muine in Applications => Multimedia => Muine. It's as simple as that!!!

Also: I am not sure, but i believe it also requires gstreamer0.8-mad plugin, just like rhythmbox, but i'm not positive.  You might also want to re-comment universe, but you don't have to comment out mono, if you don't want to.

Happy Listening.

---

### Post by sebast on 2004-12-25
As today (December 25th 2004), Muine 0.7 is out.  :D 

It's not yet in getsweaaa.com so I decided to install it from source.

I had to install a couple of packages without any problems. However, I tried to install GTK-Sharp from sources and I got this error:

```

checking for gacutil... no
configure: error: No gacutil tool found
```

Can somebody tell me what to do to fix that problem?

---

### Post by oddabe19 on 2004-12-25
[QUOTE=sebast]As today (December 25th 2004), Muine 0.7 is out.  :D 

It's not yet in getsweaaa.com so I decided to install it from source.

I had to install a couple of packages without any problems. However, I tried to install GTK-Sharp from sources and I got this error:

```

checking for gacutil... no
configure: error: No gacutil tool found
```

Can somebody tell me what to do to fix that problem?[/QUOTE]
 try a ```
sudo apt-get build-dep muine
``` with those repos in your sources.list, then try to build it from source, what that command does, is downloads and installs all the files you need to build X program (in this case, muine)

If i were home, I'd build one for you, but i'm with relatives for christmas, sorry.

---

### Post by sebast on 2004-12-25
I tried it, but I get this error:

```
sebb@ubuntu:~ $ sudo apt-get build-dep muine
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
**E: Build-Depends dependency for muine cannot be satisfied because no available versions of package libgtk-cil can satisfy version requirements**
```

---

### Post by Kitsch on 2004-12-31
[QUOTE=sebast]As today (December 25th 2004), Muine 0.7 is out.  :D 

It's not yet in getsweaaa.com so I decided to install it from source.

I had to install a couple of packages without any problems. However, I tried to install GTK-Sharp from sources and I got this error:

```

checking for gacutil... no
configure: error: No gacutil tool found
```

Can somebody tell me what to do to fix that problem?[/QUOTE]

Maybe you need to do this first:

```
sudo apt-get install mono-gac
```

---

### Post by kmf on 2005-01-01
There is a newer version availible at [http://muine.gooeylinux.org/muine-0.7.1.tar.gz](http://muine.gooeylinux.org/muine-0.7.1.tar.gz)
:) Grab it while it's hot :)

I'm also having weird issues compiling it maybe this will sort it out

Karl

---

### Post by brk3 on 2005-01-05
This player seems sweet. Album cover handling is something i miss in rhytmbox. im having trouble getting it installed though. lets see it included in hoary!

---

### Post by frankps on 2005-01-09
I get no sound from Muine when using the one available from Synaptic (v0.6.3-4).

I can also not compile the latest version of it.


Frank

---

### Post by rwabel on 2005-01-09
[QUOTE=kmf]There is a newer version availible at [http://muine.gooeylinux.org/muine-0.7.1.tar.gz](http://muine.gooeylinux.org/muine-0.7.1.tar.gz)
:) Grab it while it's hot :)

I'm also having weird issues compiling it maybe this will sort it out

Karl[/QUOTE]

even 0.8 version out with plugin feature. But the problem is that it depends on gtk-sharp2. It's not yet released.
Did you achieve to compile it from source? I'm on hoary and would love to either get somehow the needed gtk-sharp or get a compiled deb

---

### Post by ow50 on 2005-01-11
I also tried to compile the new 0.8.0 version, but i get the error "No package 'dbus-sharp' found". How can i acquire dbus-sharp?

---

### Post by rwabel on 2005-01-11
[QUOTE=ow50]I also tried to compile the new 0.8.0 version, but i get the error "No package 'dbus-sharp' found". How can i acquire dbus-sharp?[/QUOTE]

I just remember that I once tried to compile beagle which needs dbus. I'm on hoary and there was a instruction for building the needed dbus from cvs sources. Try this one, but you will get in trouble later with gtk-sharp2. Better wait for a deb package

---

### Post by Humboldt on 2005-01-12
Thanks for the tips Oddabe10

I have installed muine after reading your HOWTO. It works very well - more functional than any other gnome player in my opinion. Works better and are more easy to handle than Rhythmbox or xmms for example. Filelistcreation for example is so smoooth. Cant understand why it is not standard in the gnome desktop - and in Ubuntu. Something for upcoming versions of Ubuntu maybe.

Thanks again for the HOWTO

---

### Post by Humboldt on 2005-01-12
[QUOTE=Humboldt]Thanks for the tips Oddabe10

Should be Oddable19 of c...

---

### Post by Humboldt on 2005-01-12
[QUOTE=Humboldt][QUOTE=Humboldt]Thanks for the tips Oddabe10

Should be Oddabe19 and nothing else

---

### Post by rwabel on 2005-01-12
if you are on hoary you have it already in the repository :-)
But both are still 0.6.3 version, I would love to see 0.8

---

### Post by jokull on 2005-02-07
I am a total newbie. I've tried installing Muine a couple of times now using the respository given in the HOWTO. Every time it seems to go fine but whenever I start the program from Applications -> Sound & Video -> Muine it hangs on "Starting Muine" in the taskbar. After a couple of seconds it dissapears from the taskbar without a trace and never displays an error or anything of the sort.

I'm using the hoary repositories to build my dependencies. Any help would be appreciated.

---

### Post by rwabel on 2005-02-07
[QUOTE=jokull]I am a total newbie. I've tried installing Muine a couple of times now using the respository given in the HOWTO. Every time it seems to go fine but whenever I start the program from Applications -> Sound & Video -> Muine it hangs on "Starting Muine" in the taskbar. After a couple of seconds it dissapears from the taskbar without a trace and never displays an error or anything of the sort.

I'm using the hoary repositories to build my dependencies. Any help would be appreciated.[/QUOTE]

well I don't use the version from the howto, I'm taking them directly from CVS.

apt-get install muine did work without any problems?

what does it say when you start muine from a a shell? So you can see what the error message is.
Maybe it will help to see where the problem is.

---

### Post by stuNNed on 2005-02-07
the repos for this have moved.

it's actually now:

deb [http://www.getsweaaa.com/~tseng/muine/](http://www.getsweaaa.com/~tseng/muine/) ./

stuNNed

---

### Post by stuNNed on 2005-02-07
this is only for hoary, NOT warty.

---

### Post by Shadow Skill on 2005-02-19
Has anyone ever successfully compiled Muine from source?  I can't get it to compile on fc3 or even Ubuntu which still has the old version two versions old in fact.  I can't get this thing to find mono.pc whenever I point it to /usr/bin/pkg-config so it can find gtk-sharp [do note that version 1.9 is indeed the correct version to use.] it wont even work even if I export the relevant paths at the same time with a colon.

---

### Post by ember on 2005-02-19
I managed to compile gtk#-1.9.2 from source today, yet I did not get gnome# and gnome-vfus# compiled in. Maybe I'll look at that tomorrow. I hope all that will become a little easier, when hoary is out (I'm still on warty), because Muine is more or less just what I was looking for
(except for the stop button that I miss in all gstreamer-applications)

---

