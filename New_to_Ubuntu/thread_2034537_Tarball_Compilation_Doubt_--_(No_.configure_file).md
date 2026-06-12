---
title: "Tarball Compilation Doubt -- (No .configure file)"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by Farvez Afridi on 2012-07-28
Hey There All :).

I'm a user of ubuntu for a couple of months and i'm loving it a lot; Certainly Ubuntu is one of the best operating systems out there.

But recently I've experienced a problem which is Bugging me A LOT, I.E To Compile a software from source (Installing from tar.gz & tar.bz2).

Most of the time it works with the following processes:

```

tar -xjvf <file>.tar.gz
cd <program name>
./configure
make
sudo make install

```

In my case i'm trying to install Thunderbird Beta and the first two steps works, then I type ./configure it says > bash: ./configure: No such file or directory
I'm so tired of this, Help really needed please!

---

### Post by Kelvari on 2012-07-28
Have you tried running ```
ls -lR
```to see if the configure file might be - for some reason - in another directory, or if it contains an automatic installer script?

---

### Post by jerome1232 on 2012-07-28
> **Farvez Afridi said:**
> Hey There All :).

I'm a user of ubuntu for a couple of months and i'm loving it a lot; Certainly Ubuntu is one of the best operating systems out there.

But recently I've experienced a problem which is Bugging me A LOT, I.E To Compile a software from source (Installing from tar.gz & tar.bz2).

Most of the time it works with the following processes:

[LIST=1]
[*]tar -xjvf <file>.tar.gz
[*]cd <program name>
[*]./configure
[*]make
[*]sudo make install
[/LIST]
In my case i'm trying to install Thunderbird Beta and the first two steps works, then I type ./configure it says I'm so tired of this, Help really needed please!

Most tarbells that come from mozilla are **pre-compiled binaries**, meaning it's the program itself, you simply run the executable in there. So run the executable file in there, use your file browser for ease of use if you want.

---

### Post by Farvez Afridi on 2012-07-30
> Most tarbells that come from mozilla are pre-compiled binaries, meaning it's the program itself, you simply run the executable in there. So run the executable file in there, use your file browser for ease of use if you want
So, What is the extension of the executable file? (E.G - .exe in Windows).

---

### Post by Farvez Afridi on 2012-07-30
> **Kelvari said:**
> Have you tried running ```
ls -lR
```to see if the configure file might be - for some reason - in another directory, or if it contains an automatic installer script?

Exactly I have a couple of other tarballs like that, I.E the Configure file is in other directory of the folder.
Would you post the output of "ls - LR"?

---

### Post by c2tarun on 2012-07-30
no, its not like .exe in Ubuntu. Try running ls on terminal and if there'll any executable it will be displayed in green or pink color. But it might be possible that it will not be executable till now. If you didn't find anything in green, try posting the output of ls -l

---

### Post by gshreya3 on 2013-04-16
I am new to linux especially in installation of packages. Please send me information/weblink about tarball compilation. 
Specifically I want to know about: 
After the steps
./configure
make
make install
where all the files related to package goes. Is it there inside the current directory.
Then what about binaries?
 Due to compilation whether the Global PATH is changed?
Please help me on these lines.

---

### Post by Paqman on 2013-04-16
> **gshreya3 said:**
> I am new to linux especially in installation of packages. Please send me information/weblink about tarball compilation. 


Generally there's no need to ever compile from source, and if using a distro that has a package manager with precompiled packages (such as Ubuntu) doing so is in fact undesirable and can lead to problems.

If you're new to Linux I would suggest getting all your software from the official repositories (look in Ubuntu Software Centre), or Ubuntu-compatible sources such as PPAs or .deb files.

---

### Post by Impavidus on 2013-04-16
> **gshreya3 said:**
> I am new to linux especially in installation of packages. Please send me information/weblink about tarball compilation. 
Specifically I want to know about: 
After the steps
./configure
make
make install
where all the files related to package goes. Is it there inside the current directory.
Then what about binaries?
 Due to compilation whether the Global PATH is changed?
Please help me on these lines.

As a direct answer to your questions: if the tarball contains well-behaved scripts everything is installed in /usr/local and it doesn't change your PATH. You may be able to choose were it installs. If it's not well-behaved you never know. The configure, make, make install may not even work, or it may work and ruin your system if you're not careful. So it's best to try and stay with the official repositories

---

