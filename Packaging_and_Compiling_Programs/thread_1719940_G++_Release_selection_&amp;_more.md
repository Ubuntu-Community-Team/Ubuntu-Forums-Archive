---
title: "G++ Release selection &amp; more"
date: 2011-04-02
forum: Packaging and Compiling Programs
---

### Post by Aaron2 on 2011-04-02
I'm trying to set up G++ on Ubuntu to compile C++, but Its not obvious to me which release of G++ should be used for Ubuntu.

I believe this is the correct directory location:
[http://mirrors-us.seosue.com/gcc/releases/gcc-4.6.0/](http://mirrors-us.seosue.com/gcc/releases/gcc-4.6.0/)

Any help apreciated.

---

### Post by MadCow108 on 2011-04-02
just install the build-essential package
it includes the gcc compiler supported by your ubuntu version which is 4.4 in maverick (4.5 is also available), plus a bunch of stuff needed for compiling stuff (libc6-dev, make)
```
sudo apt-get install build-essential
```

for 4.5 if available:
```
sudo apt-get install gcc-4.5
# c++
sudo apt-get install g++-4.5
```

you can get 4.6 from this ppa:
[https://launchpad.net/~ubuntu-toolchain-r/+archive/test/+packages](https://launchpad.net/~ubuntu-toolchain-r/+archive/test/+packages)
but only use that if you really need it.

---

### Post by Aaron2 on 2011-04-03
Wow 

1. Would I be better off with Ver 4.4 or 4.5 G++ then?
2. Is Maverick a package that would include all individual items I need?

3. So may choices and variables.
So would this be the correct choice from your above URL:
[gcc-4.6 - 4.6.0-1ubuntu1~ppa1]("https://launchpad.net/%7Eubuntu-toolchain-r/+archive/test/+sourcepub/1566144/+listing-archive-extra")_ _? (This will be used on an Intel Atom 330 Platform)

Only use your URL if I really need it?? or install all items only if I really need them??

Not sure if I should I install every item under this heading or not?  I just want to use CodeLite and G++ on Ubuntu to create and compile apps for a class.  One coming project will be to convert a hardware control VB6 app to C++, so libraries will be important.  I only have an 8GB SS drive, at the moment.

---

### Post by MadCow108 on 2011-04-03
> 
I just want to use CodeLite and G++ on Ubuntu to create and compile apps for a class

for codelite just do this:
```
sudo apt-get install codelite codelite-plugins
```
it will also install the needed compilers (gcc and g++)

> **Aaron2 said:**
> Wow 

1. Would I be better off with Ver 4.4 or 4.5 G++ then?

depends which version you need.
if you do not need the features of 4.5 (which is mainly the link time optimizer), stick with the default version which is 4.4 in maverick 10.04.
> 
2. Is Maverick a package that would include all individual items I need?

almost everything you need is packaged, linux distributions are very developer friendly.
gcc includes the C compiler, g++ the c++ compiler, gjc-jdk the java compiler etc.
just type in what you need in the command line and it will tell you what to install if its missing.
e.g:
```
$ gcj
The program 'gcj' is currently not installed.  You can install it by typing:
sudo apt-get install gcj-jdk
```
to see what a package is use: apt-cache show gcc
> 
3. So may choices and variables.
So would this be the correct choice from your above URL:
[gcc-4.6 - 4.6.0-1ubuntu1~ppa1]("https://launchpad.net/%7Eubuntu-toolchain-r/+archive/test/+sourcepub/1566144/+listing-archive-extra")_ _? (This will be used on an Intel Atom 330 Platform)


as you seem inexperienced with package based distributios I do not recommend to use this ppa. Do you **really** **require** 4.6?
if you really need it here's how to install, but as this is a experimental ppa do so on own risk, I'll not help you recovering your system if something fails.
```
sudo apt-add-repository ppa:ubuntu-toolchain-r/test/ubuntu
sudo apt-get update
sudo apt-get install gcc-4.6
sudo apt-get install g++-4.6
```

---

