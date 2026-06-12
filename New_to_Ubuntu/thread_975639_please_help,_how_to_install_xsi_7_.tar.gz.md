---
title: "please help, how to install xsi 7 .tar.gz?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by enri2 on 2008-11-08
the file is in .tar.gz file, so i extracted it and there is a setup file .what do i do now?
i searched google but nothing was helping.

---

### Post by houbysoft.xf.cz on 2008-11-08
Generally you would need to launch the program using
```

./nameofprogram

```
in terminal. However, this varies from program to program. Could you post what program are you trying to execute?
Also, it may be in the repositories, try to install it using
```

sudo apt-get install name_of_program

``` in terminal.

---

### Post by taurus on 2008-11-08
Most of the time, you would run these commands to build or install something from source.

```
./configure
make
sudo make install 
-or-
sudo checkinstall
```
However, that is not always the case.  So, either tell us what you plan to install (name of the program) or where you've downloaded the file.  See if there is either README or install.txt after you unpack it.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by Cannaregio on 2008-11-08
copy your target to a new folder
change directory to that folder
```
tar -xzf yourtarget
```
list here ALL the files you will obtain, please

---

### Post by Paqman on 2008-11-08
> **enri2 said:**
> the file is in .tar.gz file

What exactly are you trying to install? Have you checked all the repos? Can you find a .deb?

---

### Post by phidia on 2008-11-08
There should be a README file in there too.
There is a general method to install from source and you will need to have the build-essential package installed. So open the package manager or use the terminal "sudo apt-get install build-essential" that will ask for the install cd btw.

The site [here]("http://www.psychocats.net/ubuntu/installingsoftware") provides the details on the type of install you are asking about-see the last resorts section.

---

### Post by adult swim on 2008-11-08
with taurus' advice make sure you change directories to the location that you extracted the tarball to. 
ie 
```
cd /path/to/folder
```
EDIT: i was way too slow on that one

---

### Post by DrMega on 2008-11-08
I'm surprised nobody has mention this excellent website, that gives tons of useful info:

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

---

### Post by enri2 on 2008-11-08
im trying to install xsi 7

---

### Post by houbysoft.xf.cz on 2008-11-08
EDIT: oops, too slow.

The most helpful thing would be if you post from where you downloaded the .tar.gz, and what's the name of the program.

---

### Post by enri2 on 2008-11-08
i had run the setup of xsi 6 like 3 months ago, but i don't remember how i did it(i thik it was some thing like "run setup"or "open setup" i don't remember :(

---

### Post by houbysoft.xf.cz on 2008-11-08
> **enri2 said:**
> im trying to install xsi 7

OK, could you now post the exact location from where you downloaded it?

---

### Post by Cannaregio on 2008-11-08
Again:

copy your target to a new folder
change directory to that folder

```
tar -xzf yourtarget
```

list here ALL the files you will obtain, please

---

### Post by enri2 on 2008-11-08
_setup
libstdc++.so
libgcc_s.so.1
setup
and some tar.bz2 files

---

### Post by houbysoft.xf.cz on 2008-11-08
Then try to run setup. Open a terminal, cd to the dir where you have the extracted files (ex.: if they are on your desktop in folder xy, type "cd ~/Desktop/xy), and then type
```

./setup

```.

---

### Post by enri2 on 2008-11-08
> **houbysoft.xf.cz said:**
> Then try to run setup. Open a terminal, cd to the dir where you have the extracted files (ex.: if they are on your desktop in folder xy, type "cd ~/Desktop/xy), and then type
```

./setup

```.
i get this
Error: you need to be root to run this program

---

### Post by oldos2er on 2008-11-08
> **enri2 said:**
> i get this
Error: you need to be root to run this program

 Run "sudo ./setup"

---

### Post by adult swim on 2008-11-08
sudo ./setup

---

### Post by houbysoft.xf.cz on 2008-11-08
Yes, so run ```

sudo ./setup

```
It will ask you for your password, just enter it (you will see no output, that's ok) and hit enter.

---

