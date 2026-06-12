---
title: "[Howto] install a working Twin(Text-based WINdows) on Xubuntu 8.04"
date: 2010-01-29
forum: Outdated Tutorials &amp; Tips
---

### Post by yannis on 2010-01-29
I read [this article]("http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/") and really liked the idea of working entirelly on test-based enviroment.

I tried w3m i liked it and i always used mplayer in terminal!
So i want to give a try in Twin.

The first thing to do is type 'twin', i got 'twin not installed, if you want sudo ...'. So i did it
```
sudo apt-get install twin
```

for a some reason(might be i have the greek version of xubuntu). the twin started but all the text is screwed up and in gibberish. So i googled it.

Here how it goes.

[LIST=1]
[*]**Download the source** from the [linuz.sns.it]("http://linuz.sns.it/~max/twin/")
```
$ wget http://linuz.sns.it/~max/twin/twin-0.6.2.tar.gz
```
[*]**Extract it**
```
$ tar -zxvf twin-0.6.2.tar.gz
$ cd twin-0.6.2
```
[*]and you will get the uncompressed files, ready to configure and compile with...
**_BUT_**
for a strange reason the configure create files **.modules** that are full with lines like these
```
-e
-e
-e

-e ifeq ($(SYS_SHLIBS),native)

-e endif
```

if you run 'make' you will take errors like ".modules:1: *** missing separator.  Stop."

so first eliminate all lines with just -e and remove -e before ifeq(i've done it manually possibly there is an easier way!)

and then run
```
$ ./configure
$ make
```

[*] your next headache is the *flags files that are also full of orphans '-e'. Enerytime you see '*** missing separator.  Stop." error you know what to do just eliminate the '-e's.

and then finally you can run
```
$ make install
```

[*] to start your new windows manager simply type
```
$ twstart
```
or
```
$ twin
```
[/LIST]

enjoy!

---

