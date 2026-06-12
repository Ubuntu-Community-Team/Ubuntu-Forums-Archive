---
title: "Cannot compile error"
date: 2007-01-12
forum: Programming Talk
---

### Post by mafifk on 2007-01-12
I try to install M4-1.4.8 

after step

./configure

the below error came out

checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

How to solve and overcame this problem.

all the program that i try to compile ,show the same error. ](*,) 

Please help me, I'm very new in Linux. :(

---

### Post by Arndt on 2007-01-12
> **mafifk said:**
> I try to install M4-1.4.8 

after step

./configure

the below error came out

checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

How to solve and overcame this problem.

all the program that i try to compile ,show the same error. ](*,) 

Please help me, I'm very new in Linux. :(

What's the last part of the file config.log?

---

### Post by charrin on 2007-01-12
Ubuntu has not a C compiler by default. This is a big difference with other distributions.

You have to go to Synaptic (System->Admin->Synaptic) and look for the package "build-essentials". Just double click on it and click Apply and it will download (or pick from the install CD) the necesary packages to install the C and C++ compiler gcc and the rest of things to compile applications.

I hope this will be that you are looking for ;)

---

### Post by ajgreeny on 2007-01-12
You probably need to install build-essentials from the repos.  Have a look to see if it's already installed and if not install it.

---

