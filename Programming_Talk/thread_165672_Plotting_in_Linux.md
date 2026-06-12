---
title: "Plotting in Linux"
date: 2006-04-25
forum: Programming Talk
---

### Post by krypto_wizard on 2006-04-25
Hi,

I recently used Matlab for one of the small projects. Which app in Linux is closest to Matlab which can do most stuff which it does if not everything ?

Thanks

---

### Post by arnieboy on 2006-04-25
[QUOTE=krypto_wizard]Hi,

I recently used Matlab for one of the small projects. Which app in Linux is closest to Matlab which can do most stuff which it does if not everything ?

Thanks[/QUOTE]
use labplot.
if u want a clone of Origin, use [qtiplot]("http://kde-apps.org/content/show.php?content=14826&PHPSESSID=be8efae8f1cb12f75f6ba813bd89c78b")
Matlab also exists for linux by the way though it comes separately.

---

### Post by Parkotron on 2006-04-25
The answer is... Matlab! Mathworks supports Matlab on Windows, Mac and *nix. I believe even possible to share one license between installations on different operating systems.

If, however, you're looking for a free software alternative to Matlab there are a few options, but none of them are as comprehensive as Matlab itself. Scilab, Octave, Euler and GNUPlot all have some Matlab like abilities. Depending on your task, you should probably be able to find one suited to your needs.

[edit] You beat me to it arnieboy.

---

### Post by ow50 on 2006-04-25
[QUOTE=krypto_wizard]Which app in Linux is closest to Matlab which can do most stuff which it does if not everything ?[/QUOTE]
[Octave.](http://www.gnu.org/software/octave/)

For plotting:
[http://www.gnu.org/software/octave/doc/interpreter/Plotting.html#Plotting](http://www.gnu.org/software/octave/doc/interpreter/Plotting.html#Plotting)
> All of Octave's plotting functions use gnuplot to handle the actual graphics. Most types of plots can be generated using the basic plotting functions, which are **patterned after the equivalent functions in Matlab**. The use of these functions is generally straightforward, and is the preferred method for generating plots. However, for users familiar with gnuplot, or for some specialized applications where the basic commands are inadequate, Octave also provides two low-level functions, gplot and gsplot, that behave almost exactly like the corresponding gnuplot functions plot and splot. Also note that some advanced Matlab features from recent versions are not implemented, such as handle-graphics and related functions.

---

### Post by GoldBuggie on 2006-04-25
I second that for octave. I have thaught some Matlab courses on the University here in Stockholm and on my laptop I use octave. I also recommend it for students wanting to either try linux or for them that has it.

It does however depend on what you want to do. For calculations & plotting of data it is perfect. If you need to write a GUI it won't get you anywere.

Remember that many numerical algoritm packages are free to use. Matlab is built on such software but has other advantaes as well. But I mention it so you don't feel that you are lacking in the numerical algorithm side when you are using octave.


Btw...I use **koctave** as an editor for **octave.**

---

### Post by DCDraco on 2006-10-24
I am very intested in getting qtiplot were can I download it for Unbutu drapper?

---

### Post by Lord Illidan on 2006-10-24
You have to pay for a binary, it seems. However, you can get the source and download it yourself, which is what I am doing now. It comes with a readme file.

EDIT : It also seems quite hard...i wonder if someone would care to do a howto?

---

### Post by DCDraco on 2006-10-24
let me know how it goes good luck with it, but do you know if the payment to that web site is trust worthy?

---

### Post by Lord Illidan on 2006-10-24
> **DCDraco said:**
> let me know how it goes good luck with it, but do you know if the payment to that web site is trust worthy?

No idea.. PayPal should be trustworthy..
As for the source code, it needs so many libs etc, that I have a suspicion that the author really doesn't want you to compile it, just so you can pay for the binaries.

---

### Post by DCDraco on 2006-10-24
That is really shitty. My flatmate runs SuSe 10.0 on his Dell and he got it for free. Everything work nicely. We were both extreemly impressed with this software. Maybe I will in the just cough up 10 euros for the binary but it would be nice if it could be free. Although so far I cannot find it anywhere that is free. Well thanx for the info. i am very saddened that it didn't work out for you and that the have made it inaccesible for ubuntu useser to get it free.

---

### Post by amo-ej1 on 2006-10-26
if you only need plotting and not really matlab you can simply try to use gnuplot, (which is also the backend that octave uses). Personally for simple graphs I simply use gnuplot.

For more advanced things you should take a look at gnu octave.

---

### Post by pla7ma on 2007-01-22
You can install the rpm packages of suse using the command 

alien --to-deb qtiplot-0.8.5-1.pm.1.x86_64.rpm

you also have to install this package which doesn't seem do be included in ubuntu :

alien --to-deb ./qwtplot3d-0.2.6-1.el4.rf.x86_64.rpm 

I then used dpkg -i to install the generated packages
If it complains on startup, just use synaptic to install the missing things, they should all be in the ubuntu distro. I did not compile anything to get it going. 
The similarity with origin is indeed impressive

---

### Post by fadder on 2007-01-22
Another good option is matplotlib, which is to be used from python, or eve better from ipython.

---

### Post by der_vegi on 2007-04-01
there is a repository for qtiplot on my university's homepage:

[http://debian.physik.hu-berlin.de/]("http://debian.physik.hu-berlin.de/")

these binaries work for me using feisty on amd64.

---

