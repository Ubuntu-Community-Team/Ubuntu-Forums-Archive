---
title: "[SOLVED] Installing XAutoClick...."
date: 2008-10-02
forum: New to Ubuntu
---

### Post by timstone on 2008-10-02
ok...got this far...installed build-essential and then did

```

tar xvzf xautoclick-0.19-src.tar.gz
cd /home/tim/Desktop/xautoclick-0.19-src.tar.gz
./configure

```

got an error here for some reason saying "make: Nothing to be done for `all'."
```

make 

```

```

sudo make install

```

everything seemed to have installed at /usr/local/man/man1

checked the directory and there was only 1 file... xautoclick.1

wtf do i do now?

---

### Post by Michael.Godawski on 2008-10-02
Here the manual :)
_[http://xautoclick.sourceforge.net/documentation.html]("http://xautoclick.sourceforge.net/news.html")_

>  Depending on which libraries are available on your system, any of **aautoclick**, **cautoclick**, **gautoclick**, **gautoclick2** or **qtautoclick** should work now.Try to run in terminal one of the stressed commands

```
gautoclick
gautoclick2
qautoclick
```

---

### Post by timstone on 2008-10-02
none of those commands worked...

```

~$ gautoclick
bash: gautoclick: command not found
~$ gautoclick2
bash: gautoclick2: command not found
~$ qautoclick
bash: qautoclick: command not found

```

oh and that URL must be something else you were working on....its a post on another forum about a USB stick drive

yes, im a noob :)

---

### Post by 3rdalbum on 2008-10-02
> **timstone said:**
> ok...got this far...installed build-essential and then did

```

tar xvzf xautoclick-0.19-src.tar.gz
cd /home/tim/Desktop/xautoclick-0.19-src.tar.gz
./configure

```

The second command should be:

cd /home/tim/Desktop/xautoclick-0.10-src

Or whatever the directory is called. You can't change directory into a compressed archive.

There is "kautoclick" in the repositories - are you aware of this program?

---

### Post by Michael.Godawski on 2008-10-02
sorry 
link fixed.

weird that none of the commands work; and the installation was complete and flawless?

---

### Post by timstone on 2008-10-02
> **3rdalbum said:**
> The second command should be:

cd /home/tim/Desktop/xautoclick-0.10-src

Or whatever the directory is called. You can't change directory into a compressed archive.

There is "kautoclick" in the repositories - are you aware of this program?

yea i didnt direclty copy/paste that code i just typed it and messed up....and no i wasnt aware of kautoclick, but now i am, ill give it a shot and see what happens...



> **Michael.Godawski said:**
> sorry 
link fixed.

weird that none of the commands work; and the installation was complete and flawless?

yea im pretty sure, i didnt see any errors anywhere

---

### Post by timstone on 2008-10-02
maybe I'm just too stupid to be using linux....this is what i get with kautoclick

this is after its already extracted...
```

tim@tim-desktop:~$ cd /home/tim/Desktop/k
tim@tim-desktop:~/Desktop/k$ ./configure
configure: error: cannot find sources (acinclude.m4) in . or ..
tim@tim-desktop:~/Desktop/k$

```

---

### Post by dirkbee on 2008-10-17
> **timstone said:**
> 
got an error here for some reason saying "make: Nothing to be done for `all'."


That's because you don't have any of the X11, GTK+ or QT development packages installed. If you look at the output of ./configure you'll see that the endreport says 'no' to all the xautoclick variants.

Try something like:

sudo apt-get install xserver-xorg-dev gtk2-dev

then run ./configure again, make and sudo make install

HTH

---

### Post by JTLJudoMan on 2009-05-29
I found this directory since I was trying to install the same thing.

I followed all the steps but when I get to installing the GTK developer part I get this.

~/xautoclick-0.20-src$ sudo apt-get install xserver-xorg-dev gtk2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-dev is already the newest version.
E: Couldn't find package gtk2-dev


Unfortunately I have installed xserver-xorg-dev fine and still have the same problems as the original poster.  Unfortunately kautoclicker doesn't click fast enough for me and therefore is not an option as I haven't been able to find a place to change the artificial limit of 200 ms.

---

