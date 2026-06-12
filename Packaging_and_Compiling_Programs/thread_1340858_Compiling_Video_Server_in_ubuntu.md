---
title: "Compiling Video Server in ubuntu"
date: 2009-11-29
forum: Packaging and Compiling Programs
---

### Post by vijaysoft on 2009-11-29
Hi , i am a beginner in Ubuntu . I moved to Linux from windows for my application developments . I found a article about Live video streaming using Mobile phone to Website. In that project they are using a **Video server **for streaming the video but that Server is for linux . I also got the source code of that Server . I want to compile that server in ubuntu . But i don't know how to compile that in linux , it also require some libraries like libjpeg,libcuel,expat how to configure that things in ubuntu


u plz go through the link 

[http://www.movino.org/faq](http://www.movino.org/faq)

---

### Post by SevenMachines on 2009-12-01
if your build complains of missing dependencies then you generally need to install the headers for that dependency. these are the packages in the ubuntu repositories with the <some-package>-dev form. 

for example, if you try to run ./configure and get something like,

checking for jpeg.... no

then you will probably need to install libjpeg-dev

from the readme.txt for building the server on linux you posted it looks like you need to install
libjpeg-dev libcurl-dev  libexpat-dev

and then go into the server/ directory of the downloaded source and run 
$make

---

### Post by vijaysoft on 2009-12-01
how  to install those libjpeg , libcurl , libexpat in linux , please help me

---

### Post by SevenMachines on 2009-12-01
from a command line,
$ sudo apt-get install libjpeg-dev libcurl-dev  libexpat-dev

i would warn though, compiling and installing software in linux is going to be a challenge if you find installing libraries from the ubuntu repositories difficult. 
there are thousands of software packages in the repositories ready for you to use, you might want to try and use them until you are a bit more comfortable with linux

---

