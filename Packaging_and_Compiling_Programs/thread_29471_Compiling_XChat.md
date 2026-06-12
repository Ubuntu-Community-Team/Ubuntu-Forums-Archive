---
title: "Compiling XChat"
date: 2005-04-24
forum: Packaging and Compiling Programs
---

### Post by TestDummy! on 2005-04-24
Okay, here's what I want to do but I really have no clue how to do it

I noticed Ubuntu comes with XChat 2.4.1. I want to update it to 2.4.3 by compiling from the source provided on [www.xchat.org](www.xchat.org) 

But, I have no clue on how to really do it. ](*,)  

I have the package, I'm almost sure I have all the required stuff installed to compile stuff together, I just don't know how I go about replacing 2.4.1 with 2.4.3 after it's complied. 

Any help would be great,

---

### Post by TravisNewman on 2005-04-24
[http://www.xchat.org/compiling/](http://www.xchat.org/compiling/)

extract the source, cd into that directory then
./configure
make
sudo make install
enter your password
done ;)

---

### Post by DJ_Max on 2005-04-24
[QUOTE=TestDummy!]Okay, here's what I want to do but I really have no clue how to do it

I noticed Ubuntu comes with XChat 2.4.1. I want to update it to 2.4.3 by compiling from the source provided on [www.xchat.org](www.xchat.org) 

But, I have no clue on how to really do it. ](*,)  

I have the package, I'm almost sure I have all the required stuff installed to compile stuff together, I just don't know how I go about replacing 2.4.1 with 2.4.3 after it's complied. 

Any help would be great,[/QUOTE]
 You have to uninstall your current xchat deb binary, since you will be installing from source.

---

### Post by TravisNewman on 2005-04-24
Thanks DJ_Max, I left that part out. :)

---

### Post by DJ_Max on 2005-04-24
> Thanks DJ_Max, I left that part out. 
 :cool:

---

### Post by TestDummy! on 2005-04-26
Aha! There, I finally got it to compile. It wasn't working before but I was missing  a certain GTK library. I installed it and it compiled fine but..

How do I go about removing this when I want to upgrade to the next one? It doesn't seem to show up in synaptic or whatever it's called.  :-?

---

### Post by DJ_Max on 2005-04-26
[QUOTE=TestDummy!]Aha! There, I finally got it to compile. It wasn't working before but I was missing  a certain GTK library. I installed it and it compiled fine but..

How do I go about removing this when I want to upgrade to the next one? It doesn't seem to show up in synaptic or whatever it's called.  :-?[/QUOTE]
 Of course it's not going to be in synaptic, Synaptic is only a frontend for apt-get. To uninstall it, you should be able to go into the directory you compiled it in, and do a
sudo make uninstall

---

### Post by TestDummy! on 2005-04-26
Out of curiosity, wouldn't 

"sudo apt-get uninstall xchat" work too?

---

### Post by DJ_Max on 2005-04-26
[QUOTE=TestDummy!]Out of curiosity, wouldn't 

"sudo apt-get uninstall xchat" work too?[/QUOTE]
 No, 
apt == .deb binaries
apt != source installs

Apt doesn't even know xchat is installed on your system if you installed from source.

BTW, it wouldn't be apt-get uninstall, it would be apt-get remove ;-)

---

### Post by b3nw on 2011-05-06
> **TestDummy! said:**
> Aha! There, I finally got it to compile. It wasn't working before but I was missing  a certain GTK library. I installed it and it compiled fine but..

How do I go about removing this when I want to upgrade to the next one? It doesn't seem to show up in synaptic or whatever it's called.  :-?


It would be awesome for people who read this thread in the future if you could state which GTK library you needed to install....

didn't realize this thread was 2005, feel free to delete this.

---

