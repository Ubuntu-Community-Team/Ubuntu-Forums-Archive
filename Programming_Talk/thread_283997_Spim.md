---
title: "Spim"
date: 2006-10-25
forum: Programming Talk
---

### Post by ivoencarnacao on 2006-10-25
Is anyone using Spim/Xspim on Edgy?

Is it just me or the one in the repos doesnt work?
When i try to run it with xspim it shows a window without buttons, sometimes the buttons are there but they dont work!

Here are some screenshots i took:

with [buttons](http://img120.imageshack.us/img120/1042/1jz6.png)!
without [buttons](http://img175.imageshack.us/img175/1117/2mx8.png)!


Could someone provide some help here?


Thanks!

---

### Post by ivoencarnacao on 2006-10-25
No volunteers?

---

### Post by km3k on 2006-10-26
I have the same problem, but haven't found a solution yet.

---

### Post by ivoencarnacao on 2006-10-26
> **km3k said:**
> I have the same problem, but haven't found a solution yet.

Well, it seems that Spim/Xspim is really broken in Edgy.

The solution would be maybe an older version of Ubuntu, Dapper for instance or even Breezy, since both use older versions of Spim.


Could you or anyone try one of the above and report?


Thanks!

---

### Post by ivoencarnacao on 2006-10-26
It seems the one in Dapper does work.
At least the buttons are there and they do work.

---

### Post by bauglir on 2006-12-12
how do i install that on edgy, i mean, how do i install an older version?

---

### Post by tbanack on 2007-02-13
I had the same problem not being able to get SPIM to work on edgy, and the only solution I found was one that REALLY makes me cringe.  I downloaded the Windows version from the SPIM website : [http://www.cs.wisc.edu/~larus/spim.html]("http://www.cs.wisc.edu/~larus/spim.html"). Then I installed it, running through wine. It works fine but I would rather use the linux version. So if someone else finds a solution to get it running on Edgy, please let me know.

---

### Post by ukch on 2007-05-23
When an Ubuntu package doesn't work for me, I usually try out the equivalent Debian package. I have installed Spim 7.3-1 from packages.debian.org (non-free/electronics) and it works fine for me, and can be installed with dpkg just like any other package.

---

### Post by chemicalgr on 2007-05-24
Well try this site SPIM on linux 
[http://archvlsi.ics.forth.gr/~kateveni/225/](http://archvlsi.ics.forth.gr/~kateveni/225/)
this is a greek one,i hope you have the neccesary encoding for greek Language

---

### Post by alzeih on 2008-02-25
My uni uses a modified version of spim, so I have no option but to compile it myself. 

I'm running Gutsy and having the same problems.

---

### Post by meonkeys on 2009-01-24
Anyone have spim working (either the command line or GUI version) working on Ubuntu 8.10?

...after installing libxaw7-dev and libxt-dev I was able to compile xspim by following the provided instructions.

---

### Post by Ludachrispeed on 2009-02-10
same question here... I've gotten to the point where I can compile xspim, and even run it, but all the buttons are blank and it is completely non-functional.

---

### Post by CabanaBoi on 2009-03-16
I was following the instructions to compile xspim 7.4 and was having the same problem (Non functional GUI). The problem was during the make process of compiling the source code, during which some people might have seen errors relating to X11.

As meonkeys pointed out, we need to install the X11 development libraries including libxaw7-dev and libxt-dev. Also, the bison parser needs to be installed. After this just follow the instructions in the Readme file included with the Xspim source to recompile xspim. It basically says:

Go to Terminal and change the directory to the xspim source and type the following commands:
xmkmf
make
sudo make install

If all goes well you can then run xspim by typing xspim in the terminal.

Hope this helps. :D

---

### Post by Berserker v7 on 2009-03-16
XSpim is indeed a very buggy software, so why don't just leave it and try another cool open-source software, MARS(MIPS Assembler and Runtime Simulator), developed i beleive by the students of Missouri State University?

Download link: [http://courses.missouristate.edu/KenVollmar/MARS/download.htm](http://courses.missouristate.edu/KenVollmar/MARS/download.htm)

Its way better than XSpim and in my opinion, even better than PCSpim... provides you with a lot of data regarding register values(even the extended registers), etc. for debugging and better understanding... and the complete MIPS instruction set is available in the help pages... will run on any OS that has got the Java Runtime Environment installed...

Once you have downloaded the Jar archive from the link, just execute the command
```
java -jar Mars.jar
```
in the download directory...

---

### Post by meonkeys on 2009-04-04
See [this bug]("https://bugs.launchpad.net/bugs/293585") for
[LIST]
[*]a [spim/xspim source package]("http://revu.ubuntuwire.com/p/spim")
[*]a [spim/xspim binary package]("http://launchpadlibrarian.net/21654725/spim_7.3-1_i386.deb")
[*]status on inclusion of spim/xspim in Debian/Ubuntu
[/LIST]

[https://bugs.launchpad.net/bugs/293585](https://bugs.launchpad.net/bugs/293585)

---

### Post by liviubero on 2009-06-04
> **Berserker v7 said:**
> XSpim is indeed a very buggy software, so why don't just leave it and try another cool open-source software, MARS(MIPS Assembler and Runtime Simulator), developed i beleive by the students of Missouri State University?

Download link: [http://courses.missouristate.edu/KenVollmar/MARS/download.htm](http://courses.missouristate.edu/KenVollmar/MARS/download.htm)

Its way better than XSpim and in my opinion, even better than PCSpim... provides you with a lot of data regarding register values(even the extended registers), etc. for debugging and better understanding... and the complete MIPS instruction set is available in the help pages... will run on any OS that has got the Java Runtime Environment installed...

Once you have downloaded the Jar archive from the link, just execute the command
```
java -jar Mars.jar
```in the download directory...

Thanks for that!

---

