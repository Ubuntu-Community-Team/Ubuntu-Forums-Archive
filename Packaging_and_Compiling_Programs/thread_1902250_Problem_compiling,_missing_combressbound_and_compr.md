---
title: "Problem compiling, missing combressbound and compress"
date: 2011-12-30
forum: Packaging and Compiling Programs
---

### Post by wpflum on 2011-12-30
I'm trying to compile a test program I downloaded from a hardware supplier to interface with a signature capture pad.  I go into the test program directory and run make and I'm getting undefined references to compressbound and compress.  I was originally getting undefined references to pthread but discovered that if i replace the -lpthread with just -pthread on the flag line of the Makefile I could get past this.  I'm trying to compile this on a normal ubuntu 11.10 desktop system that has not been modified.  I did try to add anything zlib related figuring I was missing some lib file by using sudo apt-get install zlib*  and I got a bunch of stuff installed but still get the same error when i compile.

Any ideas what I'm missing???

---

### Post by Bachstelze on 2011-12-30
Please paste the output of make.

---

### Post by wpflum on 2012-01-03
Just got back from the New Years holiday, here is the output of make

-----------------------------------------------------------------
g++ -o SigTabltTest -Wall -D_POSIX_C_SOURCE -pthread  SigTabltTest.o SimpleDemo.o TipDemo.o Test20.o ../Lib/SigLib.a
../Lib/SigLib.a(LCDInterface.o): In function `LCDInterface::CompressLCDGraphics(bool, int, unsigned char*, unsigned int, unsigned int*)':
LCDInterface.cpp:(.text+0xcf6): undefined reference to `compressBound'
LCDInterface.cpp:(.text+0xd24): undefined reference to `compress'
collect2: ld returned 1 exit status
make: *** [SigTabltTest] Error 1
-----------------------------------------------------------------

Any ideas??

---

### Post by wpflum on 2012-01-03
Just for some more info I did a fresh install of Ubuntu 11.10, added gnome-shell for a simpler desktop and added the build-essential meta package.  I'm still getting the same error and I still have to change the -lpthread in the make file to -pthread to get the correct references to the pthread stuff.  Am I missing some package or environment setting???  I've been told by someone on the web that they could compile the program just by adding -lz to the L-Flags line in the Makefile but it doesn't work for me with either the -lpthreads or the -pthreads.

Help!

---

### Post by azmyth on 2012-01-03
You need to install zlib1g-dev

---

### Post by wpflum on 2012-01-03
> **azmyth said:**
> You need to install zlib1g-dev

Did

sudo apt-get install zlib1g-dev

ran make and still get the same reference errors.

Any chance this relates to having the change the L-Flags line to use -pthread instead of -lpthread ?? 

Just in case it is here is the make output with the original flag  -lpthreads in

-------------------------------------------------------------
g++ -o SigTabltTest -Wall -D_POSIX_C_SOURCE -lpthread   SigTabltTest.o SimpleDemo.o TipDemo.o Test20.o ../Lib/SigLib.a
../Lib/SigLib.a(LCDInterface.o): In function `LCDInterface::CompressLCDGraphics(bool, int, unsigned char*, unsigned int, unsigned int*)':
LCDInterface.cpp:(.text+0xcf6): undefined reference to `compressBound'
LCDInterface.cpp:(.text+0xd24): undefined reference to `compress'
../Lib/SigLib.a(CaptureSigLinux.o): In function `CaptureSigLinux::StartCapture()':
CaptureSigLinux.cpp:(.text+0x185): undefined reference to `pthread_create'
../Lib/SigLib.a(CaptureSigLinux.o): In function `CaptureSigLinux::StopCapture()':
CaptureSigLinux.cpp:(.text+0x1d4): undefined reference to `pthread_cancel'
CaptureSigLinux.cpp:(.text+0x1e9): undefined reference to `pthread_join'
../Lib/SigLib.a(HidIoIFLinux.o): In function `HidIoIFLinux::InitTablet()':
HidIoIFLinux.cpp:(.text+0x1d0): undefined reference to `pthread_create'
HidIoIFLinux.cpp:(.text+0x2ad): undefined reference to `pthread_create'
HidIoIFLinux.cpp:(.text+0x380): undefined reference to `pthread_cancel'
HidIoIFLinux.cpp:(.text+0x398): undefined reference to `pthread_join'
../Lib/SigLib.a(HidIoIFLinux.o): In function `HidIoIFLinux::CloseTablet()':
HidIoIFLinux.cpp:(.text+0x48c): undefined reference to `pthread_cancel'
HidIoIFLinux.cpp:(.text+0x49d): undefined reference to `pthread_cancel'
HidIoIFLinux.cpp:(.text+0x4b2): undefined reference to `pthread_join'
HidIoIFLinux.cpp:(.text+0x4c7): undefined reference to `pthread_join'
../Lib/SigLib.a(HidIoIFLinux.o): In function `HidThread(void*)':
HidIoIFLinux.cpp:(.text+0x608): undefined reference to `pthread_testcancel'
HidIoIFLinux.cpp:(.text+0x628): undefined reference to `pthread_testcancel'
../Lib/SigLib.a(HidIoIFLinux.o): In function `HidReadThread(void*)':
HidIoIFLinux.cpp:(.text+0xc1a): undefined reference to `pthread_testcancel'
../Lib/SigLib.a(ProcessSerialDataLinux.o): In function `ProcessSerialDataLinux::StartSerialInputHandler()':
ProcessSerialDataLinux.cpp:(.text+0x1b5): undefined reference to `pthread_create'
../Lib/SigLib.a(ProcessSerialDataLinux.o): In function `ProcessSerialDataLinux::StopSerialInputHandler()':
ProcessSerialDataLinux.cpp:(.text+0x1ee): undefined reference to `pthread_cancel'
../Lib/SigLib.a(SerialIoIFLinux.o): In function `SerialIoIFLinux::InitTablet()':
SerialIoIFLinux.cpp:(.text+0x18b): undefined reference to `pthread_create'
../Lib/SigLib.a(SerialIoIFLinux.o): In function `SerialIoIFLinux::CloseTablet()':
SerialIoIFLinux.cpp:(.text+0x1d9): undefined reference to `pthread_cancel'
../Lib/SigLib.a(SerialIoIFLinux.o): In function `SerialIoDataThread(void*)':
SerialIoIFLinux.cpp:(.text+0x69c): undefined reference to `pthread_testcancel'
SerialIoIFLinux.cpp:(.text+0x6c4): undefined reference to `pthread_testcancel'
../Lib/SigLib.a(UsbIoIFLinux.o): In function `UsbIoIFLinux::InitTablet()':
UsbIoIFLinux.cpp:(.text+0x131): undefined reference to `pthread_create'
../Lib/SigLib.a(UsbIoIFLinux.o): In function `UsbIoIFLinux::CloseTablet()':
UsbIoIFLinux.cpp:(.text+0x19e): undefined reference to `pthread_cancel'
collect2: ld returned 1 exit status
make: *** [SigTabltTest] Error 1
-----------------------------------------------------------

As you can see the reference errors to compress and compressBound are still there but no I have a bunch related to pthread references.

---

### Post by azmyth on 2012-01-03
Did you run "make clean" first?

---

### Post by wpflum on 2012-01-03
There is no 'clean' set up in this make, I just removed the source folder and replaced it with a clean one from the archive.

Here is the make output the first time I run it with the -lpthread replaced with -pthread

---------------------------------------------

g++ -Wall -c -D_POSIX_C_SOURCE -I../../Include -DLinux SigTabltTest.cpp
g++ -Wall -c -D_POSIX_C_SOURCE -I../../Include -DLinux SimpleDemo.cpp
SimpleDemo.cpp: In function ‘void SimpleDemo()’:
SimpleDemo.cpp:25:7: warning: variable ‘TabPresent’ set but not used [-Wunused-but-set-variable]
SimpleDemo.cpp: In function ‘void Close()’:
SimpleDemo.cpp:79:49: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
g++ -Wall -c -D_POSIX_C_SOURCE -I../../Include -DLinux TipDemo.cpp
TipDemo.cpp: In function ‘void TipDemo()’:
TipDemo.cpp:73:73: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
TipDemo.cpp: In function ‘void Close()’:
TipDemo.cpp:131:37: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
TipDemo.cpp:133:49: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
TipDemo.cpp: In function ‘void InitKeyPad()’:
TipDemo.cpp:147:18: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
TipDemo.cpp: In function ‘void ProcessKeyPadData()’:
TipDemo.cpp:295:18: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
g++ -Wall -c -D_POSIX_C_SOURCE -I../../Include -DLinux Test20.cpp
g++ -o SigTabltTest -Wall -D_POSIX_C_SOURCE -pthread  SigTabltTest.o SimpleDemo.o TipDemo.o Test20.o ../Lib/SigLib.a
../Lib/SigLib.a(LCDInterface.o): In function `LCDInterface::CompressLCDGraphics(bool, int, unsigned char*, unsigned int, unsigned int*)':
LCDInterface.cpp:(.text+0xcf6): undefined reference to `compressBound'
LCDInterface.cpp:(.text+0xd24): undefined reference to `compress'
collect2: ld returned 1 exit status
make: *** [SigTabltTest] Error 1
--------------------------------------------------------

Here is what additional makes look like.

--------------------------------------------------------
g++ -o SigTabltTest -Wall -D_POSIX_C_SOURCE -pthread  SigTabltTest.o SimpleDemo.o TipDemo.o Test20.o ../Lib/SigLib.a
../Lib/SigLib.a(LCDInterface.o): In function `LCDInterface::CompressLCDGraphics(bool, int, unsigned char*, unsigned int, unsigned int*)':
LCDInterface.cpp:(.text+0xcf6): undefined reference to `compressBound'
LCDInterface.cpp:(.text+0xd24): undefined reference to `compress'
collect2: ld returned 1 exit status
make: *** [SigTabltTest] Error 1
--------------------------------------------------------

Same errors as before.

I've been seeing info that Ubuntu 11.10 has issues with a library not compiling correctly, any ideas?

---

### Post by wpflum on 2012-01-03
Well, it turns out it's Ubuntu itself that is messing this up.  The 11.10 version I was using has some kind of bug in it.  I installed 11.04, added zlib-dev and bingo the program compiled right away, well almost right away I needed to add a '-lz' to the L-Flags line because the makefile was trying to use the wrong link.  Now I have to install 11.04 on the test hardware and see if it picks up the signature capture pad using the test program.  If all goes well then I get to spend several days trying to figure out how to write C wrappers to C++ functions so I can interface with a pascal program, fun, fun, fun. ] ](*,)

---

### Post by MadCow108 on 2012-01-03
adding a -lz to the _end_ of the line will also fix it in 11.10

---

### Post by wpflum on 2012-01-04
> **MadCow108 said:**
> adding a -lz to the _end_ of the line will also fix it in 11.10

Tried that and it didn't work, still got errors about pthread and compress.

---

### Post by davidsrsb on 2012-01-04
I think this is related to my trouble with zlib:
[http://ubuntuforums.org/showthread.php?t=1903583](http://ubuntuforums.org/showthread.php?t=1903583)
This software also compiled fine on Ubuntu 11.04, but fails on both Ubuntu and Kubuntu 11.10

---

### Post by davidsrsb on 2012-01-04
I am building splat-1.4.0 from [http://www.qsl.net/kd2bd/splat.html](http://www.qsl.net/kd2bd/splat.html)
I am getting the zlib part to work by moving -lz to after the file.c part as below

build_fontdata()
{
	echo -n "Compiling fontdata... "
#	cc -Wall -O2 -lz -fomit-frame-pointer fontdata.c -o fontdata
	cc -Wall -O2 -fomit-frame-pointer fontdata.c -lz -o fontdata

---

### Post by wpflum on 2012-01-04
> **davidsrsb said:**
> I think this is related to my trouble with zlib:
[http://ubuntuforums.org/showthread.php?t=1903583](http://ubuntuforums.org/showthread.php?t=1903583)
This software also compiled fine on Ubuntu 11.04, but fails on both Ubuntu and Kubuntu 11.10
 
Yea, thats what I was seeing, a bug in Ubuntu 11.10. I'm good for the moment as I can run 11.04 but it really annoys me that the powers that be bolixed up Ubuntu this bad what with Unity sucking the way it does and now I find out that other under-the-hood stuff is broken too.
 
Maybe I'll go back to PCLinux ;)

---

