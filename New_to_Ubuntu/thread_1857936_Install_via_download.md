---
title: "Install via download"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by VeryFoggy on 2011-10-11
First - I am on vacation, and completely stressed out, so please use small words.
 
Back story - Using a laptop with win xp. My win xp froze up and on reboot refused to load. That is my last straw. I had looked at Ubuntu about a year ago, and unless there is a better suggestion, that is what I am going to load. 
 
I have the hard drive out of my laptop, and connected to my mothers netbook (win 7) via USB connection (so it comes up like a thumb drive). I used the right-click format option as a starting point. 
 
?1 - Do I need to do something else to prepare the drive?
?2 - Is Ubuntu a good choice, or would there be a better choice to load? I don't do a lot of programming, or gaming, I mainly just surf the web and write papers.
?3 - How do I download/install it so that when I put the drive back into my laptop that it will just come up?

---

### Post by Lisiano on 2011-10-11
1) Nope. There was no need to do anything using Windows either, unless you plan to backup files from it.
2) I say, good choice.
3) The same way you would do it if you were installing on your mothers netbook. Get a USB flash drive, follow the instructions on how to make a USB flash drive on the [download page]("http://www.ubuntu.com/download/ubuntu/download"), install but when asked, pick your HDD instead of your mothers netbook, (Probably will be the 2nd one), I would recommend swapping the hard drive of your mothers netbook with yours so you don't accidentally confuse one with the other, this way you don't even have to change anything during the install. Linux is agnostic to what hardware it was installed on and on what hardware it is working with, so it doesn't matter if install it one machine and use it in another machine
Alternative 3) Just put the disk back inside and do the install using a CD or USB.

---

### Post by Mark Phelps on 2011-10-11
The SAFEST thing for you do to at this point would be to remove the existing hard drive from your mother's netboot, replace it with your drive -- and then boot directly from the USB stick containing the Ubuntu installation files.  Do NOT boot from your hard drive in the netbook.

The main reason I suggest this, is that there is a risk with BOTH drives connected to the netbook, that GRUB will be installed to the Netbook hard drive instead of yours.  This would be a major problem because (1) when you went to boot from your drive in your PC, it would not boot because GRUB would be missing, (2) when you mother later went to boot her netbook, it probably would NOT boot because your hard drive is missing.

---

### Post by VeryFoggy on 2011-10-11
Wish me luck. I am downloading Ubuntu now, and will put it on my thumbdrive, then run it on my laptop with my hard drive plugged back in.

---

### Post by 11jmb on 2011-10-11
One more consideration: if you are unable to boot your computer from usb (a fairly recent feature for some computers) you will have to burn an ubuntu cd.

if you boot from a cd, you should be able to put your computer back together before installing and not worry about breaking another computer.

---

### Post by VeryFoggy on 2011-10-13
> **VeryFoggy said:**
> Wish me luck. I am downloading Ubuntu now, and will put it on my thumbdrive, then run it on my laptop with my hard drive plugged back in.

It worked. Now I have to figure out how to load all of my favorite programs. :D

I will be doing a lot of combing through the forums, and you may see another thread from me soon. Let's hope not too many. [-o<[-o<[-o<

---

