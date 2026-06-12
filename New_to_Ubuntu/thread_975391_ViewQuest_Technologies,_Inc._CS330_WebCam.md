---
title: "ViewQuest Technologies, Inc. CS330 WebCam"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2008-11-08
I have spent hours upon hours searching these forums on all threads related to the topic and have still found almost nothing.


After typing "lsusb" in the Terminal, I got this:

Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0733:0401 ViewQuest Technologies, Inc. CS330 WebCam
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

After searching info on getting my Intel Create and Share Webcam (which apparently is the CS330 ^ ) I came across several references to spca5xx, but THEN this website said that this has been changed in Gutsy (I originally had Feisty and then upgraded to Gutsy by "Update Manager?" That button on the upper right side.

[https://help.ubuntu.com/community/Spca5xx?action=fullsearch&context=180&value=gspca&titlesearch=Titles](https://help.ubuntu.com/community/Spca5xx?action=fullsearch&context=180&value=gspca&titlesearch=Titles)

The website ^ says this: 

Ubuntu 7.10 (Gutsy), and 8.04 (Hardy)

Since Gutsy the spca5xx driver has been replaced by gspca. If the webcam does not automatically work check that the gspca module has been loaded with

lsmod | grep gspca


so after typing "lsmod | grep gspca"

I get this:

gspca                 608336  0 
videodev               29312  1 gspca
usbcore               138632  4 gspca,ehci_hcd,uhci_hcd

(I have no idea what any of this means) ;) Very much a beginner here.

So After reading around I decided to download Camorama from Synaptic Package Manager. It is now uder Applications. 

When I click it to open the "Camorama" program a window pops up saying this: "Could not connect to video device (/dev/videoO). Please check connection."

So then I downloaded "GyachE Improved" to try out my webcam. After going to the Actions Menu and Selecting "Start My Webcam..." I get a window that pops up saying: "GyachI (Webcam Broadcaster): An error occurred at 'ioctl VIDIOCSPICT'. Could not set camera properties."

So basically, how do I get to use my webcam? What do I have to do? It worked fine with Windows ME with the windows driver and Create and Share software they gave me way back when.

But I am not sure how to use this thing in Ubuntu 7.10,  Someone please help, as I have gone ALL OVER this forum and nothing has worked, and I'm downright exhausted of searching the "Entire Internet" more than a few times :p

Thx

---

### Post by hansdown on 2008-11-08
Hi DesiArnez6.

I found some good answers  [http://www.google.ca/search?q=ViewQuest+Technologies%2C+Inc.+CS330+WebCam+in+ubuntu+7.10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=ViewQuest+Technologies%2C+Inc.+CS330+WebCam+in+ubuntu+7.10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Have you tried gqcam? It's in the repositories.

Hope this helps.

---

### Post by DesiArnez6 on 2008-11-08
> **hansdown said:**
> Hi DesiArnez6.

I found some good answers  [http://www.google.ca/search?q=ViewQuest+Technologies%2C+Inc.+CS330+WebCam+in+ubuntu+7.10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=ViewQuest+Technologies%2C+Inc.+CS330+WebCam+in+ubuntu+7.10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Have you tried gqcam? It's in the repositories.

Hope this helps.

ok, sounds good, I downloaded "gqcam" from Synaptic package manager, then typed "gqcam" into the Terminal. 

The response was "/dev/video: No such file or directory" 

So, I clicked on the link you provided to the Google Canada page and the 3rd link was one that I hadn't coma across.  It was: [http://forum.skype.com/index.php?act=Print&client=printer&f=153&t=101297](http://forum.skype.com/index.php?act=Print&client=printer&f=153&t=101297)

After reading downward I found this: 

"I did a
CODE
sudo ln -s /dev/video0 /dev/video

and then I can see myself when I use
CODE
gqcam"

So I went back to the Terminal and decided to type: 
"ln -s /dev/video0 /dev/video" and I get:
"ln: creating symbolic link `/dev/video' to `/dev/video0': Permission denied"

So then I tried to type the following into the Terminal:
"sudo ln -s /dev/video0 /dev/video"
then password


...OK seemed to work... so I typed "gqcam" into the Terminal, and...

"/dev/video: Permission denied"

Sigh... Ok, now I'll try "sudo gqcam"
than password...

BRAVO.. REALLY Bad quality, BUT, Webcam seems to work.

so I try clicking on the Camorama Icon from "Applications Menu"

...Same error as before from my 1st post.

so now I try "sudo camorama" in the terminal...AND....

IT Works?!?!?!??


Hmm. I guess my question is, WHY must I open the program with sudo from Terminal to get it to work?

---

### Post by hansdown on 2008-11-08
That does seem odd.

I have a logitec quickcam pro 9000, and all it needs is to use cheese.
Are you able to click applications> graphics> and just click gqcam to start it?

---

### Post by DesiArnez6 on 2008-11-10
Nope, Gqcam doesn't show up in My Applications Menu, It can only be opened in the Terminal with sudo command.

Also tried to download "cheese", same issue, but terrific webcam quality. Downside is that all photos are saved into the root, which makes deleting or moving files around a real pain (having to use the terminal and "sudo su" for everything)

Also realized that Gyachi workes fine from the Applications Menu, but the error still comes up when trying to start webcam....
However.... If I start Gyachi with "sudo" in the Terminal, then the Webcam screen DOES launch, but with a pink screen only, and it refuses to actually broadcast.

So for now I'm able to at least take pictures with cheese which automatically save to root.. complicated but better than nothing

AND, I'm still unable to BROADCAST my webcam in Gyachi (I can see OTHER peoples webcams just fine)


:) At least I made SOME Progress :p

---

### Post by loell on 2008-11-10
you really need to upgrade to either 8.04 or 8.10 , it can  make the difference in detecting your webcam work properly. :)

---

### Post by aias on 2008-11-11
I have the same camera (Intel Create and Share). it works well out of the box with 8.04 (I run Kubuntu - so I used kopete to check that it works).  I also installed Skype which shows the webcam working.  However, I tried running the live version of 8.10 and all I get is a nice black window where the output from the webcam should be.  I have not found anything about how to get it working under 8.10 which is why I am still using 8.04.

---

