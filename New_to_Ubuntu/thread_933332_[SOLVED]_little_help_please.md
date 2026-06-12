---
title: "[SOLVED] little help please"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-09-29
im trying to set up my ubuntu computer so i can use my wiimote as a mouse and im following this guide,but im having some bother with it.

this is what it asks you to enter into the terminal

> mkdir Wii
cd Wii/
wget "http://downloads.sourceforge.net/libwiimote/libwiimote-0.4.tgz?modtime=1173542681&big_mirror=0"
tar -zxvf libwiimote-0.4.tgz 
cd libwiimote-0.4/
autoconf
./configure
make
sudo make install

wen i get to the second last command

> make

i get this error

> daniel@DV6000:~/Wii/libwiimote-0.4$ make
make: *** No targets specified and no makefile found.  Stop.


could someone please help me with this-thanks in advanced-Daniel.

---

### Post by Het Irv on 2008-09-29
look back thought what happened when you typed in the commands and see if you got any errors.

---

### Post by betterthanjordan79 on 2008-09-29
Ah-i got this error-i missed this first time...any idea what could fix this

> daniel@DV6000:~/Wii/libwiimote-0.4$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for hci_remote_name in -lbluetooth... no
configure: error: We require BlueZ


---

### Post by Het Irv on 2008-09-29
[http://www.bluez.org/](http://www.bluez.org/)

I looks like you may need to install this first before running the configure command.

---

### Post by silverglade00 on 2008-09-29
BlueZ is the bluetooth software. Assuming you have bluetooth on that computer, just open up Synaptic and install bluez-gnome. That should get you going past that error.

---

### Post by betterthanjordan79 on 2008-09-29
i already have it installed...any other ideas?

---

### Post by betterthanjordan79 on 2008-09-29
sorry for double posting but i got it sorted-my silly mistakes!!thaks for ur times!!

---

### Post by bioshake on 2009-01-21
I have the same error and have everything I can see that has anything to do with bluez installed...

What gives?

---

### Post by jrasith on 2009-03-05
I believe that this may shed some light on those who are also experiencing this problem... Apparently, in version 2.14 of libbluetooth, hci_remote_name() was depreciated (see the two links below).

[http://osdir.com/ml/gnome.apps.bluetooth/2005-01/msg00032.html](http://osdir.com/ml/gnome.apps.bluetooth/2005-01/msg00032.html)

[http://lists.usefulinc.com/pipermail/gnome-bluetooth/2005-January/000769.html](http://lists.usefulinc.com/pipermail/gnome-bluetooth/2005-January/000769.html)

In my installation (Ubuntu 8.10 Intrepid Ibex 64 bit), 4.14 is the version that is used. The articles hint that the symbols were reintroduced in 2.15 but I don't know what has happened since then.

Anyone else have any ideas, I also am having this problem; when running the configure script you get the following error:

```
checking for hci_remote_name in -lbluetooth... no
configure: error: We require BlueZ
```

UPDATE: I edited the configure file and replaced hci_remote_name with hci_read_remote_name in the script and it ran fine. I am now going to check on if it compiles and runs.

UPDATE 2: Alright, to compile, I needed to do the same replace in wiiremote_link.c as I did in the configure script and I also modified the make file in src directory from

```
libcwiimote.so: $(SOURCES) $(HEADERS)
	$(CC) $(CFLAGS) $(INCLUDES) $(SOURCES) -shared -o $@  $(LIBS)
	@cp $@ $(LIBDIR)
```

to the following (note I added -fPIC, as suggested by the compiler)

```
libcwiimote.so: $(SOURCES) $(HEADERS)
	$(CC) $(CFLAGS) -fPIC $(INCLUDES) $(SOURCES) -shared -o $@  $(LIBS)
	@cp $@ $(LIBDIR)
```

This gets things to compile but I don't know if the libraries will run or not *shrug*. Anyone have any thoughts?

UPDATE 3: Alright, well I ran the 3rd test program and things seem to be working but it's not throughly tested, hopefully the people over at libwiimote will update things...

Peace;
-Joshua

---

### Post by Rikiji on 2009-11-05
> **jrasith said:**
> I believe that this may shed some light on those who are also experiencing this problem... Apparently, in version 2.14 of libbluetooth, hci_remote_name() was depreciated (see the two links below).

[http://osdir.com/ml/gnome.apps.bluetooth/2005-01/msg00032.html](http://osdir.com/ml/gnome.apps.bluetooth/2005-01/msg00032.html)

[http://lists.usefulinc.com/pipermail/gnome-bluetooth/2005-January/000769.html](http://lists.usefulinc.com/pipermail/gnome-bluetooth/2005-January/000769.html)

In my installation (Ubuntu 8.10 Intrepid Ibex 64 bit), 4.14 is the version that is used. The articles hint that the symbols were reintroduced in 2.15 but I don't know what has happened since then.

Anyone else have any ideas, I also am having this problem; when running the configure script you get the following error:

```
checking for hci_remote_name in -lbluetooth... no
configure: error: We require BlueZ
```

UPDATE: I edited the configure file and replaced hci_remote_name with hci_read_remote_name in the script and it ran fine. I am now going to check on if it compiles and runs.

UPDATE 2: Alright, to compile, I needed to do the same replace in wiiremote_link.c as I did in the configure script and I also modified the make file in src directory from

```
libcwiimote.so: $(SOURCES) $(HEADERS)
	$(CC) $(CFLAGS) $(INCLUDES) $(SOURCES) -shared -o $@  $(LIBS)
	@cp $@ $(LIBDIR)
```

to the following (note I added -fPIC, as suggested by the compiler)

```
libcwiimote.so: $(SOURCES) $(HEADERS)
	$(CC) $(CFLAGS) -fPIC $(INCLUDES) $(SOURCES) -shared -o $@  $(LIBS)
	@cp $@ $(LIBDIR)
```

This gets things to compile but I don't know if the libraries will run or not *shrug*. Anyone have any thoughts?

UPDATE 3: Alright, well I ran the 3rd test program and things seem to be working but it's not throughly tested, hopefully the people over at libwiimote will update things...

Peace;
-Joshua

thank you a lot.

---

### Post by hicks1gb on 2012-06-19
Hi, could you please explain step by step how you managed to solve the error?

---

### Post by nothingspecial on 2012-06-19
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Closed.

---

