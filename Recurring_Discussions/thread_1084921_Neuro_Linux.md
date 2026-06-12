---
title: "Neuro Linux"
date: 2009-02-20
forum: Recurring Discussions
---

### Post by pedja_portugalac on 2009-02-20
> **hifly1231 said:**
> Is anyone using Nero Linux 3.5.2.3 in Ubuntu 8.10?  If so, is it working?  If it is, could someone help me figure out how to burn CD's in it?  I can't seem to figure it out.  Thanks!!!

Why would you use nero-linux when you have all you need in Ubuntu (out of the box)? Use Brasero, it's great and free.
PS: Using proprietary software, such as nero, you can harm your dear OS!!!

---

### Post by kelvin spratt on 2009-02-20
Nero will not harm your OS, its totally self contained and it is totally accurate in what it writes. Yes it does cost money but if you want consistency then its the best available option.

---

### Post by theozzlives on 2009-02-20
I've used Nero since my Windows days, just used to it.

---

### Post by Doug11 on 2009-02-20
I tried nero for linux as well and ended up switching back to K3B,,i find its about the easiest with most options. Quite user friendly. But I guess thats what it's all about. Finding what suits you best.

---

### Post by pedja_portugalac on 2009-02-20
> **kelvin spratt said:**
> Nero will not harm your OS, its totally self contained and it is totally accurate in what it writes. Yes it does cost money but if you want consistency then its the best available option.
I disagree with you. When I start to use Ubuntu, Brasero wasn't there out of the box and I didn't want to mix KDE and GNOME applications. So I tried nero, the application I was using when I was on XP (I never pay applications - not even XP OS). What happened was many freezes along with many fu..ed CDs and DVDs and of course security holes it leaved so I reinstalled brand new Ubuntu without it and I used command line utilities for all kind of jobs. But now with Brasero you have authentic nero burning room for linux out of the box. Someone say here, how to burn an .iso image, with Brasero just double click on it (.iso) and Brasero open right project. Nothing more then that. The only thing nero-linux can do Brasero for the moment can't is burning BD discs (blue ray) but then again I think it's very bugy. That said, if you want to f.ck with nero, use stolen serials or drop some money for nothing do it, it's your right...

---

### Post by TransitMan on 2009-02-21
Pay no attention to the poster pedja_portugalac for he/she does not know what they speak of.
Nero for Linux will not have any security holes in it.
As for burning an .iso, you need to open Nero, go to Recorder, then choose Burn Image.
Also, across the top is a drop down list with either Image Recorder or your CD and/or DVD burner listed. Make sure you have your burner in the window before trying to burn a .iso or any file for that matter.

As for the rest of you, I have tried to help the original OP with his burner problems with K3b, Brasero and a couple of other Ubuntu burners, all of which failed for him. So to tell him to use those, especially when he has stated here that none of them work is a wasted effort, unless you have a working solution for him to get them running correctly.

---

### Post by pedja_portugalac on 2009-02-21
> **hifly1231 said:**
> OK, I'm working with a fresh install of Ubuntu 8.10, and I can't get ANY of the CD burning utilities to work, not even the built-in.  How did you get Brasero to work in Ubuntu 8.10? 
First of all insert one blank CD or DVD in your optical drive (burner) in your case for windows_XP.iso it's a blank CD you'll need. After few seconds Nautilus (window manager) will ask you to choose what application to launch. Instead of the default "Open CD/DVD Creator" in drop down tab choose "Open Brasero Disc Burner". Ones it's done you'll see Brasero window called "New Data Disc Project". In the middle box, under Name, choose the path to your .iso image and double click on it. It will now appear in the box on right side. Now click Burn in the lower right corner and follow the dialogue till the end of burning. Another way to burn with Brasero is to close nautilus dialogue after the blank CD has been inserted and under Applications > Sound & Video manually open Brasero Disc Burning application. After the main window opening choose Burn Image tab and then find the Path to the .iso image you have on your computer (HDD) and you want to burn onto CD or DVD. Click Burn and follow the dialogue. There's other ways to burn CDs/DVDs but for now this two methods are enough.    
> I'm also not understanding how Nero Linux 3.5.2.3 debian package is going to leave a security hole in my Ubuntu.(?)
It can be in many ways. Opening backports on your system, buffer overflow etc, etc.

> **TransitMan said:**
> Pay no attention to the poster pedja_portugalac for he/she does not know what they speak of.

and you know?

---

### Post by TransitMan on 2009-02-21
> **pedja_portugalac said:**
> It can be in many ways. Opening backports on your system, buffer overflow etc, etc. ...and you know?

It has never been proved that Nero for Linux opens any ports, interferes with the operating system in any way detrimental, nor causes harm to the system.
However, if you are stupid enough to run as ROOT using any and all programs, then you are opening yourself to all types of problems, especially the ones you describe.
Nero does not run as ROOT, therefore only has privligies to do what the user wants it to do.
Lastly, sometimes a program like Nero can solve a problem that Linux can't at the time, due to bugs in the OS, which has been documented. This is why there is a variety of FREE and PAID or PROPRIETARY programs for Linux. In the end it comes down to what the individual user wants to use.

If you think otherwise, put forth your system findings with all ports opened by Nero.

---

### Post by handy on 2009-02-21
> **pedja_portugalac said:**
> Why would you use nero-linux when you have all you need in Ubuntu (out of the box)? Use Brasero, it's great and free.
PS: Using proprietary software, such as nero, you can harm your dear OS!!!

For some of us, NeroLinux is the most reliable solution on the hardware we use.

I have been using NeroLinux since an early version 2.* & I have nothing but praise for it, as it has never done a thing wrong, on any distro I have used it with.

Full marks to NeroLinux & thankfully they sell it cheap as well. :-D

---

### Post by alexandari on 2009-02-22
Nero linux? are you joking me? there`s nothing better than k3b...

---

### Post by hifly1231 on 2009-02-24
> **TransitMan said:**
> Pay no attention to the poster pedja_portugalac for he/she does not know what they speak of.
Nero for Linux will not have any security holes in it.
As for burning an .iso, you need to open Nero, go to Recorder, then choose Burn Image.
Also, across the top is a drop down list with either Image Recorder or your CD and/or DVD burner listed. Make sure you have your burner in the window before trying to burn a .iso or any file for that matter.

As for the rest of you, I have tried to help the original OP with his burner problems with K3b, Brasero and a couple of other Ubuntu burners, all of which failed for him. So to tell him to use those, especially when he has stated here that none of them work is a wasted effort, unless you have a working solution for him to get them running correctly.

I'm not paying attention.  He's still trying to tell me to use Brasero after I've stated that **it's not working**.

I'll try to follow your instructions exactly, and let you know what my results are.  Nero Linux 3 is working fine.  I just don't know exactly what to do to burn an .iso yet.  Thanks for your help!!!

---

### Post by TransitMan on 2009-02-25
You know how to get ahold of me if you don't want to do the thread, for sake of others flaming or not reading correctly.

---

### Post by anewguy on 2009-02-25
The best approach here, and believe me - not me, would be for you to go with a single responder to this thread, try everything they tell you, then if it doesn't work, post back (as you have been TRYING to) stating you have problems with that and now want to just do "x".  You have been asking a pretty specific question - not IF you should use Nero for Linux, but instead HOW to use it.  I'm sorry that your experience with this thread has broken down to a contest of "who's is bigger", rather than realizing there is a large world of hardware out there (some CD and DVD drives I could ONLY get to work even in Windows with NERO - so it may be a similar situation here.  The train of thought of the thread has been lost.  Follow the previous poster's advice that said to contact him outside of the thread - let him/her help you as much as they can.  If you exhaust that source and still have problems, then open a new thread.  Forget the "should use this or should use that" stuff - not for anything bad, mind you - they are all very valid suggestion especially in the open source world on Linux - but instead for not realizing you are just asking for help on 1 product.

Again, I apologize (I'm not a moderator or anything like that - it's just I've seen this "p***ing contest" break out on some of my early threads when all I wanted was an answer, not an open debate.

As I said, please do not hold any of this against the other responders in your thread - everyone has good intentions, and I would never condemn them for trying to help.  I just think it's best for you to work "off-forum" with the person that offered and then after doing everything they ask if things still don't work - post back again.  It will eliminate some frustration for you for now.

Best of luck!
Dave ;)

---

### Post by hifly1231 on 2009-02-25
> **anewguy said:**
> The best approach here, and believe me - not me, would be for you to go with a single responder to this thread, try everything they tell you, then if it doesn't work, post back (as you have been TRYING to) stating you have problems with that and now want to just do "x".  You have been asking a pretty specific question - not IF you should use Nero for Linux, but instead HOW to use it.  I'm sorry that your experience with this thread has broken down to a contest of "who's is bigger", rather than realizing there is a large world of hardware out there (some CD and DVD drives I could ONLY get to work even in Windows with NERO - so it may be a similar situation here.  The train of thought of the thread has been lost.  Follow the previous poster's advice that said to contact him outside of the thread - let him/her help you as much as they can.  If you exhaust that source and still have problems, then open a new thread.  Forget the "should use this or should use that" stuff - not for anything bad, mind you - they are all very valid suggestion especially in the open source world on Linux - but instead for not realizing you are just asking for help on 1 product.

Again, I apologize (I'm not a moderator or anything like that - it's just I've seen this "p***ing contest" break out on some of my early threads when all I wanted was an answer, not an open debate.

As I said, please do not hold any of this against the other responders in your thread - everyone has good intentions, and I would never condemn them for trying to help.  I just think it's best for you to work "off-forum" with the person that offered and then after doing everything they ask if things still don't work - post back again.  It will eliminate some frustration for you for now.

Best of luck!
Dave ;)

Thank you for your thoughts and advise.  I think that you are **ABSOLUTELY** right.  Please believe me when I say that I _**wouldn't**_ be using Nero Linux 3 if the built-in CD burner or **_ANY_** of the CD burners in my repository were working correctly.  My policy is to never go outside my Intrepid Ibex for **ANYTHING** unless I **_absolutely_** _**have**_ **_to_**.  That's what makes Linux so much better than Windoze...you don't have to cruise the Internet looking for software...it's right here at your fingertips!!!  In fact, Nero Linux 3 is the **ONLY** thing I have installed on my computer that didn't come from the repository.  I love Ubuntu Forum.  I've only been using Linux for a few months, and have gotten the answer to every single question I've had so far on here.  I do appreciate everyone's input, but I also understand that as with all forums, it's easy for everyone to get off track because of different opinions.  I'll take TransitMan up on his offer.  I'm positive that he can help me.

---

### Post by stchman on 2009-02-27
> **hifly1231 said:**
> Question answered thanks to TransitMan.

What was the problem just so the other forum members can benefit from the knowledge you gained?

---

### Post by hifly1231 on 2009-02-27
> **stchman said:**
> What was the problem just so the other forum members can benefit from the knowledge you gained?

Read the thread.

---

### Post by crjackson on 2009-02-27
> **kelvin spratt said:**
> nero will not harm your os, its totally self contained and it is totally accurate in what it writes. Yes it does cost money but if you want consistency then its the best available option.

+1

---

### Post by crjackson on 2009-02-27
> **hifly1231 said:**
> I'm not paying attention.  He's still trying to tell me to use Brasero after I've stated that **it's not working**.

I'll try to follow your instructions exactly, and let you know what my results are.  Nero Linux 3 is working fine.  I just don't know exactly what to do to burn an .iso yet.  Thanks for your help!!!

Look - There is a LOT of BS and Crap in this thread. YES - Ibex has burning issues out of the box on SOME hardware. Including some of my many systems.

NERO - **_NEVER!_**fails for me on those machines that won't burn optical media otherwise.

NERO does NOT have anything to do with "Backports" etc...  That's just misinformation.

If you have Nero installed, right click on your .iso file and from the context menu> Open with NERO.  Once open click the flame image on the nero toolbar.

---

### Post by hifly1231 on 2009-02-28
> **crjackson said:**
> Look - There is a LOT of BS and Crap in this thread. YES - Ibex has burning issues out of the box on SOME hardware. Including some of my many systems.

NERO - **_NEVER!_**fails for me on those machines that won't burn optical media otherwise.

NERO does NOT have anything to do with "Backports" etc...  That's just misinformation.

If you have Nero installed, right click on your .iso file and from the context menu> Open with NERO.  Once open click the flame image on the nero toolbar.

I'm glad someone else **_FINALLY_** acknowledged the burning issues in **Ubuntu**!!!  crjackson, I tried **_EVERYTHING_** possible with the built in Gnome Nautilus burner, and every single burner in the repository before I broke down and installed Nero Linux 3.  It came down to the fact that I either did that, or install DeepBurner in **WINE**, and although I would rather use either a built in Ubuntu application, or something out of the repository, as a last resort I would at least prefer to install a **Linux** package **_ANY_** **_DAY_** rather than a **Windoze** application.  Besides, I have now already burned an .iso of Xubuntu, so I'm good to go now.

---

### Post by stchman on 2009-03-02
> **hifly1231 said:**
> Read the thread.

I don't use Nero, I was making that comment for other forum members.  My DVD burners work perfectly with K3b and Brasero.

If you want to be that way that is OK by me.

---

### Post by bodhi.zazen on 2009-03-02
These posts were for the most part off topic and I apologize if I did not get each and every post or left some in the other thread, but I read as much as I could stand.

I will leave this thread open for the moment, but please keep the conversation civil and respect the opinions of others even though you may disagree with them.

---

