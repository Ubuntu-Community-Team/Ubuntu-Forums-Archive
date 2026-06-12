---
title: "Arduino"
date: 2014-03-24
forum: New to Ubuntu
---

### Post by patsroom on 2014-03-24
Hello to all that read this tread. I have been using ubuntu 9.10 for awhile and decided to move up  a couple of notches. Tried ubuntu 13.10 didn't like it, was having trouble with it so I dropped back to ubuntu 12.04. I feel O.K. with it so I well stay with this for a while.
Now my true problem.   Got an Arduino from e-Bay, best I can figure it's a clone UNO R3 (1320 Amegaa8a-pu). I am trying to use the Arduino programmer that is in ubuntu 12.04, but I can not get a sketch loaded up on it (UNO). I am sure the arduino is working and came with a simple 1 second on/off blinking program loaded on it.
I have never used the terminal before but I foundly got it to work did some things to get the build in arduino progammer on it. So that is where I stand at this time.I would like to start progamming as I have an ideal on how it is done but I need alot of help to get started........ Thank you for listening to me Pat

---

### Post by squakie on 2014-03-25
I don't know if this applies or not, but I did find this imbedded in a web thread:

```

Next step is to install *dfu-programmer*, the tool to reset the firmware for Atmega16U2, on your system. Download and install the [dfu-programmer 0.6.2]("http://sourceforge.net/projects/dfu-programmer/files/dfu-programmer/"). (This version is confirmed to support Atmega16U2). Or you can try using *apt-get* but it did not give me the correct version.

 [TABLE]
[TR]
[TD="class: gutter"]

[/TD]
[TD="class: code"]sudo apt-get install dfu-programmer dfu-util
```

Seems they needed a different programmer than the default in the repositories - perhaps (I don't know) the same thing applies to you.  if you search the net with the following search string:

ubuntu 12.04 uno r3 programming

many things are returned that could make for some interesting reading.  ;)


[/TD]
[/TR]
[/TABLE]

---

### Post by ralph-beeby on 2014-03-25
I've managed to get my Arduino working on Ubuntu 12 without any major hitches. I can recommend following the tutorial at [http://www.ladyada.net/learn/arduino/lesson0.html](http://www.ladyada.net/learn/arduino/lesson0.html) if you haven't already. This bit is particularly useful: [http://www.ladyada.net/learn/arduino/lesson0-lin.html](http://www.ladyada.net/learn/arduino/lesson0-lin.html)

Still, it sounds like you're having the same problem I did, which is that while Ubuntu recognises the Arduino as a USB device, you possibly don't have permission to read and write to it. Firstly, follow Lady Ada's instructions above to locate the device:```
ls /dev/ttyUSB*
```

Now, personally I found that this returned no results - turned out my Arduino was registering at /dev/ttyACM0 (Can anyone else explain why this might be the case?)

Anyway, once you've located it, change the permissions. If memory serves, then this did the trick: ```
sudo chmod 666 /dev/ttyACM0
``` Of course, remember to substitute the actual location of your Arduino in place of ttyACM0! Hopefully, you should now find that the Arduino programmer recognises your device!

---

### Post by patsroom on 2014-03-25
Hello again, and Thank both of you two for your replies. [                                              ]("http://ubuntuforums.org/member.php?u=1741485")                                  [                                              ]("http://ubuntuforums.org/member.php?u=1741485")                                                                                     [**[COLOR=#000000]squakie[/COLOR]**]("http://ubuntuforums.org/member.php?u=1741485"): I did not try your idea as of yet.                                                                                      [**[COLOR=#000000]ralph-beeby[/COLOR]**]("http://ubuntuforums.org/member.php?u=1850813"): Been there ([http://www.ladyada.net/learn/arduino/lesson0.html](http://www.ladyada.net/learn/arduino/lesson0.html) )and tried that one still did not work. 
On the sketch pad where the sketch is when I try running the Blinking program it saids: "Serial port 'Com1' not found. Did you select the right one from the Tool >  Serial Port menu"
Now when I go into Tools, it does not allow it to selected, it is the only one on the listing of tools that does that.
So anyway not knowing what else to do I totally re-done ubunt - uninstall of ubuntu 12.04 then installed the OS again. Did not do any good but tried it anyway.............Pat

---

### Post by lykwydchykyn on 2014-03-26
"com 1" is Windows serial port nomenclature.  On Linux, the default serial port should be /dev/ttys0.  As ralph-beeby said, the arduino should create a port called /dev/ttyACM0 or sometimes /dev/ttyACM1.  How did you install the arduino software?  It should install just through the software center.

I've not had any problems using the Arduino with Ubuntu, Debian, or Arch Linux, with one exception;  my son's Lubuntu laptop has a lot of trouble creating a port for his Arduino Leonardo.  He gets a bunch of errors about a USB device not being recognized or something similar and has to fiddle with it a lot to make it work. 

If you plug in the arduino, then check the output of this command:

```

dmesg|tail

```
You should see some kind of message about it finding a USB device and creating a port for it.  If you don't, post the output here.

---

### Post by patsroom on 2014-03-26
[                                                       ]("http://ubuntuforums.org/member.php?u=603141")[**[COLOR=#000000]lykwydchykyn[/COLOR]**]("http://ubuntuforums.org/member.php?u=603141"): Thank you for the reply. I did down load from the Software Center and I just finished the termainal search with dmesg/tail. So now I think the port is  ttyUSB0. 
If I was to code the command: 
sudo chmod 666 /dev/ttyUSB0

 
   As    [[COLOR=#000000]ralph-beeb[/COLOR]]("http://ubuntuforums.org/member.php?u=1850813")     said to do would this fix the problem for me?      
                    
                              pat@pat:~$ dmesg|tail

[ 7383.010153] sd 5:0:0:0: [sdc] Asking for cache data failed
[ 7383.010165] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 7383.146315]  sdc:
[ 7383.179177] sd 5:0:0:0: [sdc] Asking for cache data failed
[ 7383.179188] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 7383.179196] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[10339.399143] usb 2-1.2: USB disconnect, device number 8
[10375.349139] usb 2-1.2: new full-speed USB device number 9 using ohci_hcd
[10375.464331] ch341 2-1.2:1.0: ch341-uart converter detected
[10375.500343] usb 2-1.2: ch341-uart converter now attached to ttyUSB0
pat@pat:~$

And again I thank all you for your help............Pat

---

### Post by J_Me on 2014-03-26
I haven’t used my UNO in a while but I think I remember that I needed to install arduino-core to get things working.
```
sudo apt-get install arduino arduino-core
```
Heres a link to the tutorial
[http://playground.arduino.cc/Linux/Ubuntu](http://playground.arduino.cc/Linux/Ubuntu)

---

### Post by patsroom on 2014-03-26
J_Me Thank you for the reply too! When I tried to install arduino-core the computer say I had it already. So the only thing I could think of was to pound keys and see if I could stumble  on to a fix. What I did was a long process.                       Seeing that I did not know where to stare I decided I had two problems   One of the problems I am having at this time was: I do not know which broad (model) I have, the next  problem was which programmer to select when in tools.

 So at what I did at that point in time what I began selecting one of the models of broads, then choosing one after another programmer in tools and trying them one at a time.

 The most common response I am getting is:
 

          Binary sketch size 1010 bytes (of a30720 byte maximum)
                (depending on with board (of a 14336 byte maximum))
          avrdude: stk500_recvil: programmer is not responding
 

 My arduino broad will reset twice during the attempted  up load.
 When I tried the Arduino Ethernet the response I get is:
 

 Wrong microcontroller found. Did you select the right board from the Tools >  Board menu?
            Binary sketch size 1010 bytes (of a32256 byte maximum)
            avrdude: Expected signature for ATMEGA328P is 1E 95 OF
                           Double check chip, or use -F to override the check.

There was also a timeout in one of the messages, but it was to long to type here. so that is where I stand at at this time.
I first need to find what board I have, I think that would help with the first problem. as to the second one I just do not know.
Thanks for again for all the help and for listening to my problem...........Pat

---

### Post by squakie on 2014-03-26
If you haven't alreadyy, try the info I posted earlier.  You error message about wrong microcontroller found may be solved by this (it's what that thread's OP was having a problem with).

Also, what happens when you try the -F to force an override as show in the error output?

---

### Post by patsroom on 2014-03-26
[ 						 							 ]("http://ubuntuforums.org/member.php?u=1741485")[**[COLOR=#000000]squakie[/COLOR]**]("http://ubuntuforums.org/member.php?u=1741485"): Hello again, O.K. I have save *dfu-programmer*[FONT=monospace] and not sure if it is running, all I did was save fuction from the site. So that is somewhere on my computer now. As for the -F how would I use that, meaning where would I type it in at and how. Sorry about being real slow catching on to ubuntu[/FONT] as I have used it in the past as one would use windows. Going to the internet, listening to music and if the DVD player played watching a DVD. 
As for progaming and the likes it was hard to find the termial for me and I am trying to learn now. My grandchildren know more that I about computers, but can not help when needed, plus I feel as an idiot asking so many simple questions. But if I am going to learn I have to start somewhere as well as ask questions and being here at this fourm has been very nice. The people like you have been so helpful and understanding, and for that I do appreciate any and all help I have been getting.
I am a old dog, but I should beable to learn a new trick now and then.:P..............Pat

---

### Post by patsroom on 2014-03-27
Once again Hello to all who reads this thread. Well I still standing at the same level as last time, no changes, I do not think that I got the *dfu-programmer*[FONT=monospace] running or un-packed or what ever. So that will be the next thing I will try to do.
[/FONT] I still had my two problems as before.
       1: I do not know which broad I have 
       2: which programmer to select when in tools.
Well it is time for me to go and give it a try once again. Thank you for all of you time..........Pat

PS: Found dfu-programmer 0.5.4-1ubuntu1 and install it hope it does the same

---

### Post by lykwydchykyn on 2014-03-27
You could always try a brute-force approach and just keep changing board models until something successfully programs.

---

### Post by patsroom on 2014-03-27
Hi lykwydchykyn, When I went to key pounding that is just what I done I changed every board after going and changing every program in Tools. So as to "brute-force", well it just did not work for me, I tried it..........Pat

---

### Post by lykwydchykyn on 2014-03-27
Maybe this board is a dud?  You said you got it off Ebay?

---

### Post by patsroom on 2014-03-27
Hello, To answer you, it is yes I did get it from e-Bay and it could be a dud, But I will keep trying I quess till I tire of it. I hope that if anyone has any ideal as to how to get it to work I am willing to try..............Thanks Pat:sad:

---

### Post by squakie on 2014-03-28
can you post back the entire file name of the file that was downloaded?

also - if you can wait a week before I can mail it (on disability and no money until next Thursday April 3) - I have a SParkfun Arduino Uno, a power supply for it and a Parallax Passive Infared detector I can send to you IF you are in the US.  Won't ship it outside the U.S..  (was going to make a detector and trigger a spray of air freshener after my cat had entered then exited the litter box ;)  Unfortunately that cat died and the one I have now isn't quite so odiferous.)

---

### Post by squakie on 2014-03-28
Well, I went to the site and downloaded it myself to see if I can walk you through getting it installed.  On the first page that comes up following that link, I chose the topmost version of the software.  This went to a 2nd screen that shows 3 files - you need the dfu-programmer-0.6.2.tar.gz file (the zip file is for Windows according to the readme file). Click on that file to start the download.  When the download finishes, open up the file manager (if you are running one of the later Ubuntu's, it should be in the menus).Double-click on the "Downloads" folder, then double click on the file "dfu-programmer-0.6.2.tar.gz".  This should start the install process and you should be able to follow the on-screen instructions to do so.  Once that is done, check the menus for the dfu-programmer.

---

### Post by patsroom on 2014-03-28
Hello squakie, So sorry to hear of your pet's death. Like you I know about disablity and the lower on money thing. As I have to watch my Ps and Qs on it as well, I quess that is why I having a hard time giving up on 12 dollar arduino](*,):p.
I am going back to the site and try again. Thank you so much for your time.......Pat

---

### Post by patsroom on 2014-03-28
Again Hello to all, Well I download the file and then exacted it in place when I open the little box it came in. That is when it asked if I want to exact it so I did. Is that how it is done? I hope so and again Thanks to all for all the help I have been getting...Pat

---

### Post by squakie on 2014-03-28
Yes, that would unpack it to the folder "dfu-programmer-0.6.2" in the "Downloads" folder.  Before you can use it, some addition steps are needed.  If you read the readme file in that folder it will give you those instructions.  Briefly, what you need to do is:

[LIST]
[*]open a terminal window (ctrl/alt/t) where you get access to the command line
[*]type:
[LIST]
[*]cd Downloads <press enter>
[*]cd dfu-programmer-0.6.2 <press enter>
[*]./configure <press enter>
[*]make <press enter>
[*]sudo make install <press enter> The password is your normal password and won't be echoed on the screen.
[/LIST]
[/LIST]

If any type of error messages come up please post them back here and I'll see if I can help.


The dfu-programmer should now be in the menus.

BTW - if you want the hardware I mentioned it is free as I have no use for it anymore.  Send me a Private Message with your name and address (remember, U.S. only) and I'll ship it out next Thursday or Friday.

---

### Post by patsroom on 2014-03-29
Hi again to all, well I tried the above then type my password in. I am not sure what I am suppose to see or what to hunt for. So here I am back again............Thank you.Pat
pat@pat:~/Downloads/dfu-programmer-0.6.2$ sudo make install
[sudo] password for pat: 
Making install in src
make[1]: Entering directory `/home/pat/Downloads/dfu-programmer-0.6.2/src'
gcc -DHAVE_CONFIG_H -I.    -Wall -g -O2 -I/usr/include/libusb-1.0 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
main.c:27:20: fatal error: libusb.h: No such file or directory
compilation terminated.
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/pat/Downloads/dfu-programmer-0.6.2/src'
make: *** [install-recursive] Error 1
pat@pat:~/Downloads/dfu-programmer-0.6.2$

---

### Post by coldcritter64 on 2014-03-30
> **patsroom said:**
> Hi again to all, well I tried the above then type my password in. I am not sure what I am suppose to see or what to hunt for. So here I am back again............Thank you.Pat
pat@pat:~/Downloads/dfu-programmer-0.6.2$ sudo make install
[sudo] password for pat: 
Making install in src
make[1]: Entering directory `/home/pat/Downloads/dfu-programmer-0.6.2/src'
gcc -DHAVE_CONFIG_H -I.    -Wall -g -O2 -I/usr/include/**libusb-1.0** -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
main.c:27:20: fatal error: **libusb.h: No such file or directory**
compilation terminated.
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/pat/Downloads/dfu-programmer-0.6.2/src'
make: *** [install-recursive] Error 1
pat@pat:~/Downloads/dfu-programmer-0.6.2$

Your install appears to be missing the header files for libusb and you are trying to build a package that is looking for it.

Run the following code in terminal,
```
apt-cache policy libusb-dev
```

When I run this code on my Debian install I get:
> ```
yeti:~ $ apt-cache policy libusb-dev
libusb-dev:
  Installed: (none)
  Candidate: 2:0.1.12-20+nmu1
  Version table:
     2:0.1.12-20+nmu1 0
        500 http://ftp.au.debian.org/debian/ wheezy/main amd64 Packages
                                                                      [  OK  ] 
yeti:~ $
```

If you get a similar result when you run the code above, (Installed: (none) ) 

Install the package with ...
```
sudo apt-get install libusb-dev 
```

Then run the make command that previously failed again.
 Cheers, coldcritter64

Edit: @ OP, +1 to squakie's next post, install build-essential as well.

---

### Post by squakie on 2014-03-30
yes, all you need to do is install the development files for libusb..  You can do this either withe apt-get shown above, or through the package manager.   While not needed directly,  you should also install the build-essential package - it installs some dependencies that are useful for compiling a program.  

As a short explanation for why you need libusb-dev:

The "make" is actually compiling the program from source code.  The program obviously uses the libusb functions to "talk" over the USB interface to the Arduino.  In order to compile such a program, libusb-dev must be installed as it includes the headers, etc., needed for compiling a program using libusb.

Sorry I didn't think of that - it's always one of the first packages I install after installing Ubuntu on my systems because of what I have coded in the past and still try my hand at now and then with USB devices.

So, to recap, do the following in a terminal window:

sudo apt-get install libusb-dev build-essential

EDIT:  when that it done, you'll need to rerun the configure, make and then make install.

---

### Post by patsroom on 2014-04-01
Spent the time re-doing startiing from what [**[COLOR=#000000]coldcritter64[/COLOR]**]("http://ubuntuforums.org/member.php?u=1722380") had suggested then I  re-ran the configure, make and then make install part as what [**[COLOR=#000000]squakie[/COLOR]**]("http://ubuntuforums.org/member.php?u=1741485") said.
But still no, I think the libusb file did not take but not sure, Thanks to all time you guys have invested, I hope to be able to repay it in time...........Pat

pat@pat:~$ apt-cache policy libusb-dev
libusb-dev:
  Installed: 2:0.1.12-20
  Candidate: 2:0.1.12-20
  Version table:
 *** 2:0.1.12-20 0
pat@pat:~$ sudo apt-get install libusb-dev
       ( brunch of code lines)
libusb-dev is already the newest version.
pat@pat:~/Downloads/dfu-programmer-0.6.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
        (removed only the positive lines for this code)
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking for gcc option to accept ISO C89... none needed
using libusb_1.0
checking for ANSI C header files... no
checking stdlib.h presence... no
configure: WARNING: stdlib.h: accepted by the compiler, rejected by the preprocessor!
configure: WARNING: stdlib.h: proceeding with the compiler's result
checking for GNU libc compatible malloc... no
checking for working memcmp... no
make[2]: Entering directory `/home/pat/Downloads/dfu-programmer-0.6.2/src'
gcc -DHAVE_CONFIG_H -I.    -Wall -g -O2 -I/usr/include/libusb-1.0 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
main.c:27:20: fatal error: libusb.h: No such file or directory
compilation terminated.
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/pat/Downloads/dfu-programmer-0.6.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/pat/Downloads/dfu-programmer-0.6.2/src'
make: *** [all-recursive] Error 1
pat@pat:~/Downloads/dfu-programmer-0.6.2$ sudo make intall
make: *** No rule to make target `intall'.  Stop.
pat@pat:~/Downloads/dfu-programmer-0.6.2$ sudo make install
Making install in src
make[1]: Entering directory `/home/pat/Downloads/dfu-programmer-0.6.2/src'
gcc -DHAVE_CONFIG_H -I.    -Wall -g -O2 -I/usr/include/libusb-1.0 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
main.c:27:20: fatal error: libusb.h: No such file or directory
compilation terminated.
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/pat/Downloads/dfu-programmer-0.6.2/src'
make: *** [install-recursive] Error 1
pat@pat:~/Downloads/dfu-programmer-0.6.2$

---

### Post by squakie on 2014-04-02
I suspect this is a case of the make looking in a different folder from where the libusb-dev headers, etc., got installed.  Without looking at the entire configure and make to see what it is setting up it would be hard to tell.

If you want to just wait, I'll be sending out the Arduino Uno tomorrow so it shouldn't take too long to get there.

---

### Post by squakie on 2014-04-05
I mailed everything late this afternoon.  I would think it would be there by maybe Tuesday or Wednesday.  Hope you enjoy it!

---

### Post by squakie on 2014-04-05
BTW - did you install the build-essential package as I recommended and retry it all?

---

### Post by patsroom on 2014-04-05
[**[COLOR=#000000]squakie[/COLOR]**]("http://ubuntuforums.org/member.php?u=1741485") "did you install the build-essential package as I recommended and retry it all?"  While I have alittle time I think that would be a good idea while I wait. And I Thank You very much for the shipment. I will let you know when it gets here.
Thank You.............Pat

---

### Post by patsroom on 2014-04-08
[**[COLOR=#000000]squakie[/COLOR]**]("http://ubuntuforums.org/member.php?u=1741485") Thank you so much! The package arrived today and was loaded with so much, again all I can say is Thank You.
I am now reloading my ubuntu then I will re-install the Arduino programmer tomorrow...............Pat

---

### Post by steeldriver on 2014-04-08
Haven't read the whole thread but just wanted to throw in that the configure error

```

gcc -DHAVE_CONFIG_H -I.    -Wall -g -O2 -I**/usr/include/libusb-1.0** -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
main.c:27:20: fatal error: **libusb.h**: No such file or directory

```

suggests it's missing **libusb-1.0-0-dev** (not the same package as libusb-dev - at least not on my system)

```

$ apt-file search '/usr/include/libusb-1.0/libusb.h'
libusb-1.0-0-dev: /usr/include/libusb-1.0/libusb.h

```

---

### Post by squakie on 2014-04-08
Thanks steeldriver - I missed that.  I'm so used to installing all of that right away on a new install that it just didn't come to mind!  

OP - the only reason I mentioned build-essential is that even though it says in the description that it is for building packages it has some dependencies it installs (or maybe I should say it worked this way the last time I paid any attention ;).  Those dependencies at least used to include things like the linux headers (not to be confused with the libusb headers), the compilers, etc.  I suspect some of this may have changed but again it's just a package I install right away when I've done a fresh install.

I think steeldriver hit it on the button for you!

BTW - you're welcome for the Arduino stuff.  Just play it forward sometime if you can with some piece of hardware you are no longer using.  Another member did this for me a few years ago when I was in desparate need of an external modem and couldn't afford one.  I'm just trying to follow in his footsteps and be even 1/4 the person he is - thanks Larry! ;)

---

### Post by patsroom on 2014-04-09
It's Alive!:lolflag:.   I guess I had a very dead chip on my board, moved chips around and the board did work so now I know that all this hard work _did_ pay off. I learned from all of this and with the help I was able to install the needed software. Thank You to all so much and thank you to the forum for being here to help everyone here. And a very special Thanks again goes out to [**[COLOR=#000000]squakie[/COLOR]**]("http://ubuntuforums.org/member.php?u=1741485").

---

