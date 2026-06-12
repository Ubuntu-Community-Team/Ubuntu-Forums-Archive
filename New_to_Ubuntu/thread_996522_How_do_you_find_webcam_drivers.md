---
title: "How do you find webcam drivers?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by suomalainen on 2008-11-28
Ubunteros,

I ran the lsusb command in terminal to find out more about my webcam and received the following info:


Bus 002 Device 004: ID 04c1:009d U.S. Robotics (3Com) HomeConnect WebCam [vicam]

But then in Ubuntu & Google I try to search for drivers and can't find anything.

Maybe I'm searching the wrong way? What should I be doing?


Thanks!

---

### Post by abeisgreat on 2008-11-28
If you haven't already, upgrade to 8.10. 2.6.27 solved all my webcam issues

---

### Post by suomalainen on 2008-11-28
Yea, but 8.04LTS has 3 or 5 year support. IT's really stable too.

---

### Post by abeisgreat on 2008-11-28
I spent several hours trying to get my cam workin in 8.04 with no luck, then it was plug n play in 8.10

---

### Post by suomalainen on 2008-11-28
Thanks but no thanks. I want it installed in 8.04LTS...

---

### Post by loell on 2008-11-28
base on [http://cateee.net/lkddb/web-lkddb/USB_IBMCAM.html](http://cateee.net/lkddb/web-lkddb/USB_IBMCAM.html)

maybe your webcam is ready to be used, have you tried any webcam application yet?

---

### Post by suomalainen on 2008-11-28
loell,

Thanks for the link;

[http://cateee.net/lkddb/web-lkddb/USB_IBMCAM.html](http://cateee.net/lkddb/web-lkddb/USB_IBMCAM.html)

I can see under:

Hardware
USB

Numeric ID (from LKDDb) and names (from usb.ids) of recognized devices: the the following is listed:

vendor: 04c1 ("U.S. Robotics (3Com)"), product: 009d ("HomeConnect WebCam [vicam]")

Running the lsusb command in TERMINAL this appears to match;

Bus 004 Device 002: ID 04c1:009d U.S. Robotics (3Com) HomeConnect WebCam [vicam]

But now I'm at a loss how to move forward or what to do. 

Any suggestions?

---

### Post by suomalainen on 2008-11-28
Forgot to add:

I would like to use my webcam with Skype. As can be seen in the attached pic it appears to be recognized under 'SELECT WEBCAM" but when I click on 'TEST" Skype automatically closes.

I thus need to relaunch Skype to get it running....

Any thoughts why the webcam isn't working???

---

### Post by crazyness003 on 2008-11-28
There are so many things that could have gone wrong. But since Skype is 'seeing' it, maybe you hsould test it in another app. Try Cheese. Its like the Apple PhotoBooth app (only free).
Get it by this command in the terminal (Applications -> Accessories -> Terminal)
```
sudo apt-get install cheese
```
Test it with that, if it dosnt work, then you definitely know the os is not communicating with the webcam.

---

### Post by suomalainen on 2008-11-29
crazyness003,

I installed "CHEESE" and I cannot see any video. However, I also have 'Xawtv' installed and as soon as I launched that program I could see a live webcam video feed...

Is this a good sign?

What next?

---

### Post by suomalainen on 2008-11-29
Regarding 'CHEESE', although I cannot see a live video feed I did use the "mic' to record a audio feed. This part was successful because when I stopped the video recording I could not see any video but could hear my voice.

Does this info help?

---

### Post by loell on 2008-11-29
when i try to look around  for solutions it seems i'm at a dead end :(

is this a fairly old webcam model? the sad news is even previous 4 versions before hardy heron have had this problem.

---

### Post by suomalainen on 2008-11-29
IT"S 10 YEARS OLD but others have it working. and when you read this post it's documented as being supported.

---

### Post by loell on 2008-11-29
> when you read this post it's documented as being supported.

can you post the link so we can have more ideas as to why its not showing any images?

---

### Post by suomalainen on 2008-11-29
Loell, The links are all refered to in this post. Is this ok? When you read from the beginning you will see them.

---

### Post by loell on 2008-11-29
> **suomalainen said:**
> Loell, The links are all refered to in this post. Is this ok? When you read from the beginning you will see them.

oh you mean the "link" i've posted? :)

yes it  said one of the supported but then you can't use it properly, and if you look around further, say gooogling the brand or device id

you'll see

[http://ubuntuforums.org/showthread.php?t=552689]("http://ubuntuforums.org/showthread.php?t=552689")

plus reading at some old mailing list, it would indicate that the driver was made in 2000-2003, this driver may have to be adjusted or fixed to make it work properly.

---

### Post by o.besner on 2008-11-29
This may or may not be useful to you. Only one way to know.

If you are running a 64-bit installation of Linux, Skype has glitches. Tons of 'em. You just need to dodge them one by one.

I'm using Arch Linux on an x86_64 install with kernel 2.6.27 . What I had to do to get skype running is this:

1) Close skype. It must be dead.
2) create a file on your desktop. call it "skype"

3) Copy this inside the newly-created skype file using your favorite text editor (probably gedit) :
--------------------------------------
 
#!/bin/bash

SKYPE_BIN_PATH="/usr/bin"
LIBV4L="/opt/lib32/usr/lib/libv4l/v4l1compat.so"

LD_PRELOAD=${LIBV4L} skype

exit 0

-----------------------------
4) save and quit. 
5) launch skype by double-clicking on the "skype" file you just created and by choosing the "Run" option.

Tadam !

Try it. It'll take 5 minutes, and maybe it'll work for you. I had the exact same bug with my cam.

---

### Post by suomalainen on 2008-11-29
o.besner,

I followed your instructions but nothing happened?????

I do have a 64-bit machine.

Everytime I launch Skype-->Options-->Video Devices and test my webcam Skype automatically crashes. Here I mean that Skype automatically closes itself.

I have a 32 bit version of Skype on another machine it too is 8.04LTS and a few moments ago I switched webcams to see what would happen with the 32 bit machine. The result was exactly the same. It too crashed.

---

### Post by o.besner on 2008-11-29
Have you tried starting Skype from the console ?

Open a console and type skype, then make it crash.

What is the error message ?

The console's #1 function in Ubuntu is to see the errors on exit :)

---

### Post by suomalainen on 2008-11-29
o.besner,

Here is what I found via TERMINAL launch of SKYPE.

Does this help you?

pa@pa-desktop:~$ skype
Skype V4L: Failed to set picture format
Skype V4L: Could not find a suitable capture format
Starting the process...
Skype Xv: Xv ports available: 1
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 93
Aborted
pa@pa-desktop:~$

---

### Post by crazyness003 on 2008-11-29
sorry to say this souma, but it may appear that your webcam is not supported. If you can give us some info about it, maybe scour google with that info.
Or maybe try this [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)
Its supposed to find, download, and install your webcam drivers. Worth a shot. It has 32bit and 64bit instructions.

EDIT: Look at this too [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by suomalainen on 2008-11-29
crazyness003, If you look the links within this post the conclusion is that the webcam is supported

Example of a post in this thread includes:

 Re: How do you find webcam drivers?
loell,

Thanks for the link;

[http://cateee.net/lkddb/web-lkddb/USB_IBMCAM.html](http://cateee.net/lkddb/web-lkddb/USB_IBMCAM.html)

I can see under:

Hardware
USB

Numeric ID (from LKDDb) and names (from usb.ids) of recognized devices: the the following is listed:

vendor: 04c1 ("U.S. Robotics (3Com)"), product: 009d ("HomeConnect WebCam [vicam]")

Running the lsusb command in TERMINAL this appears to match;

Bus 004 Device 002: ID 04c1:009d U.S. Robotics (3Com) HomeConnect WebCam [vicam]

But now I'm at a loss how to move forward or what to do.

Any suggestions?


I'm Still working on what you sent me....

---

### Post by crazyness003 on 2008-11-29
Im not exactly sure. But im searching using the vendor: product code you gave (sorry, i didnt see that at first). Evidently, 3com discontinued the product and never released Linux drivers for it. Some dudes at sourceforge tried getting it working, but i dont know if they succeeded. 
See these liks
[http://sourceforge.net/forum/forum.php?thread_id=1097419&forum_id=69637](http://sourceforge.net/forum/forum.php?thread_id=1097419&forum_id=69637)
[http://homeconnectusb.sourceforge.net/](http://homeconnectusb.sourceforge.net/)
[http://sourceforge.net/projects/homeconnectusb](http://sourceforge.net/projects/homeconnectusb)

I think i read that you need to recompile your kernel tho (?) not sure. Check out the SF page. 
also what kernel number are you. It also seem like there hasent been much activity there, so your mileage may vary. Sorry. Thats all i could find.

---

### Post by suomalainen on 2008-11-29
Crazyness003,

Can you look this link please:

[http://www.digi.com/products/videosensors/watchportcameras.jsp](http://www.digi.com/products/videosensors/watchportcameras.jsp)

It looks like the same camera just new name...

---

### Post by crazyness003 on 2008-11-29
it is the same. If you look at this link [http://homeconnectusb.sourceforge.net/](http://homeconnectusb.sourceforge.net/) in the second paragraph
> Update October 8, 2002: **Discontinued no more!** The ViCam has been resurrected!  Thanks to [inside out networks]("http://www.ionetworks.com/") the [camera is back in production!]("http://www.ionetworks.com/products/watchportv.html").  Kudos to ionetworks for seeing the value in this little camera!  Still among the best on the market!  
But also
> I am still receiving email from people asking if the 3Com HomeConnect WebCam **Lite** is supported...  The answer is **NO**.  These two cameras, although both manufactured by 3Com, are **not** based on the same hardware.  None of the development team has a HomeConnect Lite, so we have no way of developing a driver for it. 
Its the same camera...but different/updated hardware.

Dunno how this is gonna help.

---

