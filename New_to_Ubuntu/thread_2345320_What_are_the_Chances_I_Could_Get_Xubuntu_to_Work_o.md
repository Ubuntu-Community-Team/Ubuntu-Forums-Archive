---
title: "What are the Chances I Could Get Xubuntu to Work on My Computer?"
date: 2016-12-02
forum: New to Ubuntu
---

### Post by happydog500 on 2016-12-02
I started using Linux off and on back in 1993. I got away from it, but came back full time about a year a go. In Mint 17.3, my dual monitors (Computer Monitor and HDTV across the room) only shows up on the TV. I had to unhook the TV, boot up and hook it back in. I could then go in and set the monitor to default.

 In Mint 18, I'd boot up to two blank monitors. I could unhook the TV, then boot up and plug it back in. When rebooted, I'd get two blank screens. Tried since it came out to get it fixed, but "no way no how." xrandr works, but not after re-booting. 

Still not sure why it will work, but after re-booting, not work. I don't like the direction Mint is going in, and the community is backwards. I would like to get behind a distro and support it all I can. 

 I'm using onboad  Radeon HD 6410D. When I look that  up, mine is listed as "fully supported" for the AMDGUP drivers.

  Out of 15 distros, none will work with dual monitors except Mint 17.3. What are the chances we could get Xubuntu to work with my dual monitors? 

 Thank you, 
 Chris.

---

### Post by QIII on 2016-12-02
Hello!

Where are you seeing that it is fully supported by AMDGPU? 

It is fully supported by the Radeon driver and by fglrx in Ubuntu up to 14.04.1.

Xubuntu will likely work very well with the Radeon driver, so you should be able to run any release.

---

### Post by happydog500 on 2016-12-03
Xubuntu doesn't work past 14.04. It was the AMDGPU Driver that my video was "fully supported." Tried to look for it again, but kept getting phone calls and the game was on. Will look for it again. fglrx works but not past 14.04 because of xorg 1.8. 

 Chris.

---

### Post by QIII on 2016-12-03
Notice that I said it is fully supported by the* Radeon *driver.  Your GPU is not supported by the AMDGPU driver in any case.  It is supported by the Radeon driver under any release.  It is supported by fglrx up to 14.04.1.

You can find my compiled list of GPUs currently supported by AMDGPU [here]("http://theleftcoastgeek.net/index.php/categories/11-amd-gpu-support-with-amdgpu-and-amdgpu-pro"), and my compiled list of GCN hardware that might possibly eventually be supported [here]("http://theleftcoastgeek.net/index.php/categories/12-possible-amdgpu-pro-supported-gpus-by-the-end").

---

### Post by happydog500 on 2016-12-03
Although I found mine is "fully supported" for xubuntu,  did a quick ubuntu search and found it doesn't work. Looking farther, I found this, just as I posted and was criticized for. (notice what AMD's reputation is towards Linux, and what "People might just....")
> With the release of Ubuntu 16.04, ......

Firstly, it's just not compatible. You won't find fglrx in 16.04 repositories, nor will you find a version for 16.04 online. If you download the latest version from AMD's website and install it, you'll run into Low Graphics Mode, **blank screens**, and other nasty stuff you don't want to happen.

You might be hoping that AMD will step in to update the driver, but then **you must not know AMD's reputation for ditching support for even slightly older cards on Linux**. **Since AMD doesn't want to update the driver, Canonical could make one for Ubuntu, except it won't**.

There's always the possibility that AMD will release another widely compatible graphics driver **or that people might just move away from AMD on Linux.** 

 I knew of a big problems with AMD and Linux, but wanted to see if someone at Ubuntu community, had a way to get thousands of people who can't use Linux, able to use it. 

 Is the answer to What are the chances I could get xubunut 16 to work on my computer, "no way no how?" 

 Thank you for the help,
  Chris.

P.S. Just found out that ubuntu 14.04 now comes with xorg 1.18, which makes fglrx not work.

---

### Post by deadflowr on 2016-12-04
> P.S. Just found out that ubuntu 14.04 now comes with xorg 1.18, which makes fglrx not work.
Grab the 14.04.1 image from here:
[http://old-releases.ubuntu.com/releases/14.04.2/]("http://old-releases.ubuntu.com/releases/14.04.2/")
you need to scroll down till you get to the correct iso:
either
> ubuntu-14.04.1-desktop-i386.iso              22-Jul-2014 22:38  1.0G  Desktop image for 32-bit PC (i386) computers (standard download)
for 32-bit
or
> ubuntu-14.04.1-desktop-amd64.iso             22-Jul-2014 22:36  1.0G  Desktop image for 64-bit PC (AMD64) computers (standard download)
for 64-bit
these contain the older X stack (and the original 3.13 kernel series that came with 14.04)
they will not upgrade to the newer stacks unless you do that manually, yourself.
the amd driver will install and work with these.

Edit: Forgot to mention that these stacks (the X stack and the kernel 3.13) are fully supported for the entire duration of 14.04's release.
So no worries about them being out-of-date or unsupported.

---

### Post by QIII on 2016-12-04
I will say this one more time:

Your card is fully supported by the *open source Radeon Driver*.  fglrx will not work beyond 14.04.1.  Your card is not supported by AMDGPU.

The AskUbuntu post you quoted?  Obviously the author was not aware of the full story and was under the same "the sky is falling" misconceptions as everyone else.  The author came to an incorrect assumption:  that the demise of fglrx meant AMD was no longer going to support it's products in Linux.

So, misconceptions aside, what this means for you:

Radeon -- Yes
fglrx -- No
AMDGPU -- No

For the "thousands who can't use Linux":  Radeon.  Will they be able to game with it?  No.  That much is true.

Where did you find you can't run Xubuntu with your card?

The reputation you speak of is hoisted and carried along by continued repetition of internet legend that has existed for years -- from a time before AMD bought ATI 8 years ago and when ATI support was, indeed, atrocious.  If you find a thousand complaints about AMD on the web, it is easy to conclude that the reputation is correct.  Is that 1,000 of 1,001 users?  1000 of 10,000 users?  1,000 out of 1,000,000 users?  There is an inherent "referral bias" in using such information to draw a conclusion:  People do not take to the web in droves to complain about things that are working.

The answer to your question is this:
[B][I]
If you install Xubuntu 16.04 or later, the installer will see that you have an AMD GPU, check if it is supported by AMDGPU, find that it isn't and install the open source Radeon driver to make it work.  [/I][/B]

You are getting wrapped around the axle assuming that if it won't use AMDGPU and you can't install fglrx then your graphics card won't work.  That assumption is incorrect.  The open source Radeon driver, which AMD has worked hand in hand with the open source community to make better and better over the last few years (primarily Canonical, by the way), fully supports your GPU.

I am not a fanboy.  AMD continually makes me angry.  AMD makes atrocious business decisions.  AMD frequently makes great leaps forward in technology only to think they "have it made" and remain blissfully ignorant when everyone else catches up and passes them by.  But I do try to operate on fact rather than myth.

The cards for which fglrx support was dropped?  Still supported by the open source Radeon driver.  The ones that aren't supported by AMDGPU?  Radeon.  Remember, the Radeon driver is developed by the open source community with AMD's help.

If you don't want to use AMD products, don't.  You'll be in good company.  But there is no need to perpetuate myth.

---

### Post by happydog500 on 2016-12-04
Thank you.

  Went to download xubuntu 14.04.2. With a fiber Gig download, says it will take 5 hours. I downloaded it from a torrent from the xubunut website and got > "Tracker gave an error. Requested download is not authorized for use with this tracker" as it was downloading.

 Hope that's not a problem.

 Chris.

---

### Post by QIII on 2016-12-04
What you want is 14.04.1 or earlier, actually.

---

### Post by happydog500 on 2016-12-04
> **QIII said:**
> I will say this one more time:

Your card is fully supported by the *open source Radeon Driver*.  fglrx will not work beyond 14.04.1.  Your card is not supported by AMDGPU.

So:

Radeon -- Yes
fglrx -- No
AMDGPU -- No

For the "thousands who can't use Linux":  Radeon.  Will they be able to game with it?  No.  That much is true.

Where did you find you can't run Xubuntu with your card?

The reputation you speak of is hoisted and carried along by continued repetition of internet legend that has existed for years -- from a time before AMD bought ATI 8 years ago and when ATI support was, indeed, atrocious.  If you find a thousand complaints about AMD on the web, it is easy to conclude that the reputation is correct.  Is that 1,000 of 1,001 users?  1000 of 10,000 users?  1,000 out of 1,000,000 users?  There is an inherent "referral bias" in using such information to draw a conclusion:  People do not take to the web in droves to complain about things that are working.

The answer to your question is this:
[B][I]
If you install Xubuntu 16.04 or later, the installer will see that you have an AMD GPU, check if it is supported by AMDGPU, find that it isn't and install the open source Radeon driver to make it work.  [/I][/B]

You are getting wrapped around the axle assuming that if it won't use AMDGPU and you can't install fglrx then your graphics card won't work.  That assumption is incorrect.  The open source Radeon driver, which AMD has worked hand in hand with the open source community to make better and better over the last few years (primarily Canonical, by the way), fully supports your GPU.

I am not a fanboy.  AMD continually makes me angry.  AMD makes atrocious business decisions.  AMD frequently makes great leaps forward in technology only to think they "have it made" and remain blissfully ignorant when everyone else catches up and passes them by.  But I do try to operate on fact rather than myth.

The cards for which fglrx support was dropped?  Still supported by the open source Radeon driver.  The ones that aren't supported by AMDGPU?  Radeon.  Remember, the Radeon driver is developed by the open source community with AMD's help.

If you don't want to use AMD products, don't.  You'll be in good company.  But there is no need to perpetuate myth.

Very, very good writing (or should I say typing). Thank you very much for this information. I was referring to people who have tried the Radeon driver and it did not work. 

 Ubuntu 16 doesn't work on my computer either.   

 Thank you for the understanding on the AMD driver. All those people who can't use Linux, ask and never get that theoretically, the Radeon driver is supposed to work. 

 Chris.

---

### Post by QIII on 2016-12-04
If 16.04 is not working with the Radeon driver, then you should start a support request here asking for help.

Unity may be too heavy for it, that is true.  But it should work.

Xubuntu should work.

If you are having problems, ask for help.

---

### Post by happydog500 on 2016-12-04
OK, I'll do that. Again, I'm not using Ubuntu right now. If I do, I get blank screens and that makes it hard to work on. I will try again. I downloaded Xubuntu 16 and will install tomorrow. 
 Thank you very much for the support. It has been the best so far.
 Chris. 

 Chris.

---

### Post by aaronfranke on 2016-12-04
What kind of 3D support can we expect from the radeon driver? Does it depend on the specific chip?

---

### Post by kurt18947 on 2016-12-04
> **aaronfranke said:**
> What kind of 3D support can we expect from the radeon driver? Does it depend on the specific chip?

Is this of any help?

[https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)

---

### Post by happydog500 on 2016-12-04
Just a quick note before I have to go. Will install Xubuntu this afternoon or evening. 

 Any Linux Distro, including, Mint, Debian, Ubuntu, any alternate Ubuntus, openSUSE, Elementary, Manjaro, Fedora, Slaix, Slackel, LXLE, Puppy, ROSA, and several more, all start on my TV (VGA), and none on my Monitor (DVI). The only one that works is Windows, All versions. 

 What makes Linux favor VGA over DVI? Not one Linux will start on the monitor, only the TV. 

 Thank you,
 Chris.

---

### Post by happydog500 on 2016-12-04
Got home and installed. Not sure if it's a disaster. After rebooting a few times to check, each time, no signal to the TV at all. Computer monitor boots up blue, but no icons or panel. If I wait, noting appears. If I move the mouse, the screen flickers once, jumps and the panel and icons show up. 

 Just after boot, I get some kind of error that wants to send to ubuntu because of a internal problem. Sure doesn't feel very stable. One thing that is good, if I leave out that I can't watch videos on my TV, I'm typing on xbunutu, which booted up on the computer monitor. That is a step in the right direction and even tho the flicker and jerks, having to move the mouse to get icons an panel, I'm posting this from my computer!

 Chris.

---

### Post by happydog500 on 2016-12-07
Posted an update in the wrong forum. Xubuntu now works on both monitors!! I could not believe after 15 distros, xubuntu's running on both monitors!!! Nice!

For the last couple days, running real nice. Sad to say, came home tonight to watch a movie, it only works on one monitor now. Can't believe Linux wrecked another movie night. I'll have to reboot into Windows to watch a video. 


 Chris.

---

### Post by happydog500 on 2016-12-08
I know this is not the thread to ask, just wanted to give an update to the question. When I boot up, the Volume icon at the top is white. When I start a video, the icon turns red and the sound quits. Kind of surprised, I thought Ubuntu was farther along then it is. 

 I posted the question about video last night but haven't got a response yet. I think in this thread, someone suggested that I start a support request. I did a couple months a go but got no response. I got a message that after 45 days without a response, my question got deleted. 

 Chris.

---

### Post by happydog500 on 2016-12-10
> **QIII said:**
> What you want is 14.04.1 or earlier, actually.

 Thank you for letting me know. Are you sure 14.04.1 is the latest? Guess the answer to the question is no, can't get xubuntu to work on my computer. Will try, very disappointedly the older version. If it's as much unstable and video not working, I may have to skip Linux again. 

 Wish AMD would work better with Linux. I'll never get another AMD video again. Download says in red, "not authorized to download for use with this tracker." Can't even download an iso of *ubuntu 14.04.1. 

 Chris.

---

### Post by wildmanne39 on 2016-12-10
>  Wish AMD would work better with Linux. I'll never get another AMD video again. 
This is not the case they work very closely with ubuntu to get this working but there were changes recently that caused the issue and they are working to resolve the issue, I just bought one myself and the driver worked great but there is an issue where it causes a blank screen, so yes t is a work in progress.

I hope to get ubuntu installed tomorrow in my new laptop and I will be very aggressive in finding the solution.

---

### Post by happydog500 on 2016-12-10
Tried Xubuntu 14.04.1.  No go. This one had 800x600 and a blank TV screen. I did xrandr and the desktop set up right, but still no TV. This is better because they all have started blank on the computer, at least Ubuntu is on the computer but no on the TV. 

 Chris.

---

### Post by happydog500 on 2016-12-12
> **wildmanne39 said:**
> This is not the case they work very closely with ubuntu to get this working but there were changes recently that caused the issue and they are working to resolve the issue, I just bought one myself and the driver worked great but there is an issue where it causes a blank screen, so yes t is a work in progress.

I hope to get ubuntu installed tomorrow in my new laptop and I will be very aggressive in finding the solution.

 This is very nice that you will help. Thank you for any work that you do. Can't believe this. I got 14.04.1 working on both monitors. Just when you think everythings OK, the screens go blank after 10 minutes. It's just a setting, but it's a known problem and settings don't work. In other distros, "Power Management" settings is where it's fixed. Xubuntu doesn't do anything if you change it to 'never' or disable it altogether. 

After looking around, there is *more* screen settings (how many different screen settings are in different places?) called, "light lock". Made adjustment and will see if that fixes it.  

Looks like it got fixed in Ubuntu 15. They went away from xscreensaver.  

  If you do any work, to give you any input, the open source driver works in 14.03, but the open source doesn't work in 16. Now, flgrx works noticeably better then the open-source, but the open source does in fact work in 14. 

Wanted to make sure it was noted that it's not the open source driver doesn't work, and flgrx does. It's open source does work in 14, not in 16. 

Thank you,
 Chris.

---

### Post by happydog500 on 2016-12-20
> **wildmanne39 said:**
> I hope to get ubuntu installed tomorrow in my new laptop and I will be very aggressive in finding the solution.

Just tried two more ubuntu flavors and get worse and worse outcomes. Have you aggressively found any solutions? 

 Thank you,
 Chris.

---

### Post by wildmanne39 on 2016-12-23
Hello, using kernel 4.9 with xorg.server 1.19 is supposed to fix the issue but I have not figured out how to install the 1.19 xorg.server.

---

### Post by happydog500 on 2016-12-31
I could not get mine to work. I gave up on the Ubuntu community. I had to switch to another distro to use Linux. 


 Chris.

---

### Post by vasa1 on 2017-01-01
> **happydog500 said:**
> I could not get mine to work. I gave up on the Ubuntu community. I had to switch to another distro to use Linux. 


 Chris.

Okay. All the best with whichever distro or operating system you move to!

---

