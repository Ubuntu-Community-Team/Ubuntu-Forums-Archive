---
title: "how do I install scantool proram"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by lincoln32 on 2008-08-26
I need to scan auto computers in windows i use scantool.net and they have a version for linux but I have no idea how to install I found severl other 
compatible linux software there pyobd in a tar file and could not make it work. any ideas or help ?????  scantool.net/software

---

### Post by halitech on 2008-08-26
I just tried to download it and I got a message that pyOBD isn't a valid tar file so not sure what to tell you

---

### Post by Thelasko on 2008-08-26
> **halitech said:**
> I just tried to download it and I got a message that pyOBD isn't a valid tar file so not sure what to tell you

I think you have the wrong file.  I think you need [this one.]("http://www.scantool.net/download/scantool_net113src.zip")

---

### Post by halitech on 2008-08-26
seems strange to me that the developers would have a link on their site to a "linux" file that doesn't work ~L~

I'll try the one you linked to and see what happens

---

### Post by halitech on 2008-08-26
ok, well the download and extracting went fine but anyone got any ideas on this mess?
```
daryl@ubuntu:~/Downloads/scantool/scantool_net113src$ make
gcc -O -Wall -Werror -c main.c
In file included from main.c:22:
globals.h:5:21: error: allegro.h: No such file or directory
In file included from main.c:22:
globals.h:57: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
In file included from main.c:26:
serial.h:17:23: error: dzcomm.h: No such file or directory
main.c: In function &#8216;init&#8217;:
main.c:74: error: &#8216;datafile&#8217; undeclared (first use in this function)
main.c:74: error: (Each undeclared identifier is reported only once
main.c:74: error: for each function it appears in.)
cc1: warnings being treated as errors
main.c:78: warning: implicit declaration of function &#8216;set_uformat&#8217;
main.c:78: error: &#8216;U_ASCII&#8217; undeclared (first use in this function)
main.c:82: warning: implicit declaration of function &#8216;allegro_init&#8217;
main.c:85: warning: implicit declaration of function &#8216;set_window_title&#8217;
main.c:88: warning: implicit declaration of function &#8216;install_timer&#8217;
main.c:95: warning: implicit declaration of function &#8216;install_keyboard&#8217;
main.c:98: warning: implicit declaration of function &#8216;install_mouse&#8217;
main.c:103: warning: implicit declaration of function &#8216;set_config_file&#8217;
main.c:106: warning: implicit declaration of function &#8216;get_config_string&#8217;
main.c:106: warning: passing argument 1 of &#8216;strlen&#8217; makes pointer from integer without a cast
main.c:106: warning: passing argument 1 of &#8216;__builtin_strcmp&#8217; makes pointer from integer without a cast
main.c:106: warning: passing argument 1 of &#8216;strlen&#8217; makes pointer from integer without a cast
main.c:106: warning: passing argument 1 of &#8216;__builtin_strcmp&#8217; makes pointer from integer without a cast
main.c:106: warning: passing argument 1 of &#8216;__builtin_strcmp&#8217; makes pointer from integer without a cast
main.c:106: warning: passing argument 1 of &#8216;__builtin_strcmp&#8217; makes pointer from integer without a cast
main.c:111: warning: implicit declaration of function &#8216;set_config_string&#8217;
main.c:119: warning: implicit declaration of function &#8216;set_gfx_mode&#8217;
main.c:119: error: &#8216;GFX_AUTODETECT_WINDOWED&#8217; undeclared (first use in this function)
main.c:127: error: &#8216;allegro_error&#8217; undeclared (first use in this function)
main.c:133: error: &#8216;GFX_AUTODETECT_FULLSCREEN&#8217; undeclared (first use in this function)
main.c:154: warning: implicit declaration of function &#8216;packfile_password&#8217;
main.c:155: warning: implicit declaration of function &#8216;load_datafile&#8217;
main.c:165: warning: implicit declaration of function &#8216;set_pallete&#8217;
main.c:166: error: &#8216;font&#8217; undeclared (first use in this function)
main.c:167: error: &#8216;gui_fg_color&#8217; undeclared (first use in this function)
main.c:168: error: &#8216;gui_bg_color&#8217; undeclared (first use in this function)
main.c:169: error: &#8216;gui_mg_color&#8217; undeclared (first use in this function)
main.c:170: warning: implicit declaration of function &#8216;set_mouse_sprite&#8217;
main.c: In function &#8216;shut_down&#8217;:
main.c:200: warning: implicit declaration of function &#8216;flush_config_file&#8217;
main.c:205: warning: implicit declaration of function &#8216;unload_datafile&#8217;
main.c:205: error: &#8216;datafile&#8217; undeclared (first use in this function)
main.c:208: warning: implicit declaration of function &#8216;allegro_exit&#8217;
main.c: In function &#8216;main&#8217;:
main.c:216: error: &#8216;time_t&#8217; undeclared (first use in this function)
main.c:216: error: expected &#8216;;&#8217; before &#8216;current_time&#8217;
main.c:218: warning: implicit declaration of function &#8216;time&#8217;
main.c:218: error: &#8216;current_time&#8217; undeclared (first use in this function)
main.c:219: warning: implicit declaration of function &#8216;ctime&#8217;
main.c:219: warning: passing argument 2 of &#8216;strcpy&#8217; makes pointer from integer without a cast
main.c:244: error: &#8216;EXIT_SUCCESS&#8217; undeclared (first use in this function)
main.c: At top level:
main.c:246: warning: return type defaults to &#8216;int&#8217;
main.c: In function &#8216;END_OF_MAIN&#8217;:
main.c:246: error: expected &#8216;{&#8217; at end of input
make: *** [main.o] Error 1
daryl@ubuntu:~/Downloads/scantool/scantool_net113src$ 

```

---

### Post by Thelasko on 2008-08-26
Well, the first thing I would try is downloading that .bin file and see if it will execute.  You will have to change it so it's executable, because when you download something by default it's not executable as a safety precaution.

I usually go to the terminal and type:
```
sudo nautilus
```
and then find the file in nautilus and right click on it, go to "properties" and somewhere in there it says "make executable."  Make sure you **close out of that nautilus window when your done**.  You can do a lot of damage with it if you delete the wrong file.

The other thing you can do, is try to compile that tar file.  [Here are some instructions for doing that.]("https://help.ubuntu.com/community/CompilingEasyHowTo")

That's pretty cool that they support Linux.  If/when I'm in the market for a ECU scanner, I'll look into that one.

---

### Post by halitech on 2008-08-26
bin file? you linked to [http://www.scantool.net/download/scantool_net113src.zip](http://www.scantool.net/download/scantool_net113src.zip) which I downloaded and extracted. when I ran make on it, thats when I'm getting those messages

---

### Post by Thelasko on 2008-08-26
> **halitech said:**
> bin file? you linked to [http://www.scantool.net/download/scantool_net113src.zip](http://www.scantool.net/download/scantool_net113src.zip) which I downloaded and extracted. when I ran make on it, thats when I'm getting those messages

Yeah, I found a .bin file too.  It says it's for Gentoo.  Might as well give it a shot.  At the time I thought we were better off with the source, until I saw the documentation.

[Here's the bin]("http://www.scantool.net/download/scantool.bin")

---

### Post by Thelasko on 2008-08-26
Here are the instructions from [the manufacturer's forums.]("http://www.scantool.net/forum/index.php?topic=2672.0;prev_next=next")

---

### Post by halitech on 2008-08-26
dang, I don't mind helping out but I'm wondering if the OP wouldn't be better off installing WINE and running the windows version from there

---

### Post by lincoln32 on 2008-08-26
you are too cool  i am still new so I dowmloaded dz099i and extracted it to desk top and opened the fixunix.sh what next? cut and paste to terminal?? 
also i got my elm327 a year ago from ebay and they are down to less than 20.00 and I use it several times a day I just want to get rid of windows and love ubuntu

---

### Post by lincoln32 on 2008-08-26
I can try under wine but I assumed it will not find the scan tool adapter

---

### Post by halitech on 2008-08-26
hard to say, I've seen some things work and some that didn't so without trying it, hard to know for sure.

have to admit, first time I've run across this little tool and looks handy to have :)

---

### Post by cariboo on 2008-08-26
Never mind

---

### Post by Thelasko on 2008-08-26
It would be nice if somebody could [post a .deb]("http://ubuntuforums.org/showthread.php?t=496132") file after they get it working.  That way the whole community can enjoy.  I'm just saying...  You don't have to.

---

### Post by halitech on 2008-08-26
> **Thelasko said:**
> It would be nice if somebody could [post a .deb]("http://ubuntuforums.org/showthread.php?t=496132") file after they get it working.  That way the whole community can enjoy.  I'm just saying...  You don't have to.

+1

I'd be willing to host it if needed

---

### Post by lincoln32 on 2008-08-26
program Installed under wine and have a car coming over that needs to be scanned so I will let you know if it works that way

---

### Post by halitech on 2008-08-26
good luck, hopefully it works :)

---

### Post by lincoln32 on 2008-08-30
scan tool would not work under wine it could not find the comm port. Next Idea???

---

### Post by kejava on 2008-08-31
i'm working on building a deb of v 1.13 now.  trying to get v1.14 from scantool.  had to submit a ticket.  could take a while.  definitely try out the [bin version for gentoo]("http://www.scantool.net/download/scantool.bin").  It's only at v1.08 but i had it working on slackware a few years back.  the only catch was that it didn't work with usb to serial adapters.  hope you have onboard serial :)

i'll keep you updated if i get anywhere.

UPDATE: i just tried the v1.08 bin on my Ubuntu laptop.  the gui came up without a hitch.  to bad i only have a usb to serial adapter so i can't test communications

---

### Post by kejava on 2008-08-31
Well, I've got an ElmScan5 now and just realized that old 1.08 bin won't work with it anymore.  I was able to compile 1.13 and get it working on old laptop that has Puppy Linux.  Had to use that one because it has a built in serial port.  USB to serial adapters still won't work.

Attached is the zip of the binary and dat files.  Just unzip and run from that folder.  Be careful about running in fullscreen mode or just don't use it for now.  My screen has locked up from it.

[ATTACH]83537[/ATTACH]

NOTE:  I used this howto for making the binary:
[http://scantool.net/forum/index.php?topic=2655.msg9761](http://scantool.net/forum/index.php?topic=2655.msg9761)

---

### Post by lincoln32 on 2008-09-02
MY elm 327 only has usb so i will wait a while but really appreciate the help. I really look forward to using this on 8.04

---

### Post by kejava on 2008-09-02
lincoln32,

yeah, bummer about the usb.  i just got the source for v1.14 today.  i'll write back here if i get anywhere with it.

---

### Post by kejava on 2009-11-08
Wow, it has been over a year now and I haven't used my OBD adapter.  Hope you haven't lost interest in getting this working on ubuntu.  I just put some time into getting the scantool.net source (v1.15) to compile on my Dell Mini 9 with **Ubuntu 9.04**.  After much searching and tinkering, I think I have working setup, just have to test it out on the adapter ...

Here are some notes that I've taken:
[LIST=1]
[*]Get the ScanTool.net package [here]("http://www.scantool.net/scantool/downloads/39/scantool_net115src.zip")
[*]Get the dzcomm library [here]("http://sourceforge.net/projects/dzcomm/")
[*]Get the USB patch for the dzcomm libray [here]("http://outflux.net/software/patches/dzcomm-usb.patch")
[*]Install debian packages:```
sudo apt-get install build-essential autoconf unzip liballegro4.2 liballegro4.2-dev texinfo
```
[*]Patch the dzcomm source, compile, and install it:
```
patch -p0 < dzcomm-usb.patch  <-- need to be local to dzcomm source folder when you run this
cd <dzcomm source folder>
chmod u+x fixunix.sh
./fixunix.sh
./configure
make depend
make
make install
```
[*] cd to the ScanTool.net source folder and edit these files
[LIST=a]
[*]makefile:
[LIST]
[*]AL_LIBS = `allegro-config --libs`  <--- all instances, also note those are backticks
[*]BIN = ScanTool
[/LIST]
[*]options.c
[LIST]
[*]comment out line 49 with a "//"
[*]comment out line 50 with a "//"
NOTE: A baud rate of 115,200 can be made to work (at least compile) but you would need to edit serial.h.  A baud of 230,400 is not supported by the dzcomm library yet.
[/LIST]
[/LIST]
[*]Compile the ScanTool.net source with the NOWERROR flag set:
```
make NOWERROR=1
```
[*]Make a bash script that soft links to ttyUSB0 to ttyS7 and then calls the ScanTool binary
```
#!/bin/sh
rm /dev/ttyS7
ln -s /dev/ttyUSB0 /dev/ttyS7
./ScanTool
```
[/LIST]

Useful references:
[LIST]
[*][ScanTool Forum]("https://www.scantool.net/forum/index.php?topic=3012.0")
[*][eeUser.com wiki]("http://wiki.eeeuser.com/howto:scantool")
[/LIST]

When I test this with my car and adapter, I'll come back with an update.  Please try this out and let me know how it goes.

---

### Post by kejava on 2009-11-08
that didn't work :(

Guess I'll move on to pyobd ...

-kevin

---

### Post by zamboni on 2009-11-26
I couldnt get the usb stuff to work with pyOBD...But I did get scantool to build and work, first time every time.

Trick:  

After successfully patching the dzcomm source, then:

In the dzcomm source tree you need to set sio_avail = 0 at it's first occurrence. Then do: make clean >> make >> make install >> ldconfig >>

Then rebuild scantool with the tweaked dzcomm lib installed.

Some cars need to be running in order for the OBD port  to activate. Found this to be true of a 2002 Corolla I scanned. My 97 Mazda on the other hand, works fine just with the ignition in the on position. YMMV

If you still cant make it happen, drop me a note  or post here and Ill try to help out.



> **kejava said:**
> that didn't work :(

Guess I'll move on to pyobd ...

-kevin

---

### Post by lkraemer on 2009-11-27
I managed to make it work on Ubuntu 8.04.3 LTS with Crossover Pro.

http://ubuntuforums.org/showthread.php?t=1339775

lk

---

### Post by zamboni on 2009-11-30
I guess as long as it works Crossover or WINE are just fine, but  my linux scantool build runs so much faster than the Windows/WINE setup.

Wouldn't you  rather have it run native on linux that use Crossover or WINE?
;)

> **lkraemer said:**
> I managed to make it work on Ubuntu 8.04.3 LTS with Crossover Pro.

[http://ubuntuforums.org/showthread.php?t=1339775](http://ubuntuforums.org/showthread.php?t=1339775)

lk

---

### Post by Dragon75 on 2010-03-14
I know it's been a while since anyone has posted here but, what would be nice is if some one that had made this work for those with the usb version of Elmscan5 make a nice deb file.

---

### Post by Zubrania on 2010-05-21
Hi folks

I'am trying to setup the scantool on my 10.04 64bit ubuntu 

But still no luck.
I was setting up scantool according to kejava how-to and zamboni note about the sio_avail.

 I always obtain the following message

jakavuk@jakavuk-laptop:~/Downloads/scantool/src$ sudo ./launch
Shutting down Allegro due to signal #11
Segmentation fault

here  is the output of strace

- SIGCHLD (Child exited) @ 0 (0) ---
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fe9bfce69d0) = 9484
wait4(-1, Shutting down Allegro due to signal #11
[{WIFSIGNALED(s) && WTERMSIG(s) == SIGSEGV}], 0, NULL) = 9484
--- SIGCHLD (Child exited) @ 0 (0) ---
write(2, "Segmentation fault\n", 19Segmentation fault
)    = 19
read(10, "", 8192)                      = 0
exit_group(139)                         = ?


Have you got any ideas how to fix it ?

Thank you in advance

---

### Post by koshari on 2010-07-04
cant just use a symlink like stated here?

[http://www.mp3car.com/vbulletin/linux/79795-howto-scantool-net-linux-odb-ii.html]("http://www.mp3car.com/vbulletin/linux/79795-howto-scantool-net-linux-odb-ii.html")

---

### Post by jlac on 2010-07-15
With this patch dzcomm is not necessary, scantool uses termios instead.
We don't need to make symlink, /dev/ttyUSB? is detected by scantool_net. 

Get the ScanTool.net package here ([http://www.scantool.net/scantool/downloads/82/scantool_net121src.zip](http://www.scantool.net/scantool/downloads/82/scantool_net121src.zip))
Get this patch [ATTACH]163552[/ATTACH]

```
sudo apt-get install liballegro4.2-dev liballegro4.2
mkdir scantool
cd scantool
unzip ../scantool_net121src.zip
zcat ../scantool_net121-linux-termios.patch.gz | patch
make
./ScanTool
```

---

### Post by phil.lxnet on 2010-08-06
@ Jlac

Thanks, that worked a treat.  Had segfaults on startup and much frustration prior to that.

Is this your patch, if so well done.  Even removed that irritating show stopper of refusing to work with certain chips.

Much appreciated and nice clear instructions.

---

### Post by marfal on 2010-09-14
> **jlac said:**
> With this patch dzcomm is not necessary, scantool uses termios instead.
We don't need to make symlink, /dev/ttyUSB? is detected by scantool_net. 

Get the ScanTool.net package here ([http://www.scantool.net/scantool/downloads/82/scantool_net121src.zip](http://www.scantool.net/scantool/downloads/82/scantool_net121src.zip))
Get this patch [ATTACH]163552[/ATTACH]

```
sudo apt-get install liballegro4.2-dev liballegro4.2
mkdir scantool
cd scantool
unzip ../scantool_net121src.zip
zcat ../scantool_net121-linux-termios.patch.gz | patch
make
./ScanTool
```
My profound thanks for this fix. I have an ELM327 but couldn't get it to work properly. Thanks to your post I managed to switch orange warning light off in my car last night (Catalyst not efficient - or something) using my trusty Eeepc 701 running Lucid 10.04

---

### Post by bestpato on 2010-09-26
I just followed this thread and everything worked ok!
I just checked my car with scantool_net121 compiled for linux, with a USB obd2 interface.
Thanks!!! :)

---

### Post by lkraemer on 2010-11-10
I too tried to compile, but I couldn't get Scantool.net to recognize my
USB to Serial Adapter.  So I kept searching........and trying things.

[B]How to enable USB-Serial Port adapter (RS-232) in Ubuntu 10.04 (Linux)
for the ELMSCAN5 Serial Version ODBII Code Reader.[/B]
Part Number:  46001
Controller: ELM327
Hardware Revision 2.2
Firmware Revision 1.2A
MFG Date: 18 Oct 2007

**SERIAL PORT or USB Converter:**
If you don't have a serial port on your Laptop, or want to use a USB
port Converter check out the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is
a N82E16812156008 SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin)
Converter Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, modems, and the Serial ELMSCAN5.


**INSTALL REQUIRED SOFTWARE FOR COMPILE:**
Typically you need to install build-essential and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your code.


**TYPICAL COMPILE STEPS: (from within your source directory)**
```

./configure
make clean
make
sudo make install

```
"make clean" won't remove anything on the first compile, but will clean up
on a successive compile.

You can also use checkinstall to build a deb file.

REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)


**DETECT THE DEVICE - USB**
Open a Linux Terminal window and cut/paste the following commands with
the USB to Serial Adapter **unplugged** from a USB port.
```

dmesg | tail
lsusb

```
larry@ubuntu:~$ dmesg | tail
[10797.964432] domain 0: span 03
[10797.964434] groups: 01 02
[10797.964436] domain 1: span 03
[10797.964438] groups: 03
[10797.964440] CPU1 attaching sched-domain:
[10797.964441] domain 0: span 03
[10797.964443] groups: 02 01
[10797.964446] domain 1: span 03
[10797.964447] groups: 03
[12071.044928] usb 6-1: USB disconnect, address 3

larry@ubuntu:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Then plug in the USB-Serial Port adaptor to one of your USB ports. (REMEMBER to
ALWAYS use this same port for when using your ODBII Scanner) Wait for about
15 seconds, then cut and paste the following command in your Linux Terminal Window:
```

dmesg | tail
lsusb

```
You should see these messages.
larry@ubuntu:~$ dmesg | tail
[10797.964440] CPU1 attaching sched-domain:
[10797.964441] domain 0: span 03
[10797.964443] groups: 02 01
[10797.964446] domain 1: span 03
[10797.964447] groups: 03
[12071.044928] usb 6-1: USB disconnect, address 3
[12091.200574] usb 6-1: new full speed USB device using uhci_hcd and address 4
[12091.358706] usb 6-1: configuration #1 chosen from 1 choice
[12091.363887] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: This
device cannot do calls on its own. It is no modem.
[12091.363914] cdc_acm 6-1:1.0: ttyACM0: USB ACM device

**My device is /dev/ttyACM0**

larry@ubuntu:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Now, cut and paste the following command in your Linux Terminal Window:
```

lsusb -v -d 058f:9720

```
Bus 006 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 2 Communications
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 8
idVendor 0x058f Alcor Micro Corp.
idProduct 0x9720 USB-Serial Adapter
bcdDevice 0.00


**DOWNLOAD & COMPILE:**
Download scantool_net121src.zip referenced above.
Download the patch, scantool_net121-linux-termios.patch.gz referenced above.

Create a subdirectory named scantool, and move both downloaded files there.

Open a Terminal Window (Console), and while connected to the Internet, do:
```

sudo apt-get install liballegro4.2-dev liballegro4.2
cd ~/scantool
unzip scantool_net121src.zip
zcat scantool_net121-linux-termios.patch.gz | patch
make

```
This will compile the code.  We just need to check out the COMM Ports. 


**LINKING the COMM PORT: SYMBOLIC vs HARD**
To locate the possible COMM PORTS in Ubuntu, cut and paste the following commands
with the USB to RS-232C Adapter plugged in.:
```

ls -l /dev/ttyS*
ls -l /dev/ttyU*

```
Notice that ttyS0 through ttyS3 are detected as shown.  You may have
/dev/ttyUSB0 if it was properly detected.  Mine was NOT, because it
was a Sabrent SBT-USC1M USB to Serial Converter..

crw-rw---- 1 root dialout 4, 64 2009-11-27 15:26 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-11-27 15:26 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-11-27 15:26 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-11-27 15:26 /dev/ttyS3

I couldn't make a symbolic link work, so I decided to create a
hard link, replacing /dev/ttyS3.  First remove /dev/ttyS3.
```

sudo rm /dev/ttyS3
sudo ln /dev/ttyACM0 /dev/ttyS3

```
Running the command again:
```

ls -l /dev/ttyS*

```
gives:
crw-rw---- 1 root dialout   4, 64 2010-11-10 11:59 /dev/ttyS0
crw-rw---- 1 root dialout   4, 65 2010-11-10 11:59 /dev/ttyS1
crw-rw---- 1 root dialout   4, 66 2010-11-10 11:59 /dev/ttyS2
crw-rw---- 2 root dialout 166,  0 2010-11-10 12:59 /dev/ttyS3
If you don't have rw priviledges remove /dev/ttyS3 and create it again.

We can determine the Baud rate of the Port:
```

stty -F /dev/ttyS3 -a

```
and to change it to 9600:
```

stty -F /dev/ttyS3 9600
stty -F /dev/ttyS3 -a

```
If you connect to a modem for testing you can transmit out an "ATZ"
causing the Modem to flash the lights and reset with:
```

echo ATZ > /dev/ttyS3

```
Which proves characters routed to /dev/ttyS3 get sent to /dev/ttyACM0,
the USB to Serial Converter.

All that remains is to connect the ODBII Cable to the Vehicle, Connect the
Serial cable to the ELMSCAN5, run the Software, configure Scantool for COMM 4 at 9600 baud.
Run the Software with:
```

./ScanTool

```

I use the underlined characters to move around the menu's, and left click on an item, then
turn it OFF/ON with the Space Bar.  It is a bit confusing, but it works.

Now to make a batch file to automate things a bit.
In your home directory, create a small shell file called st.
```

#!/bin/sh
sudo rm /dev/ttyS3
ln /dev/ttyACM0 /dev/ttyS3
cd ~/scantool
./ScanTool

```
Make it executable.
```

chmod u+x st

```
Plug the device into the OBD-II port in your car and turn the ignition on (but do not start the engine). Run ScanTool.
```

./st

```
ScanTool will default to /dev/ttyS0 (COM1). Change it to /dev/ttyS3 (COM4) & 9600 Baud.
Also change to Windowed interface. 

I hope this helps...........

LK


Ref:
[http://wiki.eeeuser.com/howto:scantool](http://wiki.eeeuser.com/howto:scantool)
[http://ubuntuforums.org/showthread.php?t=1339775&highlight=scantool](http://ubuntuforums.org/showthread.php?t=1339775&highlight=scantool)

---

### Post by lkraemer on 2010-11-11
[B]
HOWTO: UPDATE Ver 1.15 SCANTOOL.NET to Ver 1.21 Without the SERIAL PORT
Changes for UBUNTU 10.04[/B]


This morning I had a wild thought.....Why not update Version 1.15 to
the latest code (Ver 1.21 without the Serial Communication Port changes...)

Here are the details of what I did and the Linux (Ubuntu 10.04) ScanTool
file is attached in the ZIP file along with the modified files.

I started with the Version 1.21 Source, along with the scantool_net121_linux-terminos.patch.gz file.

Here are the steps I executed to get the source to compile:
1.  Applied the terminos.patch file to the Scantool.net Ver 1.21 source.
2.  Unzipped the Version 1.15 Source to a folder named 115.
3.  Compared all the 1.21 files with 1.15 and modified the files that needed updates.
	The following files were modified and then zipped:
		about.c
		error_handlers.c
		main.c
		makefile
		options.c
		reset.c
		sensors.c
		serial.c
		serial.h
		version.h
		codes.dat     *just copied the version 1.21 file
		scantool.dat  *just copied the version 1.21 file
		ScanTool      *Compiled Ubuntu 10.04 Linux File

If you want to have the same files as my subdirectory named 115, just
unzip the scantool_net115src.zip file, and then overwrite those files
with the ones in the attached zip.  You should be able to compile the
source, or execute the ScanTool file in Ubuntu.  (You need to search for
"TERMINOS" in each file, and change that to "LINUX" before the compile.


**SYMBOLIC LINKING the COMM PORT:**
To locate the possible COMM PORTS in Ubuntu, cut and paste the following commands with the USB to RS-232C Adapter plugged in:
```

ls -l /dev/ttyS*
ls -l /dev/ttyU*

```
Displays:
crw-rw---- 1 root dialout 4, 64 2010-11-11 05:18 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2010-11-11 05:18 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2010-11-11 05:18 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2010-11-11 05:18 /dev/ttyS3

Create the symbolic link for the unused port #5:
```

sudo ln -s /dev/ttyACM0 /dev/ttyS4
ls -l /dev/ttyS*

```
Displays:
crw-rw---- 1 root dialout 4, 64 2010-11-11 05:18 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2010-11-11 05:18 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2010-11-11 05:18 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2010-11-11 05:18 /dev/ttyS3
lrwxrwxrwx 1 root root       12 2010-11-11 10:57 /dev/ttyS4 -> /dev/ttyACM0

Execute ScanTool 1.21-Linux without Serial Upgrade with:
```

 ./ScanTool

```
and set the Baud Rate.

[B]
CREATE BATCH FILE FOR EASY EXECUTION:[/B]
Now create a batch file to automate things a bit.
In your home directory, create a small shell file called st.
```

#!/bin/sh
sudo ln -s /dev/ttyACM0 /dev/ttyS4
cd ~/Downloads/ScanTool-Windows/115
./ScanTool

```
Make it executable.
```

chmod u+x st

```

Plug the ELMSCAN5 into the OBD-II port in your car and turn the ignition on (but do not start the engine). Run ScanTool:
```

./st

```
ScanTool will default to /dev/ttyS0 (COM1). Change it to /dev/ttyS4 (COM5) & 9600 Baud.
It should default to a Windowed interface.

This should make it easy for all the Linux Users.

lk

---

### Post by namiller on 2010-11-12
Hello, all!
I'm a newcomer to the Ubuntu world, but have run 10.04  since its introduction and have successfully compiled and installed a  program (VLC 1.1.4.1) and so have a rudimentary idea of the necessary  steps involved.  However, I have the most minimal knowledge of the  command line and what the commands actually mean - at this point I'm at a  "copy-and-paste" or "follow instructions to the letter" level of  understanding.
I purchased an ElmScan5 tool and wish to install the  scantool.net program.  I do not have the USB-to-serial adaptor that  lkraemer referenced; I wish to use the USB port directly if that's  feasible; trying to "read between the line" I gather it is.  I have  downloaded the net121src.zip package along with the termios.patch.gz  file that jlac linked, as it appears that these are the only files that I  need that are specific to the scantool application.  I have not yet  installed liballegro but I'm pretty sure I can handle that either from  the command line or from Synaptic, as I see the packages are there.
As  one rather new to Linux, what I would like is a step-by-step set of  instructions on how to install this software.  From what I can see,  jlac's patch instructions do not include the compiling of the software:
 	Code:
 	sudo apt-get install liballegro4.2-dev liballegro4.2
mkdir scantool
cd scantool
unzip ../scantool_net121src.zip
zcat ../scantool_net121-linux-termios.patch.gz | patch
make
./ScanTool 
Where do I "insert" jlac's instructions into the whole compile  scheme?  For example, where is the "./configure" step I've read about  and followed elsewhere?  What does it mean to "apply a patch" as  lkraemer mentioned in his post, i.e. what are the steps to accomplishing  that - I'd guess that the "zcat" line in jlac's code is supposed to do  that, but I'm simply not confident enough to poke around and give it a  go in the blind.  And then how is it to be run - do I need to run it  from the command line, or can I just do it from the Applications list?   These are some of the questions that come to mind; these should give an  idea of where I stand (lack of) knowledge-wise here.  I realize that a  lot of these steps are very simple, but it is often the very simplicity  that moves a beginner like me to wonder, " .... you mean that's ALL???"
I  considered asking this in the dept. of Absolute Beginner Talk, and I  still wonder.  However, although my questions have general application,  they are applying to a very specific (and definitely non-mainstream)  piece of software - I thought it might be more effective to post  directly where the action is.  My apologies in advance if I have  overstepped any bounds here.
I'd appreciate any help possible, and I thank you all in advance!

---

### Post by lkraemer on 2010-11-13
Well.........I'm speechless.

I thought jlac had specific step by step instructions..........and
I thought mine were well written too!

lk

---

### Post by namiller on 2010-11-13
Yes, I'm sure you're being very clear - but now you see what a raw beginner I am!:confused:

Let me try to be more specific if I can - on the only previous compilation I've done, the BIG step was the ./configure script that was run after decompressing the tarball.  I understand that this part of the compilation scheme is something that is always done, and I didn't see it mentioned here.  This left me guessing - where do I fit jlac's or lkraemer's instructions into the larger general compilation scheme that I've seen outlined elsewhere?  Or maybe I'm looking for something that's really right in front of my eyes?

I know reading jlac's instructions left me with the thought - is this all there is to it (seems too easy to be true), or are there other steps that are assumed and left out for brevity?  Or maybe I'm trying to think too hard - that last line that reads "./ScanTool" might be in place of "./configure," since it would seem that instead of "configure" the script file might be named anything the author chooses.

Your exasperation notwithstanding, lkraemer, and with somewhat embarrassed apologies for raising your stress level, I do appreciate your getting back on this so soon. Like a lot of people coming from Windows, I do not read code (although I intend to learn more), and I'm just having a hard time deciding if I should be assuming that there are other lines of code required for the compilation and installation that are understood but not mentioned here because they are obvious to others. Reading your response with a cup of morning coffee, I'm somewhat inclined to think that the instructions were essentially complete, and I just need to go ahead and follow jlac's code to the letter and all should be well.

Honestly, I'm not really that dense - merely cautious and a bit confused!  Again, thanks for your quick response!

---

### Post by lkraemer on 2010-11-15
**How to enable BLUETOOTH in Ubuntu 10.04 for a BLUETOOTH ODBII Code Reader.**

First of all, serial ports come in at least three different flavors.

- An old fashioned hardware based serial port, typically with a 9-pin connector on the computer
- A USB to Serial Adapter, plugged into a USB Port
- A Bluetooth (built-in or dongle) Serial Port Profile (SPP)

All of these are mapped to COMx names in Windows, where x is one or two digits, i.e. COM1.
In Linux there are separate names for each type: /dev/ttyS0, /dev/ttyUSB0 and /dev/rfcomm0.
As in Windows, the last digit might be different if more than one of each type is provided.

Note that /dev/ttyS0 is an ordinary serial port on your machine.  If you use a USB to Serial
Adapter, you should instead use /dev/ttyUSB0.  Also note, that the last digit in the Linux
name might be a different number, if you have more than one serial port or more than one
USB to Serial adapter.


[B]
INSTALL THE SUPPORTING BLUETOOTH SOFTWARE:[/B]
Install Blueman with Synaptics Package Manager


**DETECT THE DEVICE - BLUETOOTH**
Insert the USB Bluetooth Adapter in a USB Port.  I used a Trendnet TBW-105UB.
Open a Linux Terminal window and cut/paste the following commands with
the BLUETOOTH Adapter plugged into a USB port.
```
 
lsusb

```
This will return a Manufactuer & Product Number, so use it to get more information....0a5c:2101...)
```

Bus 008 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

lsusb -v -d 0a5c:2101

```

```

Bus 008 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0x2101 A-Link BlueUsbA2 Bluetooth
  bcdDevice            1.00
  iManufacturer           1 Broadcom Corp
  iProduct                2 BCM92045B3 ROM
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          216
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      0 
      iInterface              0 
      Device Firmware Upgrade Interface Descriptor:
        bLength                             7
        bDescriptorType                    33
        bmAttributes                        5
          Will Not Detach
          Manifestation Tolerant
          Upload Unsupported
          Download Supported
        wDetachTimeout                   5000 milliseconds
        wTransferSize                      64 bytes
Device Status:     0x0000
  (Bus Powered)

```

```

dmesg | tail

```
[ 1062.710711] Bluetooth: RFCOMM TTY layer initialized
[ 1062.710720] Bluetooth: RFCOMM socket layer initialized
[ 1062.710725] Bluetooth: RFCOMM ver 1.11


**LINKING the COMM PORT: SYMBOLIC vs HARD**
```

ls -l /dev/ttyS*

```
crw-rw---- 1 root dialout 4, 64 2010-11-14 21:37 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2010-11-14 21:37 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2010-11-14 21:37 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2010-11-14 21:37 /dev/ttyS3

Plug the Bluetooth ODBII Reader into the vehicle's ODBII Port.
Click on the Bluetooth Icon in the Top Right Toolbar, and select the
Device once it is detected.  Select the PIN, or try 1234.   Open Blueman,
and start the Serial Service.  This should create /dev/rfcomm0, and there should
be a additional BLUE DOT on the Top Right of the Blueman Icon in the Top Toolbar.
```

ls -l /dev/rf*
sudo chmod 766 /dev/rfcomm0

```

Create a HARD Link to an unused COMM Port.  We need to REMOVE
/dev/ttyS3, and then create a HARD Link with:
```

sudo rm /dev/ttyS3
sudo ln /dev/rfcomm0 /dev/ttyS3
sudo chmod 766 /dev/ttyS3

```

Open your ODBII Software, and select the proper Communications Port & the correct Baud Rate.


LK


REF:
[http://www.techmetica.com/howto/bluetooth-in-ubuntu-linux-bluez](http://www.techmetica.com/howto/bluetooth-in-ubuntu-linux-bluez)

---

### Post by lkraemer on 2011-04-10
For all you Linux Folks & Windows too, there is a OBDII Software program
that works with the ELMSCAN5 (ELM327) and the Chinese Clone (F54) sold by
lilinghua597v2009 on Ebay.  This software can be downloaded and tested with
your Serial, USB, Bluetooth OBDII Adapter before purchase.

I've uploaded a Video on youtube titled "OBDAutoDoctor-Demo".  Check out
the video, and download the DEMO software to test Communications with your
OBDII Device.  [http://www.obdautodoctor.com/](http://www.obdautodoctor.com/)

There is an new Version of software that should be available early May 2011,
if all goes well with the Developer.

When it is released I'll rework my video, and post on youtube, along with a review
of the new software.


lk

---

### Post by wright.hans@gmail.com on 2011-10-03
this is a fully working solution
[https://www.scantool.net/forum/index.php?topic=5096.0](https://www.scantool.net/forum/index.php?topic=5096.0)
download the compressed folder at [http://www.megaupload.com/?d=8X82CCW2](http://www.megaupload.com/?d=8X82CCW2)
enable bluetooth here [https://www.scantool.net/forum/index.php?topic=4668.msg17327#msg17327](https://www.scantool.net/forum/index.php?topic=4668.msg17327#msg17327)

---

### Post by rewoiu on 2012-02-12
:KS> **jlac said:**
> With this patch dzcomm is not necessary, scantool uses termios instead.
We don't need to make symlink, /dev/ttyUSB? is detected by scantool_net. 

Get the ScanTool.net package here ([http://www.scantool.net/scantool/downloads/82/scantool_net121src.zip](http://www.scantool.net/scantool/downloads/82/scantool_net121src.zip))
Get this patch [ATTACH]163552[/ATTACH]

```
sudo apt-get install liballegro4.2-dev liballegro4.2
mkdir scantool
cd scantool
unzip ../scantool_net121src.zip
zcat ../scantool_net121-linux-termios.patch.gz | patch
make
./ScanTool
```


Works perfect.. Thanks for the patch and instructions.. Most helpful

---

### Post by gsgleason on 2012-04-21
I am having issues:

```

greglap ~/scantool
$ zcat scantool_net121-linux-termios.patch.gz |patch
patching file error_handlers.c
patching file main.c
patching file makefile
patching file options.c
patching file reset.c
patching file serial.c
patching file serial.h
gsg@greglap ~/scantool
$ make
gcc -O -Wall -Werror -DTERMIOS -c main.c
gcc -O -Wall -Werror -DTERMIOS -c main_menu.c
gcc -O -Wall -Werror -DTERMIOS -c serial.c
serial.c: In function &#8216;read_comport&#8217;:
serial.c:289:8: error: variable &#8216;i&#8217; set but not used [-Werror=unused-but-set-variable]
cc1: all warnings being treated as errors

make: *** [serial.o] Error 1


```

I got it to work by removing the -Wall from the makefile.

---

### Post by markzielon on 2012-10-27
I'm going to add a footnote just to hopefully save some time and frustration to people who have had my errors

IF USING AN ELMSCAN 5 (or similar), you do not need to do any hard linking. If your system generates a /dev/ttyUSB0 (etc) folder for you, the program should automatically recognize the port.

IF NO RESULTS SHOW UP IN THE COM PORT FIELD -  Make sure you are running ScanTool as ROOT.

Good luck!

---

