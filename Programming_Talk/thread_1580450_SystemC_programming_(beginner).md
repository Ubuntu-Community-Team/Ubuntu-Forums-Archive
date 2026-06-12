---
title: "SystemC programming (beginner)"
date: 2010-09-23
forum: Programming Talk
---

### Post by marouane87 on 2010-09-23
Hi :)

I know that for Visual studio, there's a library to be added to be able to program SystemC, however, I want to program using ubuntu too, so I installed it using VirtualBox (Ubuntu 10.4).
I have no idea what application to use for programming on ubuntu and how to associate it for SystemC.

Thank you very much :)

---

### Post by schauerlich on 2010-09-23
You need a compiler and an editor. For the compiler, install build-essential:

```
sudo apt-get install build-essential
```

You should have any number of editors available already.

See here for more info: [http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

---

### Post by marouane87 on 2010-09-23
Thank you very much, but how to add SystemC or is it alreaddy installed once I installbuild-essential?

---

### Post by nvteighen on 2010-09-23
I had to look up what SystemC was...

SystemC is a set of C++ classes and macros, so you should use the g++ compiler, because you'll actually be using C++. The build-essentials package will set the compiler up and using it is as simple as it's shown in the link given to you by schauerlich.

Now, the issue I see is that it seems no SystemC implementation is there to use in GNU/Linux. I'm not even sure I understand what SystemC is, but I feel it may be redundant because C is used in the GNU/Linux world for what SystemC seems to be...

---

### Post by marouane87 on 2010-09-23
Thank you for the answer :)

SystmC is used for hardware description (I'm studying industrial electronic engineering), I think I'll need to install systemc-2.2.0.tgz (downloaded from [http://www.systemc.org/downloads/standards/](http://www.systemc.org/downloads/standards/)), the problem may'll be on how to install it and then how to call that library every time I want to make a new SystemC project.

---

### Post by nvteighen on 2010-09-24
> **marouane87 said:**
> Thank you for the answer :)

SystmC is used for hardware description (I'm studying industrial electronic engineering), I think I'll need to install systemc-2.2.0.tgz (downloaded from [http://www.systemc.org/downloads/standards/](http://www.systemc.org/downloads/standards/)), the problem may'll be on how to install it and then how to call that library every time I want to make a new SystemC project.

Who the hell is this people, that ask for a password for downloading it? I haven't got time to try this out, so I couldn't take a look on the file.

First read the README... it'll be of much more help than anything I can tell you about a tarball I haven't ever seen :D

Anyway, to link with any library, you do this. Suppose it is a shared library whose filename is "libblah.so", installed in the system directories (/lib, /usr/lib, /usr/local/lib are Ubuntu's defaults):

```

g++ -o myapp main.cpp SillyClass.cpp math_routines.cpp -Wall -Wextra -lblah

```

The -l flag is used to link with a library. The name you use is the library's filename with "lib-" and extension stripped off, hence "libblah.so" becomes "-lblah"... or "libm.so" (the C Math Library) > "-lm".

If the library isn't located at a system default directory, what you do is to add places where the compiler should also look at. For example, let's say I downloaded "libblah.so" from a website and placed under ~/programming/lib (~ = user's home directory... I got the impression that you're also new to GNU/Linux, but I'm not sure). So, what I should do is:

```

g++ -o myapp main.cpp SillyClass.cpp math_routines.cpp -Wall -Wextra -L~/programming/lib -lblah

```

The -L flag adds places where to find libraries... It's a bit weird because it doesn't use a space to separate flag from argument... so yes, you write it the way I did above: -L./ (that'd be to search in the current directory), -L/opt/ (also search at /opt), etc.

Be aware that installing libraries in non-default places and compiling them as I did above won't make the application work (the runtime linker won't know where to find the libraries), it will just make it compile. To make it work you have to tweak an environment variable, but that's another story... Let's see if you can compile something with SystemC first. That's why there are default locations and people are expected to use them: to avoid Windows's "DLL hell"... any "respectable" program should use them.

---

### Post by marouane87 on 2010-09-26
Thank you very much for the explanation (and I'm sorry to be late since I haven't internet connection for the last few days)

I found a tutorial and I'm trying to follow it but I have some troube with the commands (I'm a beginner, I used ubuntu for a while but it was just stadard use: multimdia, internet etc... and it's my first time for programming on linux)

Please how to make the actions on the page 26 of the this file please: [http://www.dti.dk/_root/media/27325_SystemC_Getting_Started_artikel.pdf](http://www.dti.dk/_root/media/27325_SystemC_Getting_Started_artikel.pdf)

And a final question, do you think it would be better to use Eclipse on ubuntu? 

Thank you again and sorry for the disturbance.

---

### Post by spjackson on 2010-09-26
> **marouane87 said:**
> Please how to make the actions on the page 26 of the this file please: [http://www.dti.dk/_root/media/27325_SystemC_Getting_Started_artikel.pdf](http://www.dti.dk/_root/media/27325_SystemC_Getting_Started_artikel.pdf)

Those instructions seem pretty clear. What specifically are you having trouble with?
> 
And a final question, do you think it would be better to use Eclipse on ubuntu? 
It's largely a matter of taste; I wouldn't use Eclipse (with CDT) unless I could identify clear advantages that it would give me. Some people choose Eclipse because it is (or is similar to) what they are familiar with.

---

### Post by marouane87 on 2010-09-26
Sorry, I thought they weren't true commands :oops:

I don't know for Eclipse, I'm thinking may it would be more easy with its IDE than writing on blanc file and try to link it with a library using commands like nvteighen has told me. I didn't use it before and on windows we're going to use Visual Studio (to make systemC programs), and I'm trying to do it on both windows and linux.

---

### Post by spjackson on 2010-09-26
> **marouane87 said:**
> Sorry, I thought they weren't true commands :oops:

The lines in bold that begin with $ are the commands for you to type (without typing the $), except that where it has```
<user>
```you are meant to replace that with your username. If you don't know what that is then type```
$ whoami
```There are two preliminary steps on page 26 of your instructions, i.e. steps 1 and 2. Here the actual commands are not given. Something along the following lines should suffice for step 1. 
```
$ cd $HOME
$ tar xzvf full_path_to_the_tgz_download
```For step 2 you need
```
$ mkdir /home/<user>/systemc-2.2.0/objdir
$ cd /home/<user>/systemc-2.2.0/objdir

```

---

### Post by marouane87 on 2010-09-26
Thank you very much :D

---

