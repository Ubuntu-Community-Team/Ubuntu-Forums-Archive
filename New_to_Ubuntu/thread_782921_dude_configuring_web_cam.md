---
title: "dude configuring web cam"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by viswanathan on 2008-05-05
well all that i know about my web cam is its creative live on writing this i am installing my camorama what else how to procced from here well my lsusb out put is some what like this```
root@maplye-desktop:~# lsusb
Bus 004 Device 002: ID 05ac:120a Apple Computer, Inc. iPod Nano
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 041e:4067 Creative Technology, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

any info would be of great help :lolflag:

---

### Post by joshsmith on 2008-05-05
try the program cheese too, it is cooler

what do you want to do with your webcam? you didnt say. on ubuntu things generally just work

---

### Post by viswanathan on 2008-05-05
well my web cam is creative live the worst part is my cam is not gettng detected camorama easycam2 every apllication r stating the same problem ```
could not connect to video devices (/dev/video0). please check the connections
```  this is my lsusb out put see here the web cam is detected but i ant figure out what is the problem ```
root@maplye-desktop:~# lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 041e:4067 Creative Technology, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
root@maplye-desktop:~# 
```

plzzzzzz helllllppppp my dad is already mad at me rght now :(

---

### Post by TeoBigusGeekus on 2008-05-05
What is the specific model of your webcam: Optia,Vista or something else?

---

### Post by tamoneya on 2008-05-05
The first thing you need to do is to calm down.  We will help you out as best as we can and posting three seperate threads is not going to help you at all.

Have you tried looking at these posts?
[http://ubuntuforums.org/showthread.php?t=78370](http://ubuntuforums.org/showthread.php?t=78370)
[http://ubuntuforums.org/showthread.php?t=343067](http://ubuntuforums.org/showthread.php?t=343067)
[http://ubuntuforums.org/showthread.php?t=700439](http://ubuntuforums.org/showthread.php?t=700439)

They all seem to have similar problems to you.  See how far along on those you get.  If you get stuck or run into errors post them here and we will get this resolved.

---

### Post by viswanathan on 2008-05-06
soory dude about posting posts 3 times my father was really pissed thats the reason

---

### Post by viswanathan on 2008-05-06
> **joshsmith said:**
> try the program cheese too, it is cooler

what do you want to do with your webcam? you didnt say. on ubuntu things generally just work


i just wanna web cam to work in skype coz most of the time m father wld use skype for his office work

---

### Post by viswanathan on 2008-05-06
> **tamoneya said:**
> The first thing you need to do is to calm down.  We will help you out as best as we can and posting three seperate threads is not going to help you at all.

Have you tried looking at these posts?
[http://ubuntuforums.org/showthread.php?t=78370](http://ubuntuforums.org/showthread.php?t=78370)
[http://ubuntuforums.org/showthread.php?t=343067](http://ubuntuforums.org/showthread.php?t=343067)
[http://ubuntuforums.org/showthread.php?t=700439](http://ubuntuforums.org/showthread.php?t=700439)

They all seem to have similar problems to you.  See how far along on those you get.  If you get stuck or run into errors post them here and we will get this resolved.
[B]
dude what ever i do i get the same error " could not connect to viedo devices (/dev/video0) please check connection [/B]

---

### Post by viswanathan on 2008-05-06
guys this may be irritating but i really need hrlp i tried out camorama easycam2 cheese everything giving only 1 response could not locate /dev/viedo0/


dude plllllllzzzzzzzzzz my father wld be here by evening 5 ist and he would screw very badly coz i was d one who removed windows and installed ubuntu

---

### Post by inportb on 2008-05-06
Geez... 4 posts in a row would not get you faster responses. Chill on the anxiety, because it's distracting you.

Have you read this? [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by viswanathan on 2008-05-06
easycam2 bro yes tried it but error is as follows ```
No camera, or no compatible camera found
```

---

### Post by subzero316 on 2008-05-06
hope this helps,
download and install drivers from here.
[URL="Creative driver link"]
http://opensource.creative.com/webcam.html[/URL]

---

### Post by viswanathan on 2008-05-06
dude i dont know what version is my webcam it was presented from my sister

---

### Post by TeoBigusGeekus on 2008-05-06
I have a Creative Live Cam Vista which used to work with Skype following directions from this page
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

After a kernel update, it just stopped working. 

With the latest Skype version it makes Skype crash...

The Skype guys are working on a new beta, so I put my hopes on that one...

You could find a possible solution in the page I gave you, although the solutions mentioned there might not work if you are using Hardy or have updated Gutsy to the latest kernels.

Suggestion 1:
You find a camera from this page that "simply works" and buy it. Avoid Logitech Quickcams - too dark to see anything...

Suggestion 2:
Find the specific model of your camera and try the drivers mentioned in the page. Who knows, you might be lucky...

---

### Post by frodon on 2008-05-06
some users have reported your webcam to work with ov51x drivers.

Sources :
[http://forum.ubuntu-fr.org/viewtopic.php?id=85263](http://forum.ubuntu-fr.org/viewtopic.php?id=85263) (post #14)
[http://forum.ubuntu-it.org/index.php?topic=145684.msg1114047](http://forum.ubuntu-it.org/index.php?topic=145684.msg1114047)

If you want to try this here are the instructions, open a terminal and type the following :
```
mkdir webcam-driver
svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver
cd webcam-driver
sudo apt-get install linux-headers-`uname -r`
make
sudo make install
sudo modprobe ov51x-jpeg
```You may need the build-essential package to be able to compile the drivers.

---

### Post by viswanathan on 2008-05-06
```
Creative Live! Cam Optia 7.10  041e:4057   uvcvideo     
```
```
Works fine after installing the [WWW] uvc driver 
```

and the happy news is sir ```
Bus 003 Device 002: ID 041e:4067 Creative Technology, Ltd 

```

now i tried installing uvc drivers hrough subversion and is in my home folder now what to do sir ????????

---

### Post by viswanathan on 2008-05-06
> **frodon said:**
> some users have reported your webcam to work with ov51x drivers.

Sources :
[http://forum.ubuntu-fr.org/viewtopic.php?id=85263](http://forum.ubuntu-fr.org/viewtopic.php?id=85263) (post #14)
[http://forum.ubuntu-it.org/index.php?topic=145684.msg1114047](http://forum.ubuntu-it.org/index.php?topic=145684.msg1114047)

If you want to try this here are the instructions, open a terminal and type the following :
```
mkdir webcam-driver
svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver
cd webcam-driver
sudo apt-get install linux-headers-`uname -r`
make
sudo make install
sudo modprobe ov51x-jpeg
```You may need the build-essential package to be able to compile the drivers.



sir what is 'uname -r '

---

### Post by TeoBigusGeekus on 2008-05-06
[http://ubuntuforums.org/showthread.php?t=593231]("http://ubuntuforums.org/showthread.php?t=593231")

Best of luck!

---

### Post by viswanathan on 2008-05-06
any 1 'uname -r ' im totally new to linux and i dont know whta this is well i did as sir frodon told me to and this is the error what i got 


```
maplye@maplye-desktop:~$ mkdir webcam-driver 
maplye@maplye-desktop:~$ svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver
A    webcam-driver/test
A    webcam-driver/test/getjpeg.c
A    webcam-driver/test/Makefile
A    webcam-driver/ov511-decomp.c
A    webcam-driver/ChangeLog
A    webcam-driver/ov518-decomp.c
A    webcam-driver/ov519-decomp.c
A    webcam-driver/ov51x-jpeg.h
A    webcam-driver/ov51x-jpeg-core.c
A    webcam-driver/Makefile
A    webcam-driver/ov7670.h
Checked out revision 101.
maplye@maplye-desktop:~$ cd webcam-driver 
maplye@maplye-desktop:~/webcam-driver$ sudo apt-get install linux-headers-'uname -r'
[sudo] password for maplye: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r
maplye@maplye-desktop:~/webcam-driver$ 


```

---

### Post by TeoBigusGeekus on 2008-05-06
You don't need the ov51x drivers, you need the uvc driver. Follow the directions from my last post.

---

### Post by TeoBigusGeekus on 2008-05-06
Hey, wait a moment!!!

Live Cam Optia is 4057 and you have 4067. If the uvc does not work try the ov51x driver...

---

### Post by viswanathan on 2008-05-06
not working sir same problem cant /dev/viedo0

---

### Post by viswanathan on 2008-05-06
thanxxxxxxxxx thanxxx a looootttttttttttt guys 


but there is no colour in my web cam what might be d problem

---

### Post by viswanathan on 2008-05-06
guys guys plzzzzzzzzzz colour there is nly 30 minutes b4 my father comes

---

### Post by steveneddy on 2008-05-06
You have really got to get a grip. 

We all help here for free and no one likes to be pestered into helping anyone.

Maybe some of the links posted have something on there that you could read and figure out the problem yourself.

Posting every 10 minutes begging for help will not help your cause.

Have you tried Googling the problem?

---

### Post by TeoBigusGeekus on 2008-05-06
Which driver worked at the end?

---

### Post by viswanathan on 2008-05-06
ov51x

---

### Post by TeoBigusGeekus on 2008-05-06
Try this:

```
gksudo gedit /etc/modprobe.d/options
```

Add this line at the end

```
options ov51x-jpeg force_palette=13
```

save and do a restart.

---

### Post by viswanathan on 2008-05-06
thnx dude it helped

---

### Post by TeoBigusGeekus on 2008-05-06
Everything solved? Camera works with Skype?

---

### Post by viswanathan on 2008-05-06
y sir if webcam works with cheese it dosent work with skype ???????? coz i dnt use lot of skype new to it :lolflag:

---

### Post by tamoneya on 2008-05-06
> **TeoBigusGeekus said:**
> I have a Creative Live Cam Vista which used to work with Skype following directions from this page
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

After a kernel update, it just stopped working. 

With the latest Skype version it makes Skype crash...

The Skype guys are working on a new beta, so I put my hopes on that one...

You could find a possible solution in the page I gave you, although the solutions mentioned there might not work if you are using Hardy or have updated Gutsy to the latest kernels.

Suggestion 1:
You find a camera from this page that "simply works" and buy it. Avoid Logitech Quickcams - too dark to see anything...

Suggestion 2:
Find the specific model of your camera and try the drivers mentioned in the page. Who knows, you might be lucky...
As TeoBigusGeekus said it is a bug in skype and the current kernel.  If new skype linux beta comes out you could always try that and you may get better results.

---

### Post by inportb on 2008-05-08
btw, it's `uname -r`
not 'uname -r'

(i hope it helps you in the future)

---

### Post by TeoBigusGeekus on 2008-05-31
[http://ubuntuforums.org/showthread.php?t=794466]("http://ubuntuforums.org/showthread.php?t=794466")

---

