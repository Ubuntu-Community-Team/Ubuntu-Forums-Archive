---
title: "Gonna buy a new laptop, how will ubuntu fare on it"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by neo1691 on 2012-05-22
Hey folks, 

Very excited as i am gonna buy a new **ASUS** laptop tomorrow.
I just wanted to know how will ubuntu 12.04 LTS run on it(with respect to all drivers support etc).
Its a free dos laptop.

Here are rough specs:
1) ***Core i5*** 2nd Generation processor
2) ***750 gb hdd*** (5400 RPM)
3) Ram:just upgraded it to ***8 GB***!!!! :KS before it was 6gb
4) ***2gb nvidea gt 630 M*** graphics card


You can find a detailed information about the specs on [THIS]("http://www.flipkart.com/asus-k53sm-sx010d-2nd-gen-ci5-4-gb-750-gb-2gb-graphics-dos/p/itmd7vs3bhr6jtgb?pid=COMD7VPKTSFNFZWM&_l=VLGMT56bjfBrqnhZ9Jn1Xg--&_r=Z6KOKTxWMMK9aemsYJX3AQ--&ref=574160a2-b514-48fe-8cf4-6c37833e787c") site.

Looking forward for your replies. 

(As I want to dedicate my new laptop to ubuntu.. say bye bye to doze) :guitar:

---

### Post by Brizlitman on 2012-05-22
DUDE...NICE SPECS! Well you can run Precise Pangolin(12.04) from a live cd or live usb just to check whether your wifi and everthing else work out of the box before you install. Have fun!

---

### Post by Nick_Kats on 2012-05-22
It will work just fine ;)

---

### Post by roelforg on 2012-05-22
I'm yealous...
Though my older systems work just fine.

---

### Post by neo1691 on 2012-05-22
Thanks a lot..!! OMG i am so so happy!! What a gift for my birthday!!!

Well, i will just need windows for flashing my android phone and playing fifa 12.

I am already deciding what OS should i install first, Ubuntu or Doze... 

And what partitions should i choose!! :P (I am going mad!! )

EDIT: I have upgraded my ram to 8GB.. YEAH... 
I wanted to ask should i go for 32 bit or 64 bit version of ubuntu??

---

### Post by nguyenphivu on 2012-05-22
Congrats!!

---

### Post by mastablasta on 2012-05-22
64bit, since you have a 64bit CPU.
 
if it doesn't use Optimus then it should work fine, otherwise prepare to do some work (check bumblebee).
 
install windows first. as it will be easier to add linux later.

---

### Post by roelforg on 2012-05-22
> **neo1691 said:**
> : I have upgraded my ram to 8GB.. YEAH... 
I wanted to ask should i go for 32 bit or 64 bit version of ubuntu??
 
I'd go with 32-bit pae.
The 32-bit pae kernel has a mem limit of 64gb but it has more drivers then the 64-bit kernel.
 
EDIT:
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)
Some info on pae is on the page

---

### Post by neo1691 on 2012-05-22
> **mastablasta said:**
> 64bit, since you have a 64bit CPU.
 
if it doesn't use Optimus then it should work fine, otherwise prepare to do some work (check bumblebee).
 
install windows first. as it will be easier to add linux later.
Sorry but i dont really know anything about optimus, can you please elaborate?

---

### Post by neo1691 on 2012-05-22
> **roelforg said:**
> I'd go with 32-bit pae.
The 32-bit pae kernel has a mem limit of 64gb but it has more drivers then the 64-bit kernel.
 
EDIT:
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)
Some info on pae is on the page
But what are the advantages of using PAE, as on the link you posted, its said that the same thing is achieved by switching to 64 bit os

---

### Post by roelforg on 2012-05-22
> **neo1691 said:**
> But what are the advantages of using PAE, as on the link you posted, its said that the same thing is achieved by switching to 64 bit os
 
No it isn't the same.
It's a 32 bit os, but you can use 4+gb ram like 64bit.
 
The difference that i think is important is that 32bit has more drivers then 64bit and some closed drivers are only in 32 bit.
It also has the benefit of being portable if your system melts down (say your 64bit melts down and you've only got a 32bit system at hand).
I've been running 32bit ubuntu on my 64bit laptop for a while now and there's no advantage for 64bit over 32bit.
It's just more convinient because binary packages outside the repos and ppas are usually 32bit only.

---

### Post by neo1691 on 2012-05-22
> **roelforg said:**
> No it isn't the same.
It's a 32 bit os, but you can use 4+gb ram like 64bit.
 
The difference that i think is important is that 32bit has more drivers then 64bit and some closed drivers are only in 32 bit.
It also has the benefit of being portable if your system melts down (say your 64bit melts down and you've only got a 32bit system at hand).
I've been running 32bit ubuntu on my 64bit laptop for a while now and there's no advantage for 64bit over 32bit.
It's just more convinient because binary packages outside the repos and ppas are usually 32bit only.
Hmm!! Even the download site of ubuntu says 32 bit is recommended. I will go for 64 bit Doze and 32 bit ubuntu

---

### Post by Ubun2to on 2012-05-22
> **neo1691 said:**
> Thanks a lot..!! OMG i am so so happy!! What a gift for my birthday!!!

Well, i will just need windows for flashing my android phone and playing fifa 12.

I am already deciding what OS should i install first, Ubuntu or Doze... 

And what partitions should i choose!! :P (I am going mad!! )

EDIT: I have upgraded my ram to 8GB.. YEAH... 
I wanted to ask should i go for 32 bit or 64 bit version of ubuntu??
You had better thank the person well-that person is nice to get you such a good laptop.
I think Wine could work to get your Android phone to sync with the Windows program (I think 'flashing' isn't the best word for synchronization when you consider you can get arrested for flashing someone in public).
I say install Ubuntu first-it's the best OS ever. If you need Losedoze for the Android sync application, and Wine won't work, just setup a virtual machine.
Also, since it's over 4 GB RAM, you need the 64 bit OS.

---

### Post by roelforg on 2012-05-22
> **Ubun2to said:**
> You had better thank the person well-that person is nice to get you such a good laptop.
I think Wine could work to get your Android phone to sync with the Windows program (I think 'flashing' isn't the best word for synchronization when you consider you can get arrested for flashing someone in public).
I say install Ubuntu first-it's the best OS ever. If you need Losedoze for the Android sync application, and Wine won't work, just setup a virtual machine.
Also, since it's over 4 GB RAM, you need the 64 bit OS.
 
Didn't i just explain pae and it's ability to boost the 32bit linux ram limit from 3gb to 64gb? And how it's just so much easier to be able to use closed source drivers as (when you're lucky enough to have them for linux) they're usually 32bit.

---

### Post by neo1691 on 2012-05-22
> **Ubun2to said:**
> You had better thank the person well-that person is nice to get you such a good laptop.
I think Wine could work to get your Android phone to sync with the Windows program (I think 'flashing' isn't the best word for synchronization when you consider you can get arrested for flashing someone in public).
I say install Ubuntu first-it's the best OS ever. If you need Losedoze for the Android sync application, and Wine won't work, just setup a virtual machine.
Also, since it's over 4 GB RAM, you need the 64 bit OS.
Well, flashing in the sense, changing the ROM of my android phone. Yeah its more like changing the whole android version of my phone. And fifa 12 is still not there for Linux.. (Maybe i will be a Linux programmer and code a similar game for Linux :P) 

And 32 but vs 64 bit, its getting way over my head!!

Oh EDIT: Its a gift from my mom!! Thank you mummy!! :D 
Gonna get this tomorrow!!

---

### Post by roelforg on 2012-05-22
> **neo1691 said:**
> Well, flashing in the sense, changing the ROM of my android phone. Yeah its more like changing the whole android version of my phone. And fifa 12 is still not there for Linux.. (Maybe i will be a Linux programmer and code a similar game for Linux :P) 
 
And 32 but vs 64 bit, its getting way over my head!!
 
Oh EDIT: Its a gift from my mom!! Thank you mummy!! :D 
Gonna get this tomorrow!!
 
I've run 32bit ubuntu with pae on 64bit, 4gb hw just fine.
32bit will give you the least headackes as most apps and drivers are native to 32bit and not everyone has the gear to build 64bit packages making 3rd party debs usually 32 bit.
If you ever need to swap a hd with another pc, it'll just work and not complain about not having a 64bit cpu in that pc.
 
This is stuff i learned from experience and installing 32bit ubuntu on 2 64bit systems.
and 64bit on 1 system (it was a pain getting 64bit packages for some stuff).
 
EDIT:
Btw, you're lucky to get a sys with those specs!

---

### Post by neo1691 on 2012-05-22
> **roelforg said:**
> I've run 32bit ubuntu with pae on 64bit, 4gb hw just fine.
32bit will give you the least headackes as most apps and drivers are native to 32bit and not everyone has the gear to build 64bit packages making 3rd party debs usually 32 bit.
If you ever need to swap a hd with another pc, it'll just work and not complain about not having a 64bit cpu in that pc.
 
This is stuff i learned from experience and installing 32bit ubuntu on 2 64bit systems.
and 64bit on 1 system (it was a pain getting 64bit packages for some stuff).
 
EDIT:
Btw, you're lucky to get a sys with those specs!
Thanks!! Anyways i have got 8 gb ram, and i have a copy of 12.04 32 bit staring right in front of me! :P

---

### Post by mastablasta on 2012-05-22
> **neo1691 said:**
> Sorry but i dont really know anything about optimus, can you please elaborate?
 
Nvidia optimus is hybrid graphics switchin that is officialy supported (by nvidia) only in windows7. bumlebee is unnoficial support by community. sometimes it works, sometimes not. the idea is that when powerfull graphics acceleration is not needed the laptop would switch to low powered intel GPU, conserving less power and thus increasing battery time on laptop. so that laptops can get 10+ hours of battery life.
 
[http://www.webupd8.org/2012/01/bumblebee-30-released-nvidia-optimus.html](http://www.webupd8.org/2012/01/bumblebee-30-released-nvidia-optimus.html)
[http://bumblebee-project.org/install.html](http://bumblebee-project.org/install.html)
 
AMD also has GPU switching but is now officially supported by AMD in many laptop models.
 
as for 32bit PAE kernel - it was suggetted to use it because some linux drivers are only 32bit. 
 
i would still try 64bit first and if it all works leave it at that. i mean with that much ram and 64bit CPU why indeed would someone try to use 32 bit OS? as i know all windows7 preloaded notebooks come with 64bit as soon as there is more than 4GB ram (maybe even on lower ram) eventhough widnows also have 32bit PAE kernel.

---

### Post by Paddy Landau on 2012-05-22
I would agree to try 64-bit first. Without it, you won't be able to use the full functionality of (say) virtual machines.

I also agree to just try 64-bit from a Live USB first; test Internet access and anything else you might require. If it works, go for it.

The Ubuntu download page does recommend 32-bit; I don't know why, because Canonical had decided to recommend 64-bit from version 12.04.

---

### Post by neo1691 on 2012-05-22
> **mastablasta said:**
> Nvidia optimus is hybrid graphics switchin that is officialy supported (by nvidia) only in windows7. bumlebee is unnoficial support by community. sometimes it works, sometimes not. the idea is that when powerfull graphics acceleration is not needed the laptop would switch to low powered intel GPU, conserving less power and thus increasing battery time on laptop. so that laptops can get 10+ hours of battery life.
 
[http://www.webupd8.org/2012/01/bumblebee-30-released-nvidia-optimus.html](http://www.webupd8.org/2012/01/bumblebee-30-released-nvidia-optimus.html)
[http://bumblebee-project.org/install.html](http://bumblebee-project.org/install.html)
 
AMD also has GPU switching but is now officially supported by AMD in many laptop models.
 
as for 32bit PAE kernel - it was suggetted to use it because some linux drivers are only 32bit. 
 
i would still try 64bit first and if it all works leave it at that. i mean with that much ram and 64bit CPU why indeed would someone try to use 32 bit OS? as i know all windows7 preloaded notebooks come with 64bit as soon as there is more than 4GB ram (maybe even on lower ram) eventhough widnows also have 32bit PAE kernel.
I understand that ironhead is going to be the next version of bumblebee.. Will it be stable.. 
[THIS]("http://ubuntuforums.org/showthread.php?t=1871226") thread tells me that i dont need to install any propitiatory drivers for nvidea, just use bumblebee.

And will i be able to use all hardware acceleration and 3d effects on ubuntu. (compiz fusion) ?? with my graphics card??

---

### Post by neo1691 on 2012-05-22
> **Paddy Landau said:**
> I would agree to try 64-bit first. Without it, you won't be able to use the full functionality of (say) virtual machines.

I also agree to just try 64-bit from a Live USB first; test Internet access and anything else you might require. If it works, go for it.

The Ubuntu download page does recommend 32-bit; I don't know why, because Canonical had decided to recommend 64-bit from version 12.04.
How do i check the system stability and performance on a 64 bit live ubuntu??

---

### Post by digithal on 2012-05-22
[QUOTE=neo1691]And will i be able to use all hardware acceleration and 3d effects on ubuntu. (compiz fusion) ?? with my graphics card??[/QUOTE]
Don't worry, for sure you will.
Also, read carefully: [**nVidia Optimus and Ubuntu explained**](http://ubuntuforums.org/showthread.php?t=1657660) and [**Bumblebee installation process**](https://wiki.ubuntu.com/Bumblebee).

---

### Post by alphacrucis2 on 2012-05-22
> **mastablasta said:**
> 64bit, since you have a 64bit CPU.
 
if it doesn't use Optimus then it should work fine, otherwise prepare to do some work (check bumblebee).
 
install windows first. as it will be easier to add linux later.

If you can. then disable optimus in the BIOS. It's more trouble than it is worth even with Windows.

---

### Post by neo1691 on 2012-05-22
> **digithal said:**
> Don't worry, for sure you will.
Also, read carefully: [**nVidia Optimus and Ubuntu explained**](http://ubuntuforums.org/showthread.php?t=1657660) and [**Bumblebee installation process**](https://wiki.ubuntu.com/Bumblebee).

Thanks a lot, but the second link ain't working here.
EDIT: working now :P

> **alphacrucis2 said:**
> If you can. then disable optimus in the BIOS. It's more trouble than it is worth even with Windows.

Thanks, but as a matter of fact, I will have to experience it. 


By the way the laptop's manufacturer is ASUS.. Hope its a ubuntu friendly manufacturer

---

### Post by digithal on 2012-05-22
Hi again, **@neo1691**! :)
As a long time ASUS user, I can say only good words. Never faced any serious problem, that can't be solved quickly.
BTW my main machine is almost the same as yours but different vga. So enjoy your new notebook and have fun with Ubuntu :)

About disabling Optimus, I think ASUS removed this option from K5* series a long time ago.

---

### Post by neo1691 on 2012-05-22
> **digithal said:**
> Hi again, **@neo1691**! :)
As a long time ASUS user, I can say only good words. Never faced any serious problem, that can't be solved quickly.
BTW my main machine is almost the same as yours but different vga. So enjoy your new notebook and have fun with Ubuntu :)

About disabling Optimus, I think ASUS removed this option from K5* series a long time ago.
Whoa!! Thanks a lot!!Thats so cheering!!
Whats your say on 32/64 bit versions of ubuntu on Asus!!

---

### Post by digithal on 2012-05-22
> **neo1691 said:**
> Whoa!! Thanks a lot!!Thats so cheering!!
Whats your say on 32/64 bit versions of ubuntu on Asus!!
Well, my thumbs are always up for 64 bit. And the statement that 64 bit OS is only for computers with >=4gb memory, is totally wrong!

I agree with **@roelforg** that there are still many precompiled binary packages that are usually 32 bit. And sometimes its a real pain to get them working. Plus I'm not a fan of messing different arch libs.

So, my suggestion is to go ahead and try Ubuntu 64, it doesn't hurt. The choice is yours :)

And hey, check this out, maybe it will be interesting to you: [**Ubuntu 12.04 LTS: 32-bit vs. 64-bit Performance**](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_3264&num=1).

Regards!

---

### Post by roelforg on 2012-05-22
> **digithal said:**
> Well, my thumbs are always up for 64 bit. And the statement that 64 bit OS is only for computers with >=4gb memory, is totally wrong!

I agree with **@roelforg** that there are still many precompiled binary packages that are usually 32 bit. And sometimes its a real pain to get them working. Plus I'm not a fan of messing different arch libs.

So, my suggestion is to go ahead and try Ubuntu 64, it doesn't hurt. The choice is yours :)

And hey, check this out, maybe it will be interesting to you: [**Ubuntu 12.04 LTS: 32-bit vs. 64-bit Performance**]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_3264&num=1").

Regards!

Those benchmarks still say that 32bit-pae wins over 64bit in most catogories,
only the heavy video stuff and the hd speed* are slower.

* I don't get how the hd suddenly got slower. I don't think there's much difference in the hd-drivers in the kernel for 32/64-bit, so i'm confused by that one.

And for those who keep going on about the ram, here are some stone-hard facts:
32-bit pae linux kernel: 64GB max ram
64-bit pae linux kernel: 128GB max ram
And i don't think anybody here has a desktop that has ram amounts even close to 64gb.

---

### Post by Paddy Landau on 2012-05-22
> **digithal said:**
> I agree with **@roelforg** that there are still many precompiled binary packages that are usually 32 bit. And sometimes its a real pain to get them working.
However, that's usually no problem if you're just using the standard sorts of packages (as I do), and don't need unsupported 64-bit drivers.

I've been with 64-bit since 10.04. Apart from earlier Flash incompatibilities, I've had no problems related to it.

> **digithal said:**
> ... maybe it will be interesting to you: [**Ubuntu 12.04 LTS: 32-bit vs. 64-bit Performance**]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_3264&num=1").
That was interesting, thank you. I'm glad I moved to 64-bit.

---

### Post by Paddy Landau on 2012-05-22
> **roelforg said:**
> Those benchmarks still say that 32bit-pae wins over 64bit in most categories...
Uh, no. Where do you see that? There is one test where they are the same (OpenArena); one test where 32-bit PAE is marginally faster (0.9% for Apache Benchmark); and nine tests where 64-bit is faster, some significantly.

It is interesting that OpenArena is (marginally) faster with 32-bit non-PAE.

---

### Post by digithal on 2012-05-22
**@roelforg** - My comment about the RAM was that its absolutely wrong to choose 32/64 bit just because of it since both architectures can handle more then 3GB. And you prooved it with PAE facts. But about the performance tests, please read the graphics again :)

---

### Post by roelforg on 2012-05-22
> **Paddy Landau said:**
> Uh, no. Where do you see that? There is one test where they are the same (OpenArena); one test where 32-bit PAE is marginally faster (0.9% for Apache Benchmark); and nine tests where 64-bit is faster, some significantly.
 
It is interesting that OpenArena is (marginally) faster with 32-bit non-PAE.
 
I missed the little texts that said "less is better" on most tests... :oops:
I switched computers and now i see it! (must be a rendering bug, cause they're just not there on the pc i posted from)

---

### Post by ammofreak on 2012-05-22
Hi ):P

Ubuntu works perfectly on Asus laptops...:)

---

### Post by Paddy Landau on 2012-05-22
> **roelforg said:**
> (must be a rendering bug, cause they're just not there on the pc i posted from)
Computers are trouble! LOL

---

### Post by roelforg on 2012-05-22
> **Paddy Landau said:**
> Computers are trouble! LOL
 
I was thinking more along the lines of IE and rendering problems.

---

### Post by neo1691 on 2012-05-22
> **ammofreak said:**
> Hi ):P

Ubuntu works perfectly on Asus laptops...:)
Thanks a lot..

I am gonna run ubuntu 64 bit live first and check if internet and all is working or not!! IF no then i will happily move to 32 bit!

EDIT: This thread also deals with the same discussion PAE or not(32/64) [http://askubuntu.com/questions/20049/does-ubuntu-desktop-32bit-support-more-than-4gb-memory-with-default-installation]("http://askubuntu.com/questions/20049/does-ubuntu-desktop-32bit-support-more-than-4gb-memory-with-default-installation")

Edit: 
This article also recommends 64 bit.
[https://help.ubuntu.com/community/32bit_and_64bit]("https://help.ubuntu.com/community/32bit_and_64bit")
So theorotically, PAE makes 32 bit processors (who are limited to 4gb memory) access upto 64 gigs of memory. But that's just to overcome the 4 gb limitation. But when you have got 64 bit machine, i think the kernel will automatically support it.

Can somebody agree with me. will ubuntu automatically detect my 8 gb memory?? (and what will be the same on 32 bit?)

---

### Post by digithal on 2012-05-22
**@neo1691** - you are correct.
Ubuntu 64 will detect and use all your memory without doing anything further.
Ubuntu 32 will detect all your memory, but its not gonna use the full capacity untill you enable PAE.

---

### Post by neo1691 on 2012-05-22
> **digithal said:**
> **@neo1691** - you are correct.
Ubuntu 64 will detect and use all your memory without doing anything further.
Ubuntu 32 will detect all your memory, but its not gonna use the full capacity untill you enable PAE.
4 Hours remaining for me to get my beast!! :D

---

### Post by mastablasta on 2012-05-23
> **Paddy Landau said:**
> The Ubuntu download page does recommend 32-bit; I don't know why, because Canonical had decided to recommend 64-bit from version 12.04.
 
they've changed their decision after noticing that substantial number of computers (25% or so) running ubuntu are only 32bit capable.
 
otherwise if i had a mashcine like that i would definatelly go after 64 bit.
 
as i said if windows7 came preloaded, it would be 64bit.

---

### Post by Paddy Landau on 2012-05-23
> **mastablasta said:**
> they've changed their decision after noticing that substantial number of computers (25% or so) running ubuntu are only 32bit capable.
That makes sense. I wonder if a change to the wording would make sense? Something like, "64-bit (recommended unless your computer is older than [noparse]2008)[/noparse]" or something like that.

---

### Post by neo1691 on 2012-05-23
Yeah!! Finally got it!! Here is the public link of the unboxing!!....

[https://www.facebook.com/media/set/?set=a.308432675905963.72920.100002176981494&type=1&l=4adb7d9b23](https://www.facebook.com/media/set/?set=a.308432675905963.72920.100002176981494&type=1&l=4adb7d9b23)

However doze goes first into it!! :P

EDIT: Ok now running ubuntu live 64 bit.. Just awesome.. speed is super..wifi is working, so is internet.. also system monitor shows 7.7 gb of memory!! :D

What else should i check before installing ubuntu 64??

---

### Post by digithal on 2012-05-23
> **neo1691 said:**
> Yeah!! Finally got it!! Here is the public link of the unboxing!!....

[https://www.facebook.com/media/set/?set=a.308432675905963.72920.100002176981494&type=1&l=4adb7d9b23](https://www.facebook.com/media/set/?set=a.308432675905963.72920.100002176981494&type=1&l=4adb7d9b23)

However doze goes first into it!! :P

EDIT: Ok now running ubuntu live 64 bit.. Just awesome.. speed is super..wifi is working, so is internet.. also system monitor shows 7.7 gb of memory!! :D

What else should i check before installing ubuntu 64??
Gratz for getting your new toy! :)
Now install Ubuntu and if you face any troubles, Ubuntu Forums is the place to ask.

---

### Post by goaliedude3919 on 2012-05-23
I just thought I would add that I agree with the other people who have said that it is best to just disable Optimus, if possible. If that is still an option in the Asus BIOS, I highly recommend disabling it. My computer has Optimus and it was causing me to always boot in Unity2D as opposed to Unity#d, meaning that I couldn't see any of the fancy effects and an customizations I made to Unity wouldn't take place. Disabling Optimus is what finally allowed me to fully utilize Ubuntu. and its features.

---

