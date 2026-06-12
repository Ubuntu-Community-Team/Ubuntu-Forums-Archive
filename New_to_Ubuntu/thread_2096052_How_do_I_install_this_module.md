---
title: "How do I install this module?"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by Ryuichi1 on 2012-12-18
Okay okay, I'm  new to ubuntu and I have drawing tablet, Hanvon, I found the module for  it but I don't know how to install it. I've searched hours online for  this and didn't have any luck.
 Below is the link to a screenshot of the content of the tarball and the readme file.

[http://screencloud.net/v/sJ2](http://screencloud.net/v/sJ2)

Wat do? D:

P.S I accidentally posted this thread on the "Hardware" section. **removed - Celene** 
asl;jnsal I'm a dumbass, sorry.

---

### Post by sandyd on 2012-12-18
The files you show in the archive is the source code for the kernel module (driver) itself. We will compile it before installing.

Firstly, I am assuming the "hanvon-20111102.tgz" file is in your "Downloads" folder.

Open a terminal (Click on the Unity dash on the top-left hand corner of the screen and type in 'terminal').

Then, enter this in.
```

cd ~/Downloads
#Create a clean folder to extract and compile the driver
mkdir -p hanvon_drivers/build
mv hanvon-20111102.tgz hanvon_drivers
cd hanvon_drivers
tar xvf hanvon-20111102.tgz
mv hanvon/* build
#Install gcc and other tools needed to build kernel module from source
sudo apt-get install build-essential
#type in password at this point, it will not show up
cd build
#Compile Module
make
#Insert module in kernel
sudo insmod ./hanvon.ko
```
It should (according to the readme at least) show up if you run
```

lsmod
```

btw, don't worry about it if you ever post in the wrong section. Just click on the "report abuse" button on the left hand side of the screen (for me, I see yours at the bottom left of your post), and ask for someone to move it :)

---

### Post by Ryuichi1 on 2012-12-18
> **sandyd said:**
> The files you show in the archive is the source code for the kernel module (driver) itself. We will compile it before installing.

Firstly, I am assuming the "hanvon-20111102.tgz" file is in your "Downloads" folder.

Open a terminal (Click on the Unity dash on the top-left hand corner of the screen and type in 'terminal').

Then, enter this in.
```

cd ~/Downloads
#Create a clean folder to extract and compile the driver
mkdir hanvon_drivers
mv hanvon-20111102.tgz hanvon_drivers
cd hanvon_drivers
tar xvf hanvon-20111102.tgz
#Install gcc and other tools needed to build kernel module from source
sudo apt-get install build-essential
#type in password at this point, it will not show up
#Compile Module
make
#Insert module in kernel
sudo insmod ./hanvon.ko
```
It should (according to the readme at least) show up if you run
```

lsmod
```

btw, don't worry about it if you ever post in the wrong section. Just click on the "report abuse" button on the left hand side of the screen (for me, I see yours at the bottom left of your post), and ask for someone to move it :)
[B]Thanks for replying, man. 
When I tell it to make it, it gives me this message tho:
```

"No targets specified and no makefile found.  Stop.[/B]"

vinizzz@ubuntu:~$ cd ~/Downloads
vinizzz@ubuntu:~/Downloads$ mkdir hanvon_drivers
mkdir: cannot create directory `hanvon_drivers': File exists
vinizzz@ubuntu:~/Downloads$ mv hanvon-20111102.tgz hanvon_drivers
mv: cannot stat `hanvon-20111102.tgz': No such file or directory
vinizzz@ubuntu:~/Downloads$ cd hanvon_drivers
vinizzz@ubuntu:~/Downloads/hanvon_drivers$ tar xvf hanvon-20111102.tgz
hanvon/
hanvon/hanvon.c
hanvon/README
hanvon/Makefile
vinizzz@ubuntu:~/Downloads/hanvon_drivers$ sudo apt-get install build-essential
[sudo] password for vinizzz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms libfaac0 libquicktime2 linux-headers-3.5.0-17 nvidia-settings
  python-xkit screen-resolution-extra
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.7 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libstdc++6-4.7-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.7-multilib gcc-4.7-doc libstdc++6-4.7-dbg
  libstdc++6-4.7-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++6-4.7-dev
0 upgraded, 8 newly installed, 0 to remove and 162 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
vinizzz@ubuntu:~/Downloads/hanvon_drivers$ make
make: *** No targets specified and no makefile found.  Stop.
vinizzz@ubuntu:~/Downloads/hanvon_drivers$
```

---

### Post by sandyd on 2012-12-18
> **Ryuichi1 said:**
> [B]Thanks for replying, man. 
When I tell it to make it, it gives me this message tho:

"No targets specified and no makefile found.  Stop.[/B]"

vinizzz@ubuntu:~$ cd ~/Downloads
vinizzz@ubuntu:~/Downloads$ mkdir hanvon_drivers
mkdir: cannot create directory `hanvon_drivers': File exists
vinizzz@ubuntu:~/Downloads$ mv hanvon-20111102.tgz hanvon_drivers
mv: cannot stat `hanvon-20111102.tgz': No such file or directory
vinizzz@ubuntu:~/Downloads$ cd hanvon_drivers
vinizzz@ubuntu:~/Downloads/hanvon_drivers$ tar xvf hanvon-20111102.tgz
hanvon/
hanvon/hanvon.c
hanvon/README
hanvon/Makefile
vinizzz@ubuntu:~/Downloads/hanvon_drivers$ sudo apt-get install build-essential
[sudo] password for vinizzz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms libfaac0 libquicktime2 linux-headers-3.5.0-17 nvidia-settings
  python-xkit screen-resolution-extra
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.7 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libstdc++6-4.7-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.7-multilib gcc-4.7-doc libstdc++6-4.7-dbg
  libstdc++6-4.7-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++6-4.7-dev
0 upgraded, 8 newly installed, 0 to remove and 162 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
vinizzz@ubuntu:~/Downloads/hanvon_drivers$ make
make: *** No targets specified and no makefile found.  Stop.
vinizzz@ubuntu:~/Downloads/hanvon_drivers$
run
```

sudo apt-get install build-essential
#type in password at this point, it will not show up
cd ~/Downloads/hanvon_drivers/hanvon
#Compile Module
make
#Insert module in kernel
sudo insmod ./hanvon.ko
```
instead (for some reason, the screenshot didn't show directory structure inside the tar...)

Also, make sure you don't have anything else installing via the software center/apt/synaptic

---

### Post by Ryuichi1 on 2012-12-18
**...Dx Why is it not working?**

vinizzz@ubuntu:~/Downloads/hanvon_drivers/hanvon$ make
make -C /lib/modules/3.5.0-19-generic/build M=/home/vinizzz/Downloads/hanvon_drivers/hanvon modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-19-generic'
  CC [M]  /home/vinizzz/Downloads/hanvon_drivers/hanvon/hanvon.o
/home/vinizzz/Downloads/hanvon_drivers/hanvon/hanvon.c: In function &#8216;hanvon_irq&#8217;:
/home/vinizzz/Downloads/hanvon_drivers/hanvon/hanvon.c:104:3: error: implicit declaration of function &#8216;err&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/vinizzz/Downloads/hanvon_drivers/hanvon/hanvon.o] Error 1
make[1]: *** [_module_/home/vinizzz/Downloads/hanvon_drivers/hanvon] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-19-generic'
make: *** [all] Error 2
vinizzz@ubuntu:~/Downloads/hanvon_drivers/hanvon$

---

### Post by sandyd on 2012-12-18
> **Ryuichi1 said:**
> **...Dx Why is it not working?**

vinizzz@ubuntu:~/Downloads/hanvon_drivers/hanvon$ make
make -C /lib/modules/3.5.0-19-generic/build M=/home/vinizzz/Downloads/hanvon_drivers/hanvon modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-19-generic'
  CC [M]  /home/vinizzz/Downloads/hanvon_drivers/hanvon/hanvon.o
/home/vinizzz/Downloads/hanvon_drivers/hanvon/hanvon.c: In function ‘hanvon_irq’:
/home/vinizzz/Downloads/hanvon_drivers/hanvon/hanvon.c:104:3: error: implicit declaration of function ‘err’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/vinizzz/Downloads/hanvon_drivers/hanvon/hanvon.o] Error 1
make[1]: *** [_module_/home/vinizzz/Downloads/hanvon_drivers/hanvon] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-19-generic'
make: *** [all] Error 2
vinizzz@ubuntu:~/Downloads/hanvon_drivers/hanvon$
something is wrong with the source code - but you can probably ignore that warning that it treated as an error.
What is the link to the download?

---

### Post by Ryuichi1 on 2012-12-18
Ignore it? How? 

Also, this. [http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/](http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/)

---

### Post by snowpine on 2012-12-18
Are you using the required 2.6 linux kernel? You can check with:

```
uname -a
```

If you have a newer ubuntu release then you probably have 3.x kernel.

---

### Post by Ryuichi1 on 2012-12-18
> **snowpine said:**
> Are you using the required 2.6 linux kernel? You can check with:

```
uname -a
```

If you have a newer ubuntu release then you probably have 3.x kernel.
vinizzz@ubuntu:~$ uname -a
Linux ubuntu 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

**So does that mean I need to get the 2.6 linux kernel? e_e If so, how?**

---

### Post by snowpine on 2012-12-18
I suggest you contact the manufacturer of your drawing tablet to obtain updated instructions for current Ubuntu releases. Or use the forum Search feature to see how other users have managed to get this tablet working. Good luck! :)

---

### Post by Favux on 2012-12-19
I had no trouble building the hanvon.ko but don't have an actual Hanvon tablet to test it on.  Others have not been so fortunate:  [http://ubuntuforums.org/showthread.php?t=1178978](http://ubuntuforums.org/showthread.php?t=1178978)

---

### Post by MZ250Supa5 on 2013-11-28
Followed these directions to install the latest hanvon-2111113.tgz module, and it works fine. However I'm having to go through the process from 'cd hanvon_drivers' every time I reboot the machine, which is a bit of a pain.  Anyone got any ideas how I make this change permanent?

---

### Post by Favux on 2013-11-28
Right, you don't need to do an insmod or modprobe each time if you copy the driver/module into an appropriate directory.  See:  [http://ubuntuforums.org/showthread.php?t=1178978&p=11242767&viewfull=1#post11242767](http://ubuntuforums.org/showthread.php?t=1178978&p=11242767&viewfull=1#post11242767)

---

### Post by MZ250Supa5 on 2013-11-28
Thanks for the reply Favux, but following those directions doesn't seem to work - though I will have another look when I'm less tired.

I get this:

ceridwen@ceridwen:~$ sudo cp hanvon.ko /lib/modules/'ceridwen -r'/kernel/drivers/input/tablet
[sudo] password for ceridwen: 
cp: cannot stat ‘hanvon.ko’: No such file or directory
ceridwen@ceridwen:~$ 


I'm a little stumped, as it must have 'hanvon.ko' as doing the insmod does give me tablet functionality.

---

### Post by Favux on 2013-11-29
Hi,

It's from using 'ceridwen -r' in the path.  Enter **uname -r** in a terminal and it will return the current kernel.  So that is a specific command asking the kernel for its name and doesn't mean yourname.  The backticks ` allow you to use **uname -r** in a path, the shell reads **`uname -r`** as the current kernel, with is part of the path.

---

### Post by MZ250Supa5 on 2013-11-29
I'm still getting "cannot stat &#8216;hanvon.ko&#8217;: No such file or directory" when entering this command string, though hanvon.ko must exist - I'm nor sure where I'm going wrong here. 
"

---

### Post by MZ250Supa5 on 2013-11-29
Duh!  Egg on face time - I didn't cd to the directory containing havnon.ko.

Thanks of your help Favux

This time things seem to have worked, but even if they haven't at least I know that I'm very close :)

I usually use a Wacom Bamboo, which when I first got one was a pain and a half to install, but is now virtually 'plug 'n' play' but wanted to try out this Hanvon tablet to see if it's worth going to all the trouble with -  and it is. It's not as capable on Linux as it is on Windows. (no handwriting recognition which is almost frigtheningly good on Windows) but it's certainly uo to the job in terms of functionality in Gimp etc.  I'd say that Wacom would be somewhat up against it if Hanvon natively supported Linux, which I'm sure is putting a lot of people off. I was certainly enthused enough by the fact that drivers existed to give it a go, though I was slightly intimidated, (unneccesarily) by the fact that the drivers needed compiling, the first time I've done anything like that.  At about half the cost of a similarly specced Wacom, the Hanvon is a bargain.

---

### Post by Favux on 2013-11-29
Good.  Glad you got it working.  :)

I wonder if pressure from competitors is why Wacom rebranded its Bamboo Pen and Touches to Intuos Pen and Touches and now calls the Intuos's Intuos Pro?  It would sure be nice if someone offered handwriting recognition in linux, I bet they would clean up.  Not that CellWriter isn't a good app.

---

### Post by MZ250Supa5 on 2013-11-30
It would be great if someone did handwriting recogniton in Linux. I have used cellwriter, and whilst I can see uses for it, it's not quite the same.  What astonished me more than anything when using the handwriting recogniton in Windows is that it worked with Libre Office - I had suspected that it might just have been with MS Office that it would have worked.

I'm not sure what persuaded Wacom to change the name of their entry level tablets, but on cost alone they are going to have a tough fight is even half the competiton is as good as the Hanvon.  I have a Wacom MTE 4450 K, which I bought second hand on ebay, as I don't like the look, or design of the more recent tablets.  I also managed to source a new, old stock Wacom Bamboo, so I have a 'spare', plus of course I now have the Hanvon.

---

### Post by MZ250Supa5 on 2014-01-18
Grrrr! recent kernel upgrade completely removed Hanvon tablet functionality, and repeating the directions no longer works - it compiles fine, installs fine, and works, but I know when I reboot I'm going to have to do it all again because when I issue the 'sudo cp hanvon.kp /lib/modules/'uname -r'/kernel/drivers/input/tablet' command I get this as a response from the terminal:

'cp: cannot create regular file &#8216;/lib/modules/uname -r/kernel/drivers/input/tablet&#8217;: No such file or directory'

Why is it that every kernel upgrade seems to tak out some basic functionality of the operatring system - surely it can be made to detect what is already there and what dependencies are required, it seems 'intelligent' enough to detect the lack of required dependencies when attempting to manually install porgrams that need unsatisfied dependencies so why htis palaver every time?  It used to happen a lot with Nvidia drivers in 10.04.

---

### Post by MZ250Supa5 on 2014-01-18
Eggo on face again - it'd been a while since I'd last had to go through the palaver instlaling this driver, and I'd forgotten that where the command uses `uname -r` that they aren't single quotation marks... duh!

---

