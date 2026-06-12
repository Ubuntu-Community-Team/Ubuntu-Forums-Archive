---
title: "I need a script (or anything) that will disable auto exposure for a UVC usb camera"
date: 2009-09-22
forum: Programming Talk
---

### Post by Nate_is_cool on 2009-09-22
I don't care what it is but I need it. Something that will disable auto exposure/priority. My camera gets about 3-4fps with it enabled. Without it I get 10+fps. Can someone hepl me PLEASE?!

Much thanks

---

### Post by Zugzwang on 2009-09-23
Have you had a look into the documentation and/or source code of your UVC cam's driver?

---

### Post by Nate_is_cool on 2009-09-23
Honestly, I have no clue how where to find it. If you can post a link I will compile it. I'm just not all to sure what to change in it. I think its something to do with shutter speed. Any help please?

---

### Post by Zugzwang on 2009-09-23
Step 1: Plug in your device
Step 2: Type "dmesg" in the terminal to find out the name of the driver
Step 3: Google for it.

---

### Post by Nate_is_cool on 2009-10-01
Sorry for not understanding this but i typed in dmesg and i got alot of ouput. only thing related to my cameras is 

[   10.448261] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a5)
[   10.469067] input: UVC Camera (046d:09a5) as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input6
[   10.477577] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a5)
[   10.498207] input: UVC Camera (046d:09a5) as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input7


i also found an article on how to disable it, but it doesn't specify where to input these commands

[http://forums.quickcamteam.net/showthread.php?tid=182](http://forums.quickcamteam.net/showthread.php?tid=182) 

I'm not all to good when it comes down to the kernel and driver layer of linux. sorry for any stupid questions.

---

### Post by Zugzwang on 2009-10-01
> **Nate_is_cool said:**
> 
i also found an article on how to disable it, but it doesn't specify where to input these commands

[http://forums.quickcamteam.net/showthread.php?tid=182](http://forums.quickcamteam.net/showthread.php?tid=182) 

I'm not all to good when it comes down to the kernel and driver layer of linux. sorry for any stupid questions.

Oh, these commands are for the terminal, but they require a program that is not part of the standard linux distribution.

You can however try to compile it yourself and check those commands. You can download the sources here: [http://www.quickcamteam.net/software/libwebcam](http://www.quickcamteam.net/software/libwebcam)

Good luck!

---

### Post by Nate_is_cool on 2009-10-01
Alright so I edited the source code and added Exposure auto to 0.

now all i need to do is 
./configure 
make
make install

is that correct?

Will i have to do this everytime I restart or is it permanent (up until they update the driver of course)

Thank you for the support

---

### Post by Nate_is_cool on 2009-10-08
I still am having problems on what to do. I am very simple when it comes to drivers in linux. I installed some software but I can't  seem to find anything. Can someone just please fix this. Its really annoying and I've tried searching google but nothing comes up

---

### Post by Zugzwang on 2009-10-09
The point is the following. According to the web-site you referred to, you will not need to modify the driver. Instead, there is a utility ("uvcdynctrl") which will modify some parameters for you. You have to compile it first. I'm trying that right now for you....

There seems to be a little bug, described in [http://forums.quickcamteam.net/archive/index.php/thread-181.html](http://forums.quickcamteam.net/archive/index.php/thread-181.html). I'll integrate the quick fix.

by reading the README-file and the post mentioned above, I came up with the following list of commands to compile this tool. You might need in install some packages to get it running (like libxml2-dev).
```

cd /tmp
mkdir webcam
cd webcam
wget http://www.quickcamteam.net/dev/libwebcam-0.1.1.tar.bz2
tar xfv *.bz2
svn co -r178 http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk
cp trunk/uvcvideo.h libwebcam-0.1.1/Common/include
cp trunk/uvc_compat.h libwebcam-0.1.1/Common/include
cd libwebcam-0.1.1
cmake .
make

```
The control program is then located in "/tmp/webcam/libwebcam-0.1.1/Apps/Apps/uvcdynctrl". After compilation, you might want to copy it somewhere else such that it doesn't get deleted when restarting the computer. You do not need to rebuild it every time you restart the computer.

---

### Post by Nate_is_cool on 2009-10-13
OK so I did all that and i still get 

ERROR: Unable to set new control value: A Video4Linux2 API call returned an unexpected error 5. (Code: 12)

when i input 

uvcdynctrl -s "Exposure, Auto" 0

what could this mean??

---

### Post by Nate_is_cool on 2009-10-13
im going to continue to bumb until i either get banned or someone answers my question.
 :guitar:

---

### Post by Nate_is_cool on 2009-10-14
bumped....

---

### Post by Zugzwang on 2009-10-14
I'm afraid that nobody here will know the answer. You might want to consider using an older version of the driver. I think, there's some information on building the driver as a kernel module yourself on the web pages you mentioned.

Other than that, "internal errors" are what they are - internal errors. You will need to ask someone knowing the internals to solve that problem. Probably you have a look if there are Video4Linux mailing lists or if not, you might want to consider writing an e-mail to someone of the authors of some of the programs/drivers involved in this issue.

---

### Post by Nate_is_cool on 2009-10-14
No hate or anything But im going to try Fedora. I think the problem lies in Ubuntu its self

---

### Post by Zugzwang on 2009-10-15
> **Nate_is_cool said:**
> No hate or anything But im going to try Fedora. I think the problem lies in Ubuntu its self

This is rather unlikely. By reading the stuff behind the links in this thread, you will see that the problem is that the writers or video4linux and/or uvcvideo have changed something in the API and the writers of the control utility and the library behind it haven't updated their library (yet?). You will see this problem with every distribution that uses the newer drivers. As Ubuntu is actually comparably slow with updating drivers (in my oppinion), you're unlikely to have more luck with other distributions.

---

### Post by andersja on 2010-09-24
FYI I think libwebcam is now packaged in the Ubuntu repositories for Maverick.

This should work in the terminal:

```
sudo aptitude install uvcdynctrl
```

bugs can be filed against it here:
[https://launchpad.net/ubuntu/+source/libwebcam](https://launchpad.net/ubuntu/+source/libwebcam)

More info on usage here:
[http://forum.skype.com/index.php?showtopic=152201](http://forum.skype.com/index.php?showtopic=152201)

See also:
[https://bugs.launchpad.net/ubuntu/+bug/394635](https://bugs.launchpad.net/ubuntu/+bug/394635)

---

### Post by Elfy on 2010-09-24
Closed - OP has not been here since February and is likely not using a dev version.

---

