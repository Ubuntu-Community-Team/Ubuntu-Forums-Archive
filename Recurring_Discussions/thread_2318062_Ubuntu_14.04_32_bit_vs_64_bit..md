---
title: "Ubuntu 14.04 32 bit vs 64 bit."
date: 2016-03-22
forum: Recurring Discussions
---

### Post by poorguy on 2016-03-22
Hey all,

Other than I can use more ram is there any other advantage to using 64 bit Ubuntu over 32 bit Ubuntu.


Thanks.

---

### Post by kansasnoob on 2016-03-22
I believe Chrome browser is now only available for 64 bit.

---

### Post by poorguy on 2016-03-22
I just 3.0 gb ram is enough for 64 bit Ubuntu.

I notice 32 bit support is being dropped and some apps are no longer supported anymore.

Yeah I could switch from 32 to 64 bit with nothing to loose as I only web browse and save everything to a thumb drive.

---

### Post by goofprog on 2016-03-22
32bit linux with pae over 64 bit linux does it matter? yes.  Actually 32 bit applications are faster because I believe the op codes are optimized on the data bus.  Meaning it should push over two instructions on a 64 bit data bus BUT that is just how I think.  I do have 64 bit linux.  I thought for a time ago there was only 32bit flash that was the updated version and I used to use 32bit linux because I could use the most up-to-date flash player.

---

### Post by grahammechanical on 2016-03-22
It is old data but relevant and definitive.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

Regards

---

### Post by QIII on 2016-03-22
Moved to Recurring Discussions

---

### Post by poorguy on 2016-03-22
Ok well installed Ubuntu Mate 14.04 64 bit install and updates 45 to 50 minutes about the same time that 32 bit takes on the same desktop.

Apparently my motherboard isn't 64 bit capable as I'm only showing 3.2 gb ram and I have 4.0 gb installed.

So far I really don't notice any difference between 32 and 64 bit.
Everything seems lighting quick as before when running 32 bit.

Well guess I'll see what I find.
Seems like I read somewhere that 64 bit provided better security I don't know why that would be.

Thanks for the link grahammechanical always interested in the differences of 32 and 64 bit OS.

Thanks for the input.

---

### Post by poorguy on 2016-03-22
Yeah all seems to be working well glad I switched.
Google Earth 64 bit seems to have some glitches and if I can't work them out I will try the 32 bit version.

Ok I stop bugging everyone was just curious as I have been reading about all the 32 bit becoming unsupported.

Good Evening To All.

---

### Post by mörgæs on 2016-03-23
> **poorguy said:**
> 
I have been reading about all the 32 bit becoming unsupported.

Please post a link if it is about other software than Chrome.

---

### Post by mörgæs on 2016-03-23
> **goofprog said:**
> Actually 32 bit applications are faster because I believe the op codes are optimized on the data bus.  Meaning it should push over two instructions on a 64 bit data bus BUT that is just how I think.

If you post statements like this we would appreciate a link.

---

### Post by poorguy on 2016-03-23
> **mörgæs said:**
> Please post a link if it is about other software than Chrome.

Mainly it has been only about Chrome.
No specific link just bits and pieces.
Just seems to be the start.
I see where Ubuntu will be dropping 32 bit support on the standard distro read that here on the forums.

---

### Post by oldfred on 2016-03-23
I do not know if a conclusion was reached or not.

 Developer's discussion of deemphasis of 32 bit Ubuntu - Nov 2014 
[http://www.phoronix.com/scan.php?page=news_item&px=MTgzODE](http://www.phoronix.com/scan.php?page=news_item&px=MTgzODE)
[http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/](http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version. 

But issue with Ubuntu is that with Unity it needs somewhat newer hardware, 2GB of RAM or more,  and decent video.

The Lubuntu & Xubuntu versions then would be the better choices for 32 bit installs on older hardware.

On the other hand some vendors have build lightweight systems that are 32 bit boot or otherwise limited (often limited RAM). So those few systems may need a 32 bit system.

---

### Post by poorguy on 2016-03-23
Although all of my Linux computers were probably designed for 32 bit OS I am finding that they will support 64 bit Linux and seem to run well.

Still can't see the great advantage of 64 bit over 32 bit other than the increase of ram.
Perhaps the best advantage I see with 64 bit is it does work on the newer motherboards with UEFI Bios where 32 bit doesn't.

As far as Google Chrome no longer supporting 32 bit IMO no loss for this end-user.

Good Day To All.

---

### Post by poorguy on 2016-03-24
Well after some lengthy searching all I can come up with is the only real advantage using 64bit OS is the utilization of 64 bit hardware which is being used in today's computers.

Apparently the hardware manufactures are way ahead of the software developers.
That makes sense as it seems that hardware is rolled out faster then software can be developed for the newer hardware.

If nothing else I learned a lot of things I didn't understand before and that is cool.

---

### Post by yoshii on 2016-06-13
According to the FAQ section of WineHQ (the Wine official website), the 32-bit version of Wine is more stable than the 64-bit version.  
So if you prefer to use a lot of Wine programs, the 64-bit version is a disadvantage, not an advantage.  This might influence which you prefer for your OS.  

Personally, in all my years, I have never used any program of any type that required more than the standard 2 GB of application RAM out of the 4 GB of standard 32-bit RAM.  
Maybe if I started making fancy videos I would utilize more hardware RAM.  But for music composing and image editing and light video editing, I just don't need more than 4 GB of hardware RAM.  

And I do still like using a lot of old classic 32-bit Windows freewares like IrfanView, PhotoFilter7, and Foobar2000.  I also use 32-bit Reaper (paid for) for music composing and it reported works on 32-bit Wine while the 64-bit version of Reaper fails on the 64-bit version of Wine.  Reaper is my main DAW program, so that's why I stuck with 32-bit.  

I'm not saying that 64-bit is bad, though.  When the time comes I will change to 64-bit.  Yet so far, still in 2016, I don't need it.

---

### Post by JayKay3OOO on 2016-06-13
I don't know about the answer, but you can install the PAE extension to linux 32 bit OS so you can see and use all your ram from the 32 bit installation.

---

### Post by mörgæs on 2016-06-14
All Buntus are by default PAE-enabled and have been for some years. No need to change anything here.

---

### Post by T.J. on 2016-06-14
if I might add my two cents?  If you have 64 bit hardware, use it.  The design of the circuitry is intended for it.  The main reason that 32 bit software is still used is because of Windows.  Traditional Windows apps are 32 bit, because of the assumption that you want it to run on older machines that are 32 bit only.  Unfortunately, that means that 64 bit processors have to have 32 bit circuits in addition to the 64 bit ones.  This makes processors slower, more costly, and wasteful of energy.

---

