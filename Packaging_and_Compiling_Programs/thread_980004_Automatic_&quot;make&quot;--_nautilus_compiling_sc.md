---
title: "Automatic &quot;make&quot;-- nautilus compiling script."
date: 2008-11-12
forum: Packaging and Compiling Programs
---

### Post by MaxIBoy on 2008-11-12
Put this file in $HOME/.gnome2/nautilus_scripts and set it as executable. It's good form to use a .sh file extension. Notice that it avoids using root privileges whenever possible. I think it needs tweaking, I'm not sure if it's exactly right. However, I do guarantee that this will *not* break your system. Testers wanted! I'd like to get this absolutely bulletproof, handling as many different convoluted compiling processes as possible. 
```
#! /bin/bash
xterm -hold -e "if ( test -a configure )
then 
	gksudo chmod +x configure && ./configure
fi 


if !( test -a *Makefile* )
then
	echo 'There is probably nothing to compile.'
else
	make clean && make && ( make install || gkusudo make install ) || echo 'The compile did not work. See the above text for debugging.
It is possible that you did not have all dependencies.'
fi
read"
```

Note the ability to handle errors.

---

### Post by wildman4god on 2008-11-12
Thanks I will test this and let you know what goes wrong, I don't know how to script my self yet.

---

### Post by MaxIBoy on 2008-11-12
I think it's correct, but I can't be sure. I did some more testing, and it seems to be be behaving itself. Running it in my "desktop" folder shows "probably nothing to compile." It accurately told me about how I "may have missing dependencies" and helpfully showed me the output of "make" so I could see what packages I was missing. So far, it's handled all errors.

I haven't tested it very much on *valid* and problem-free scenarios yet. I haven't tested to see if the automatic "configure" running code works. It's conceivable that it might compile properly and still report an error in some situations.

---

