---
title: "White screen on boot"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by ddropp on 2013-04-09
Greetings all. I've been trying to install ubuntu and other linux distros but I have the same problem with all distros.
While selecting to boot my usb, I get prompted to select "install ubuntu" and after I select one option, I get a white screeen. 
I've tried everything (nomodeset etc.) but nothing seems to work. Can someone suggest another route to solve this?

Thanks in advance.

---

### Post by UltimateCat on 2013-04-09
Hi:

Need to know a few thing in order to help you--

How are you trying to install Ubuntu?

By USB memory stick?  External drive? DVD/CD?
I almost always install Linux by DVD/CD and I always use a DVD + R and it works great!
You can try burning the LIVE ISO Image and install that way--

What computer do you have and what type of architecture?
Desktop or laptop?

---

### Post by ddropp on 2013-04-10
Hey!

I am installing via a USB Drive.

My machine is a netbook with the following specifications:

Intel Atom N2800 1.86GHz
4GB DDR3
Integrated HD Graphics

---

### Post by wickedpuppy on 2013-04-10
Do you see an option to "Try Ubuntu without any change to your computer"? And if so , have you tried it?

---

### Post by ddropp on 2013-04-10
> **wickedpuppy said:**
> Do you see an option to "Try Ubuntu without any change to your computer"? And if so , have you tried it?

Yes. I've tried it and I get the white screen again. 

Plus I've tried installing with wubi and I get the same white screen.

---

### Post by black veils on 2013-04-12
its the processor, something to do with cedar trail/cedarview.

it doesnt look good, seems the best you will get is vesa with low resolution in 12.04, or maybe something like this will work for you:

"the drivers in ppa:sarvatt/cedarview are now  also in precise-update, since a little earlier than the release of  Ubuntu 12.04.1. If someone is interested in making it work also with full video  acceleration (1080p at 10% CPU or less), I wrote a small guide that  maybe can help someone (feedback appreciated):

  [http://linuxeeepc.blogspot.com/2012/08/lubuntu-on-eeepc-1025c-with-correct.html](http://linuxeeepc.blogspot.com/2012/08/lubuntu-on-eeepc-1025c-with-correct.html)

  It is fully tested on an Eeepc 1025c, but it should work on any cedar trail netbook."

 
[I]
[COLOR=#006400]source: [http://askubuntu.com/a/180329](http://askubuntu.com/a/180329)[/COLOR][/I]

---

### Post by Rob Sayer on 2013-04-13
I'm typing this on an acer netbook with an atom 2600 cpu that uses the same cedarview gma3600 integrated gpu as the atom 2800, accoriding to the intel page I just looked at.  I'm running kubuntu 12.04.  I've had issues with hardware support but nowhere near the problems you're having.  Had problems with brghtness levels and 3d but it always had the correct resolution.

What version of ubuntu did you try from the usb?  I wouldn't recommend 12.10 for a cedarview/cedartrail machine.  13.04 has better support ... I tried the alpha 2 and beta 1 versions and the video worked fine.  But I'm not prepared to deal with a pre release OS so I'm waiting for the finished release of 13.04.  Then I'll upgrade.

If it was 12.10 you tried and you try 12.04 instead (and you get some working video of course), the patches from the sarvatt ppa mentioned in the above link are not the correct way to do it.  I tried them but they tie you to an older kernel.  That solves the video problem but can introduce others.

12.04 kernel support for the cedarview driver packages is there, but it's in a newer version than the one you get on the 12.04 install iso.  If you can install 12.04, do not install them until you update the system repeatedly so make sure you have everything.  Then you can install them without losing video.

Good luck.

---

