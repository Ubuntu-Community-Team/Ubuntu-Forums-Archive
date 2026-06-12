---
title: "A Study - multi-threaded make and quad core chips"
date: 2008-12-17
forum: Programming Talk
---

### Post by graysky on 2008-12-17
As a follow-up to the information presented in [this thread](http://ubuntuforums.org/showthread.php?t=1014190) looking at the CONCURRENCY_LEVEL variable as it related to compile speed on a quad core, I said I would look at the make -j switch and report back.

Why?  Many threads are out there teaching how to compile this or that and they all seem to disagree on the number the user is supposed to specify for an optimal build.  Is it equal to the number of cores, or is it 1+ the number of cores, etc.  I guess I just got curious.

Hardware specs: Xeon X3360 @ 8.5x400 = 3.40 GHz; 4 gigs of DDR2 @ 1,003 MHz.

The test I used was to compile MPlayer-1.0rc2:

```
$ ./configure --prefix=/usr
$ time make -jx
```

X was 1, 4,5,6,7, and 8.  I also did a 'make clean' between runs.

make -j1 

real	3m5.603s 
user	2m57.105s 
sys	0m8.819s 

make -j4

real	0m51.907s 
user	2m48.286s 
sys	0m9.416s 

make -j5

real	0m50.207s 
user	2m49.652s 
sys	0m9.026s 

make -j6

real	0m50.233s
user	2m49.696s
sys	0m8.819s

make -j7

real	0m50.080s
user	2m50.106s
sys	0m9.076s

make -j8
real	0m51.336s
user	2m51.132s
sys	0m9.173s

Just so you know, the 1 sec difference isn't real in my opinion.  When I repeated the make -j4 example for a second time, the result was 1.5 sec slower.  Conclusion: on this system 4-8 gave a result that was within error.

---

### Post by Bakerconspiracy on 2008-12-17
I did some mathematical theory in response to your post:

I took the last five samples you took and create a confidence interval. With 95% confidence I can say that the mean compile time of the package on your computer is captured by the interval (49.8415 , 51.6637) seconds.

In other words 51 seconds for the compile time is a very real possibility.

(50.7526 for the sample mean, .7339 for std deviation)

Hope you enjoyed haha.

---

