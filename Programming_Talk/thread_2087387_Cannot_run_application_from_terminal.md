---
title: "Cannot run application from terminal"
date: 2012-11-23
forum: Programming Talk
---

### Post by Bart_D on 2012-11-23
Hello,

I am trying to run an application from the terminal in Ubuntu but can't get it going. I am trying to run cgview: cgview is a particle trajectory and geometry display program for the EGS code. Combinatorial geometry , cylinder-slab geometry and slab geometry can be displayed with it.

I am trying to run it after I installed it from page 15 here:
[http://rcwww.kek.jp/research/egs/kek/cgview/cgview-2.4.0/manualE.pdf](http://rcwww.kek.jp/research/egs/kek/cgview/cgview-2.4.0/manualE.pdf)

Here is the error I am getting:

```
buser@ubuntu:/usr/local/cgview$ ls
cgview  cgview-2.4.0-eng.tar.gz  doc  help  libborqt-6.9.0-qt2.3.so  sample
buser@ubuntu:/usr/local/cgview$ ./cgview &
[1] 3503
buser@ubuntu:/usr/local/cgview$ bash: ./cgview: No such file or directory

[1]+  Exit 127                ./cgview
```

Is there any reason why this error is occuring?

---

### Post by Bachstelze on 2012-11-23
The binary is 32-bit, I will hazard a guess that you have a 64-bit system. Install [font=monospace]gcc-multilib[/font].

---

### Post by Zugzwang on 2012-11-23
@OP: Can you copy&paste the output of "ls -la" here? Either cgview is not an executable file, or the executable flag is just missing.

---

### Post by Bachstelze on 2012-11-24
> **Zugzwang said:**
> @OP: Can you copy&paste the output of "ls -la" here? Either cgview is not an executable file, or the executable flag is just missing.

The file is there, and it is executable. If the file is not executable, you get permission denied, not no such file.

---

### Post by spjackson on 2012-11-24
I got this working on 64-bit Precise as follows:
```

$ tar xzf ../cgview-2.4.0-eng.tar.gz
$ ./cgview
bash: ./cgview: No such file or directory
$ sudo apt-get install ia32-libs
$ ./cgview 
./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings
$ LD_LIBRARY_PATH=. ./cgview
./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings
$ cd /usr/lib/i386-linux-gnu
$ sudo ln -s libjpeg.so.8 libjpeg.so.62
$ cd ~/Downloads/cgview
$ LD_LIBRARY_PATH=. ./cgview 

```

---

### Post by Bart_D on 2012-11-24
I am trying this right now.....

will post back shortly....

> **Bachstelze said:**
> The file is there, and it is executable. If the file is not executable, you get permission denied, not no such file.

Yes, you're right. The file is definitely there.

---

### Post by Bart_D on 2012-11-24
> **Bachstelze said:**
> The binary is 32-bit, I will hazard a guess that you have a 64-bit system. Install [font=monospace]gcc-multilib[/font].

Here is my output after installing [font=monospace]gcc-multilib[/font]:

```
buser@ubuntu:/usr/local/cgview$ ./cgview &
[1] 3732
buser@ubuntu:/usr/local/cgview$ ./cgview: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

[1]+  Exit 127                ./cgview

```
--------------------------------X--------------------------

I entered:
```
sudo apt-get install ia32-libs
```

Here is my output after entering [font=monospace]cd /usr/lib/i386-linux-gnu[/font]

```
buser@ubuntu:/usr/lib$ cd /usr/lib/i386-linux-gnu
bash: cd: /usr/lib/i386-linux-gnu: No such file or directory
```

I am using a 64-bit system. Could this be affecting it?

---

### Post by Bart_D on 2012-11-24
> **spjackson said:**
> I got this working on 64-bit Precise as follows:
```

$ tar xzf ../cgview-2.4.0-eng.tar.gz
$ ./cgview
bash: ./cgview: No such file or directory
$ sudo apt-get install ia32-libs
$ ./cgview 
./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings
$ LD_LIBRARY_PATH=. ./cgview
./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings
$ cd /usr/lib/i386-linux-gnu
$ sudo ln -s libjpeg.so.8 libjpeg.so.62
$ cd ~/Downloads/cgview
$ LD_LIBRARY_PATH=. ./cgview 

```

In which folder was the .tar.gz file downloaded - was it the Downloads folder? Was a folder created in /usr/local (as the user manual indicated), or did you just use the Downloads folder?

---

### Post by spjackson on 2012-11-24
> **Bart_D said:**
> Here is my output after installing [font=monospace]gcc-multilib[/font]:

```
buser@ubuntu:/usr/local/cgview$ ./cgview &
[1] 3732
buser@ubuntu:/usr/local/cgview$ ./cgview: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

[1]+  Exit 127                ./cgview

```

When I installed ia32-libs I got, amongst other files, /usr/lib/i386-linux-gnu/mesa/libGL.so.1

> 
Here is my output after entering [font=monospace]cd /usr/lib/i386-linux-gnu[/font]

```
buser@ubuntu:/usr/lib$ cd /usr/lib/i386-linux-gnu
bash: cd: /usr/lib/i386-linux-gnu: No such file or directory
```

I am using a 64-bit system. Could this be affecting it?

I did my install on 64-bit. If you install ia32-libs you should get this directory. Maybe it's different on Quantal, but it doesn't look like it, for example: [http://packages.ubuntu.com/quantal/i386/libc6/filelist]("http://packages.ubuntu.com/quantal/i386/libc6/filelist")

---

### Post by spjackson on 2012-11-24
> **Bart_D said:**
> In which folder was the .tar.gz file downloaded - was it the Downloads folder? Was a folder created in /usr/local (as the user manual indicated), or did you just use the Downloads folder?
I downloaded the tarball to ~/Downloads and unpacked it in ~/Downloads/cgview. I didn't see any point in using /usr/local. Note that I used LD_LIBRARY_PATH for the included .so; I didn't try to work out the right i386 directory to use on 64-bit. I am always reluctant to put stuff that isn't under package control in /usr/... although I did create the symlink to satisfy the dependency on libjpeg.so.62

---

### Post by Bart_D on 2012-11-24
Sorry for the questions....I am not incredibly comfortable with the terminal.

> **spjackson said:**
> I downloaded the tarball to ~/Downloads and unpacked it in ~/Downloads/cgview......I did create the symlink to satisfy the dependency on libjpeg.so.62

The User Manual indicates:

```
Copy and Make Symbolic link in /usr/lib.
[ /usr/local/cgview ]# cp ./libborqt-6.9.0-qt2.3.so /usr/lib
[ /usr/local/cgview ]# cd /usr/lib
[ /usr/lib ]# ln -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so
```

So you did:

```

[ /Downloads/cgview ]# cp ./libborqt-6.9.0-qt2.3.so /usr/lib
[ /Downloads/cgview ]# cd /usr/lib
[ /Downloads/lib ]# ln -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so
```

Is this correct?

---

### Post by spjackson on 2012-11-26
No, I didn't do that. As I said, I didn't put anything in /usr/lib/... except for that libjpeg link. Step 3 in the manual indicates that you can either use step 4 or 5 & 6. I chose 5 & 6.

---

### Post by Bart_D on 2012-11-26
Here is what I have tried on Ubuntu 12.10 64-bit:

Manually created a new folder in Downloads called cgview and put the *.tar.gz file there. Then:

```

$ sudo apt-get install ia32-libs
$ cd Downloads
$ cd cgview
$ tar zxvf cgview-2.4.0-eng.tar.gz
$ ./cgview 
./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings
$ LD_LIBRARY_PATH=. ./cgview
./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings
$ cd /usr/lib/i386-linux-gnu
$ sudo ln -s libjpeg.so.8 libjpeg.so.62
$ cd ~/Downloads/cgview
$ LD_LIBRARY_PATH=. ./cgview
./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings

```

Am I missing something?

> **spjackson said:**
> ...Note that I used LD_LIBRARY_PATH for the included .so; I didn't try to work out the right i386 directory to use on 64-bit......I did create the symlink to satisfy the dependency on libjpeg.so.62

Could you post the commands for these 2 steps?

---

### Post by spjackson on 2012-11-27
> **Bart_D said:**
> Here is what I have tried on Ubuntu 12.10 64-bit:

Manually created a new folder in Downloads called cgview and put the *.tar.gz file there. Then:

```

$ sudo apt-get install ia32-libs
$ cd Downloads
$ cd cgview
$ tar zxvf cgview-2.4.0-eng.tar.gz
$ ./cgview 
./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings
$ LD_LIBRARY_PATH=. ./cgview
./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings
$ cd /usr/lib/i386-linux-gnu
$ sudo ln -s libjpeg.so.8 libjpeg.so.62
$ cd ~/Downloads/cgview
$ LD_LIBRARY_PATH=. ./cgview
./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings

```

Am I missing something?



Could you post the commands for these 2 steps?

That error is precisely the one you get if libborqt-6.9-qt2.3.so cannot be loaded for some reason. So what's the reason?

Step 5 in the manual is:
```

ln -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so

```
Did you do this in the directory ~/Downloads/cgview ?

Step 6 in the manual is:
```

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:./

```
For this I just did:
```

LD_LIBRARY_PATH=. ./cgview

```
which you are doing, and this is effectively the same.

If you created the link libborqt-6.9-qt2.3.so and are setting LD_LIBRARY_PATH correctly, then you need to investigate why this library isn't loading.
```

ldd libborqt-6.9-qt2.3.so

```
Do the above. Are any libraries shown as Not Found? Maybe libjpeg.so.8 isn't installed by ia32-libs on 12.10.

---

### Post by Bart_D on 2012-11-27
Ok, so I now did steps 5 and 6:
STEP 5: in the directory ~/Downloads/cgview:
```

ln -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so

```

STEP 6: in the directory ~/Downloads/cgview:
```

LD_LIBRARY_PATH=. ./cgview

```

But I got this:
```
X Error: GLXBadContextTag 176
  Major opcode:  154
X Error: GLXBadContextTag 176
  Major opcode:  154
X Error: GLXBadContextTag 176
  Major opcode:  154
X Error: GLXBadContextTag 176
  Major opcode:  154
Runtime error 231 at 08069B5D
Segmentation fault (core dumped)
$ ~/Downloads/cgview$ 
```

Here is the output for:
```
$ ldd libborqt-6.9-qt2.3.so
linux-gate.so.1 =>  (0xf777a000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf701c000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf6ee6000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf6eb9000)
	libSM.so.6 => /usr/lib/i386-linux-gnu/libSM.so.6 (0xf6eb0000)
	libICE.so.6 => /usr/lib/i386-linux-gnu/libICE.so.6 (0xf6e96000)
	libjpeg.so.62 => /usr/lib/i386-linux-gnu/libjpeg.so.62 (0xf6e3f000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf6c95000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf6c72000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf6c6d000)
	/lib/ld-linux.so.2 (0xf777b000)
	libuuid.so.1 => /lib/i386-linux-gnu/libuuid.so.1 (0xf6c67000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf6c63000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf6c5c000)
$ ~/Downloads/cgview$ 
```

I searched for libjpeg.so.8 in synaptic, but the search found 0 items.

I searched on Google and found this:
[http://pkgs.org/ubuntu-12.10/ubuntu-main-amd64/libjpeg-turbo8_1.2.1-0ubuntu2_amd64.deb.html](http://pkgs.org/ubuntu-12.10/ubuntu-main-amd64/libjpeg-turbo8_1.2.1-0ubuntu2_amd64.deb.html)

Do you think this (missing) could be the problem? Is there some other way I could check to see if it is installed?

---

### Post by dwhitney67 on 2012-11-27
> **spjackson said:**
> 
Step 6 in the manual is:
```

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:./

```
For this I just did:
```

LD_LIBRARY_PATH=. ./cgview

```
which you are doing, and this is effectively the same.


No it is not.

Perhaps you meant:
```

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:~/Downloads/cgview

```
------

EDIT:  Never mind; initially I did not realize that your were merely pointing out a short-cut to running the CGview application.

---

### Post by spjackson on 2012-11-27
> **Bart_D said:**
> Ok, so I now did steps 5 and 6:
STEP 5: in the directory ~/Downloads/cgview:
```

ln -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so

```

STEP 6: in the directory ~/Downloads/cgview:
```

LD_LIBRARY_PATH=. ./cgview

```

But I got this:
```
X Error: GLXBadContextTag 176
  Major opcode:  154
X Error: GLXBadContextTag 176
  Major opcode:  154
X Error: GLXBadContextTag 176
  Major opcode:  154
X Error: GLXBadContextTag 176
  Major opcode:  154
Runtime error 231 at 08069B5D
Segmentation fault (core dumped)
$ ~/Downloads/cgview$ 
```

Here is the output for:
```
$ ldd libborqt-6.9-qt2.3.so
linux-gate.so.1 =>  (0xf777a000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf701c000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf6ee6000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf6eb9000)
	libSM.so.6 => /usr/lib/i386-linux-gnu/libSM.so.6 (0xf6eb0000)
	libICE.so.6 => /usr/lib/i386-linux-gnu/libICE.so.6 (0xf6e96000)
	libjpeg.so.62 => /usr/lib/i386-linux-gnu/libjpeg.so.62 (0xf6e3f000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf6c95000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf6c72000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf6c6d000)
	/lib/ld-linux.so.2 (0xf777b000)
	libuuid.so.1 => /lib/i386-linux-gnu/libuuid.so.1 (0xf6c67000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf6c63000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf6c5c000)
$ ~/Downloads/cgview$ 
```

I searched for libjpeg.so.8 in synaptic, but the search found 0 items.

I searched on Google and found this:
[http://pkgs.org/ubuntu-12.10/ubuntu-main-amd64/libjpeg-turbo8_1.2.1-0ubuntu2_amd64.deb.html](http://pkgs.org/ubuntu-12.10/ubuntu-main-amd64/libjpeg-turbo8_1.2.1-0ubuntu2_amd64.deb.html)

Do you think this (missing) could be the problem? Is there some other way I could check to see if it is installed?
No, I don't think this is the problem at all. This line:
```

libjpeg.so.62 => /usr/lib/i386-linux-gnu/libjpeg.so.62 (0xf6e3f000)

```
shows that the dependency is resolved, so the symlink you made for libjpeg must have been successful.

It is now loading the libraries but crashing in X. I don't get that on 12.04. I don't think I can help with this problem I'm afraid.

---

### Post by Bart_D on 2012-11-27
I've got onboard Intel video.

What graphics card, and driver, are you using with Precise 64-bit?

---

### Post by dwhitney67 on 2012-11-27
1. Download CGview into ~:
```

$ cd 

$ wget http://rcwww.kek.jp/research/egs/kek/cgview/cgview-2.4.0/cgview-2.4.0-eng.tar.gz

```

2. Create ~/cgview directory:
```

$ mkdir ~/cgview

```

3. Unpack compressed tar-ball using within ~/cgview:
```

$ cd ~/cgview

$ tar xzvf ~/cgview-2.4.0-eng.tar.gz

```

4.  Install 32-bit libjpeg:
```

sudo apt-get install libjpeg62:i386

```

5.  Setup libborqt-6.9-qt2.3.so (per PDF instructions for CGview):
```

ln -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so

```

6.  Run CGview
```

LD_LIBRARY_PATH=. ./cgview

```

Voilà.

---

### Post by Bart_D on 2012-11-27
> **dwhitney67 said:**
> 
.
.
.

Voilà.

Thanks.

What graphics card, and driver, are you using?

---

### Post by dwhitney67 on 2012-11-27
> **Bart_D said:**
> Thanks.

What graphics card, and driver, are you using?

It shouldn't matter, but I believe I'm using a generic VESA driver as offered by VMPlayer.

In other words, I installed the CGview application on my laptop, which has an Intel 915 chipset, yet I'm accessing it remotely on my Fedora 16 Virtual Machine using SSH.

---

### Post by Bart_D on 2012-11-27
So presumably you downloaded it into home/cgview. Correct?

Was that on 12.10?

Does the order of your steps 4 and 5 make a difference? I mean, I have already run step 5, but not step 4.

---

### Post by dwhitney67 on 2012-11-27
> **Bart_D said:**
> So presumably you downloaded it into home/cgview. Correct?

Was that on 12.10?

Does the order of your steps 4 and 5 make a difference? I mean, I have already run step 5, but not step 4.

The installation took place within ~/cgview.  The tilde represent one's home directory; this is not the same as /home/cgview.  If you prefer, try using $(HOME)/cgview.  However Bash interprets the tilde to be one's home directory.

No, the ordering of Steps 4 and 5 don't make a difference.

As for the installation system, it's a Kubuntu 12.10 x86-64 system.

I'm accessing it remotely via a Fedora 16 x86-64 virtual machine that runs on a separate system.

---

### Post by Bart_D on 2012-11-27
Okay, so I wiped out my Ubuntu 12.10 and re-installed it, ran all updates and then ran through your 6 steps.

The last step gives me the following error:
```
duser@ubuntu:~/cgview$ LD_LIBRARY_PATH=. ./cgview
./cgview: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
duser@ubuntu:~/cgview$ ls
cgview  doc  help  libborqt-6.9.0-qt2.3.so  libborqt-6.9-qt2.3.so  sample
duser@ubuntu:~/cgview$ 
```

EDIT: It seems like the file cgview is not there, yet I can see it.

---

### Post by dwhitney67 on 2012-11-27
> **Bart_D said:**
> Okay, so I wiped out my Ubuntu 12.10 and re-installed it...

That was beyond the scope of my instructions, but whatever makes you happy.

> **Bart_D said:**
> 
The last step gives me the following error:
```
duser@ubuntu:~/cgview$ LD_LIBRARY_PATH=. ./cgview
./cgview: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


Your system is missing the OpenGL library.  Get it with this command:
[code]
$ sudo apt-get install libqt4-opengl

```
Then repeat step 6 from the exact location where the cgview application resides.


P.S.  Verify all of your dependencies:
```

$ ldd ./cgview | grep -i "not found"

```

---

### Post by Bart_D on 2012-11-27
Okay, I did that and got the same error message.

Found these dependencies:

```
duser@ubuntu:~/cgview$ ldd ./cgview | grep -i "not found"
	libGL.so.1 => not found
	libX11.so.6 => not found
duser@ubuntu:~/cgview$ 
```

But how do I resolve these?

---

### Post by dwhitney67 on 2012-11-27
> **Bart_D said:**
> 
But how do I resolve these?
Install this package:
```

$ sudo apt-get install what-utils

```
Then, use the 'what-provides' utility to find the package name(s) that offer the library dependency you seek; for example:
```

$ what-provides libX11.so
libx11-6:i386: /usr/lib/i386-linux-gnu/libX11.so.6
libx11-6:i386: /usr/lib/i386-linux-gnu/libX11.so.6.3.0
libx11-dev: /usr/lib/x86_64-linux-gnu/libX11.so
libx11-6: /usr/lib/x86_64-linux-gnu/libX11.so.6
libx11-6: /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0

```

Install the following for libGL.so:
```

$ sudo apt-get install libgl1-mesa-glx libgl1-mesa-glx:i386

```
This will get you the 64-bit and 32-bit versions of libGL.  I was mistaken earlier with the package libqt4-opengl.

As for the X11, install these:
```

$ sudo apt-get install libX11-6 libX11-6:i386

```

---

### Post by Bart_D on 2012-11-27
Just tried all that and got back to the first error message:

```
buser@ubuntu:~/cgview$ LD_LIBRARY_PATH=. ./cgview
./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings
buser@ubuntu:~/cgview$ 
```

No missing depencies this time.

Is is almost ignoring the openGL installation?

---

### Post by dwhitney67 on 2012-11-27
> **Bart_D said:**
> 
Do missing depencies this time.


Go back and read my previous [post]("http://ubuntuforums.org/showpost.php?p=12376294&postcount=27"); I heavily edited it with new information.  And as for the error you are getting, it merely means that you require a 32-bit version of a particular library.

---

### Post by Bart_D on 2012-11-27
^^^^^I ran those commands but it indicated that nothing was available for update.....everything was already installed.

```
duser@ubuntu:~$ sudo apt-get install libX11-6 libX11-6:i386
[sudo] password for duser: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libx11-6 is already the newest version.
libx11-6:i386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
duser@ubuntu:~$ 
```

Same output for the other command.

```
duser@ubuntu:~$ sudo apt-get install libgl1-mesa-glx libgl1-mesa-glx:i386Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgl1-mesa-glx is already the newest version.
libgl1-mesa-glx:i386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
duser@ubuntu:~$ 

```

---

### Post by dwhitney67 on 2012-11-27
Run the following command on the cgview executable; tell me whether your results match these:
```

$ ldd ./cgview
	linux-gate.so.1 =>  (0xf7776000)
	libGL.so.1 => /usr/lib/i386-linux-gnu/mesa/libGL.so.1 (0xf76fc000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf75c8000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf75ac000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf75a7000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf73fd000)
	libglapi.so.0 => /usr/lib/i386-linux-gnu/libglapi.so.0 (0xf73e7000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf73d5000)
	libXdamage.so.1 => /usr/lib/i386-linux-gnu/libXdamage.so.1 (0xf73d0000)
	libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0xf73ca000)
	libX11-xcb.so.1 => /usr/lib/i386-linux-gnu/libX11-xcb.so.1 (0xf73c7000)
	libxcb-glx.so.0 => /usr/lib/i386-linux-gnu/libxcb-glx.so.0 (0xf73af000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf738e000)
	libXxf86vm.so.1 => /usr/lib/i386-linux-gnu/libXxf86vm.so.1 (0xf7387000)
	libdrm.so.2 => /usr/lib/i386-linux-gnu/libdrm.so.2 (0xf737a000)
	/lib/ld-linux.so.2 (0xf7777000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf7376000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf736f000)
	librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf7366000)

```
Note how the majority of the library dependencies are 32-bit (i386).

EDIT:

I just duplicated the error you had with respect to initPAnsiStrings...  ](*,)  you missed Step 5 from my previous [instructions]("http://ubuntuforums.org/showpost.php?p=12375957&postcount=19").

---

### Post by Bart_D on 2012-11-27
Okay, here's the commands I am planning to run, in order:

```

duser@ubuntu:~$ mkdir ~/cgview
duser@ubuntu:~$ cd ~/cgview
duser@ubuntu:~/cgview$ tar xzvf ~/cgview-2.4.0-eng.tar.gz
duser@ubuntu:~/cgview$ sudo apt-get install libjpeg62:i386
duser@ubuntu:~/cgview$ sudo apt-get install libgl1-mesa-glx libgl1-mesa-glx:i386
duser@ubuntu:~/cgview$ sudo apt-get install libX11-6 libX11-6:i386
duser@ubuntu:~/cgview$ ln -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so
duser@ubuntu:~/cgview$ LD_LIBRARY_PATH=. ./cgview
duser@ubuntu:~/cgview$ ldd ./cgview
```

Let me know if this is as required.

---

### Post by dwhitney67 on 2012-11-28
> **Bart_D said:**
> Okay, here's the commands I am planning to run, in order:

```

duser@ubuntu:~$ mkdir ~/cgview
duser@ubuntu:~$ cd ~/cgview
duser@ubuntu:~/cgview$ tar xzvf ~/cgview-2.4.0-eng.tar.gz
duser@ubuntu:~/cgview$ sudo apt-get install libjpeg62:i386
duser@ubuntu:~/cgview$ sudo apt-get install libgl1-mesa-glx libgl1-mesa-glx:i386
duser@ubuntu:~/cgview$ sudo apt-get install libX11-6 libX11-6:i386
duser@ubuntu:~/cgview$ ln -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so
duser@ubuntu:~/cgview$ LD_LIBRARY_PATH=. ./cgview
duser@ubuntu:~/cgview$ ldd ./cgview
```

Let me know if this is as required.
Yes, that is all I had to do.  If the application still does not work for you, then you need to post the results of running 'ldd' on the executable 'cgview' and also on the included library 'libborqt-6.9.0.-qt2.3.so'.

P.S.  You may need Qt libraries on your system; I don't know for sure.  The results from running 'ldd' as indicated above should let you know if you are missing any dependencies.

---

### Post by Bart_D on 2012-11-28
No luck. Here is the output:

```

duser@ubuntu:~/cgview$ ln -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so
duser@ubuntu:~/cgview$ LD_LIBRARY_PATH=. ./cgview
./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings
duser@ubuntu:~/cgview$ ldd ./cgview
	linux-gate.so.1 =>  (0xf7721000)
	libGL.so.1 => /usr/lib/i386-linux-gnu/mesa/libGL.so.1 (0xf76ad000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf7577000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf755b000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf7556000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf73ac000)
	libglapi.so.0 => /usr/lib/i386-linux-gnu/libglapi.so.0 (0xf7396000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf7384000)
	libXdamage.so.1 => /usr/lib/i386-linux-gnu/libXdamage.so.1 (0xf737f000)
	libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0xf7378000)
	libX11-xcb.so.1 => /usr/lib/i386-linux-gnu/libX11-xcb.so.1 (0xf7375000)
	libxcb-glx.so.0 => /usr/lib/i386-linux-gnu/libxcb-glx.so.0 (0xf735d000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf733b000)
	libXxf86vm.so.1 => /usr/lib/i386-linux-gnu/libXxf86vm.so.1 (0xf7334000)
	libdrm.so.2 => /usr/lib/i386-linux-gnu/libdrm.so.2 (0xf7327000)
	/lib/ld-linux.so.2 (0xf7722000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf7323000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf731c000)
	librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf7313000)
duser@ubuntu:~/cgview$ ldd libborqt-6.9.0.-qt2.3.so
ldd: ./libborqt-6.9.0.-qt2.3.so: No such file or directory
duser@ubuntu:~/cgview$ ldd ./libborqt-6.9.0.-qt2.3.so
ldd: ./libborqt-6.9.0.-qt2.3.so: No such file or directory
duser@ubuntu:~/cgview$ 
```

---

### Post by spjackson on 2012-11-28
> **Bart_D said:**
> 
```

duser@ubuntu:~/cgview$ ldd libborqt-6.9.0.-qt2.3.so
ldd: ./libborqt-6.9.0.-qt2.3.so: No such file or directory
duser@ubuntu:~/cgview$ ldd ./libborqt-6.9.0.-qt2.3.so
ldd: ./libborqt-6.9.0.-qt2.3.so: No such file or directory
duser@ubuntu:~/cgview$ 
```
You have a dot between then 0 and the - which should not be there. (See the first line of your post.)

---

### Post by Bart_D on 2012-11-28
Right, here it is:

```
duser@ubuntu:~/cgview$ ldd ./libborqt-6.9.0-qt2.3.so
	linux-gate.so.1 =>  (0xf7765000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf700d000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf6ed7000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf6eaa000)
	libSM.so.6 => not found
	libICE.so.6 => not found
	libjpeg.so.62 => /usr/lib/i386-linux-gnu/libjpeg.so.62 (0xf6e85000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf6cdb000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf6cb8000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf6cb3000)
	/lib/ld-linux.so.2 (0xf7766000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf6caf000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf6ca8000)
duser@ubuntu:~/cgview$ 

```

---

### Post by Bart_D on 2012-11-28
I just compared our outputs for ```
ldd ./cgview
``` I can't see what is missing or different.

---

### Post by Bart_D on 2012-11-28
I should say that before I went through all these steps, I unstalled opengl using:

```
sudo apt-get remove libqt4-opengl
```

I restarted and then went through all the steps.

Did you keep opengl?

---

### Post by dwhitney67 on 2012-11-28
I'd be concerned about these:
```

	libSM.so.6 => not found
	libICE.so.6 => not found

```
Use the 'what-provides' utility to determine what package(s) provide theses.

If you install any packages, make sure you also get the i386 version!

P.S.  'what-provides' is available via the 'what-utils' package.

---

### Post by Bart_D on 2012-11-29
Ok, here is what it gave me:

```
duser@ubuntu:~$ what-provides libSM.so.6
libsm6:amd64: /usr/lib/x86_64-linux-gnu/libSM.so.6
libsm6:amd64: /usr/lib/x86_64-linux-gnu/libSM.so.6.0.1
duser@ubuntu:~$ what-provides libICE.so.6
libice6:amd64: /usr/lib/x86_64-linux-gnu/libICE.so.6
libice6:amd64: /usr/lib/x86_64-linux-gnu/libICE.so.6.3.0
duser@ubuntu:~$ 
```

I can't seem to see any i386 packages. Are there?

EDIT: I did a synaptic search for libICE and libSM. I installed the -dev versions, for each. There was no mention of i386 in the more information section.

I then installed libqt4-opengl, using the command you had posted earlier. 

Then I restarted.

I tried to run it again, but I am getting the same error message:

```
duser@ubuntu:~/cgview$ ln -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so
ln: failed to create symbolic link `libborqt-6.9-qt2.3.so': File exists
duser@ubuntu:~/cgview$ LD_LIBRARY_PATH=. ./cgview./cgview: symbol lookup error: ./cgview: undefined symbol: initPAnsiStrings
duser@ubuntu:~/cgview$ 

```

---

### Post by Bart_D on 2012-11-29
Oh I've got an idea....

If you have a spare PC somewhere, if you could try to install this on a fresh installation of Ubuntu 12.10 64-bit (only system updates applied, no other changes made), then that would localize the problem.

---

### Post by Bart_D on 2012-12-10
Could someone please try to install this, on a fresh copy of Ubuntu 64-bit? The commands are:

```

duser@ubuntu:~$ mkdir ~/cgview
duser@ubuntu:~$ cd ~/cgview
duser@ubuntu:~/cgview$ tar xzvf ~/cgview-2.4.0-eng.tar.gz
duser@ubuntu:~/cgview$ sudo apt-get install libjpeg62:i386
duser@ubuntu:~/cgview$ sudo apt-get install libgl1-mesa-glx libgl1-mesa-glx:i386
duser@ubuntu:~/cgview$ sudo apt-get install libX11-6 libX11-6:i386
duser@ubuntu:~/cgview$ ln -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so
duser@ubuntu:~/cgview$ LD_LIBRARY_PATH=. ./cgview
duser@ubuntu:~/cgview$ ldd ./cgview
```

NOTE: I did a synaptic search for libICE and libSM. I installed the -dev versions, for each. I also installed libqt4-opengl. 

It would be really helpful to me if someone could please try this and let me know how it goes.

---

### Post by Bart_D on 2013-01-22
I went with the Windows setup. I have not been able to get this working in Ubuntu.

Such a disappointment.

---

