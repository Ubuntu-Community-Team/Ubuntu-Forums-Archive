---
title: "I can Not get ANY tar.gz package to install"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Brightbelt on 2008-07-11
Hi,
I'm trying to install several tar.gz packages that are associated with qJackctl, which is the audio interface program for Ardour Digital Audio Workstation. 

I don't think what programs those are is so important. The thing is: 
1) I'm reading the 'Install' instructions for these tar.gz packages
2) I'm extracting the packages onto my desktop
3) I'm doing the 'cd Desktop/foldername' directory in the terminal and that goes fine.
4) And I'm doing these lines:

```
sudo ./configure
sudo make
sudo make install
```

And actually I can't get the configure part to go right - errors come up. Here's an example:

```
brightbelt@brightbelt-laptop:~$ cd Desktop/qjackctl-0.3.3
brightbelt@brightbelt-laptop:~/Desktop/qjackctl-0.3.3$ sudo ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
brightbelt@brightbelt-laptop:~/Desktop/qjackctl-0.3.3$ 
```

I get similar results for all my tar.gz packages.

I appreciate any help anyone could offer. 

BTW, would it be possible for SOMEONE to make a tar.gz Installer program???? That would be a dream.

Many Thanks for any help,
Frank B.

---

### Post by Bachstelze on 2008-07-11
First, **do not** run configure scripts as root. Just **./configure** will do. The same goes for the compilation (make), only the installation needs to be done as root (sudo make install).

Second, *sudo apt-get install build-essential*.

> **Brightbelt said:**
> BTW, would it be possible for SOMEONE to make a tar.gz Installer program???? That would be a dream.

No it would not. Every program is different and is compiled in different ways, so an universal source installer (whatever that would mean) is impossible.

---

### Post by RATM_Owns on 2008-07-11
Edit: Beaten.

Yeah, just
sudo apt-get install build-essential
Then
./configure
make
sudo make install

---

### Post by Brightbelt on 2008-07-11
Thanks, guys, for the build-essential tip especially. I'm still getting this however (you'll see the very end of the build-essential process):

```
Setting up build-essential (11.3ubuntu1) ...
brightbelt@brightbelt-laptop:~/Desktop/qjackctl-0.3.3$ ./configure
./configure: line 1362: config.log: Permission denied
./configure: line 1372: config.log: Permission denied
brightbelt@brightbelt-laptop:~/Desktop/qjackctl-0.3.3$ 

```

---

### Post by Bachstelze on 2008-07-11
You'll have to first clean up the mess you've done by running ./configure as root. The easiest ways is to just delete the source directory and start over. **Be very careful** not do make any typos when using *rm*!

```

cd ..
sudo rm -rf qjackctl-0.3.3
```

By the way, *build-essential* contains all the basic tools needed for compiling stuff. Depending on the program you're compiling, you might need some other stuff too, but if you're compiling you will *always* need the b-e.

---

### Post by aktiwers on 2008-07-11
Remember most tar.gz and source packages has a readme file. They often explains if you need to do something specific to compile the package

---

### Post by Brightbelt on 2008-07-11
Thanks Hymn on the rm code - I'll run that.

But I do have a question: Is running build-essential a generic command or do I run it in the specific folder directory of what I am installing? 

In other words, can I run it from a simple $ directory or must I run it from the following specific directory like so?  
```
cd Desktop/qjackctl-0.3.3$ sudo apt-get install build-essential
```

And do I run it first before anything else or second, after the ./configure? 

Sorry to be so inquisitive, but you can't assume anything in Linux. It has to be exact, which I've found out the hard way.

Many Thanks for all your help and Aktiwers, just so you know, refer to number 1) on my top post. I've read the 'Install' file for all these tar packages. 

Thanks, Frank B.

---

### Post by Bachstelze on 2008-07-11
> **Brightbelt said:**
> 
But I do have a question: Is running build-essential a generic command or do I run it in the specific folder directory of what I am installing?

build-essential is just a package that will install all the tools needed for compiling for you, so you don't have to go through the hassle of installing gcc, cpp, libc6-dev and many other packages yourself. You just need to do it once, then you can forget about it... until you reinstall your system ;)

---

### Post by Brightbelt on 2008-07-12
Many Thanks.... :)

---

