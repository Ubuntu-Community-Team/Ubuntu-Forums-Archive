---
title: "Eclipse and g++"
date: 2006-11-10
forum: Programming Talk
---

### Post by rvickers on 2006-11-10
I'm trying out eclipse and gcc and I get the following error:

**** Build of configuration Debug for project HelloWorld ****
make -k all 
Building file: ../main.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"main.d" -MT"main.d" -o"main.o" "../main.cpp"
/bin/sh: g++: not found
make: *** [main.o] Error 127
make: Target `all' not remade because of errors.
Build complete for project HelloWorld

I guess it can't find g++? :-k

---

### Post by josys36 on 2006-11-10
Have you tried to install the package build-essential?

Jason

---

### Post by rvickers on 2006-11-10
What do you mean by "package build-essential"?
Thx

---

### Post by qamelian on 2006-11-10
> **rvickers said:**
> What do you mean by "package build-essential"?
Thx
Unless you install the build-essential metapackage, you won't have g++ on your system. In a terminal windoe, do the following: ```
sudo aptitude install build-essential
```. This will install the most common packages needed to compile programs from source code.

---

### Post by rvickers on 2006-11-10
Ok, thanks...:cool:

---

### Post by mkrahmeh on 2008-04-20
the <aptitude install> command did not provide the g++, nor the c++ (g++ and c++ are not being recognized commands in bash)....
can we configure the eclipse to use the gcc instead of generating g++ commands ?? if not, how to install the g++ ..
thx

---

### Post by Tomosaur on 2008-04-20
If build-essential didn't install g++, just install it manually using:
```

sudo apt-get install g++

```

---

### Post by mkrahmeh on 2008-04-21
it ddnt work either..am kinda new at linux and am not getting along with the package managers available yet (namely the synaptic and adept)

i tried also to download the g++.deb file from the internet then 
```
chmod +x g++.deb
./g++.deb 
```

but still got nothing....what to do ??

---

### Post by Tomosaur on 2008-04-21
> **mkrahmeh said:**
> it ddnt work either..am kinda new at linux and am not getting along with the package managers available yet (namely the synaptic and adept)

i tried also to download the g++.deb file from the internet then 
```
chmod +x g++.deb
./g++.deb 
```but still got nothing....what to do ??

Synaptic really is more user-friendly than installing deb packages manually, so stick with that when you can.

Are you sure you're using 'sudo' to intall things?

Anyway, to install a deb package, you use the following command:

```

sudo dpkg -i ./g++.deb

```

---

### Post by mkrahmeh on 2008-04-21
ok..it seems that there is dependency problems..the g++ version am trying to install is 3.4, the error log is long but it tells that it depends on gcc-3.4-base, which is not installed..i checked the gcc's version, surprisingly it is

```
mkrahmeh@mkrahmeh-laptop:/home$ gcc --version

gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)


```

:confused:

---

### Post by Tomosaur on 2008-04-21
You're certainly having a hard time :P

I recommend you just start over again. There is absolutely no reason why g++ from the repositories shouldn't work. Can you try installing like this again, and give us any error messages you receive?

```

sudo apt-get install g++

```

That should work fine, and if it doesn't, then it could be an indication of a bigger problem.

---

### Post by mkrahmeh on 2008-04-25
indeed I am..i found out that the apt-get is getting nothing at all..internet browsers are working fine but trying 
```
ping <any website>
```
yeilds 100% packet loss..so it seems that the system is not reaching the internet in the first place..

---

### Post by alisaleh on 2008-12-08
Hello I made all the things mentioned in this thread and some other forums
I checked that the GCC is installed with GCC -v, g++ -v,and make -v.
but it always says:

make all 
make: echo: Command not found
make: *** [main.o] Error 127

I have eclipse on the Windows OS and when I downloaded it for linux I opened it and I found the projects I made on windows on the project explorer. and the environment Variables contains  The Windows PATH. if any one knows what to do plz help

---

