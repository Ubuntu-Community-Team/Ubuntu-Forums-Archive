---
title: "HELP!  Noob needs command line help!"
date: 2008-05-12
forum: Programming Talk
---

### Post by taehC on 2008-05-12
i am trying to make the "brain-machine" from makezine.
i need to execute the command
```
make program-mypov

```
but when ever i do that i get...
```
Compiling: mypov.c
avr-gcc -c -I. -g -Os			 -funsigned-char -funsigned-bitfields -fpack-struct -fshort-enums -Wall -Wstrict-prototypes -DF_CPU=8000000   	 -Wa,-adhlns=mypov.lst  -mmcu=attiny2313 -std=gnu99 mypov.c -o mypov.o
sh: avr-gcc: not found
make: *** [mypov.o] Error 127

```
please i am in desparate need of help!
please respond!

---

### Post by tamoneya on 2008-05-12
do you have build-essential installed?
```
sudo apt-get install build-essential
```

---

### Post by zenwalker on 2008-05-12
I think gcc isnt install, did u do _apt-get install build-essential_ before doing make on u r system?

---

### Post by taehC on 2008-05-12
still says same thing...
do i need to restart after installing it?

---

### Post by LaRoza on 2008-05-12
> **taehC said:**
> still says same thing...
do i need to restart after installing it?

No, you don't need to restart (this isn't Windows).

Is there a a readme or some sort of compiling instructions? It should list what you have to do and what you need.

---

### Post by zenwalker on 2008-05-12
I am getting a doutbt, why is it using avr-gcc instead of just gcc cmd? Seems strange 2 me. 

Just isee gcc cmd on konsole, and see if u get output if its correctly isntalled.

---

### Post by zenwalker on 2008-05-12
> No, you don't need to restart (this isn't Windows).
I second that :D

---

### Post by tamoneya on 2008-05-12
I havent yet looked for the article but since this is from MAKE magazine it is probably meant for an AVR microcontroller.  Are there any more directions in the article?

---

### Post by zenwalker on 2008-05-12
So then, the OP has to install avr-gcc package instead of gcc right?

---

### Post by tamoneya on 2008-05-12
probably but there are probably more details in the article.  If that is the case:```
sudo apt-get install avr-gcc
```He probably needed build-essential anyways though.

---

### Post by taehC on 2008-05-12
yes it is made to use avr, but all make says is
run make just to check if avr-gcc is working
but it doesnt say howto fix if u do get avr-gcc error...

---

### Post by taehC on 2008-05-12
> **tamoneya said:**
> probably but there are probably more details in the article.  If that is the case:```
sudo apt-get install avr-gcc
```He probably needed build-essential anyways though.

i tried that but it couldnt find the package.
is there another source i need?

---

### Post by tamoneya on 2008-05-12
try ```
sudo apt-get install avr-libc
```This may be the package which references avr-gcc

---

### Post by zenwalker on 2008-05-12
[http://www.avrfreaks.net/index.php?module=FreaksTools&func=viewItem&item_id=145](http://www.avrfreaks.net/index.php?module=FreaksTools&func=viewItem&item_id=145) more info on AVR Gcc.

---

### Post by taehC on 2008-05-12
> **tamoneya said:**
> try ```
sudo apt-get install avr-libc
```This may be the package which references avr-gcc

ok i installed that but still same error 
when i try to install avr-gcc again it still says that it has no install candidate

---

### Post by tamoneya on 2008-05-12
that wasnt meant to fix the install of avr-gcc.  It was supposed to install avr-gcc in the process.  Does the "make" work now?

---

### Post by taehC on 2008-05-12
> **tamoneya said:**
> that wasnt meant to fix the install of avr-gcc.  It was supposed to install avr-gcc in the process.  Does the "make" work now?

i know i just tried avr-gcc anyway
make still not work, same error

---

### Post by taehC on 2008-05-12
YAY!
FIXED!
for some reason, it was called gcc-avr even though i was asked for avr-gcc!
so just go to package manager and install gcc-avr to get make to work

---

### Post by tamoneya on 2008-05-12
a little odd but cool.  Have fun with your AVRs

---

