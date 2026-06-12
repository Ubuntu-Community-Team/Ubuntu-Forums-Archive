---
title: "Howto : Quickcam Messenger"
date: 2006-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by encompass on 2006-06-07
Let me start by saying this howto would have never happened had it not been for the help of the fallowing people...
Yoriko:	for the original howto for Ubuntu 5.10
sporniket: for shoing how to make the changes work at bootup
Christian Magnusson: for creating the fantastic driver with great improvements.
jarping: for the deb file, found somehow (but bummer it is no longer need)
Is this the driver I need?
What is known to work by the Ubuntuforums is the following:
ID 046d:08f6 Logitech, Inc.

To find out if you have the Camera type:
```
lsusb
```
and the terminal when the camera is plugged in.  If you have it number for number then you have the same exact camera.
If your camera is the Logitec Quickcam Messenger and you have a different output than thatgive this driver a try.  If the driver works you can add your webcam to the list. Please feel free to contact me and I can add it to the list. Your name will also be added to the list of helpers. ¶:

Let's get, extract, and install the files...
You need an external driver outside of what Ubuntu can give.
[http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/)
and down load the latest driver something like  qc-usb-messenger--- get the latest one but nothing that says unstable or testing.
```
tar -xvf qc-usb-messenger-X.X.tar.gz
``` to the file to extract it... HINT: you don't have to type it al ... just the first letters and press the tab key it will complete it for you... cool huh?
Now we need some programs and files from the Ubuntu side fo things..
```
sudo apt-get install build-essentials camorama
```
Type:
```
uname -r
```
Then type..
```
sudo apt-get install linux-headers-2.6......
```
Replacing the ..... with what was said in the uname -r command... 
That should be everything that I used.  Tell me if you think I am missing something.
ok...
```
cd qc-usb-messenger-1.3
sudo su
./quickcam.sh #Go through each step
exit

```
follow the instructions... if you are using the same cam as me you should have no trouble at all... Just when it says that it will try to run something called xawtv don't worry about that... just run camorama from the applications menu to see if the cam works.
If is does work keep going... if it doesn't work tell me.
now...
```
sudo nano /etc/modules
```
and add
```
quickcam
```
to the bottom of that list.
and press 'ctrl-x' to quit and 'y' to save.
reboot and check the camera again with camorama.
Hope it worked for you.
Thanks for reading my howto.
I have used the camera in many ways..
I have setup a live webcam feed using apache and a few other small programs.
I have used it with ekiga, and amsn to chat with friends and family.
And other things.  If you have a cool thin your doing wit your webcam... tell us about it by putting it on your own little howto.

---

### Post by jarping on 2006-06-09
working very well but and build deb´s for ubuntu

[http://kanotix.com/debian/pool/main/q/qc-usb-messenger/](http://kanotix.com/debian/pool/main/q/qc-usb-messenger/)

---

### Post by KaridaSerious on 2006-06-21
I tried this with my Logitech Quickcam Messenger Plus and it worked fine.

046d:08f0 Logitech, Inc. QuickCam Messenger

Thanks!

-KDS

---

### Post by encompass on 2006-06-21
Thanks for the good new... keep it coming!

---

### Post by KaridaSerious on 2006-06-26
The camera worked after install. But after reboot camorama just says "Cannot connect to /dev/video0. Please check your camera connection...". When I type dmesg | grep quickcam it should produce many lines of text referring to detection of my camera, but only thing it prints to screen is this:

---

dmesg | grep quickcam

[17179592.592000] usbcore: registered new driver quickcam.

---
No /dev/video0. What is the reason for this. Why the quickcam module doesn't recognise my camera after reboot?

-KDS

---

### Post by bartekk on 2006-06-26
When I do lsusb i get this output:
ID 046d:0850 Logitech, Inc. QuickCam Web

Not the same as above:ID 046d:08f6 Logitech, Inc.

And the installation fails because he can't find any webcam (whem i'm supposed to push enter all the time)

Is the cam-type difference the reason for faillure?
What can i do now?

Thx voor the howto

---

### Post by author40 on 2006-06-26
Hi encompass,

thanx for your howto. it worked very well.

author40  :p

---

### Post by encompass on 2006-06-26
[QUOTE=bartekk]When I do lsusb i get this output:
ID 046d:0850 Logitech, Inc. QuickCam Web

Not the same as above:ID 046d:08f6 Logitech, Inc.

And the installation fails because he can't find any webcam (whem i'm supposed to push enter all the time)

Is the cam-type difference the reason for faillure?
What can i do now?

Thx voor the howto[/QUOTE]
This howto is for the quickcam messenger, sorry... there is another driver here that will probably work called the qc-something or other.  As I only have this cam... I can't help you any deeper sorry.

---

### Post by encompass on 2006-06-26
[QUOTE=KaridaSerious]The camera worked after install. But after reboot camorama just says "Cannot connect to /dev/video0. Please check your camera connection...". When I type dmesg | grep quickcam it should produce many lines of text referring to detection of my camera, but only thing it prints to screen is this:

---

dmesg | grep quickcam

[17179592.592000] usbcore: registered new driver quickcam.

---
No /dev/video0. What is the reason for this. Why the quickcam module doesn't recognise my camera after reboot?

-KDS[/QUOTE]

Please tell... what installation you did... as I want to fix the problem if it is mine.  Next... check this file for the file quickcam...
```
/etc/modules
```
In addition just to make sure on everything... what is the output of your logitech quickcam messenger when you type... lsusb
Thanks..

---

### Post by roderikk on 2006-06-28
Hi,

Wow, I've been looking all over for this! My webcam (Logitech Quickcam 046d:08f6 ) now works perfectly. Just one tiny problem... when I try to use it in aMSN it doesn 't seem to work. When I go into preferences/configure webcam it says:

```
Listening FALSE
```

Also says it is firewalled even though I opened ports 6890 to 6900. Did anyone get his/her cam working in this fashion on aMSN?

EDIT: When I click 'Change Video Settings' the only option is in devices: V4L: Logitech Quickcam and in Channels: Camera. Clicking Change Video Settings doesn't seem to do anything.

---

### Post by encompass on 2006-06-28
I jsut installed amns, sadly, to test things out.  seems to work fine.  I can select the camera from the list.  PM me your account and I can try to test the cam with you. ¶: I know back in the day when I used the cam for chatting with amsn it worked then too.  Did you check the cam to work with camorama?

---

### Post by roderikk on 2006-06-29
Hi,

Thanks for the reply. However as some suggested I've now installed kopete and it seems to work (most of the times).

One problem I did suddenly get after a second reboot this morning was that I didn't have any sound at all. After removing quickcam from /etc/modules and rebooting again both sound got back ánd the webcam seemed to work. Really strange...

Thanks again, Roderik

---

### Post by Rackerz on 2006-07-03
[QUOTE=roderikk]Hi,

Thanks for the reply. However as some suggested I've now installed kopete and it seems to work (most of the times).

One problem I did suddenly get after a second reboot this morning was that I didn't have any sound at all. After removing quickcam from /etc/modules and rebooting again both sound got back ánd the webcam seemed to work. Really strange...

Thanks again, Roderik[/QUOTE]

Thanks, I'm going to try this out because my webcam wont work on bootup.

---

### Post by roderikk on 2006-07-03
Hi,

Something decidedly strange is happening now with my webcam. Sometimes it works and sometimes it doesn't. Actually the problem seems mostly related with both aMSN and Kopete since they won't give me an image/connection for the webcam most of the times while Camorama always gives me an image.

Something strange which I really don't know how to solve.

---

### Post by encompass on 2006-07-04
sounds like it is a driver issue.  I would post your problem to the creators website.  See if he has any ideas.

---

### Post by Rackerz on 2006-07-04
My webcam driver wont work after I reboot :(.

---

### Post by encompass on 2006-07-04
[QUOTE=Rackerz]My webcam driver wont work after I reboot :(.[/QUOTE]
did you do everything I wrote down?
The loading on boot issue involves the last few steps...
try this to see if the driver even works..
modprobe quickcam
Then test the camera with camoram
tell me if you get any errors and make sure to run camoram in the console too.

---

### Post by Rackerz on 2006-07-05
[QUOTE=encompass]did you do everything I wrote down?
The loading on boot issue involves the last few steps...
try this to see if the driver even works..
modprobe quickcam
Then test the camera with camoram
tell me if you get any errors and make sure to run camoram in the console too.[/QUOTE]

The driver works when I first install it, but after a re-boot it doesn't work. I have  to install it all over again. After reboot Camorama just says 'Could not connect to video device (/dev/video0). Please Check Connection.'

When I do 'modprobe quickcam' nothing happens.

---

### Post by encompass on 2006-07-05
"That should be everything that I used. Tell me if you think I am missing something."
Goto that section of my howto... did you do that... if so make sure you did all of it correctly.  And if you like... send the file here.
I am not getting why your's would have such problems and not anyone one elses.

---

### Post by Rackerz on 2006-07-05
Here is my modules file.

> 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
quickcam

---

### Post by encompass on 2006-07-06
Have you tried the ubuntu deb package?  I have no idea what to do from there.
You could do what the old driver needed... that was..

sudo rmmod quickcam
sudo modprobe quickcam
then check the cam again

if you saw nothing after typing the command it is because the driver was loaded successfully
I haven't the foggiest what to do next...  if that previous command works...  I can show you how to make it run that cammand everytime your boot.
Wish I could help you more.

---

### Post by Rackerz on 2006-07-06
When I try the deb it just says the same version is already installed :(. Those commands don't work either. Nothing comes up when I type them.

Also I noticed when using 1.2 source instead of 1.3 (the latest) the install gives permissions to root. 

crw-rw---- 1 root video 81, 0 2006-07-06 16:59 /dev/video0

Whereas 1.2 gave permission to 'darren' not root. Maybe this has something to do with it?

---

### Post by SWAT on 2006-07-06
Same problem here. It seems no device is automatically created, so logically camorama can't find /dev/video0 because it doesn't exist. lsusb tells me that my camera is recognized and connected and dmesg tells me that the quickcam modules is loaded/registered.
The question remains, how can we (if we have to, manually) create a device that connects to our webcam-hardware?

---

### Post by encompass on 2006-07-06
I say you talk to the creator of the driver.  That would be a good help for him. The driver had a problem loading on boot before.  There was a french(I think) answer to the problem.  You had to rmmod the module and load it again.  You could take it out of the modules list or rmmod it after it loads than load it by hand.  Tell me if that works.

---

### Post by Rackerz on 2006-07-07
How do we do that? Sorry I'm not great with the CLI that's all.

---

### Post by encompass on 2006-07-07
try this...
> 
sudo rmmod quickcam
sudo modprobe quickcam

then check the cam
check about three or four times.... could be it works sometimes and not others.  I checked with camorama.

---

### Post by fragos on 2006-07-07
> **encompass said:**
> try this...

then check the cam
check about three or four times.... could be it works sometimes and not others.  I checked with camorama.

I'm having a similar problem in that no mount point is created.  I installed last night and spent enjoyable time experimenting with it.  With the next reboot the mount point isn't created.  I went over every instruction in your Howto and in this thread.  Everything I do shows the driver as loaded.  I'm running Ubuntu 6.06.  I also have a TV card which consumes video0 so I edited the application menu and set canorama to run with "canorama -d /dev/video1".  No matter what I try I always come to the same problem -- no video1 mount point created.

Any suggestions?

---

### Post by encompass on 2006-07-07
sorry, I hear this driver is a little buggy for some.  I would report these problems to the driver creator on the website I provided in the howto.
Hopefully he can help out.

---

### Post by Rackerz on 2006-07-08
Strange though it is, I had to do a re-install of Ubuntu today followed the howto and much to my suprise the cam works on boot now. Thankyou :).

---

### Post by encompass on 2006-07-09
some other drivers or weird kernels must have been running.  Thaks for telling me though.[-o<

---

### Post by hatman on 2006-07-16
Excellent HOW-TO encompass... big kudos to you for getting my webcam up and running, only problem I have now is that while it works in Ekiga I can't get it to work in Camorama... for some reason that keeps wanting to use the WinTV XP 2000 Expert tv card I've got... It comes up with an error (obviously!) and wont allow me in to change any settings, is there a way of changing the settings on camorama?

---

### Post by encompass on 2006-07-16
not sure if you can select the cam you wont in the program it self, yet ¶:
but you can select it from the command line... camorama -d /dev/video(blabla a number for your cam Probably 0 or 1).
Try that... camorama in my opinion is just for testing it... ekega is for use... so great.  And thanks for the kudos... I am create an live webcam howto.. I will be using vlc live feeds and web-based uses... Check out the live webcam on my server... 84.249.13.146

---

### Post by Rackerz on 2006-07-17
I think sometimes Linux does what Windows does with the quickcam, you can't use it at the same time in different programs. Sometimes I can.

---

### Post by k420 on 2006-07-17
would this howto work on the old quickcam express

---

### Post by encompass on 2006-07-17
> **k420 said:**
> would this howto work on the old quickcam express
no... sorry, and that is a scary dog.

---

### Post by encompass on 2006-07-17
> **Rackerz said:**
> I think sometimes Linux does what Windows does with the quickcam, you can't use it at the same time in different programs. Sometimes I can.
correcto mundo... are you wanting to do that?

---

### Post by k420 on 2006-07-17
> **encompass said:**
> no... sorry, and that is a scary dog.

 what do you mean by that. And i use to have it working but since redone my system and i for got how i did it.

---

### Post by encompass on 2006-07-18
> **k420 said:**
> what do you mean by that. And i use to have it working but since redone my system and i for got how i did it.
I mean... that is a scary looking dog in that picture.
and the camera you are using doesn't work with this driver; is it only made for the Messenger Series of Camera... You could try it, but I wouldn't recommend it... sorry.

---

### Post by DRF on 2006-07-19
k420 I think that the quickcam express works with ubuntu but not with the driver in this howto.

You may find the following pages on the wiki more useful:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Daniel

---

### Post by nekmok on 2006-07-20
hi I'm new to Ubuntu and I run in to some problems when trying to follow this Howto.

with lsusb i get:

Bus 001 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 001 Device 001: ID 0000:0000

I also found "qc-usb-messenger-source_1.1-2_all.deb" via google and installed it (but not with dpkg.. just with some other thing that came up by defult)

this:
wget [http://home.mag.cx/messenger/source/qc-usb-messenger-1.3.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.3.tar.gz)
tar -xvf qc-usb-messenger-1.3.tar.gz

also seem to download and unpack

and the camorama i already have installes (from the synaptic thing)

so far so good (i guess)

but when i try:

sudo apt-get install kernal-headers-2.6.15-26-386

all i get is:

Läser paketlistor... Färdig
Bygger beroendeträd... Färdig
E: Kunde inte hitta paketet kernal-headers-2.6.15-25-386

(E: Couldn't find the package)

... I have all the repositories turned on (with univers, mulitverse)

and now i'm stuck :(


I'm happy for any help with this.

.kristofer

---

### Post by encompass on 2006-07-21
That looks like the right package... but you may want to move to the 686 kernel anyway... go into the synaptic package manager and do a name search for kernel 386 and you should see the kernal headers file that you want to use. If you want to move toe the 686 or k7 kernel you can do it at the time... jst replace the 386 with what ever kernel you want in the search.  This is the old way I did it.  Tonight when I am at my own computer I will do a look into your problem.  Perhaps I have typed something wrong.
Hope this helps you out.  feel free to im me if you want to more person help with the issue.

---

### Post by ScoobyDan on 2006-07-21
> **nekmok said:**
> sudo apt-get install kernal-headers-2.6.15-26-386

nekmok,

The actual package you want is called "linux-headers-*architecture*" (e.g. "linux-headers-386" or "linux-headers-k7"). This is a meta package that will install the headers for your current kernel version. "kernel-headers" packages are only for version 2.4 kernels, not version 2.6.


Now for my question:

encompass,

I installed the drivers following this HowTo exactly, which got my webcam working in Kopete. But, I found that I lost most (if not all) of my audio when I did this.

To try to resolve this, I have disconected the webcam, removed the "qc-usb-messenger-source_1.1-2_all.deb" package, but I still had no audio. I found that one of the four "VIA-DXS" channels on my audio mixer was set to zero (the others at 80%) - and voila! I had audio :D Unfortunately, as soon as I rebooted, I lost audio again, until I re-set the "VIA-DXS" channel.

Is there any way of "uninstalling" the "quickcam.sh" drivers? If not, does anyone have any suggestions how I can get the audio to fix at the same settings?

Many thanks

Daniel

---

### Post by encompass on 2006-07-22
Yeah... I have this problem fixed.. it has to do with your sound card settings.  Go here... and look up the multiple sound card setup...[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)
Remember to have both cards in so that you can see the cards modules loaded.  Hope this helps.:-D

---

### Post by benvdh on 2006-07-24
Hey everyone,

I have tried using the instructions in the first post and they worked untill I rebooted. After reboot /dev/video0 didn't appear anymore. Since the 

sudo rmmod quickcam
sudo modprobe quickcam

instructions didn't work, I did another run of the quickcam.sh script and everything worked once again. After reboot it didn't work again.

So I had a look at the quickcam.sh script itself to see what it did differently from what I was doing (rmmod, modprobe). There I found that when you replace the modprobe command with the insmod command everything is working once again after a reboot.

So the commands to execute after a reboot are:

sudo rmmod quickcam
sudo insmod /lib/modules/2.6.15-26-686/misc/quickcam.ko

The only problem left for me is how to run these commands automatically when the computer boots. So I don't have to do this manually everytime I want to use the webcam.

Regards,

Ben

UPDATE: Just did modprobe -v quickcam(v stands for verbose and I ran this command after I did an rmmod quickcam). And I discovered that modprobe almost does the same as I do in the above instructions only it has some kind of extra parameter: compatible=2.

Here's the complete output:

> ben@ubuntu:~$ sudo rmmod quickcam
Password:
ben@ubuntu:~$ sudo modprobe -v quickcam
insmod /lib/modules/2.6.15-26-686/kernel/drivers/usb/media/quickcam/quickcam.ko compatible=2


So probably compatible=2 is the source of the problem. Don't know how to solve this problem any further though. Maybe someone could reply ?

---

### Post by encompass on 2006-07-24
There is a solution for the problem... I think it could be done two ways... they way you speak of, adding a new script seem to be the way that works mor often but causes your installation to be a little dirty... steps 8,9,10 of [http://ubuntuforums.org/showthread.php?t=126053](http://ubuntuforums.org/showthread.php?t=126053)... but remember it is dirty...  you could try this... 
Make sure that in your /etc/modules file you have quickcam at the end of the file... that "should load the file"  I did that and it works for me.
Hope it helps...

---

### Post by WohthaN on 2006-07-25
Hi everyone, i'm having some trouble with this driver.
The problem: incostant frame flow.
The environment: linux 2.6.17.4 on amd64 whith the device 046d:08f6.
The dmesg: see below.
Any suggestion? I'm a programmer but i have no experience at all with webcams...

Thanks for the help :)

the dmesg:

[ 2848.019875] quickcam [33.015563]: ----------LOADING QUICKCAM MODULE------------
[ 2848.019958] quickcam [33.015792]: struct quickcam size: 4672
[ 2848.020243] quickcam: QuickCam USB camera found (driver version QuickCam Messenger/Communicate USB 1.3 $Date: 2006/06/06 10:00:00 $)
[ 2848.020295] quickcam: Kernel:2.6.17.4GalileO bus:2 class:FF subclass:FF vendor:046D product:08F6
[ 2848.020340] quickcam [33.016845]: poisoning qc in qc_usb_init
[ 2848.021544] quickcam [33.020155]: E00A contains 08F6
[ 2848.021596] quickcam: Sensor VV6450 detected
[ 2848.022162] input: Quickcam snapshot button as /class/input/input6
[ 2848.022299] quickcam [33.022233]: Quickcam snapshot button registered on usb-0000:00:10.0-1.2/input0
[ 2848.022530] quickcam: Registered device: /dev/video0
[ 2848.022580] usbcore: registered new driver quickcam
[ 2850.010070] quickcam [38.490838]: open users=1
[ 2850.022210] quickcam [38.524238]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[ 2850.022574] quickcam [38.525240]: set sensor=324x248 vwin=324x248
[ 2850.026598] quickcam [38.536312]: VIDIOCGWIN: 324,248
[ 2850.026645] quickcam [38.536442]: VIDIOCSWIN: call qc_sensor_setsize 162,124
[ 2850.026934] quickcam [38.537237]: set sensor=162x124 vwin=162x124
[ 2850.026980] quickcam [38.537362]: VIDIOCGWIN: 162,124
[ 2852.023341] quickcam [41.859903]: Ignore Chunk 42FF (len=806)
[ 2852.023381] quickcam [41.860018]: too little data by 11016 (expected 20088)
[ 2852.023398] quickcam [41.860066]: failed qc_imag_convert()=-52
[ 2852.023415] quickcam [41.860111]: retrying failed qc_frame_get... rounds=8
[ 2852.569934] quickcam [43.363437]: Ignore Chunk 42FF (len=861)
[ 2852.569974] quickcam [43.363550]: too little data by 9703 (expected 20088)
[ 2852.569979] quickcam [43.363563]: failed qc_imag_convert()=-52
[ 2852.569982] quickcam [43.363572]: retrying failed qc_frame_get... rounds=8
[ 2853.479955] quickcam [45.867019]: Ignore Chunk 42FF (len=723)
[ 2853.479974] quickcam [45.867073]: too little data by 7776 (expected 20088)
[ 2853.479978] quickcam [45.867085]: failed qc_imag_convert()=-52
[ 2853.479981] quickcam [45.867094]: retrying failed qc_frame_get... rounds=8
[ 2854.022915] quickcam [47.360770]: Ignore Chunk 42FF (len=691)
[ 2854.022973] quickcam [47.360933]: too little data by 8424 (expected 20088)
[ 2854.022978] quickcam [47.360946]: failed qc_imag_convert()=-52
[ 2854.022981] quickcam [47.360955]: retrying failed qc_frame_get... rounds=8
[ 2854.489555] quickcam [48.644555]: Ignore Chunk 42FF (len=691)
[ 2854.489596] quickcam [48.644671]: too little data by 11340 (expected 20088)
[ 2854.489601] quickcam [48.644684]: failed qc_imag_convert()=-52
[ 2854.489604] quickcam [48.644693]: retrying failed qc_frame_get... rounds=8
[ 2854.729916] quickcam [49.305819]: close users=0
[ 2854.731596] quickcam [49.310440]: Not streaming/connected anymore. Ignoring isoc interrupt, dev=ffff81007fd7b000 streaming=0 status=-2
[ 2854.731958] quickcam [49.311439]: Not streaming/connected anymore. Ignoring isoc interrupt, dev=ffff81007fd7b000 streaming=0 status=-2

---

### Post by encompass on 2006-07-25
> **WohthaN said:**
> Hi everyone, i'm having some trouble with this driver.
The problem: incostant frame flow.
The environment: linux 2.6.17.4 on amd64 whith the device 046d:08f6.
The dmesg: see below.
Any suggestion? I'm a programmer but i have no experience at all with webcams...

I wish I knew how to program... but I think the creator of the drive would be able to help you alot.  And the frame rate could depend on a lot of things.  I get about 4 to 7 frams a second, but if I am under a load, It slows dramatically.

The best thing to do is talk to the maker of the driver... he would be happy to get some help.

---

### Post by FooAtari on 2006-07-30
My Quickcam Messenger appears to have worked out of the box, I think...

Anyway, the colour is little off, and when I try and adjust any settings they have no effect on the image.

Any idea why this would be?

Thanks

Edit.

I installed the drivers, and the picture I now get is of a lower resolution that I had befrore....  And the adjustments still have no effect.  How can I uninstall the drivers I installed?

---

### Post by veelivar on 2006-07-31
Hello I am looking to buy a web cam for my ubuntu box, would you generally reccoment the Logitech QuickCam Messenger?  I want to use it as a general webcam and probably with a program like motion or zonemanager.

I have rwad this thread an realised some people have had problems (always seems to be the way when I try and do somthing in linux) but I wondered if more people had had success than had had problems?

Cheers,
Dan.

---

### Post by encompass on 2006-07-31
Don't get this webcam... in my opinion... I would get something like that has plug and play working... most logitech cams do work out of the box in linux.  Just this one is buggy.
And yes, linux takes a lot of work, but that is the price for choice.

---

### Post by Rackerz on 2006-07-31
I think the Quickcam messenger is a good choice, this driver works.

---

### Post by encompass on 2006-08-01
I agree... it does work... but there are so many that work with plug and play... go to walmart and keep your receipt... thats how I do my linux shoping.:lol:

---

### Post by MikeBenza on 2006-08-05
I have the same problem of no /dev/video0.  I tried everything suggested in this thread (rmmod, modprobe; rmmod, insmod).  I installed from the deb package and I added quickcam to the end of /etc/modules, but still no such luck.

*lsusb* and *dmesg | grep quickcam* show the device is there and registered...just no /dev/video0

Anyone else still stuck?

---

### Post by encompass on 2006-08-05
Make sure you have the right webcam... is it the messenger?  It has to be for this driver to work for you.

---

### Post by benvdh on 2006-08-06
Hey encompass and all others,

Got it working using a small hack from the thread en```

```compass sugested. What I did (after everything was compiled and such). First of all you have to create a new file in /etc/init.d called quickcam. To do this use the following command :

```

sudo touch /etc/init.d/quickcam && sudo chmod 755 /etc/init.d/quickcam

```

then open the file with the following command when in gnome :

```

sudo gedit /etc/init.d/quickcam

```

For KDE users :

```

sudo kate /etc/init.d/quickcam

```

then copy and paste the following script in the file:

```

#! /bin/sh
# /etc/init.d/quickcam: reload the Logitech Quickcam Messenger driver.

rmmod quickcam
insmod /lib/modules/`uname -r`/misc/quickcam.ko

```

Save the file and exit.

Then to make sure the script is launched at boot, make a symbolic link using this command :

```

sudo ln -s /etc/init.d/quickcam /etc/rcS.d/S99quickcam

```

And thats it.

I would like to thank Yoriko for most of these instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=126053"). I just adjusted them a bit.

Regards,

Ben

ps. Don't forget, if you update your kernel you will need to recompile the drivers. A new script won't be needed since it uses uname -r to open the modules folder of the latest kernel. 

To MikeBenza: Try using the latest drivers for the quickcam, not the ones from the deb packages since these are quite old.

In the first post of this thread you'll find an how-to on how-to compile these drivers. If that doesn't work try the instructions in this post. If that doesn't work either. Post the output of your lsusb command here.

---

### Post by Rackerz on 2006-08-06
> **benvdh said:**
> Hey encompass and all others,

Got it working using a small hack from the thread en```

```compass sugested. What I did (after everything was compiled and such). First of all you have to create a new file in /etc/init.d called quickcam. To do this use the following command :

```

sudo touch /etc/init.d/quickcam && sudo chmod 755 /etc/init.d/quickcam

```

then open the file with the following command when in gnome :

```

sudo gedit /etc/init.d/quickcam

```

For KDE users :

```

sudo kate /etc/init.d/quickcam

```

then copy and paste the following script in the file:

```

#! /bin/sh
# /etc/init.d/quickcam: reload the Logitech Quickcam Messenger driver.

rmmod quickcam
insmod /lib/modules/`uname -r`/misc/quickcam.ko

```

Save the file and exit.

Then to make sure the script is launched at boot, make a symbolic link using this command :

```

sudo ln -s /etc/init.d/quickcam /etc/rcS.d/S99quickcam

```

And thats it.

I would like to thank Yoriko for most of these instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=126053"). I just adjusted them a bit.

Regards,

Ben

ps. Don't forget, if you update your kernel you will need to recompile the drivers. A new script won't be needed since it uses uname -r to open the modules folder of the latest kernel. 

To MikeBenza: Try using the latest drivers for the quickcam, not the ones from the deb packages since these are quite old.

In the first post of this thread you'll find an how-to on how-to compile these drivers. If that doesn't work try the instructions in this post. If that doesn't work either. Post the output of your lsusb command here.

Yeah that basically loads the quickcam driver into the kernel or something like that so it works at boot. I use my Eyetoy as a webcam now and I have to keep using insmod.

---

### Post by MikeBenza on 2006-08-07
> **benvdh said:**
>  
To MikeBenza: Try using the latest drivers for the quickcam, not the ones from the deb packages since these are quite old.

In the first post of this thread you'll find an how-to on how-to compile these drivers. If that doesn't work try the instructions in this post. If that doesn't work either. Post the output of your lsusb command here.


I did that and now it works fine.  Thank you.

---

### Post by mikaelstaldal on 2006-08-19
The camera works fine for me, but it is possible to get sound from the build-in microphone in the camera too?

---

### Post by benvdh on 2006-08-19
Hey mikael,

It is possible to get the sound working. Just open your mixer app en select the camera device. To select it, click File > Change Device (or something similar). Then you will see the volume control for the microphone in your camera. First of all make sure that it's not muted (see the small icon on the bottom-left of the screen). It should look like a speaker with sound waves (not a speaker, with a red cross, then it's muted, to unmute, click on it). Then adjust the volume of the microphone, using the slider.

When finished configuring test it using ekiga or some kind of similar application. Don't forget to select the camera as the microphone device !

Regards,

Ben

---

### Post by encompass on 2006-08-19
Gosh, I never got it to work. heh, good for you guys, I ended up just using my original sound card mic.  Good job for you both.
And thanks for asking the question.

---

### Post by The Doc on 2006-08-20
I can't get mine to work :(

lsusb: ID 046d:08da Logitech, Inc. (it's a quickcam messenger)

I installed the dependencies and run quickcam.sh and got the following errors:

1. Kernel compiler mismatch
```
gcc-4.0 version: gcc-Version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
gcc version: gcc-Version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Make version: GNU Make 3.81beta4
Linker version: GNU ld version 2.16.91 20060118 Debian GNU/Linux
Kernel compiler: gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
[!] Kernel compiler and gcc-4.0 seem to be different versions.
```

very odd - do you find a difference? I just kept going:

2. [!] Didn't find compatible cameras.

3. ```
The driver detected the following supported cameras:
[17199633.100000] quickcam [54.112173]: ----------LOADING QUICKCAM MODULE------------
[17199633.100000] quickcam [54.112191]: struct quickcam size: 4148
[17199633.104000] usbcore: registered new driver quickcam
I will be using , if there are more cameras I'll not test them.
Press Ctrl+C to quit, Enter to continue --->

Testing if  is correct.
ls: : No such file or directory
./quickcam.sh: line 700: [: too many arguments
ls: : No such file or directory
ls: : No such file or directory
[!]  major number is .
Usually it should be 81, so there are problems ahead.
WARNING: If you press Enter, I'll try to continue anyway
```

I think you get it... Any Ideas? Modprobe works but camorama complains about a missing /dev/video0 (weird, do I have to create that?)

---

### Post by mikaelstaldal on 2006-08-20
Thanks, the camera mic seems to work in Ekiga. 

But when I start "Sound Recorder", it says "Your audio capture settings are invalid".

BTW, is it possible to use it in Skype?

---

### Post by encompass on 2006-08-20
Not yet... at least that I know of.... right now skype only works in linux when:
1. Your lucky
2. you have a mic and speakers on the same sound card.  So you have to use the one connected to your computer.  I had tried for some time... but couldn't figure it out.  It would be good to figure out.  But not in the scope of this howto.  Thanks, for your question though... I use ekiga now... cause skype is not open source friendly enough.

---

### Post by encompass on 2006-08-20
> can't get mine to work

lsusb: ID 046d:08da Logitech, Inc. (it's a quickcam messenger)
Gosh, I don't know that one.  Beyond my knowledge.  No one else has reported, from a thread search.  That this camera has worked for them.  Could be that logitech is throwing a curveball in the models.  They have been known to do that from time to time.
And about your last question.. no you don't.  It should be created when your camara driver is loaded properly.
Dang,

---

### Post by Meck1982 on 2006-09-03
Hi all,

I haven't bought a camera yet, I just want to make sure to get the right one. Today I plugged in a Logitech Quickcam Zoom, which is an outdated Model. But the great thing: It worked out of the Box with Kopete \\:D/ 
Now I was thinking about buying one of the current Modells from Logitech, maybe the Quickcam Messenger. Now I am reading this tread and do not feel very comfortable with the fact, that this camera does not seem to work without further configuration.
So can anyone recommend me a current webcam model, that works out of the box with kopete like this Logitech Quickcam Zoom?

---

### Post by encompass on 2006-09-03
Correct I would not get it.
And as for recomendations... either keep the one you have, or return to the store any one that doesn't so keep your receipt and goto walmart.

---

### Post by Meck1982 on 2006-09-03
Thx for this quick reply. You are right, I will buy one at the local store and return it in the case it does not do what I want ;-)

---

### Post by Princey on 2006-09-04
I got mine working but had to make modifications as stated in [this]("http://ubuntuforums.org/showpost.php?p=1345221&postcount=55") post. The corresponding lsusb output for mine is : > Bus 001 Device 005: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

---

### Post by encompass on 2006-09-04
Thank you for the help... the lsusb will come in handy.  Unforunately the server I plan to have the webpage about the cam on is down for now.  Lets hope it comes back soon.  But it is good none the less to have the information here.

---

### Post by maxxum on 2006-09-13
Thanks for writing the HOWTO.
I have a Logitech Quickcam Communicate STX (the driver at [http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/) seems to support this model) and my lsusb says - 
Bus 002 Device 003: ID 046d:08ad Logitech, Inc.
Bus 002 Device 001: ID 0000:0000

I have downloaded and unzipped the driver. I get this "make missing" error beyond which I did not proceed (afraid I might mess up something).

Here is the output:
```

Next I'm going to check if you have some important programs installed
and if they and the kernel are of suitable version.
Press Ctrl+C to quit, Enter to continue --->

Using specified C compiler from environment CC=gcc-4.0
./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc-4.0
/usr/bin/gcc
Warning: make missing
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
[!] Some important programs can not be found on default path.
Probably they aren't installed.
You should install them, for example, by using apt-get or rpm.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

```
Looks like a minor problem, but I am new so please help..

---

### Post by encompass on 2006-09-13
```
sudo apt-get install build-essential
```
Then try it at the point just after you extracted the file.
Should work then.

---

### Post by maxxum on 2006-09-15
Thanks, that error went away. Too bad it didn't work out. I thought I saw in the driver page that communicate STX is supported by this driver. It could not find any camera connected to my computer so I aborted the installation. Strangely, the blue light of the cam is always on when running ubuntu, whereas it only comes on when the cam is in use in windows.
I guess I will have to keep searching for a compatible cam driver for my cam...if any of you come up with anything please do post.

---

### Post by iyeo on 2006-09-23
get rid of the quickcam messenger and reinstall the spca5xx driver, but make sure you get the new one and make sure you patch it.  The autoscript on the page linked below did not work for me until I got the patch, patched, made, then reinstalled the driver.  I'm running Dapper64 and have the STX and just got it working today.  I was getting the same errors.  Strangely, video still doesn't work in Ekiga, but camorama, xawtv, and spcaqui all work reasonably well.  If anyone knows what might be up with Ekiga, some help would be appreciated.

[http://www.ubuntuforums.org/showthread.php?t=247646](http://www.ubuntuforums.org/showthread.php?t=247646)

---

### Post by iyeo on 2006-09-23
One more thing.  Spcagui menu and display comes in at 50% or lower transparency.  I can get the video to come in 100% tranparency if I switch the mode to YUV, but everything other mode has transparency.  I'm running compiz and xgl.

---

### Post by easyease on 2006-09-24
> **The Doc said:**
> I can't get mine to work :(

lsusb: ID 046d:08da Logitech, Inc. (it's a quickcam messenger)

I installed the dependencies and run quickcam.sh and got the following errors:

1. Kernel compiler mismatch
```
gcc-4.0 version: gcc-Version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
gcc version: gcc-Version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Make version: GNU Make 3.81beta4
Linker version: GNU ld version 2.16.91 20060118 Debian GNU/Linux
Kernel compiler: gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
[!] Kernel compiler and gcc-4.0 seem to be different versions.
```

very odd - do you find a difference? I just kept going:

2. [!] Didn't find compatible cameras.

3. ```
The driver detected the following supported cameras:
[17199633.100000] quickcam [54.112173]: ----------LOADING QUICKCAM MODULE------------
[17199633.100000] quickcam [54.112191]: struct quickcam size: 4148
[17199633.104000] usbcore: registered new driver quickcam
I will be using , if there are more cameras I'll not test them.
Press Ctrl+C to quit, Enter to continue --->

Testing if  is correct.
ls: : No such file or directory
./quickcam.sh: line 700: [: too many arguments
ls: : No such file or directory
ls: : No such file or directory
[!]  major number is .
Usually it should be 81, so there are problems ahead.
WARNING: If you press Enter, I'll try to continue anyway
```

I think you get it... Any Ideas? Modprobe works but camorama complains about a missing /dev/video0 (weird, do I have to create that?)


hi, Ive got the same device as this, Bus 004 Device 002: ID 046d:08da Logitech, Inc.
i found this page that lists the device as being usable with a driver,
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) , but Im completely at a loss as to what to do with this information. can anybody help?

---

### Post by easyease on 2006-09-24
ok so i found a way to get it working, I followed these instructions....
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)
I do wish hardware manufacturers would stick to making their products completely uniform when they release them.

---

### Post by encompass on 2006-09-24
That worked? woah... didn't for me... good to know though.

---

### Post by Wolf-Ekkehard on 2006-10-12
Thanks so much for this HowTo!!  I never thought that I would get this old clunker to work under any linux flavor...  But it worked right out of the box, just as you described.

One small thing: couldn't find a package build-essentials, but quickcam.sh tells you what you're missing anyway, so it's not a problem at all.

Also, just for the records: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
works for me! 

Another thing that I can't figure out:
What does this mean?

[PHP] X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/bin/sh: /usr/bin/esd: No such file or directory[/PHP]

I get it whenever I start camorama.  Looks like it's working nonetheless.

Maybe I'm just revealing that I just installed (K)ubuntu two days ago for the very first time...

---

### Post by encompass on 2006-10-13
That could be a few things... but if we are talking about your camera... odds are it is that "never working for me" Microphone built into the camera. ESD is the enlightened sound deamon.

---

### Post by hueoblue on 2006-12-04
running ./quickcam.sh, I run into this problem 
```

[!]Cannot find version.h in kernel source.
[!]Kernel source is not configured properly.
[: 435: ==: unexpected operator
You have only kernel headers but they are not configured properly. 
It's pointless to try and continue, this won't work. 
Either install properly configured kernel headers or full source with kernel configuration.

```

I used synaptic to get the kernel headers, I don't understand why this doesn't work.

I'm running edgy and
result of uname -r is :
```

2.6.17-10-386

```

Any help is much appreciated.

---

### Post by roderikk on 2006-12-05
> wget [http://home.mag.cx/messenger/source/qc-usb-messenger-1.3.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.3.tar.gz)
tar -xvf qc-usb-messenger-1.3.tar.gz

When you look on the site you'll notice that there is a newer version 1.4. This works perfectly for me. Hope this helps.

---

### Post by newtolinux... on 2006-12-09
OK, this is the first ever post that I am making running Linux.  :D  I'm really having fun learning about this great OS.  (running Ubuntu 6.10)  My problem is with my logitech quickcam...](*,) I tried these steps but it doesn't work for me.  I see all this stuff about Konsole...like I said, I'm really new to Linux but I thought that was for KDE, and I'm using gnome, which uses Terminal.  I don't know if that makes it any different, so, I also tried those commands and got some errors and it didn't work.  It told me that xawtv was missing.  so I went into the package manager and installed that.  Then I got a little farther and it says "Kernel compiler and pcc seem to be different version."  now it tells me to "export CC=kgcc" how the heck do I do about that? Like I said, I'm brand new to Linux...I'd appreciate a little help. (and when I try to do the > sudo apt-get install build-essentials camorama it says, "couldn't find package build-essentials")               Thanks,     Tom

> **encompass said:**
> Let me start by saying this howto would have never happened had it not been for the help of the fallowing people...
Yoriko:	for the original howto for Ubuntu 5.10
sporniket: for shoing how to make the changes work at bootup
Christian Magnusson: for creating the fantastic driver with great improvements.
jarping: for the deb file, found somehow!


Secondly:
If you haven't tried yet... use this deb... install with...

Is this the driver I need?
What is know to work by the Ubuntuforums is the following:
ID 046d:08f6 Logitech, Inc.

To find out if you have the Camera type:
```
lsusb
```
and the terminal when the camera is plugged in.  If you have it number for number then you have the same exact camera.
If your camera is the Logitec Quickcam Messenger and you have a different output than thatgive this driver a try.  If the driver works you can add your webcam to the list. Please feel free to contact me and I can add it to the list. Your name will also be added to the list of helpers. ¶:

Let's get, extract, and install the files...
You need an external driver outside of what Ubuntu can give. Type:
```
wget http://home.mag.cx/messenger/source/qc-usb-messenger-1.3.tar.gz
tar -xvf qc-usb-messenger-1.3.tar.gz
```
at the terminal
Now we need some programs and files from the Ubuntu side fo things..
```
sudo apt-get install build-essentials camorama
```
while that command is going you can start up another terminal or wait...
```
uname -r
```
This gives back your kernel; replace unamewith that output in the next command...
```
sudo apt-get install kernal-headers-uname
```
That should be everything that I used.  Tell me if you think I am missing something.
ok...
```
cd qc-usb-messenger-1.3
sudo su
./quickcam.sh #Go through each step
exit

```
follow the instructions... if you are using the same cam as me you should have no trouble at all... Just when it says that it will try to run something called xawtv don't worry about that... just run camorama from the applications menu to see if the cam works.
If is does work keep going... if it doesn't work tell me.
now...
```
sudo nano /etc/modules
```
and add
```
quickcam
```
to the bottom of that list.
and press 'ctrl-x' to quit and 'y' to save.
reboot and check the camera again with camorama.
Hope it worked for you.
Thanks for reading my howto.
I have used the camera in many ways..
I have setup a live webcam feed using apache and a few other small programs.
I have used it with ekiga, and amsn to chat with friends and family.
And other things.  If you have a cool thin your doing wit your webcam... tell us about it by putting it on your own little howto.

---

### Post by encompass on 2006-12-10
> **newtolinux... said:**
> OK, this is the first ever post that I am making running Linux.  :D  I'm really having fun learning about this great OS.  (running Ubuntu 6.10)  My problem is with my logitech quickcam...](*,) I tried these steps but it doesn't work for me.  I see all this stuff about Konsole...like I said, I'm really new to Linux but I thought that was for KDE, and I'm using gnome, which uses Terminal.

No is shouldn't matter to my knowledge.
> **newtolinux... said:**
> 
  I don't know if that makes it any different, so, I also tried those commands and got some errors and it didn't work.  It told me that xawtv was missing.  so I went into the package manager and installed that.


you don't need xawtv just test the camera with camorama or ekiga.

> **newtolinux... said:**
>   Then I got a little farther and it says "Kernel compiler and pcc seem to be different version."  now it tells me to "export CC=kgcc"


Looks like you need to type the command export CC=kgcc but before you try that.  what version of kubuntu are you running.  6.10 or 6.06 or something older.

> **newtolinux... said:**
> 
 how the heck do I do about that? Like I said, I'm brand new to Linux...I'd appreciate a little help. (and when I try to do the  it says, "couldn't find package build-essentials")               Thanks,     Tom
it is build-essential take out the 's' probably a typo on my part.

Hope this helps.  Personal Messenger GMAIL preffered if you have other questions.
Or simply post here.

---

### Post by rafiks on 2006-12-10
Hi! I haven't gotten the driver to compile with 2.6.19..is the developer in this forum? Is there a way to hack the source to make it compile with 2.6.19..

---

### Post by rafiks on 2006-12-10
I noticed that in 2.6.19 the config.h file is already depecrated ..

---

### Post by DRF on 2006-12-10
It does work with 2.6.19 but you have to use version 1.6
So where it says in the first post
wget [http://home.mag.cx/messenger/source/qc-usb-messenger-1.3.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.3.tar.gz)

replace that with
wget [http://home.mag.cx/messenger/source/qc-usb-messenger-1.6.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.6.tar.gz)

But if your like me i tend to open
[http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/) in a web browser and see what the latest version is and use that.

Also you want build-essential installed and you want the kernel headers.
sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)
(you can copy those directly into the terminal, writing it like that will always install the headers for the currently running kernel)

I also tend to install it using:
make all
sudo make install

in the extracted qc-usb-messenger directory instead of the install script.

But if you get stuck leave a message with your error during compiling/installing.

Daniel

---

### Post by rafiks on 2006-12-14
Yeah, I was the one who emailed the developer ..He was so nice that he replied immediately and fixed it right away!

---

### Post by encompass on 2006-12-15
Good job submitting the issue... that is how this open source ideology works.  When I get the chance I will fix all the mistakes in my howto and also submit it to the wiki's.

---

### Post by hemantpratap on 2006-12-28
Hi Encompass,
I read your post regarding installation of Quickcam in ubuntu. i was doing exactly what you have written in the forum. but i am stuck at one point and dont know what to do.
here are the details.
1. uname -r ( it gives me kernal header  , i cant remember right now what it was)
2. sudo apt-get install kernal-headers-uname
E: Cant find package kernel-header-uname 
i am not sure where i am doing some mistake.
please advise , any help will me much appriciated

---

### Post by encompass on 2006-12-28
The number you get for the result of uname -r is what you replace the uname with in the command.  What this command is doing is installing the special kernel files needed to make your program compile properly.
Let me double check my work...
It should work a little better now... sorry, they changed a few things on me...

---

### Post by nullrev on 2006-12-29
I just wanted to thank you for your guide, and add another camera that works
ID 046d:08f5 Logitech, Inc.

---

### Post by Gsyman on 2007-01-12
no luck installing Quickcam Chat webcam; i keep getting error message "could not connect to video device (/dev/video0)"
lsusb shows: ID 046d:092e Logitech, Inc.

Any ideas now to fix this?

Thanks everyone

---

### Post by encompass on 2007-01-12
This thread is only for the messenger.  Following this howto WILL NOT help you....
Try this... I did a quick search of your device from the lsusb's point of view....
Post... 6 and 7
[http://ubuntuforums.org/showthread.php?t=205782&highlight=046d%3A092e](http://ubuntuforums.org/showthread.php?t=205782&highlight=046d%3A092e)

---

### Post by rlopez on 2007-01-19
Hi guys,

I have a problem with my Quickcam Messenger. I just followed all the steps to install the driver from the latest version qc-usb-messenger-1.5, but it didn't work. I think that my problem is that I don't have the device /dev/video0, but I don't know if this device is created automatically by the quickcam script when the installation is successful.

My Quickcam Meesenger returns this number when I type the lsusb command

```

traffic@traffic-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:08da Logitech, Inc.
Bus 002 Device 001: ID 0000:0000

```

I have bought this webcam one month ago. Could you help me please?.  Thank you very much,

---

### Post by encompass on 2007-01-19
I looks like everyone in this thread that has your lusb output seems to have a problem with this driver... I would report your problem to the provider of the driver... then try what other website seem to be saying... use the spca driver.  If your running edgy it should just work.  But I guess not.

---

### Post by encompass on 2007-01-19
Check this link....
[http://ubuntuforums.org/showthread.php?p=1645689&highlight=046d%3A08da#post1645689](http://ubuntuforums.org/showthread.php?p=1645689&highlight=046d%3A08da#post1645689)
Sadly, logitech gave you a different camera then they told you.  This isn't the first time it was done either.

---

### Post by rlopez on 2007-01-21
Thank you very much.

I have followed the instructions offered by  the link and the webcam worked correctly!!!!.
I can't understand how Logitech gave me a different model of webcam.

Thank you very much again. 

In summary, if you have bought a Messenger Quickcam and the lusb command returns you this number
Bus 003 Device 002: ID **046d:08da** Logitech, Inc.
 , you must to follow this link [http://ubuntuforums.org/showthread.php?t=75284&highlight=046d%3A08da](http://ubuntuforums.org/showthread.php?t=75284&highlight=046d%3A08da)

---

### Post by encompass on 2007-01-21
Sad but closed hardware likes to do that on you.  They think no one will notice.  But we kinda live a higher standard than that.

---

### Post by schumifer on 2007-01-28
didn't i see support for logitech quickcam messenger in kernel 2.6.19? Does this cover us and how does it differentiate this guide?

---

### Post by encompass on 2007-01-28
I have hear the rumor too... not sure... let me check my feist test install...

---

### Post by roderikk on 2007-01-29
Wow, that would be really cool. That would be a real example of open source conquering every obstacle!

PS Where did you find this rumour?

---

### Post by encompass on 2007-01-29
I just sent an email to him... lets see what he says. Crossing fingers....:guitar:

---

### Post by TameLion on 2007-03-04
**The Problem**

Using latest version (1.6) of the drivers, I had the same problem as benvdh et al; the driver would work perfectly straight away but not after a reboot. Starting Camorama would tell me there was no /dev/video0.

The script posted by benvdh did not apply to me, as the new driver seems to install to a different location:

/lib/modules/`uname -r`/kernel/drivers/media/video/quickcam

and even if I tried to insmod the module from this location it did not work.


**The Solution**

Like others in this thread, the only way which DID work was to recompile the driver and let it insert the module again. So instead of running the script and recompiling over again, I simply tried to modprobe the quickcam.ko which had already been created by the previous run of the script and: viola! It worked!

I think maybe previous attempts (and fails) of installation left the old quickcam.ko module and didn't replace it with the new (successful) run of the install script. So my solution was to:

sudo cp /path/to/install-script/quickcam.ko /lib/modules/`uname -r`/kernel/drivers/media/video/quickcam

and now the entry "quickcam" in the /etc/modules file (as in the very FIRST post of this thread - thanks again for all the hard work encompass!) is enough to load the WORKING module every time on startup! :)

---

### Post by Aldoo on 2007-03-19
I just switched to Feisty.

That's a good thing that now the Quickcam Messenger is recognized out of the box.
_But:_
- Now the pictures has bad colors, and I have to tune different settings (in apps that can do so) in order to have a good enough picture. What is this new driver*? (module quickcam_messenger)
- an other problem: when I plug my webcam, the snd-usb-audio module is loaded, but it does not create the alsa device for the microphone. What is going on ? I switched to the latest ALSA then, but no difference.

---

### Post by encompass on 2007-03-20
Good gosh!
Thanks for the information.  This is great news.

---

### Post by roderikk on 2007-03-24
Hey,

Well I cannot confirm that it works out of the box with Feisty. I try to run camorama and it gives no image, and also the audio is not connected, I will now try to install the latest driver and see if those work. If anyone did get it to work right out of the box like Aldoo, could you post some more info on your setup?

EDIT: Well I tried installing the 1.6 driver in Feisty but it gives a lot of errors. If you ignore all those (also xawtv doesn't seem to work) and try in camorama I do get an image. However, I still haven't been able to configure my microphone).

---

### Post by encompass on 2007-03-25
> **roderikk said:**
> Hey,

Well I cannot confirm that it works out of the box with Feisty. I try to run camorama and it gives no image, and also the audio is not connected, I will now try to install the latest driver and see if those work. If anyone did get it to work right out of the box like Aldoo, could you post some more info on your setup?

EDIT: Well I tried installing the 1.6 driver in Feisty but it gives a lot of errors. If you ignore all those (also xawtv doesn't seem to work) and try in camorama I do get an image. However, I still haven't been able to configure my microphone).

I have personally never had the mic work... did it work before for you?

---

### Post by Princey on 2007-03-25
My mic worked when I ran Dapper but I never really went after it to test on later versions. The system recognises it but since I use a close talk microphone I never bothered to check to see if it works.

---

### Post by roderikk on 2007-03-28
Yes, it worked for me. Very unexpectedly I saw it show up in Skype (this was in Edgy).

---

### Post by BartAfterDark on 2007-04-01
Hi,

I have a logitech quickcam messenger, but this driver wont install at all.

I run Ubuntu 7.04 (2.6.20-13-generic)

```
lars@lars-desktop:~$ lsusb
Bus 005 Device 008: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
```

Ive downloaded the latest version named qc-usb-messenger-1.6 extracted. But my first problem happens when I try to install camorama with "sudo apt-get install build-essentials camorama" It then says could not find the package build-essentials

The other problem is this:

```
[!] Kernel compiler and gcc seem to be different versions.
```

When I run the quickcam.sh file :/

---

### Post by encompass on 2007-04-01
sudo apt-get install build-essential camorama 
looks like I added an "s"
That should get it for you
as for the gcc version... it still works just fine. Ignore that warning.

---

### Post by mikeee@uf on 2007-04-07
the problem:

[!] Kernel compiler and gcc seem to be different versions.

is totally normal. You can check the gcc and kernel compiler versions your self. For me they were identical but the error showed up anyway.

By the way. It won't be the only error showing up during install, but most can be ignored. Just hit enter and look if the cam works at last.

It works for me (with wrong colors :-( )

MikeE

---

### Post by acturneruk on 2007-04-24
I had this working under Edgy by following the instructions here, but since upgrading to Feisty the /dev/video0 device node isn't being created. I have tried both the latest drivers from [http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/) and the new quickcam_messenger.ko module included with the Feisty kernel without success. Anyone else seeing this, or have any idea why /dev/video0 is not being created?

---

### Post by encompass on 2007-04-24
> **acturneruk said:**
> I had this working under Edgy by following the instructions here, but since upgrading to Feisty the /dev/video0 device node isn't being created. I have tried both the latest drivers from [http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/) and the new quickcam_messenger.ko module included with the Feisty kernel without success. Anyone else seeing this, or have any idea why /dev/video0 is not being created?
Yeah that is interesting.  I will try to find time to test it and get back to you.  I only have the cam because of the forum now.  SO I have to dig it out when ever someone has a question.  It may be a while.
Have you checked for any other video?  like video1?  You could try emailing the creator.

---

### Post by acturneruk on 2007-04-24
Thanks, I appreciate any time you spend on this.

There are no other video device nodes created. The drivers worked perfectly under Edgy, with /dev/video0 being created automatically. But under Feisty, nothing happens when I modprobe the quickcam.ko.

Tonight I will try and manually create the device node and see if that helps.

---

### Post by Princey on 2007-04-24
Guess what???? I did a fresh install of Fiesty Fawn and it recognised my camera out of the box!!! Now that's super amazing.

---

### Post by acturneruk on 2007-04-24
After a bit more playing about, it seems that the qc-usb-messenger-1.6 drivers do work and create the /dev/video0 device node when first install. However, after a reboot, the device node is no longer created, and modprobe quickcam doesn't help. I have to re-run the quickcam.sh script to get it going again.

Also, the microphone no longer works (it did under Edgy), and the camera audio device no longer appears under the Volume Control panel.

Anyone got any ideas?

The quickcam_messenger.ko module that is included with Feisty by default doesn't work at all for my webcam (ID 046d:08f6 Logitech, Inc.)

---

### Post by acturneruk on 2007-04-25
After even more playing about...if I reboot with the webcam plugged in, then then the device node is created. If I plug it in after my laptop has booted, then it isn't. This is with the drivers from [http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/)

Still can't get the mic to work.

---

### Post by Drachen on 2007-04-30
Hi ):P 

I just finished installing my webcam through this tutorial and it worked fine \\:D/ 

Rebooted and Camorama and Ekiga are working with my Logitech Quickcam Messenger. Oh, and I'm using Feisty 64 bits :)

Thanks for the tutorial!

---

### Post by encompass on 2007-04-30
That's great dude!

---

### Post by jonny_boy27 on 2007-04-30
also found that, wonderfully, the camera was recognised striaght off in feisty but have no audio (which i did in dapper when comiling the driver myself - could never get it to work in edgy). Anyone got any clues, or am i just going to go and have to buy a microphone?

---

### Post by acturneruk on 2007-05-01
See [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93822](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93822)

---

### Post by S-99 on 2007-06-05
Hello, i'm a new member here. Who also has a compatible logitech quickcam messenger. Handy camera, best one i ever owned.

This is the cam i have.
Bus 002 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

It worked great with the qc-usb-messenger-1.6 driver in dapper and edgy. Then i got going with feisty yesterday, and tested it's plug and play ability with camorama and it uses /dev/video0, and it brought up a very dark, miscolored picture in a small resolution. After that none of my programs besides camorama will bring up a picture with it. Amsn and gyachi will not show a picture with my cam. Just a black screen and others viewing see a black screen as well.

So i tried putting in the trusty qc-usb-messenger-1.6 driver with the linux headers and build essential packages doing it the ./quickcam.sh installation method. And of course quickcam.sh script says there is a driver already loaded and will attempt to unload it. The script fails to unload the current driver and can't load the new driver it just compiled.
So i try to run quickcam.sh again, and it does the same thing, and it does tell me to try 
"rmmod mod_quickcam || rmmod quickcam"  as root. 
When i do this it gives me 
"ERROR: Module mod_quickcam does not exist in /proc/modules
ERROR: Removing 'quickcam': Operation not permitted".

I don't much care for the microphone on the camera as i don't really use it, but from what i can see is that i can't install the qc-usb-messenger-1.6 driver because i can't unload the driver that came with feisty for the current crap plug and play ability for my camera currently.

So, technically would unloading the driver currently in use in feisty let me load the qc-usb-messenger-1.6 driver which will probably make my cam work umm work?

---

### Post by Japaman on 2007-06-05
Hello!
I'm also an owner of the Logitech Quickcam Messenger but not happy for its operation!
My lsusb is ofcourse the same encompass ( ID 046d:08f6 Logitech, Inc. )
I should firstly say that I'm using Ububtu Feisty Fawn and my kernel is 2.6.20.15
At fisrst I tried the drivers 1.5 but nothing did work.Neither in camorama nor in msn or anywhere else.

So I tried drivers 1.6 and that's the resault

```
Press Ctrl+C to quit, Enter to continue ---> 

./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc
/usr/bin/gcc
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
/bin/readlink
gcc version: gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
gcc version: gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Make version: GNU Make 3.81
Linker version: GNU ld version 2.17.50 20070103 Ubuntu
Kernel compiler: gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Looking for more necessary programs...
Found program /sbin/depmod
Found program /sbin/insmod
Found program /sbin/rmmod
Found program /sbin/modprobe
Found program /bin/mount
Found program /usr/sbin/lsusb
depmod version: module-init-tools 3.3-pre2
insmod version: module-init-tools version 3.3-pre2
rmmod version: module-init-tools version 3.3-pre2
modprobe version: module-init-tools version 3.3-pre2
Checking whether we're root... alex
Checking for driver source code...
Checking for write permission...

Previous round done. Now checking if you have kernel source installed.
Press Ctrl+C to quit, Enter to continue ---> 
Press Ctrl+C to quit, Enter to continue ---> Press Ctrl+C to quit, Enter to continue ---> 

./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc
/usr/bin/gcc
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
/bin/readlink
gcc version: gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
gcc version: gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Make version: GNU Make 3.81
Linker version: GNU ld version 2.17.50 20070103 Ubuntu
Kernel compiler: gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Looking for more necessary programs...
Found program /sbin/depmod
Found program /sbin/insmod
Found program /sbin/rmmod
Found program /sbin/modprobe
Found program /bin/mount
Found program /usr/sbin/lsusb
depmod version: module-init-tools 3.3-pre2
insmod version: module-init-tools version 3.3-pre2
rmmod version: module-init-tools version 3.3-pre2
modprobe version: module-init-tools version 3.3-pre2
Checking whether we're root... alex
Checking for driver source code...
Checking for write permission...

Previous round done. Now checking if you have kernel source installed.
Press Ctrl+C to quit, Enter to continue ---> 


Modules loaded into the kernel:
binfmt_misc rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_conservative cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand freq_table pcc_acpi sony_acpi tc1100_wmi dev_acpi asus_acpi dock ac button battery sbs i2c_ec backlight container video af_packet lp fuse saa7134_alsa tuner snd_mpu401 snd_mpu401_uart snd_seq_dummy snd_intel8x0 snd_ac97_codec snd_seq_oss ac97_bus snd_usb_audio snd_pcm_oss snd_mixer_oss saa7134 snd_seq_midi snd_seq_midi_event snd_pcm snd_usb_lib snd_seq video_buf compat_ioctl32 ir_kbd_i2c xpad snd_rawmidi snd_seq_device snd_hwdep ir_common nvidia snd_timer videodev v4l2_common v4l1_compat i2c_core parport_pc parport snd soundcore analog gameport snd_page_alloc pcspkr iTCO_wdt iTCO_vendor_support shpchp pci_hotplug intel_agp agpgart i82875p_edac edac_mc tsdev evdev ipv6 ext3 jbd mbcache sg ide_cd cdrom ide_disk sd_mod usbhid hid piix generic 3c59x mii ata_piix floppy ehci_hcd ata_generic libata scsi_mod uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap 

Next round: let's see if you have a supported QuickCam.
Please plug in your USB camera before continuing.
Press Ctrl+C to quit, Enter to continue ---> 
I can find the following probably compatible devices:
Bus 001 Device 004: ID 046d:08f6 Logitech, Inc. 

Another round done. Let's now compile the driver, it takes a while.
This step will also clear old unnecessary files from the directory.
Press Ctrl+C to quit, Enter to continue ---> 
rm -f *.o qcset input_read show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
cd testquickcam ; make clean
make[1]: Entering directory `/home/alex/Desktop/qc-usb-messenger-1.6/testquickcam'
rm -f testquickcam *~ pic.ppm pic.gif
make[1]: Leaving directory `/home/alex/Desktop/qc-usb-messenger-1.6/testquickcam'
make -C "/lib/modules/2.6.20-16-generic/build" SUBDIRS="/home/alex/Desktop/qc-usb-messenger-1.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /home/alex/Desktop/qc-usb-messenger-1.6/.tmp_versions
rm -f /home/alex/Desktop/qc-usb-messenger-1.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/alex/Desktop/qc-usb-messenger-1.6
  gcc -m32 -Wp,-MD,/home/alex/Desktop/qc-usb-messenger-1.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/alex/Desktop/qc-usb-messenger-1.6/.tmp_qc-driver.o /home/alex/Desktop/qc-usb-messenger-1.6/qc-driver.c
/home/alex/Desktop/qc-usb-messenger-1.6/qc-driver.c:94:2: warning: #warning "Little Endian system"
/home/alex/Desktop/qc-usb-messenger-1.6/qc-driver.c: In function ‘qc_int_init’:
/home/alex/Desktop/qc-usb-messenger-1.6/qc-driver.c:773: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/alex/Desktop/qc-usb-messenger-1.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/alex/Desktop/qc-usb-messenger-1.6/qc-driver.c:2129: warning: assignment from incompatible pointer type
  gcc -m32 -Wp,-MD,/home/alex/Desktop/qc-usb-messenger-1.6/.qc-vv6450.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_vv6450)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/alex/Desktop/qc-usb-messenger-1.6/.tmp_qc-vv6450.o /home/alex/Desktop/qc-usb-messenger-1.6/qc-vv6450.c
  gcc -m32 -Wp,-MD,/home/alex/Desktop/qc-usb-messenger-1.6/.qc-formats.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_formats)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/alex/Desktop/qc-usb-messenger-1.6/.tmp_qc-formats.o /home/alex/Desktop/qc-usb-messenger-1.6/qc-formats.c
  gcc -m32 -Wp,-MD,/home/alex/Desktop/qc-usb-messenger-1.6/.qc-memory.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_memory)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/alex/Desktop/qc-usb-messenger-1.6/.tmp_qc-memory.o /home/alex/Desktop/qc-usb-messenger-1.6/qc-memory.c
  ld -m elf_i386 -m elf_i386  -r -o /home/alex/Desktop/qc-usb-messenger-1.6/quickcam.o /home/alex/Desktop/qc-usb-messenger-1.6/qc-driver.o /home/alex/Desktop/qc-usb-messenger-1.6/qc-vv6450.o /home/alex/Desktop/qc-usb-messenger-1.6/qc-formats.o /home/alex/Desktop/qc-usb-messenger-1.6/qc-memory.o
  Building modules, stage 2.
make -f /usr/src/linux-headers-2.6.20-16-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.20-16-generic/Module.symvers -I /home/alex/Desktop/qc-usb-messenger-1.6/Module.symvers -o /home/alex/Desktop/qc-usb-messenger-1.6/Module.symvers -w  /home/alex/Desktop/qc-usb-messenger-1.6/quickcam.o
  gcc -m32 -Wp,-MD,/home/alex/Desktop/qc-usb-messenger-1.6/.quickcam.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(quickcam.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -DMODULE -c -o /home/alex/Desktop/qc-usb-messenger-1.6/quickcam.mod.o /home/alex/Desktop/qc-usb-messenger-1.6/quickcam.mod.c
  ld -m elf_i386 -m elf_i386 -r -o /home/alex/Desktop/qc-usb-messenger-1.6/quickcam.ko /home/alex/Desktop/qc-usb-messenger-1.6/quickcam.o /home/alex/Desktop/qc-usb-messenger-1.6/quickcam.mod.o
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
gcc -Wall -O2 -s qcset.c -o qcset -lm
qcset.c: In function ‘pnm_open’:
qcset.c:383: warning: pointer targets in passing argument 1 of ‘fopen’ differ in signedness
qcset.c: In function ‘main’:
qcset.c:640: warning: pointer targets in passing argument 1 of ‘pnm_open’ differ in signedness
gcc -Wall -O2 -s input_read.c -o input_read
-rw-r--r-- 1 alex alex 717888 2007-06-05 19:32 quickcam.ko

Now everything should be well and the driver compiled.
Let's then try actually loading the fresh driver and testing
if it works.
Press Ctrl+C to quit, Enter to continue ---> 
To load the driver, I need to know the root password.
Password: 
.
.
.
.
[!] The QuickCam driver failed to load!
If you saw any special error messages, like about
unresolved symbols, tell about them when asking for help.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 
Try unloading and reloading the driver manually with
        rmmod quickcam; insmod ./quickcam.ko debug=-1
and then checking whether there are any messages indicating
problems with command
        dmesg
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 

I will be using , if there are more cameras I'll not test them.
Press Ctrl+C to quit, Enter to continue ---> 
Testing if  is correct.
ls: : No such file or directory
[!] You don't have read/write access to .
On many distributions, you should add yourself into the
"video" group by giving command
        adduser alex video
and then log in again to be able to access the video.
A quick alternative is just to do
        chmod a+rw 
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 

ls: : No such file or directory
ls: : No such file or directory
[!]  major number is .
Usually it should be 81, so there are problems ahead.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 


Right now driver is loaded and should be ready to run.
Let's test if user applications can see it, starting with qcset.
Press Ctrl+C to quit, Enter to continue ---> 
./qcset: invalid configuration request type
[!] qcset did not found the QuickCam camera
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 
If you like, you can quit now and start using the camera -
you have good chances that it works, if no problems were detected.
If you have X Window System running and xawtv installed,
I can now run it automatically for you.
You will then also have opportunity to install the driver permanently.
Press Ctrl+C to quit, Enter to continue ---> 

Launching xawtv (press q on xawtv window to quit it)...
If the image is not sharp, try focusing it by turning the
wheel around the camera lens.
        xawtv -noscale -noxv -c ""
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  61
  Current serial number in output stream:  61

Well, did it work, did you get a picture?
If you did, you might now want to install the driver
permanently. Just proceed to do that...
Press Ctrl+C to quit, Enter to continue ---> 

Just an extra warning: the driver (quickcam.ko) and
the utility (qcset) will be now copied into system
directories. If you have already other versions,
they will be overwritten. Verify by giving root password.
Password: 
su: Authentication failure
Sorry.
[!] Module install failed to /lib/modules/2.6.20-16-generic/misc/quickcam.ko
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 


```

And of course nothing works
I cannot understand why it sais that "authentication failed"
I don't know my passw?????
Any help?

---

### Post by Japaman on 2007-06-05
Ok I fixed it.
The cam works with camorama but not with ekiga.I suppose it's something with the settings of the prog.
I'm trying now to test it in amsn.We'll see!
And for the record I installed 1.6 drivers.I have Ubuntu Feisty and Quickcam Messenger 046d:08f6 .

---

### Post by S-99 on 2007-06-07
Yeah something i already wrote that it worked for me in camorama as well, but the settings for the color and darkness were all screwed up, and changing them did nothing for me. After that any other program i had would not work with the cam. Which was gyachi and amsn.

Also japaman the output earlier you posted from your run with quickcam.sh, it's pretty much identical to my output from it. But, does your cam work in other programs as well, since you claimed to have loaded it somehow? And if it does work in other programs what did you do for it to do so?

---

### Post by S-99 on 2007-06-07
Ok, i got my webcam working properly with right colors, good resolution, and working in other programs.
Do yourself a favor and get rid of camorama, if you do the install like have mentioned here how i did it, camorama will screw you up, and more on why it does at the bottom of this post.

What i did?
Well first off from the feisty repos i grabbed the linux headers, xawtv, and build-essential.
Then i grabbed the debian gspca driver [from here](http://mxhaard.free.fr/download.html). You want gspca and not spca5xx since gspca is for kernels above 2.6.11, and feisty is currently 2.6.20.
Extract the gspca driver, go into console and "cd" to the gspca extracted directory.
Then do "make".
When that's done "sudo make install" follows.
And then to load the driver do "sudo modprobe gspca".
Also when that is over "sudo gedit /etc/modules" and put in "gspca" as an entry in modules and save the changes to modules(gspca in modules will load the driver at startup).
This is all i did to make my cam work properly, nothing more than what you see here.

One more thing if you're one of those people like me who had only camorama working with your quickcam messenger when no other program would work with your cam. Then please uninstall camorama. I personally don't have a use for camorama, and camorama didn't want to use the gspca driver while everything else did. Starting up camorama after installing the gspca driver appears to unload the gspca driver, and go back to that plug and play driver that sucked utter ***t that wouldn't work with other programs besides camorama. Just uninstall camorama if you were a person with my situation to avoid later confusion from the stupid thing. Plus camorama is not a requirement for webcams. Plus amsn and gyachi, as well as other programs that do use webcams usually let you change the properties of the cam anyway. Camorama is unecessary.

---

### Post by gercokees on 2007-06-10
For all those who do not know how and where te grab the files mentioned above:

sudo apt-get install linux-headers-`uname -r`
sudo apt-get install build-essential
sudo apt-get install xawtv

should do the trick for you.... (a simple copy-paste into the terminal is enough.. please do not  mistake the ` for a ' in the first line P)

---

### Post by neatojones on 2007-06-12
> **Japaman said:**
> Ok I fixed it.
The cam works with camorama but not with ekiga.I suppose it's something with the settings of the prog.
I'm trying now to test it in amsn.We'll see!
And for the record I installed 1.6 drivers.I have Ubuntu Feisty and Quickcam Messenger 046d:08f6 .

I get the same errors.  How did you fix it?

---

### Post by S-99 on 2007-06-14
GET RID OF CAMORAMA, it seems to screw things up for cams.

Lol, i had the same thing, i'll give you some advice to read the rest of the posts on this page and you'll get your answer. And one thing you'll see is that yes, i also had camorama, and that was the only app that worked with my cam, while amsn, and ekiga would take a crap on me. My recommendation is you get rid of camorama since there's no real need for it and the main reason that camorama seems to screw up the webcam along with the self installed and loaded driver of either gspca or qc-usb. Get rid of camorama, if you need something like camorama that wont screw with your cam, hop on synaptic and install camstream. I really don't know why camorama is acting up. Either get rid of camorama and reinstall qc-usb, or get rid of camorama and replace it with camstream and reinstall qc-usb. And yes i did eventually go back to good old qc-usb myself.

A good hint for installing qc-usb is just to extract the archive, go to the directory and do "sudo make install". I got really pissed off at the qc-usb installer script along time ago since it's hard to make the install script go absolutely perfectly which it never does on feisty. So "sudo make install" if you want to get around the install script. "sudo modprobe quickcam", and then "sudo nano /etc/modules" and put the "modprobe quickcam" entry in there to load the module upon bootup. Of course this is just like how i installed the gspca driver except in place of it is qc-usb (gspca seemed to give me a really dark picture, so i got rid of it).

---

### Post by ajc37 on 2007-08-21
After having put in the new driver does, Quick cam messenger now work with Gyachi?, Thanks.

---

### Post by encompass on 2007-08-21
> **ajc37 said:**
> After having put in the new driver does, Quick cam messenger now work with Gyachi?, Thanks.

Your welcome?  Did you have a question?  You ended it with a question mark.
Glad if it did work.

---

### Post by roderikk on 2007-09-26
Anybody tried it yet on Gutsy? Unfortunately it doesn't yet work out of the box...

EDIT: It seems installing the new 1.7 driver allows it to work just fine under gutsy.

---

### Post by suoko on 2007-10-09
I'm trying to install a quickcam express webcam (Bus 003 Device 002: ID 046d:0840 Logitech, Inc. QuickCam Express) in GUTSY and ./quickcam.sh 
command exited with "[!] Didn't find compatible cameras."

What's up?
[edit: just tryed on feisty and worked out of the box!]

Maybe by bttv card (which is /dev/video0) causes a conflict?

UPDATE:
It works now in gutsy. Camorama only needs a '-d /dev/video1' option to work and ekiga correctly finds it under V4L

---

### Post by encompass on 2007-10-09
Did you run it in feisty before?
I don't understand why they having put this driver in the kernel yet, but they haven't for 3 releases.
Umm, I have had the same error, and installed anyway.  It seems to work just fine. And this camera is for the Quickcam Messenger, yours may be similar, but I don't think it will work with the Quickcam Express.  Sorry.  You may have the wrong driver all together.

---

### Post by e1ektrob0y on 2007-10-22
My quickcam messenger works in 7.10 in camorama, but will not work with userplane chat or msn...I haven't installed any drivers yet, it just worked out of the box. Any ideas on how to get it working for userplane chat and msn?
I'm worried if i try to install the drivers it will stop working at all:O

---

### Post by encompass on 2007-10-22
Not sure what to tell you...
YAY it is finally working in ubuntu..
and 
YIKES lets hope it doesn't... I would report a bug to ubuntu first.

---

### Post by e1ektrob0y on 2007-10-22
Ok, i went back to the 32bit installation of gutsy. The quickcam messenger now works in all my chatting apps but it is super zoomed:O should i bother trying to install other drivers or will that do nothing to correct the super zoom?

---

### Post by roderikk on 2007-10-29
Should we recommend the driver here:

[http://www.desktoplinux.com/news/NS6669895837.html](http://www.desktoplinux.com/news/NS6669895837.html)

> So if you want a specific device that doesn't work on Linux to be properly supported on Linux, Kroah-Hartman would appreciate it if you would mark up the project's Drivers Needed wiki page with the details. Or, for that matter, he encourages you to just e-mail him with your suggestion.

Kroah-Hartman concluded, "If patterns emerge, I'll approach the companies and ask them if they will work with us. Hopefully with your help, we can find some work for these 310 developers to do!"

So maybe add it here: [http://linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded](http://linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded)

---

### Post by baatz on 2007-10-30
Hi there,

My quickcam won't install, it hangs on (un)loading the driver module:
Trying to unload QuickCam driver...
ERROR: Module quickcam does not exist in /proc/modules
ERROR: Module mod_quickcam does not exist in /proc/modules

This is my cam:
Bus 002 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
I've seen this one working in replies to this how to, so i don't really get it.

lsof /dev/video0 returns nothing, and lsof/dev returns a whole list but nothing with video0 or something related.

i'm running gutsy 7.10, kernel 2.6.22.14,. and compiz trhogh xgl, what could be wrong ?

---

### Post by lssoares on 2007-11-01
HI guys,

I have my webcam working on gutsy....I will try to describe it. Please experienced people, feel free to correct the steps below....I'm just a beginner.

1) Find out which camera you have...plug in the usb and perform the command: **lsusb**
in my case:
Bus 002 Device 002: ID **046d:08f5** Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

2) find the drivers (google helps a lot!) for the specified ID...my case:
046d:08f5
I found the driver on:
[http://home.mag.cx/messenger/]("http://home.mag.cx/messenger/")
Another good site: 
[http://http://tuukkat.awardspace.com/quickcam/quickcam.html]("http://http://tuukkat.awardspace.com/quickcam/quickcam.html")

3) install needed software:
[B]sudo apt-get install linux-headers-`uname -r`
sudo apt-get install build-essential
sudo apt-get install xawtv
sudo apt-get install qcset[/B]

qcset is used on quickcam.sh (shell script from the driver I downloaded)


4) Uncompress the downloaded driver. My case:
**tar -zxvf qc-usb-messenger-1.7.tar.gz**

5) On the new folder where driver is, there's a file named quickcam.sh, this is the script that will compile and install the driver...I tried running this file several times and got several errors.
I made some workarounds that are not advisable...but it worked. Here are the steps I took:

5a) After some privileges problems while running quickcam.sh, I started running it as root (sudo -s). But be advised this is not the way it should be...I had my mother in law on the living room, asking for me every 5 minutes... :)

5b) The first error I got was during the driver compilation...something like 
error: linux/config.h:File not found
I just created an empty file called config.h on the linux headers folder and reran quickcam.sh:
**touch /usr/src/linux-headers-`uname -r`/include/linux/config.h**

Just for documentation, my kernel and gcc versions are:
2.6.22-14-generic
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)


5c) The second error I got had something to do with dmesg command on quickcam.sh not being able to find out the device...the  message was:
"I will be using ., if there are more cameras I'll not test them."
Instead of "." In my case it should refer to /dev/video0.
You can check this by executing:
**dmesg |grep "quickcam: Registered device"**

After knowing which device, I made a copy of quickcam.sh and just added the lines in bold:

VIDEODEV=`dmesg | awk '/^quickcam: Registered device:/ { print $4 }' | head -n 1`
[ -z "$VIDEODEV" ] && VIDEODEV=`dmesg | awk '/quickcam: Registered device:/ { print $5 }' | head -n 1`
[ -z "$VIDEODEV" ] && VIDEODEV=`dmesg | awk '/quickcam: Registered device:/ { print $6 }' | head -n 1`

VIDEODEV_REAL="`$REALPATH $VIDEODEV`"
[B]
VIDEODEV=/dev/video0
VIDEODEV_REAL=$VIDEODEV[/B]

...and reran the script.


5d) The next error was due to qcset not being installed, and it's referenced on the quickcam.sh as in the local path where you run the script....you should change from:
./qcset "$VIDEODEV" -i | head -n 1 | grep 'Logitech QuickCam USB'
to 
qcset "$VIDEODEV" -i | head -n 1 | grep 'Logitech QuickCam USB'

and of course...I reran the script.


5e) Add on the end of  /etc/modules the module: "modprobe quickcam" (without quotes)
**sudo gedit /etc/modules**


Sorry I did not have the time to correct the scripts...
Hope this helps.

---

### Post by NeillHog on 2007-11-10
Am I the only person with a camera where the video works but not the microphone.

Camera Quickcam messenger
Bus 005 Device 007: ID 046d:08da Logitech, Inc.
videodev               29312  1 gspca
Kubuntu 7.10

The camera works in Skype and in Ekiga. Both echo services are OK, can see myself and at least in Skype the person at the other end can also see me.

But no internal microphone.
I assume that all the stuff people are writing about drivers is when there is no video. Has anyone else experienced the "no microphone" problem?

Thanks - and have fun!

---

### Post by encompass on 2007-11-11
Woah, wait a minute!  Does skype have video support!?

---

### Post by NeillHog on 2007-11-11
Yes! Skype has a new beta version for Linux with video support.
It is definitely beta. With some cameras (mine for example) it crashes after a minute and with some the picture is not good. But it is a move in the right direction and beta is beta right.
Neill

---

### Post by pianoboy3333 on 2007-11-13
hey after I run the setup I can get camorama to open, but I get the error "Unable to capture image" in a popup and it closes right after. In addition the skype beta sees I have a camera, but an image does not appear when I try and test it. Help?

Also, when I restart it is no longer registered as a device.

---

### Post by stansford on 2007-11-15
3) install needed software:
[B]sudo apt-get install linux-headers-`uname -r`
sudo apt-get install build-essential
sudo apt-get install xawtv
sudo apt-get install qcset[/B]

qcset is used on quickcam.sh (shell script from the driver I downloaded)


hi,
Anybody know how to get qcset? I tried installing this with apt-get and it didn't have it. I also checked the ubuntu packages site and it didn't seem to know about it either....
Any help appreciated.

---

### Post by Limulus on 2007-11-16
qcset can be found in the qc-usb-utils package (see [http://packages.ubuntu.com/qc-usb-utils](http://packages.ubuntu.com/qc-usb-utils) or Synaptic for more info) or its compiled from the source you can download.

---

### Post by kris_a on 2008-01-22
Maybe I have a different version to the rest of you guys, but mine "Just Works" with Gutsy.  I didn't need to compile anything or even change any settings, I get the Video and Mic:

lsusb:
Bus 002 Device 003: ID 046d:08da Logitech, Inc.
Bus 001 Device 002: ID 046d:c03d Logitech, Inc.

From the previous posts I guess the 08da is the camera part.

The only problem I found was that 2 of the colour channels were swapped when using camorama, but you just need to add the Color Correction filter to correct it.  The camera works fine in Skype and Ekiga etc.

Hope that helps somebody :)
Kris.

---

### Post by LostinSpacetime on 2008-01-25
Hello everybody :)
I have a (probably basic) question. First to my problem.
My webcam (Logitech Quickcam Messenger) works fine on my system (Ubuntu Feisty Fawn) and after using gstfakevideo, I can use it even in Skype. My problem, is that the picture is far to dark and the auto exposure doesn't work with the driver I have. It looks like the driver used is usbvideo, but I couldn't figure out how/if one can adjust the brightness with this driver. But I found out, that there is a far better driver for this webcam, namely the quickcam-usb driver. After downloading the source, and a "sudo make install" everything seemed to be ok. sudo modprobe quickcam did its job.
Now to my question. In my case I have (at least) two drivers which can handle the webcam. It looks like the device is still using the usbvideo driver. How can I change that???

Please help!!

---

### Post by Raizor on 2008-08-19
For anyone who may have had this problem, like I did, after the initial installation of the driver and then the camera wouldn't work (it simply reported that /dev/video0 was busy) check to see if you have installed the motion package via the Synaptec Package Manager.

If you have this installed, and your camera isn't working properly after reboot, once removed you will get control of your camera back.

Might not help some people, but if it helps someone else then why not post it in the spirit of open source right?!

:guitar:

---

### Post by hitman1985 on 2008-08-28
ok, i got the quick cam messenger as well, i did all the scripts like told up ontop of the page here, the video is visible for me, but not for the other end on skype ?

anyone got some ideas?

thanks

---

### Post by encompass on 2008-08-28
I personally would ask skype.  Because the software is closed source, no one can go in and really find out what the problem is.  We just end up guessing.  Skype is paid to help you.  They are probably your best bet.  It worked for me.  And I use the newest skype version they have.

---

### Post by Kroteng on 2009-03-17
Hello,
I did everything and this happened:
- build-essentials and camorama was already installed 
- sudo apt-get install linux-headers-2.6.27-11-generic
tells, is it already installed
After running the script it comes to this point:

> Another round done. Let's now compile the driver, it takes a while.
This step will also clear old unnecessary files from the directory.
and then a lot of errors:
> /home/tobi/Desktop/qc-usb-messenger-1.8/qc-driver.c: In Funktion »qc_frame_exit«:
/home/tobi/Desktop/qc-usb-messenger-1.8/qc-driver.c:1619: Fehler: Anfrage nach Element »counter« in etwas, was keine Struktur oder Variante ist
/home/tobi/Desktop/qc-usb-messenger-1.8/qc-driver.c:1630: Fehler: Anfrage nach Element »counter« in etwas, was keine Struktur oder Variante ist
/home/tobi/Desktop/qc-usb-messenger-1.8/qc-driver.c: In Funktion »qc_frame_get«:
/home/tobi/Desktop/qc-usb-messenger-1.8/qc-driver.c:1659: Fehler: Anfrage nach Element »counter« in etwas, was keine Struktur oder Variante ist
/home/tobi/Desktop/qc-usb-messenger-1.8/qc-driver.c:1666: Fehler: Anfrage nach Element »counter« in etwas, was keine Struktur oder Variante ist
/home/tobi/Desktop/qc-usb-messenger-1.8/qc-driver.c: In Funktion »qc_v4l_open«:

and a lot of more. It's german and it says something like
Error: Querry for element "counter" is not a structure a or a variable (?)
And then its finished.
Can you help me to install the driver? 
Thank you very much :)
(Sory for my bad English.)

---

### Post by encompass on 2009-03-17
This thread is REALLY old now.  I don't even know if it still works.  I no longer use this cam, but the last I remember, it works in ubuntu just fine, you just plug it in now.
Wish I could help more.
Regards,
Jason Brower

---

### Post by encompass on 2009-03-17
> **hitman1985 said:**
> ok, i got the quick cam messenger as well, i did all the scripts like told up ontop of the page here, the video is visible for me, but not for the other end on skype ?

anyone got some ideas?

thanks

Actually, it sounds like it's on there end where the issue is... can you tell a little about there computer?  I have a similar issue when I try to display both mine and the other persons video with my intel graphics card.  They tend to not play well together.

---

### Post by CrazyBase on 2009-05-25
> **Kroteng said:**
> Hello,
I did everything and this happened:
- build-essentials and camorama was already installed 
- sudo apt-get install linux-headers-2.6.27-11-generic
tells, is it already installed
After running the script it comes to this point:


and then a lot of errors:

and a lot of more. It's german and it says something like
Error: Querry for element "counter" is not a structure a or a variable (?)
And then its finished.
Can you help me to install the driver? 
Thank you very much :)
(Sory for my bad English.)

I am receiving the same error..  Here is the output of quickcam.sh

```

bassam@bassam-desktop:~/Desktop/qc-usb-messenger-1.8$ ./quickcam.sh 
-=- Logitech QuickCam USB camera driver installer -=-
Hello! I am the (hopefully) easy-to-use, fully automated
qc-usb driver installation script.
At the moment, this is experimental, and if it doesn't work,
don't hesitate to quit this with Ctrl+C and install the
driver manually.

The driver is provided in source code form, so it has to be
compiled. This should happen automatically, but it does mean
that there are some steps required before installation.

You also need to know "root" user password to test and
install the driver.

Basically you need only to keep hitting Enter whenever you
see this prompt: --->. Sometimes you're asked root password.
Pay special attention to lines beginning with [!].
It means that some trouble has been detected.

To most important location is the path to your kernel source
or headers. This can be guessed, but you can specify it by
giving it as an argument to this script like this:
        ./quickcam.sh LINUX_DIR=/usr/src/linux

If you haven't done it yet, now it would be a good moment to
take a look at file README.

Next I'm going to check if you have some important programs installed
and if they and the kernel are of suitable version.
Press Ctrl+C to quit, Enter to continue ---> 

Using specified C compiler from environment CC=gcc
./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc
/usr/bin/gcc
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
/bin/readlink
gcc version: Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu12' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 
gcc version: Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu12' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 
Make version: GNU Make 3.81
Linker version: GNU ld (GNU Binutils for Ubuntu) 2.18.93.20081009
Kernel compiler: gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 
[!] Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
        export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 

Looking for more necessary programs...
Found program /sbin/depmod
Found program /sbin/insmod
Found program /sbin/rmmod
Found program /sbin/modprobe
Found program /bin/mount
Found program /usr/sbin/lsusb
depmod version: module-init-tools 3.3-pre11
insmod version: module-init-tools version 3.3-pre11
rmmod version: module-init-tools version 3.3-pre11
modprobe version: module-init-tools version 3.3-pre11
Checking whether we're root... bassam
Checking for driver source code...
Checking for write permission...

Previous round done. Now checking if you have kernel source installed.
Press Ctrl+C to quit, Enter to continue ---> 

Kernel source directory: /lib/modules/2.6.27-14-generic/build
Detected kernel version is 2.6.x.
Kernel version name: 2.6.27-14-generic
Kernel source version code: 132635
Driver file name: qcmessenger.ko
Module install directory: /lib/modules/2.6.27-14-generic
Driver source directory (PWD):         /home/bassam/Desktop/qc-usb-messenger-1.8
Kernel source directory (LINUX_DIR):   /lib/modules/2.6.27-14-generic/build
Module install directory (MODULE_DIR): /lib/modules/2.6.27-14-generic
Utility install directory (PREFIX):    /usr/local
User options (USER_OPT):               -DHAVE_UTSRELEASE_H=1
Driver file name (use with insmod):    qcmessenger.ko
Kernel version code:                   132635

The QuickCam driver requires other drivers from kernel.
I'll now check if those seem to be loaded.
Press Ctrl+C to quit, Enter to continue ---> 

Modules loaded into the kernel:
isofs udf crc_itu_t ipt_MASQUERADE xt_DSCP af_packet binfmt_misc bridge stp bnep sco rfcomm l2cap bluetooth ppdev apm cpufreq_stats cpufreq_userspace cpufreq_ondemand freq_table cpufreq_conservative cpufreq_powersave ipt_REJECT ipt_LOG xt_limit ipt_addrtype xt_state xt_tcpudp xt_conntrack ip6table_filter ip6_tables ipv6 nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_conntrack_ftp parport_pc lp parport snd_cs46xx gameport snd_ac97_codec ac97_bus snd_seq_dummy snd_usb_audio snd_pcm_oss snd_mixer_oss snd_pcm snd_usb_lib snd_seq_oss snd_seq_midi snd_rawmidi snd_hwdep evdev snd_seq_midi_event quickcam_messenger usbvideo videodev v4l1_compat snd_seq psmouse snd_timer snd_seq_device serio_raw snd i2c_piix4 shpchp intel_agp soundcore snd_page_alloc pcspkr pci_hotplug i2c_core agpgart iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack iptable_mangle iptable_filter ip_tables x_tables ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg ata_generic pata_acpi ata_piix libata 3c59x mii uhci_hcd scsi_mod usbcore dock fbcon tileblit font bitblit softcursor fuse 

Next round: let's see if you have a supported QuickCam.
Please plug in your USB camera before continuing.
Press Ctrl+C to quit, Enter to continue ---> 

I can find the following probably compatible devices:
Bus 001 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

Another round done. Let's now compile the driver, it takes a while.
This step will also clear old unnecessary files from the directory.
Press Ctrl+C to quit, Enter to continue ---> 

rm -f *.o qcset input_read show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
cd testquickcam ; make clean
make[1]: Entering directory `/home/bassam/Desktop/qc-usb-messenger-1.8/testquickcam'
rm -f testquickcam *~ pic.ppm pic.gif
make[1]: Leaving directory `/home/bassam/Desktop/qc-usb-messenger-1.8/testquickcam'
make -C "/lib/modules/2.6.27-14-generic/build" SUBDIRS="/home/bassam/Desktop/qc-usb-messenger-1.8" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-14-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /home/bassam/Desktop/qc-usb-messenger-1.8/.tmp_versions ; rm -f /home/bassam/Desktop/qc-usb-messenger-1.8/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/bassam/Desktop/qc-usb-messenger-1.8
  gcc -Wp,-MD,/home/bassam/Desktop/qc-usb-messenger-1.8/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-14-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(qcmessenger)" -c -o /home/bassam/Desktop/qc-usb-messenger-1.8/.tmp_qc-driver.o /home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ?qc_frame_exit?:
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:1619: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:1630: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ?qc_frame_get?:
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:1659: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:1666: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ?qc_v4l_open?:
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2688: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2693: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2708: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2714: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2716: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ?qc_v4l_close?:
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2750: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2752: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2767: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2770: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ?qc_v4l_read?:
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2804: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2826: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ?qc_v4l_mmap?:
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2855: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2862: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ?qc_v4l_ioctl?:
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2884: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:2898: error: ?struct video_device? has no member named ?type?
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:3455: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c: At top level:
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:3487: error: unknown field ?type? specified in initializer
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ?qc_usb_init?:
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:3550: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:3556: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:3559: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:3564: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:3665: error: ?struct input_dev? has no member named ?private?
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:3772: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:3774: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:3784: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:3791: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ?qc_usb_disconnect?:
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:4060: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:4062: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:4075: error: request for member ?counter? in something not a structure or union
/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.c:4079: error: request for member ?counter? in something not a structure or union
make[2]: *** [/home/bassam/Desktop/qc-usb-messenger-1.8/qc-driver.o] Error 1
make[1]: *** [_module_/home/bassam/Desktop/qc-usb-messenger-1.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-14-generic'
make: *** [qcmessenger.ko] Error 2
ls: cannot access qcmessenger.ko: No such file or directory
[!] Looks like the driver compilation failed.
Did you get any error messages above?
If asking for help, show what error messages you got.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> ^C

```

---

### Post by encompass on 2009-05-25
Are you sure the camera just works now?  I no longer need this as it works simply by plugging in the camera.  This thread is extremely old and no longer needed.  I would recommend sending a not to the creating of the driver. (The website that you downloaded the driver from.) He may be able to help.

---

### Post by CrazyBase on 2009-05-29
> **encompass said:**
> Are you sure the camera just works now?  I no longer need this as it works simply by plugging in the camera.  This thread is extremely old and no longer needed.  I would recommend sending a not to the creating of the driver. (The website that you downloaded the driver from.) He may be able to help.

When I tried using Skype, the camera didn't work.  What application did you use to get the webcam working?

---

### Post by encompass on 2009-05-29
I presume you set the skype up in skype itself.
There are a few options.
Cheese
Camorama
Amsn
Kopete (I think)
All are part of the repositories in linux.
Not sure how much money you have and if your in the states.  But I have the most perfect one, and it says it has linux support.  That quality if very good, and even has a very nice mic. Like 30USD.

---

### Post by spezifanta on 2009-06-14
I followed this instruction here:
[http://www.kuhrti.de/index.php/article/logitech-quickcam-messenger-on-ubuntu-9-04](http://www.kuhrti.de/index.php/article/logitech-quickcam-messenger-on-ubuntu-9-04)

And it **worked** even in Skype!!

---

### Post by Levo on 2009-09-04
I get this error all the time: 

```

gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 
Make version: GNU Make 3.81
Linker version: GNU ld (GNU Binutils for Ubuntu) 2.19.1
Kernel compiler: gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 
[!] Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
	export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels
```

If I ignore it, there are errors when it tries to compile the driver.
Please help!

---

### Post by encompass on 2009-09-04
This shouldn't be needed anymore at all. Your cam should work when you just plug it in.  What version of ubuntu are you running?

---

### Post by Levo on 2009-09-05
> **encompass said:**
> This shouldn't be needed anymore at all. Your cam should work when you just plug it in.  What version of ubuntu are you running?

Ubuntu Jaunty. And it is updated. The cam does not work, although it is recognized by the "lsusb" command.

---

### Post by encompass on 2009-09-05
Lsusb is just a system to recognize what is plugged in.  It is basically what a driver needs to see to make sure it's looking at the right device.
What does lsusb say?  could you past it here?

---

### Post by Levo on 2009-09-05
> **encompass said:**
> Lsusb is just a system to recognize what is plugged in.  It is basically what a driver needs to see to make sure it's looking at the right device.
What does lsusb say?  could you past it here?

Yes I know. I just wanted to tell you that the camera is correctly plugged.

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 0810:0001 Personal Communication Systems, Inc. 
Bus 002 Device 004: ID 0810:0001 Personal Communication Systems, Inc. 
Bus 002 Device 003: ID 0665:5161  
[COLOR="Red"]Bus 002 Device 002: ID 046d:08f6 Logitech, Inc. Quickcam Messenger Plus[/COLOR]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by encompass on 2009-09-05
Yeah it looks like you have the same cam I USED to have.  They changed the name with the plus at the end.  But the usb id is the same.  Interesting.
Check here...
encompass@essence:~$ apt-cache search qc-usb
qc-usb-source - source for the QuickCam Express driver
qc-usb-utils - utility programs for the QuickCam Express driver
encompass@essence:~$ 
I wonder if those will come in handy.
As well as...
[http://sourceforge.net/projects/qce-ga/files/qc-usb/0.6.4/](http://sourceforge.net/projects/qce-ga/files/qc-usb/0.6.4/)
As they say this driver works for this cam from here...
[http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)
Sadly, Logitech LOVES to change hardware on the same model of webcam.  They think it's ok, not knowing it screws drivers up for the volunteers.
If you get it working I am happy to relay people to your howto. Hint hint.
THANKS FOR USING MEMAKER! I MANAGE THAT!

---

### Post by Levo on 2009-09-05
> **encompass said:**
> Yeah it looks like you have the same cam I USED to have.  They changed the name with the plus at the end.  But the usb id is the same.  Interesting.
Check here...
encompass@essence:~$ apt-cache search qc-usb
qc-usb-source - source for the QuickCam Express driver
qc-usb-utils - utility programs for the QuickCam Express driver
encompass@essence:~$ 
I wonder if those will come in handy.
As well as...
[http://sourceforge.net/projects/qce-ga/files/qc-usb/0.6.4/](http://sourceforge.net/projects/qce-ga/files/qc-usb/0.6.4/)
As they say this driver works for this cam from here...
[http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)
Sadly, Logitech LOVES to change hardware on the same model of webcam.  They think it's ok, not knowing it screws drivers up for the volunteers.
If you get it working I am happy to relay people to your howto. Hint hint.
THANKS FOR USING MEMAKER! I MANAGE THAT!


My webcam 4 years old, but I didn't use it, so I didn't try to make it work under ubuntu. I'll check these links and post if it worked.

---

### Post by Levo on 2009-09-05
It fails when compiling. Nothing works.

---

### Post by IllegalCharacter on 2010-01-09
I've been following the instructions given here:
[http://www.kuhrti.de/index.php/article/logitech-quickcam-messenger-on-ubuntu-9-04/](http://www.kuhrti.de/index.php/article/logitech-quickcam-messenger-on-ubuntu-9-04/)

Unfortunately under Karmic and kernel version 2.6.31-16 the compilation fails because of slightly different kernel code. I tweaked it so that everything matches up and now it compiles, however when I run:```
sudo qcset /dev/video0 compat=dblbuf
```I get the error:```
qcset: ioctl VIDIOCGCHAN (Invalid argument)
```I'm not really an experienced kernel hacker, does anybody have any pointers on what to do here?

---

### Post by no2498 on 2010-01-24
i know this is old but it needs to be said
all we need now days for most cams is
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2

do not think about skipe or msn or yahoo yet

get a program to use it with first like 
cheese or wxcam or xawtv
is a lot more cant think or all of em

just get the cam up and running first

now go play enjoy :)

---

### Post by Pink_bunny_death on 2010-02-19
i am new to this whole deal... within the day.  when i try to extract this little guy...


-desktop:~$ tar -xvf qc-usb-messenger-1.8.tar.gz
tar: qc-usb-messenger-1.8.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

what do i do to fix that?

---

### Post by encompass on 2010-02-20
First off, make sure you have the right webcam. And have you checked that it already works?  This post is VERY old and the cam I made this for works just fine in linux now. (Don't have it any more though, so I can't totally confirm that.
Second, the error says that that file or directory doesn't exist.  Sounds like the name your giving it is wrong. type ls to see if your in the right directory.  I am happy to try to help you more with this on a personal conversation if we know it doesnt' work.
Go to the ubuntu software center and install cheese.  Run that and see if you get any results.  (When it is installed it's in the Sound and video menu.

---

### Post by IllegalCharacter on 2010-02-20
I'll add a note, this driver does NOT work with Karmic. I've tried to use both the 1.7 and 1.8 drivers from that site and neither work. I've even tried tweaking the driver to match the 2.6.30+ kernels and it also doesn't work (I'm not an amazing kernel hacker so that might be behind it).

Recently I switched back to Jaunty with a fresh install, and the webcam works fine out of the box. If it is that important, perhaps that is the right route to take.

---

### Post by 801TomAK on 2010-08-13
i dont know if any ones posted this but if ubuntu dosnt have a program to test your web cam just down  down load this in the terminal real quick to see if its working 
sudo apt-get install cheese

---

### Post by JohnHeikkila on 2010-10-21
I can confirm that this QuickCam driver doesn't work on Maverick (10.10).
My QuickCam Messenger Plus (046d:08f6) works out of the box with Cheese.

---

