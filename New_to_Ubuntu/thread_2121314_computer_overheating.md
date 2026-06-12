---
title: "computer overheating"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by AndEilert on 2013-03-01
Hello there good people.

So, here the other day my HDD crashed and i lost everything in my windows, and i always wanted to try Ubuntu, and so i did :) 
Until now everything has worked great, but i have the problem that the computer goes superwarm, sensors show me that everything reaches around 
89 degrees and the fans go like airplanes :(

The problem especially appears when i watch videos on YouTube and things using flash. 

This is Ubuntu 12.10.
I am using the Opera browser when surfing.
I'm using a laptop and i know that laptops dont have the best cooling, but when running windows i barely had 65 degrees.

So could anyone please help me out, i really want this to work smoothly.

Thanks in advance!:D

---

### Post by Mark_in_Hollywood on 2013-03-01
Call the "terminal" from the Applications / Accessories / Terminal Emulation

Let us start by seeing what the system is doing. At a terminal, type:

sudo iotop

and enter your password and then 

CTRL-SHIFT-T (to open a 2nd terminal tab)

and type

top

What are the CPU load averages in "top" and please post a screenprint of the iotop. To make a screenprint, press the Print-Scrn button on your keyboard.

Also, have you run Smart Monitor Tools? If you had Windows & the drive "blow up" you should have a look at:

[http://www.ubuntuupdates.org/package/core/precise/universe/base/gsmartcontrol](http://www.ubuntuupdates.org/package/core/precise/universe/base/gsmartcontrol)

---

### Post by AndEilert on 2013-03-01
Well, obviously with my luck it didn't go as warm as it usually does but.. here you go.

---

### Post by DiabolicalClaptrap on 2013-03-01
I've experienced high sys load with Opera in Puppy Linux (same scenario) myself. Maybe try clearing your cache? If that doesn't work, try reinstalling flash.
In my case, switching to FF helped.

---

### Post by samsom63 on 2013-03-01
> **AndEilert said:**
> Hello there good people.

So, here the other day my HDD crashed and i lost everything in my windows, and i always wanted to try Ubuntu, and so i did :) 
Until now everything has worked great, but i have the problem that the computer goes superwarm, sensors show me that everything reaches around 
89 degrees and the fans go like airplanes :(

The problem especially appears when i watch videos on YouTube and things using flash. 

This is Ubuntu 12.10.
I am using the Opera browser when surfing.
I'm using a laptop and i know that laptops dont have the best cooling, but when running windows i barely had 65 degrees.

So could anyone please help me out, i really want this to work smoothly.

Thanks in advance!:D

Hi, how hot was your computer when running with windows? My laptop tended to get quite hot under windows, and when I switched to ubuntu 12.10 it was even worse: fans always on (noisy like a plane taking off), overheating like crazy no matter what programmes were running (even idle, temp was very high). Apparently, ubuntu is less efficient than windows in that respect, so it overheats more easily (don't know why,nor whether this is really true). 

Anyway, this served me as a kick in the butt to go and have my laptop cleaned. It costed me £30, and since then no problem whatsoever: CPU temps are normal, fans are seldom on (and when they are, they do so without noise), even when gaming!! 
 
Bottom line: cleaning your computer is REALLY useful

---

### Post by AndEilert on 2013-03-01
> **samsom63 said:**
> Hi, how hot was your computer when running with windows? My laptop tended to get quite hot under windows, and when I switched to ubuntu 12.10 it was even worse: fans always on (noisy like a plane taking off), overheating like crazy no matter what programmes were running (even idle, temp was very high). Apparently, ubuntu is less efficient than windows in that respect, so it overheats more easily (don't know why,nor whether this is really true). 

Anyway, this served me as a kick in the butt to go and have my laptop cleaned. It costed me £30, and since then no problem whatsoever: CPU temps are normal, fans are seldom on (and when they are, they do so without noise), even when gaming!! 
 
Bottom line: cleaning your computer is REALLY useful

Around 60-70 degrees in windows.. And i know, i clean my computer quite often because it usually helps... but ubuntu just makes everything go superwarm and i dont understand why this is happening:(

> **DiabolicalClaptrap said:**
> I've experienced high sys load with Opera in Puppy Linux (same scenario) myself. Maybe try clearing your cache? If that doesn't work, try reinstalling flash.
In my case, switching to FF helped.
 
I will try to figure out how to update my flash. And i really do not want to swtich to FF :(

---

### Post by Mark_in_Hollywood on 2013-03-01
OK, so, from a terminal:

sudo apt-get install iotop

then let me see the screenshot.

I don't have a laptop. I did have Win7-64 (ultimate) and it consistently used more system resources than Linux.

As you clean the laptop regularly, the other possibility, that comes to my mind, is the disk drive has problems. Are you willing to install or if you have a S.M.A.R.T. monitor, can we get a look at the drive's health?

---

### Post by Mark_in_Hollywood on 2013-03-01
Try this one:

[http://my.opera.com/ruario/blog/flash-problems-on-linux](http://my.opera.com/ruario/blog/flash-problems-on-linux)

---

### Post by AndEilert on 2013-03-01
> **Mark_in_Hollywood said:**
> OK, so, from a terminal:

sudo apt-get install iotop

then let me see the screenshot.

I don't have a laptop. I did have Win7-64 (ultimate) and it consistently used more system resources than Linux.

As you clean the laptop regularly, the other possibility, that comes to my mind, is the disk drive has problems. Are you willing to install or if you have a S.M.A.R.T. monitor, can we get a look at the drive's health?
So i kinda provoked it this time, by running a video in the background. And this is what happends almost every time :(   I dont really know what a S.M.A.R.T monitor is.. so..

---

### Post by Mark_in_Hollywood on 2013-03-01
When I had video bleedthrough problmes, this is what I did. It's not exactly what you are qualifying, but it's simple and if it works, so much the better:

Some instruction:

Go to a Flash video object. That can be a Youtube vid or Vimeo, just as long as it's a Flash video or Flash based object on your monitor screen.

Right click on the video or object. Select "Settings" (no quotes on screen). Click on leftmost icon at bottom of Flash Player Settings windows. You will see a checkbox for Hardware Acceleration. Uncheck that box.

You are good to go.


I'm repeating myself, but please have a look at:

[http://my.opera.com/ruario/blog/flash-problems-on-linux](http://my.opera.com/ruario/blog/flash-problems-on-linux)

I'm now 75% certain that this is an Opera/Flash problem and not Ubuntu/Linux. This is NOT to say dump Opera. I have and user Opera and like it. But the various parts of Ubuntu/Opera/Flash need some tweaking.

---

### Post by AndEilert on 2013-03-01
Well, there is a light problem.. I cant turn hardware acceleration off... because when i open the little flash window, the whole thing just freeze and i cant click anything ...:( so.. what to do next?:(

---

### Post by Mark_in_Hollywood on 2013-03-01
Please read the post from the one previous to this, where I say "I repeat myself".

---

### Post by sleash78 on 2013-03-01
theres a command that might help. first, sudo apt-get install lm-sensors. then the command is sensors. you can use it when you think your computer would be too hot. it could be a hardware or software issue for why your computer is getting hot

---

### Post by zrdc28 on 2013-03-02
This will solve your problem for you, when installed there will be a icon in the taskbar upper right that looks like a lightening bolt. click on it and you can cut back
on processor speed. Ubuntu does not throttle back like windows does, it will also give you longer battery life.

sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter

---

### Post by AndEilert on 2013-03-04
I am so confused, now it goes warm with no apparent reason at all :( Why?!:confused:

---

### Post by samsom63 on 2013-03-04
> **zrdc28 said:**
> This will solve your problem for you, when installed there will be a icon in the taskbar upper right that looks like a lightening bolt. click on it and you can cut back
on processor speed. Ubuntu does not throttle back like windows does, it will also give you longer battery life.

sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter

I am pretty sure that installing jupiter alone won't solve his problem: before I had my laptop cleaned, I installed jupiter and it did not prevent the computer to over-heat. Of course it does not mean that it isn't a useful programme to regulate heat under normal circumstances.

---

### Post by samsom63 on 2013-03-04
> **AndEilert said:**
> I am so confused, now it goes warm with no apparent reason at all :( Why?!:confused:

 I'm sorry I am not knowledgeable enough to help you. I don't think it is a "Ubuntu problem", but rather a "hardware" or hardware+ubuntu combination issue.

You could try to install the lxde desktop - which is super lightweight, and see if it lowers a little the heat ??

---

### Post by AndEilert on 2013-03-04
> **samsom63 said:**
> I'm sorry I am not knowledgeable enough to help you. I don't think it is a "Ubuntu problem", but rather a "hardware" or hardware+ubuntu combination issue.

You could try to install the lxde desktop - which is super lightweight, and see if it lowers a little the heat ??

And I was beginning to have fun with Ubuntu :( Meh, might aswell just crawl back to windows:(

---

### Post by AndEilert on 2013-03-06
So i am going to make an, awful bump.. in this thread in the hope that i will get fresh eyes on the case :) If no one now i think i will give up.

I installed Jupiter as recommended up here, it helped quite alot, but this puppy still gets insanely warm :(

---

### Post by Mark_in_Hollywood on 2013-03-06
If you can get to the GRUB Recovery screen, please run the Update Grub. Have a look and see if the heat problem is gone. If that gives no satisfaction, try:

As this problem is anomalous, that is, one piece of software overheats and the other piece of software doesn't overheat, then if we believe that Ubuntu is the problem, my best idea is to use GParted (or the Windows partitioner - less easy to use IMO) and re-partition the (probably) /sda3. The /sda3 is probably where the Ubuntu OS is. After re-partitioning, re-install Ubuntu. If you can use your mobile you can even get live help during the re-install. By the bye: how did you obtain the copy of Ubuntu you used for the install? What media did you use for the install? Did you run the md5hash to see if the .iso is "clean"?

---

