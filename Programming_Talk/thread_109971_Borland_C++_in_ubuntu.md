---
title: "Borland C++ in ubuntu?"
date: 2005-12-29
forum: Programming Talk
---

### Post by meistwer on 2005-12-29
Hi there,

I've just managed to install Ubuntu in my machine and it all works fine so far, just few things had to be sorted by hand. My question is if anybody knows any C++ compiler that emulates Borland C++ Builder 5:confused:.  I'm trying to migrate in full to Linux/Ubuntu so I don't have to use Windows anymore but I need to find equivalents to some of my applications which I need for work. Another application I need help with is Altera Maxplus or any other VHDL desing and simulation tool would also be fine:rolleyes: .

Cheers

Rob

---

### Post by darth_vector on 2005-12-29
hi, i like hardware people :)

there is a package called ghdl that should cater for your VHDL needs. there are some other things in the repositories as well. do an

sudo apt-cache search vhdl

and see what you need.

---

### Post by Jengu on 2005-12-30
It depends on what you're looking for from Borland C++. If you just need any old C++ compiler, gcc, (```
apt-get install build-essential
```) will work just fine. If you also want a friendly development environment, look into anjuta or kdevelop. If you want Borland specific APIs -- then I think you're out of luck. But other libraries with equivalent functionality are probably available. Post back with more info about what exactly you're looking for.

---

### Post by Hanj on 2005-12-31
If you want the visual GUI editor in BCB, then installing Anjuta and Glade will get you pretty close. You will then be able to select "Edit application GUI" from within Anjuta.

But as Jengu said, the Borland APIs do not exist in a linux version (at least to my knowledge).

---

### Post by guttley on 2006-01-01
Dosnt Kylix include the C++ compiler, as well as pascal compiler?

How about porting your code from Builder to 'normal' C++?
ie TList = vector
The main problem is if your using the __closure keyword for callback to class methods.

---

### Post by fct on 2006-01-01
Try vdkbuilder2. It's in the repositories.

I haven't tried it, but according to the screenshots I saw some time ago, they are trying to clone the C++Builder IDE.

---

### Post by Kimm on 2006-01-01
Yes, Kylix has C++ support (free from Borlands website), but I have had not luck running it in linux

---

