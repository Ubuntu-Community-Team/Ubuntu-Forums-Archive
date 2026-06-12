---
title: "[SOLVED] Beginning development"
date: 2008-11-08
forum: Programming Talk
---

### Post by Stoodle on 2008-11-08
I really need to move along in my programming skills. Now, I'm the big cheese at my school in the computer science program (well, there are a few as good or better than me) but I know that I need way more practice because I want to be a hacker, not some 9-to-5 programmer when I'm older.

Well I figured that, having just completed a program to cut up text files for use on the iPod (lemme know if you want sauce), I need to work on something else to improve. I know I'd learn a lot developing for the applications on my computer so I decided to write a plugin  for Pidgin. I'm reading the how-to and immediately, I'm wondering, "How would I remember all of this stuff on to write a plugin?"

Second, I had a bigger problem. I copied and pasted from the site the helloworld source code just to run it but I can't "make" it. It says
> 
Next, change to the pidgin-2.0.2 directory.  If you are using Windows, run make -f Makefile.mingw to build Pidgin.  If you are using another platform, run ./configure and then make after the configuration is complete.
What do I make and how? If I do
```

make helloworld.c

```I get
```

make: Nothing to be done for `helloworld.c'.

```If I do
```

 make helloworld.so

```
I get 
```

make: *** No rule to make target `helloworld.so'.  Stop.

```So! Do you guys think you could push me in the right direction? I'd really appreciate it!

PS: If this post sounds a little weird, it's because I'm way too tired.
PPS: The search function on this site could be better.
PPPS: I had a great idea for speeding up downloading. We should download small packets that represent larger chunks of data. Those packets will tell the computer what to make and so we'll have our data but we've only had to download instructions.

---

### Post by slavik on 2008-11-08
I would suggest you first learn how to compile a tarball, then I suggest you learn how to use make and related tools for development. Then you can move onto writing plugins for pidgin. :)

---

### Post by mali2297 on 2008-11-10
Usually, the procedure is
```

./configure
make
sudo make install

```
The first command creates a Makefile adapted to your system, the second command compiles the sources specified in the new Makefile and last command installs the program.

---

### Post by Stoodle on 2008-11-10
Thanks for the push in the right direction. I did compile the helloworld plugin (which I copied from the site). I was getting some error about Network Manager but when I disabled the need for it, I was able to ./configure and make.

---

