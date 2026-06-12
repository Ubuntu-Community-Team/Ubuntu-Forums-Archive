---
title: "Help ripping DVDs"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by luvitlo on 2012-06-23
Hello everyone,
I am very rusty on Linux Kernal Operating Systems, I found Ubuntu looking for a new OS for a Laptop I was given, the previous owner fried the hard disc so I saw it as a great chance to have a truly awesome computer running only Linux OS and Ubuntu caught my attention.
I am running this OS on a HP Pavilion dv6 with a AMD Triple Core Processor 500GB Hard Disc and 4GB of Ram, overkill I know but it is running so sweet! 
My current problem is finding a DVD Ripper to put my favorite movies on my computer, I tried Acidrip but keep getting errors and another that the support programs wouldn't download. Do I need to buy the DVD Player for them to work? 
any help will be nice and also where can I find a command list?

---

### Post by lisati on 2012-06-23
I'm going to give you the benefit of the doubt for the moment and assume that you want to play DVDs you own on your machine.

There is software available in Ubuntu's software centre which can play DVDs without the need to rip them (which could raise legal issues). You might need to install the "restricted extras" package first: this can be done from the command line:
```
sudo apt-get install restricted-extras
```

If this produces an error message, please reply with the details, and we might be able to help.

---

### Post by LADmaticCA on 2012-06-23
Install ubuntu-restricted-extras

```
sudo apt-get install ubuntu-restricted-extras
```

After that install libdvdcss2:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```


Then I would recommend Handbrake for ripping DVD's. To install it in Ubuntu 12.04 you have to follow the instructions on this site:

[http://www.thepowerbase.com/2012/03/install-handbrake-in-ubuntu-12-04/](http://www.thepowerbase.com/2012/03/install-handbrake-in-ubuntu-12-04/)

Good Luck.

---

### Post by oldos2er on 2012-06-23
Changed thread title.

---

### Post by andrew.46 on 2012-06-24
If you want to rip your own dvds to disk and then convert you could always take a walk on the commandline side and try something like this technique:

FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

but if you simply want to make a straight copy of your dvd with no subsequent transcoding you can [simply use vobcopy]("http://www.andrews-corner.org/burning.html#movies") (with libdvdread and libdvdcss).

As lisati has mentioned first check the legal issues of dvd copying in your country.....

---

