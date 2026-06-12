---
title: "Extracting uBLAS module from boost library"
date: 2010-07-24
forum: Packaging and Compiling Programs
---

### Post by JohnnyRep on 2010-07-24
Hi! 

I am interested in the uBLAS  library from the boost libraries.
As far as I understood it should be possible to extract that module  with BCP and build it later on with BJAM?! 
I hope here are some boost experts around (I found a couple of threads here about boost in general, but none of them was about extracting a module out of boost)

What I've done so far:
I) So I downloaded the newest boost release. 
II) $ bcp uBLAS config build ~/workspace/libs/uBLAS 
Which seemed to be successful. At least I got all the expected  folders to the chosen destination. I also got a boost-build.jam in my  directory, so I tried a simple 
III) $ bjam toolset=gcc 

Which leads to: 
error: error: no Jamfile in current directory found, and no target  references specified. 

May be I did that all in the wrong way, but there's no real  HOWTO out there (especially for the last step). 

Hope someone can help me out!?  
Many thanks! 

J.R.

---

### Post by SevenMachines on 2010-07-24
This post probably isnt much help :) Just to let you know that the way you describe should work, and does indeed work here. That it complains of a missing Jamfile is possibly an older bjam version thing(?), i dont use it so hopefully someone else knows
> 
$ bjam -v
Boost.Jam  Version 3.1.16. OS=LINUX.

$ cd /home/niall/Desktop/boost_1_43_0/
$ mkdir -p ~/Desktop/libs/uBlas
$ bcp uBLAS config build ~/Desktop/libs/uBlas
$ cd ~/Desktop/libs/uBlas/
$ ls boost-build.jam 
boost-build.jam
$ bjam

---

