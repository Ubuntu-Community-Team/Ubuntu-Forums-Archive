---
title: "How to do an optimal aircrack-ng compilation?"
date: 2007-03-21
forum: Programming Talk
---

### Post by CyberAngel on 2007-03-21
Hello,

I used backtrack version 2 live cd to test some wpa dictionary cracking using aircrack-ng.
If someone has seen before aircrack-ng in action, it is showing to the user how many keys/s it is checking from the dictionary to find the true one.
Using backtrack this number on a PC was about 122-125 keys per second.
On the same PC using ubuntu and compiled aircrack from source I get 90 keys per second!!!
By copying the executable aircrack-ng from backtrack to ubuntu I get again 122-125 keys/s!!
That is a huge difference!

So I suppose that it has to do with the compilation and the gcc optimizations for more modern processors.
I tried some CFLAGS I found while googling (-march=pentium4 -mfpmath=sse -msse2 -mtune=pentium4) but there is no difference at all.
The same speed I get from the program by typing just "make" and compiling it, I get even with the optimized CFLAGS.

Can someone suggest something or even try it to tell me his results?
The version of aircrack-ng backtrack has is 0.7 r214 and the current version is 0.7 r232.


If you want to try it out you can use the following command to get the source from svn for the specified program.
```
svn co http://trac.aircrack-ng.org/svn/trunk/ aircrack-ng
```
Once you download the source and do the compilation there is a "test" folder that has a wpa.cap and a password.lst for the testing purposes.
The command you can use to test it is
```
aircrack-ng -w password.lst wpa.cap
```


Also that keys/s counter is good for benchmarking :P

---

### Post by Jmccaffrey on 2007-03-21
Try the c flag -O2

---

### Post by CyberAngel on 2007-03-21
Unfortunately the same results :(
The default on the Makefile was -O3 but even changing this to -O2 I am still getting the same results..
almost 90k/s.

---

### Post by CyberAngel on 2007-03-22
Now after that I`ll go crazy :shock: :roll: :shock: :roll: :shock: :roll: 

I`ve spent a lots of hours to find out how I can get the best compilation results and because with every CFLAG options I tested I was getting exactly the same results (about 90k/s) I thought that they may have compiled it using ICC (Intel C++ Compiler). So I did something simple to get some more info...

I opened the compiled executable from backtrack with a Hex viewer and checked it out a little and I found that it was compiled using gcc 3.4.6.

So the next steps?
sudo apt-get install gcc-3.4 on my kubuntu feisty!! (It is exactly the same version actually. 3.4.6)
Compiling again the program and guess what!
125k/s!!!!!!!!! with aircrack-ng r214 (same as backtrack version)
145k/s!!!!!!!!! with the latest revision (r233)

With gcc-4.1 I was getting only 90-95k/s with the last revision!!! (r233)
I didn`t checked r214 with gcc-4.1 but it will be probably even more slower.

I will try to compile it again tomorrow using Intel C++ Compiler to check the results!!!

---

