---
title: "Webcam problems suggest Hardy not yet ready for desktop"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Roger D on 2008-05-18
Hi

Bit of a tale of woe here.

I've recently upgraded from Dapper to Hardy via a fresh install. Very impressive, window performance much better, my wireless card works without problems, and the normal visual effects are very nice. I've been using linux for about three years, first Suse; then Ubuntu, and it's great to see things getting better and better.

Unfortunately, all this has been a bit undermined by my efforts to get a webcam working. I want to be able to use Skype to  talk to, and see, my daughter who, like me, lives in a rather remote part of England - our different parts are on opposite sides of  the country.

I dug around trying to identify a webcam that would work 'out of the box', settling on the Logitech Quickcam Pro 9000, which, I gather, works with the uvc drivers, part of Hardy.

I plugged it in, and nothing much happened. As a test of whether was working or not I downloaded Cheese. It 'sort of worked' at first. I got an incredibly slow video image, and managed to take a couple of photos and record a short, poor-quality, video. At one stage I managed to access the Cheese help menu, and via the Cheese FAQs learned that slow video might be due to the video processing being done by my CPU, as opposed to my graphics card. Unfortunately, when I tried to follow the advice for correcting this, what I saw on my screen didn't match the instructions. Things have subsequently gone from bad to worse - I don't know why - and when I now turn on Cheese, the activity light on my webcam comes on briefly, and then turns off.

Digging around again, I found references to lucview, which I downloaded. Again, this started off working after a fashion - I got a screen display with an image, but the image was divided into segments, which were jumping around at high speed - sorry, but I can't explain this any more clearly. Now, however, lucview has also stopped working, and when I run luvcview in my terminal I get:

roger@roger-desktop-new:~$ luvcview
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 5.
 Init v4L2 failed !! exit fatal 
roger@roger-desktop-new:~$ 

Maybe that means something to somebody.

I've posted details of my problems on the multimedia and video forum, but haven't got anywhere. A real understand of how to make problem webcams work in Ubuntu seems to be in short supply, and I keep coming across posting from other users who have just had to give up.

Given that there's so much in Hardy that is so good, this is all very frustrating. I've friends who have had their share of problems with Vista, and I've been tempted to suggested they try Ubuntu. However, the ease with which I got my webcam running on an old Windows XP box, makes me think they're better off with the devil they know.

Any comments, or advice on getting my webcam working would be much appreciated.

Best regards

Roger D

---

### Post by Roger D on 2008-05-18
Well, what do you know, but the webcam now seems to be working - at least to a useful degree. Cheese is a bit strange - I have to click on the Help menu to stop it shutting down automatically, and the video image is terribly slow. On this last point, I've followed the advice about running gstreamer-properties in my terminal and changing the video default output-plugin to X Window System (X11/XShm/Xv), but it doesn't make any difference. Also, luvcview generally works; again after a fashion. The image isn't slow, like Cheese, but, some of the controls, like tilt and pan don't work. Last, but not least, the video test in Skype seems to work.

It all seems a bit like 'work in progress' and I've now idea why it wasn't working yesterday, but perhaps we're getting there

Roger D

---

### Post by Roger D on 2008-05-19
Hi

This is turning into a bit of a blog, as opposed to a thread, but after two days on this problem I need to get a few last thoughts 'off my chest'.

Here's a summary of where I am:

1 Cheese, as I say above is 'a bit strange'. Hunting around on forums suggests the slow video is a common problem, which nobody seems to know how to fix.

2 Skype seems as though it's going to work - the video test is fine, although I've yet to test it on real call

3 luvcview works to a limited degree - I get a decent image, but I can't tilt and pan my webcam

4 I've also run gstreamer-properties. When I test the video I get a slow image, similar to Cheese and the message: Failed to construct test pipeline for 'video for Linux 2 (v4|2)'. Which suggests that, maybe, the problem with Cheese lies somewhere in my set-up, but I've no idea where.

So what's the conclusion from all this? I'm afraid it's simply that Hardy does not, as yet, provide adequate support for webcams. Without a working Cheese, there is no way to record video images. Also, there's no way to control your webcam.

I know it's all down to having the right drivers and software, and Logitech does all this for Windows users, but this kind of hole in Linux's capabilities is just the thing that, rightly, prevents the average computer user from switching from Windows to Linux - all the problems of Windows notwithstanding. I'm afraid, unlike me, most sensible people have better things to do with their weekends then trying to get a webcam to work.

It's surely just a matter of devoting the right level of resources to the problem - printers and wireless cards can be made to work happily under Linux, why not webcams? The polish and performance of a modern Linux distribution is a reflection of the millions and million of dollars that the likes of IBM, Sun, Novell, Red Hat and Mark Shuttleworth have pumped into Linux development. Progress over the last few years has been amazing, but there are still some serious deficiencies that need addressing - webcams for one, and a robust, easy-to-use backup package is another.

I'm sure this will  get sorted in time, until then, however, I'm afraid I'll be telling my friends to stick with Windows.

Comments would be welcome. And if anyone has any ideas for fixing Cheese, that would be really great.

Roger D

---

### Post by HotShotDJ on 2008-05-19
> **Roger D said:**
> I'm afraid it's simply that Hardy does not, as yet, provide adequate support for webcams.I'm afraid I see it a bit differently.  It is that the Webcam manufacturers do not provide adequate support for Linux.  Linux developers are not even asking them to spend one penny of their profits on driver development in Linux.  Just give them the specs and they'll do the work... for FREE.  They've even offered to sign Non-Disclosure Agreements! But many (but by no means all) hardware vendors are simply refusing to cooperate with anyone but Microsoft.

Of course, to the end-user, this is a distinction without a difference.  Either way, some webcams are just unusable in Linux, leaving them with few choices.  I just hate it when folks blame Linux developers rather than placing the blame where it rightly belongs -- on the hardware manufacturers.

---

### Post by Roger D on 2008-05-19
Yes, I understand what you're saying. But I carefully chose a webcam that was supposed to work 'out of the box' with Hardy, and I've had all these problems, and nobody seems to know how to begin to address them.

Don't get me wrong, I'm a huge fan of Linux, and I'm certainly not going back to Windows. But, like a lot of guys out there, I just wish I knew how to get Cheese working properly.

Anyway, many thanks for the response.

Best regards

Roger D

---

### Post by TWO on 2008-05-19
> **HotShotDJ said:**
>  Either way, some webcams are just unusable in Linux, leaving them with few choices.  I just hate it when folks blame Linux developers rather than placing the blame where it rightly belongs -- on the hardware manufacturers.

But that's the thing. People aren't going to stop blaming Linux developers. Being able to use a Linux-based OS is a fantastic thing and I suppose the fact that it is provided for free means that we can't really complain. But the fact of the matter is that free or not, the OS in question, which purports to being a fully usable desktop which can rival other mainstream distributions, is seemingly failing to provide functionality for a very common peripheral.  


> But many (but by no means all) hardware vendors are simply refusing to cooperate with anyone but Microsoft. Of course, to the end-user, this is a distinction without a difference.

Linux users are said to be in the minority, so one would expect that we should just accept these types of discrepancies. But a distribution like Ubuntu DOES provide the same functionality as popular propriety distributions and so therefore people do start to point the blame at the nearest target, when it comes to something like this. I know that no one is telling us to use Ubuntu, but people have chosen to and they expect that things will work as well as is reputed. 

The web cam issue is such an inconvenience. I can't seem to get mine to work on either Cheese or Camorama. It would be nice if there was some GUI way of being able to reinstall drivers to see if other types would work. In Ubuntu, my webcam has never played video with normal colours. It's always too blue, or too yellow. When using Skype or an Instant Messenger, it has never seemed worth the effort using a webcam. I know there are people out there who are lucky enough not to experience problems with webcams or other peripherals but the title of of this thread still rings true.  At the end of the day, no matter how anti-Microsoft people can be, in my own experience and in (no doubt in) those of others, when you plug a peripheral into a computer when using Windows, 99% of the time, it'll find the drivers. They say that Linux supports more hardware out of the box, but I'm yet to experience this fully...

(As far as this problem is concerned amongst others,) I'm willing to stick around, wait and contribute in what way I can, but the frustration is always going to be there when you just want something to work. And dual booting is going to be the norm for the foreseeable future...

TWO

---

### Post by philinux on 2008-05-19
Have you tested with amsn or kopete?

---

### Post by Roger D on 2008-05-19
No. I don't use instant messaging. But thanks for the suggestion

Roger D

---

### Post by dark_harmonics on 2008-05-19
[Rant]
> **HotShotDJ said:**
> I'm afraid I see it a bit differently.  It is that the Webcam manufacturers do not provide adequate support for Linux.  Linux developers are not even asking them to spend one penny of their profits on driver development in Linux.  Just give them the specs and they'll do the work... for FREE. 

You guys might not like this response but this person is EXACTLY RIGHT. If you have a problem with hardware compatibility with say windows XP you dont go blaming microsoft. You would go right to logitech and call their tech support and demand " Why doesnt this work with windows xp? This is obsurd!?!?" It is just as wrong to exclude the growing millions of linux users. 

This is a revolution in progress and you will find greater and greater vendor involvement, but YOU CAN MAKE A DIFFERENCE. Call them and ask for linux support. Email them and demand support for your hardware under linux. It is not that hard for them to do. 

If you are a computer technician, support hardware vendors that supply drivers for EVERYBODY. Not just Microsoft users. 
[/rant]

I have also had problems with webcam drivers in the past. It seems webcams and wireless were my biggest gripes (mostly due to poor support from hardware vendors). Did you try easycam? 
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by sdennie on 2008-05-19
Is it possible that you have the webcam hooked up to something less than a USB 2.0 port?  If that were the case, it may not have the bandwidth to fully stream the video and no operating system could fix the problem.

---

### Post by Roger D on 2008-05-19
No, I'm absolutely fine with the suggestion that I should pass the problem back to Logitech. I'll email them and ask when they don't provide drivers and  the equivalent of the HP-toobox. In my limited way I do want to do all I can to help make Linux a viable alternative to Windows.

No I haven't tried easycam - I'd never heard of it. But I'll certainly give it a try.

In reply to Vor. I am connected to a 2.0 USB port, and I've tried switching between different ports

Many thanks for the helpful respones.

Roger D

---

### Post by TWO on 2008-05-19
> **dark_harmonics said:**
> [Rant]


You guys might not like this response but this person is EXACTLY RIGHT. If you have a problem with hardware compatibility with say windows XP you dont go blaming microsoft. You would go right to logitech and call their tech support and demand " Why doesnt this work with windows xp? This is obsurd!?!?" It is just as wrong to exclude the growing millions of linux users. 

This is a revolution in progress and you will find greater and greater vendor involvement, but YOU CAN MAKE A DIFFERENCE. Call them and ask for linux support. Email them and demand support for your hardware under linux. It is not that hard for them to do. 

If you are a computer technician, support hardware vendors that supply drivers for EVERYBODY. Not just Microsoft users. 
[/rant]

I have also had problems with webcam drivers in the past. It seems webcams and wireless were my biggest gripes (mostly due to poor support from hardware vendors). Did you try easycam? 
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)


As futile as it is, I think I'd have a gripe at Microsoft as well since they make the claim that things "just work" when you plug them in even though there are occasions where things don't "just work." As you say, it's nothing to do with them. It's to do with the manufacturer.  

I think the frustration lies in the fact that we're told a certain thing by the distribution promoters, but then the outcome is sometimes quite different.


I've battling with webcams myself as well. I just tried mine on aMSN, and I was left with a low quality, dark video. It's an ELECOM UCAM-H1C30MBK, which I don't think is a major brand name, but it does come up as a 'Typhoon Easy Cam' under aMSN.

I ran luvcview in the terminal and it gave the following results:

luvcview version 0.2.1
Video driver: x11
A window manager is available
video /dev/video0
Error opening device /dev/video0: unable to query device.
 Init v4L2 failed !! exit fatal

I would really appreciate if anyone could help to remedy the output. 

TWO

---

### Post by Roger D on 2008-05-19
> **TWO said:**
> 

I think the frustration lies in the fact that we're told a certain thing by the distribution promoters, but then the outcome is sometimes quite different.


I've battling with webcams myself as well. I just tried mine on aMSN, and I was left with a low quality, dark video. It's an ELECOM UCAM-H1C30MBK, which I don't think is a major brand name, but it does come up as a 'Typhoon Easy Cam' under aMSN.

I ran luvcview in the terminal and it gave the following results:

luvcview version 0.2.1
Video driver: x11
A window manager is available
video /dev/video0
Error opening device /dev/video0: unable to query device.
 Init v4L2 failed !! exit fatal

I would really appreciate if anyone could help to remedy the output. 

TWO

All the stuff about the root cause being the lack of linux support from webcam manufacturers being accepted, this expresses my feelings exactly. I've never had this level of problem with a peripheral device before, and it's very much at variance with promotional message Ubuntu carries these days. The danger is that too much of this sort of thing will undermine confidence in the whole linux project.

I also wish I could 'help to remedy the outptut', and this is another problem. We've got all these bits of software associated with webcams, issuing error messages that nobody appears to know what to do with. Now that is surely something the Ubuntu team could do something about.

I don't care whether my windows wobbly or not, but I think a working webcam is a reasonable expectation of any desktop operating system.

Roger D

---

### Post by TWO on 2008-05-19
> **Roger D said:**
> 
I don't care whether my windows wobbly or not, but I think a working webcam is a reasonable expectation of any desktop operating system.

Roger D

I couldn't agree more. The sad thing as well is that aesthetically pleasing things like that don't even function correctly universally! 

> The danger is that too much of this sort of thing will undermine confidence in the whole linux project.


I can't help but think that either. Problems like these are the reason why people are turned off. I don't like when I hear a long time Linux user chastising a short-term user for complaining. The promise of a system that is more stable than anything and then what we find is a lot of incompatibilities and inconsistencies. I repeat, I am so grateful that people across the world have dedicated their time to creating the very system that we are using now, but I think it has to be realised that Linux is entering into a new world where the mainstream is getting interested and expecting results. 

I am definitely not your "typical" Linux user but I am more willing than the stereotypical average user to play with settings. But there does come a point where the amount of things you have to do to get things to work becomes silly. 

(Completely deviating from the topic here) but I would be totally content if the developers turned around and pledged to resolve problems like this before releasing the new version. Ubuntu should possess enough weight now to be able to encourage manufacturers to release drivers.

---

### Post by Roger D on 2008-05-19
Thanks, it's nice to feel I'm not alone, or being completely unreasonable.

Digging around, it's hard not to, I've just found the most amazing blog devoted to getting a supported webcam, like the Pro 9000, to generate a video file for uploading to Utube. You can only admire the tenacity of the guy who did this, but I also think it proves my point. It shouldn't be this difficult.

It's well worth a look:

[http://www.buberel.org/serendipity/index.php?/archives/260-Using-a-USB-Webcam-on-Ubuntu-Linux-to-produce-good-quality-video-captures-that-can-be-uploaded-to-YouTube-directly.html](http://www.buberel.org/serendipity/index.php?/archives/260-Using-a-USB-Webcam-on-Ubuntu-Linux-to-produce-good-quality-video-captures-that-can-be-uploaded-to-YouTube-directly.html)

At least it convinced me my system had recognised my webcam.

Roger D

---

### Post by HotShotDJ on 2008-05-19
> **TWO said:**
> but I would be totally content if the developers turned around and pledged to resolve problems like this before releasing the new version. Ubuntu should possess enough weight now to be able to encourage manufacturers to release drivers.What, exactly, would you have the developers do?  They have approached hardware vendors. They have made public appeals for the technical specifications from hardware vendors.  They have offered to sign NDA's with hardware vendors.  They have offered to develop the drivers at NO COST to the hardware vendors.  If ONLY those vendors will PLEASE tell them what the technical specifications ARE.  Some vendors have be very cooperative. Others have been completely uncooperative.  And some have been down-right hostile.

Developers have put YEARS of work and research into reverse-engineering drivers for a huge array of devices that would otherwise not work at all.  Then, by the time they get a device reasonably working, the vendors change the hardware and the work has to start all over again.  This problem could be ELIMINATED if only the hardware vendors would release the specifications, even under an NDA as offered by the Linux kernel developers.

I think somebody in this thread felt that they were being chastised for being frustrated with some of the hardware issues.  Please, I understand the frustration.  I was using Linux back when just getting a printer working was a chore.  So, yes, I know how you feel.  But the developers are doing everything they can to get these devices working under Linux.  In fact, their efforts have often been heroic in the face of out-right hostility from the hardware manufacturers.

---

### Post by Roger D on 2008-05-19
Maybe we/me are getting a bit hung-up on the drivers issue. I don't pretend to understand the details, but the Pro 9000 is uvc compliant, and these drivers come with Ubuntu Hardy - do they not? So it ought to work, even if it can't do all the things you can do with Windows.

Could it be that my very slow image problems with Cheese and the video test in gstreamer-properties, which  generates a very large image, is because my CPU is a  bit on the slow side? It's a Athlon 64 3000. That said, I didn't have any problems with Windows XP and an Athlon 2200.

Roger D

---

### Post by TWO on 2008-05-20
> **HotShotDJ said:**
> 
Developers have put YEARS of work and research into reverse-engineering drivers for a huge array of devices that would otherwise not work at all.  Then, by the time they get a device reasonably working, the vendors change the hardware and the work has to start all over again.  This problem could be ELIMINATED if only the hardware vendors would release the specifications, even under an NDA as offered by the Linux kernel developers.


I couldn't even begin to think of a way to get around that! That's blatant stifling of the competition. It all kind of goes over our heads though, that this is the reason why. 

> 
[http://www.buberel.org/serendipity/i...-directly.html](http://www.buberel.org/serendipity/i...-directly.html)

At least it convinced me my system had recognised my webcam.

I'll give that a try and see what it can do. Did it improve your web cam video?

---

### Post by Roger D on 2008-05-20
> **TWO said:**
> 

I'll give that a try and see what it can do. Did it improve your web cam video?

No it didn't. But thinking things over, I'm more and more convinced that, for my webcam at least, drivers are not the issue. I've long appreciated the importance of drivers, and have made a point of always buying peripherals where manufacturers do offer support for Linux. So, I've an HP printer and an Edimax wireless usb stick (where I know working drivers are built into 8,04). By going for a uvc-compatible webcam I was simply following my normal practice, and thought I wouldn't have any significant problems.

I've had a look at the easycam page [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam), but the results are really discouraging. It starts off by suggesting I try camorama and xawtv. With camorama I get the message: Could not connect to video device (/dev/video0) please check connection, and xawtv gives me:

roger@roger-desktop-new:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-16-generic)
xinerama 0: 1440x900+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
ioctl: VIDIOC_QUERYMENU(id=134217738;index=0;name="60 Hz";reserved=3080667488): Invalid argument
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0xb6ce1dd0b7d1b450 [PAL_I,PAL_D1,PAL_Nc,NTSC_M,NTSC_M_JP,?,SECAM_B,SECAM_K,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
Segmentation fault
roger@roger-desktop-new:~$ 

Also, a small screen opens briefly and then closes.

Again, none of this means much to me, but I can't help feeling that there is something wrong with the way webcam support is implemented in Hardy that has little or nothing to do with drivers

---

### Post by Roger D on 2008-05-25
Well, I've finally given up with trying to get Cheese to work, but I'm having real success with guvcview. Worth checking out at:

[http://developer.berlios.de/project/showfiles.php?group_id=8179&release_id=14666](http://developer.berlios.de/project/showfiles.php?group_id=8179&release_id=14666)

It's true - drivers are not the issue.

---

### Post by perce on 2008-05-25
You're not alone: I have two webcams which have apparently the same chipset, one works and the other doesn't.

This said, have you tried to open the multimedia system selector (under system > preferences) and change from v4l to v4l2 or vice versa? It's a cheap advise, I know, but some webcams work with one but not with the other.

---

### Post by Roger D on 2008-05-26
Always nice to know you're not alone.

Yes, I've tried the v4l to v4l2 switch, using gstreamer-properties, and it doesn't seem to make any difference. Didn't know I could do this via System>Preferences. Where do I go after Preferences?

 As far as I can tell, the Pro 9000 should work fine with Linux, it's uvc compatible, so drivers shouldn't be an issue. If you look at my last message, you'll see I'm making real progress with guvcview. Not sure what's wrong on the Cheese front, maybe my PC is a bit underpowered in the graphics department.

---

### Post by TWO on 2008-05-26
> **Roger D said:**
> Always nice to know you're not alone.

Yes, I've tried the v4l to v4l2 switch, using gstreamer-properties, and it doesn't seem to make any difference. Didn't know I could do this via System>Preferences. Where do I go after Preferences?


I think you have to right click and edit the System menu to get 'Multimedia System Selector' to appear.

I'll have to give guvcview a try.

Seems it's giving me more joy under Ubuntu. (Which makes no sense, since Kubuntu is the same thing!)
I have a picture now, only problem is it is displaying in every other colour but the colour that is actually real!

*SIGHS*

---

### Post by Roger D on 2008-05-26
Thanks for the hint about Multimedea System Selector, which I've now added to preferences. Sorry you're having colour problems. Is you webcam uvc compatible?

---

### Post by joshedmonds on 2008-05-26
You both get my thanks for the great conversation - this is Ubuntu (well it should be all Linux, but still)

I wish I could help but I don't even have a webcam!

---

### Post by TWO on 2008-08-14
Success! Finally!

Having given away the webcam which really wasn't working for me on Ubuntu, I've picked up one which I bought a few years back and to my surprise it worked as soon as I plugged it in!

The colour is fine and when I adjust settings under Camorama, it gives me no problems at all!

The camera is a Phillips PCVC730K webcam.

Just when I was about to give up on webcams on Ubuntu, it really does seem that there is some light at the end of the tunnel!

This was quite lucky! 
 
Nice to know that there is the chance for things to work! 

(Completely unrelated story but: I saw the advantage of Ubuntu over XP the other day, where when plugging in a mobile phone to the desktop I have, it took XP about 10 different downloads before I access the phone, whilst with Ubuntu, I simply plugged it in and was able to access it without a problem. Good to see some advantages at least!)

---

### Post by cariboo on 2008-08-14
I hope every one that has had problems with getting web cams to work, has sent an email of the repective manfacturers expressing their disappointment in the lack of proper drivers for their web cam. I have a Logitech Quickcam Messenger and there was a link on logitech's driver page to a 3rd party open source driver that worked right away for me, but I know people with other models are not so lucky. 

If we all contact manufacturers of devices that don't work under linux, eventually they are going to get the message that there are more of us out here than they think.

Jim

---

### Post by nickgaydos on 2008-08-14
I have an Xbox Live Vision cam and when I use the steps from  a website, it either works or gets me a 404 error (not found). One time it brought me to the gOS website :-O

---

### Post by richg on 2008-08-18
I found this thread while looking for a web cam to use with Ubuntu 8.04.
Right now I have a EEE 4G PC with built in web cam that works quite nicely. The application used is ucview.real 0.14, an easy to use video capture application. Copyright is 2007, Arne Caspian.
[http://www.unicap-imaging.com](http://www.unicap-imaging.com)
A short video I made comes up in My Videos as Video_0000.ogg.vtmp.
There is an option for an external web cam. I will check the Asus EEE PC forums and see what others have done. The 4G runs the Xandros OS. I keep the defaults as I am not much of a software type. This PC is my choice for traveling.

Since Asus has been able to do this, I would think Ubuntu could do the same.
Probably not high on their priority list.

Rich

---

