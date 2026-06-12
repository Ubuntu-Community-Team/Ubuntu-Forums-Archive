---
title: "Correct directory for USB-&gt;serial device drivers"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by Porcine Aviator on 2012-12-26
Hello all:

I recently purchased an IO Gear GUC 232A USB to serial (RS 232) converter. I downloaded the device driver files off the IOGear website. To which directory should I move the files? I am guessing dev/usb, but I'm not sure if I need to go any further, or if I need to do a mkdir to create a special new directory within dev/usb. Also, when I perform the Make Install, should I be in this same directory, or does it not matter? Unfortunately, reading other posts/ the readme file hasn't cleared this up.

By the way, I'm using 12.04 if that is germane to the discussion.

---

### Post by sandyd on 2012-12-26
> **Porcine Aviator said:**
> Hello all:

I recently purchased an IO Gear GUC 232A USB to serial (RS 232) converter. I downloaded the device driver files off the IOGear website. To which directory should I move the files? I am guessing dev/usb, but I'm not sure if I need to go any further, or if I need to do a mkdir to create a special new directory within dev/usb. Also, when I perform the Make Install, should I be in this same directory, or does it not matter? Unfortunately, reading other posts/ the readme file hasn't cleared this up.

By the way, I'm using 12.04 if that is germane to the discussion.

Can you post the link to the actual download?

Thanks!

---

### Post by bodhi.zazen on 2012-12-26
And to the how to you are using.

If you are compiling from source you usually ...

```
./configure
make
sudo make install
```

The makefile has all the specifications.

---

### Post by Porcine Aviator on 2012-12-26
Sandyd:

The drivers can be found at 

[http://www.iogear.com/support/dm/driver/GUC232A#display](http://www.iogear.com/support/dm/driver/GUC232A#display)

The "Red Hat" drivers are all basically the same, they're actually drivers that work with the same chip used in the IOGear product.

Bodhi:

Does it matter which directory I'm in? Also, how does ./configure "know" which make utility is going to run? Does it just run the one in the working directory?

Thanks to both of you for your prompt responses.

---

### Post by audiomick on 2012-12-26
Just a couple of things in case it take bohdi a while to get  back.

You don't have to "put the driver" anywhere yourself. The install process will take care of that, as far as I know.

You don't have to create a special directory for the drivers. The install process will take care of that. You do have to run the commands to invoke the install process from the directory that the file you are applying the commands to is in.

Regarding this
> Also, how does ./configure "know" which make utility is going to run? Does it just run the one in the working directory?


I haven't ever used ./configure, so I wont try to say too much. Suffice to say that "make" is a specific command. It invokes a specific utility. You can read about that by doing
```
man make
```
in a terminal. You can use man to find out about any command.
```
man command
```

Hope that helps you a bit.

---

### Post by bodhi.zazen on 2012-12-27
> **Porcine Aviator said:**
> Sandyd:

The drivers can be found at 

[http://www.iogear.com/support/dm/driver/GUC232A#display](http://www.iogear.com/support/dm/driver/GUC232A#display)

The "Red Hat" drivers are all basically the same, they're actually drivers that work with the same chip used in the IOGear product.

Bodhi:

Does it matter which directory I'm in? Also, how does ./configure "know" which make utility is going to run? Does it just run the one in the working directory?

Thanks to both of you for your prompt responses.

Those drivers are very very old, they are for a 2.4 kernel.

If you extract the archive, it contains a directory "GUC232A"

Within that directory are sub directories for red hat 7, 8, and 9

Within the sub directories is a ReadMe.txt

> To install driver -
        make inst (The Makefile will check the module and compile and link it automatically. It will also remove
                   the loaded USB-Serial driver)

To uninstall driver -
        make uninst

To uninstall all drivers (including base driver) -
        make uninst_all

To remove module (*.o) files -
        make clean

You would run those commands with sudo.

```
cd ~/GUC232A/Redhat9/

sudo make inst
```

You can also read the makefile

A nice tutorial on makefiles is here:

[http://web.mit.edu/gnu/doc/html/make_2.html](http://web.mit.edu/gnu/doc/html/make_2.html)

---

### Post by Porcine Aviator on 2012-12-27
All: thanks for your replies.
 
Bodhi: so, the directory to move the downloaded files is /usr/<username>/ , or /usr/<username>/home , or /dev/usb/ , or is it from the root?
 
Yes, I am well aware that the files are WAY old. If you research this "genre" of devices, you find that someone, somewhere along the way made some device driver files that fit a particular chip they use in these things and no one has touched it since. It was not originally made for Red Hat, really it was for generic linux.
 
Finally, I'll ask again: how does the Make utility know which set of files to compile? There does not seem to be any specifier...is it just that the make utility only works on .c files in the working directory? Furthermore, how does ./configure fit into the picture...what exactly is it configuring, and what is specifying this configuration (I assume there is some file somewhere)?

---

### Post by steeldriver on 2012-12-27
By default, 'make' looks for a file called 'Makefile' (or 'makefile') in the current directory and reads **rules **from it about what to do

By convention there's one make **target **to build stuff and another to install stuff - and again by convention the first of those targets is set as the default - i.e. when you type 

```
make
```without any arguments it finds the default target and performs the rule(s) necessary to make that (usually building the target application / libraries, in the current directory where they can't break the system if something goes wrong). Typically you check for any error messages and if all seems to have gone right you can then 

```
make install
```which performs the additional step of installing things where the system and/or dependent tools expect to find them  - 'sudo' is usually needed for that step in order to write to system locations (occasionally it isn't - for example if the default install location is the user's home, or if it's /usr/local and the user is a member of a group that can write to /usr/local)

./configure is a step ABOVE make and is used to check that you have all the prerequisite components installed and find the appropriate library paths and so on

Be aware that if the source you are trying to compile is too old, it may simply not be possible for ./configure to generate a working build on your system (because of out-of-date library dependencies and/or header files)

Hope this helps

---

### Post by Porcine Aviator on 2012-12-27
Steeldriver:

Thanks, muy excelente post. Yes, I've just been doing a little bit of reading on configure files and the make utility.

There is no configure script file in the install package...so I couldn't use that to check for prereqs. I tried using make, but the makefile apparently referenced stuff in /usr/src/linux2.4/....
which of course does not exist on such a "modern" version of linux. Interestingly enough, the only things I see in the usr/src directory are header files...and some weird 'bcmwl-5.100.82.38+bdcom' directory. So, the makefile/make utility in this instance is also kaput, at least in unmodified form...and I'm not sure how to modify this thing without breaking something important.

So....um, what do I do now folks? I can of course compile this thing manually with gcc but that seems pretty daunting not knowing what to look for in terms of header files and where I need to send the output object code. Any thoughts anyone?

---

### Post by bodhi.zazen on 2012-12-27
You need to download the linux (kernel) source code

[http://www.kernel.org/](http://www.kernel.org/)

Or you can download the ubuntu kernel source code if you wish

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I would then simply use a link

```
sudo ln -s /usr/src/linux2.4/ /your/source/code
```

If it is a very simple driver it may compile, but it may not.

See also

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by Porcine Aviator on 2012-12-27
Bodhi:

Let me try to understand what you're telling me here. Are you suggesting that I recompile an all new kernel? Or are you suggesting that I just pull in a couple of header files?

If you are suggesting the former...how do I keep all of the features of 12.04 Ubuntu intact while using this hybrid of new and old Linux builds? Or, are you suggesting that I just make a new "old school build"...so just use Gparted to create a new partition for the "old school" Linux build that is separate from the 12.04 Ubuntu build I have now?

If you are suggesting the latter...how do I know that the new object code will "play nicely" with the existing kernel code if the header files contain environment variables, etc. that are likely different?

Thanks.

---

### Post by bodhi.zazen on 2012-12-27
> **Porcine Aviator said:**
> Bodhi:

Let me try to understand what you're telling me here. Are you suggesting that I recompile an all new kernel? Or are you suggesting that I just pull in a couple of header files?

No, not compile a kernel, but you need the source code (headers) to compile your modules, which is why the make file is looking for "/usr/src/linux2.4" , the default location of kernel source code in many distros, including RH.

> If you are suggesting the former...how do I keep all of the features of 12.04 Ubuntu intact while using this hybrid of new and old Linux builds? Or, are you suggesting that I just make a new "old school build"...so just use Gparted to create a new partition for the "old school" Linux build that is separate from the 12.04 Ubuntu build I have now?

If you are suggesting the latter...how do I know that the new object code will "play nicely" with the existing kernel code if the header files contain environment variables, etc. that are likely different?

Thanks.

Basically you are compiling a kernel module. You need the linux source code to do so.

You should, IMO, keep the source code for your USB device in your home directory. I usually keep it in ~/src, up to you,  in theory you can keep it wherever you like.

I also gave you 2 pieces of information.

1. The "simple" commands you need to run to compile your module. You need to download the linux source code and necessary tools.

```
sudo apt-get install build-essential
```

2. Links to the more complex information about compiling and make files. You can read as much or little as you wish. If you have a specific question, ask, but otherwise I would be re-typing the links I gave you here.

Sorry there is a bit of a learning curve to compiling, but the links should get you started.

Also the source code you are using is very very old, who knows if it will even compile, let alone play nice with a modern kernel.

What is there to keep separate ? You have 2 source codes, the kernel and your USB module. They are in separate directories, does not matter if they are on separate partitions or not. You will compile and install the modules with the makefile

```
sudo make inst
```

You will remove them with the makefile

```
sudo make uninstall
```

The makefile tracks everything and you can read it if you like.

---

