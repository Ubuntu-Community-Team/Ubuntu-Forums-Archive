---
title: "Linux illiterate."
date: 2008-07-26
forum: New to Ubuntu
---

### Post by shrewsbury on 2008-07-26
Hey everyone. Recently I've purchased a new hard drive to install Ubuntu on. I'm a longtime Windows user but I figured it's time to take the plunge and learn something that I feel is worth learning; which is how to use Ubuntu or Linux in general.

I purchased the second hard drive so that I could dual boot between the two operating systems while I'm still getting used to Ubuntu.

Pretty much I just have a few simple questions.

1. How difficult is it to dual boot between the two operating systems? Do I just install Ubuntu on the second hard drive and it'll be good to go?

2. Where can I find drivers for my specific hardware and how do I install them? I tried installing some programs on Ubuntu through VMware but I'll be damned if I could figure it out.

Anyways, I'm completely, 100%, positively, Linux illiterate so if anyone can answer these questions and if anyone has any tips for a beginner, it would be great to know.

Thanks in advance. :guitar:

---

### Post by scragar on 2008-07-26
1 installing to a second HD is harder than to the same HD, but it can be done, just make sure your BIOS is set to boot from the second HD first, otherwise windows will always boot before ubuntu can offer you a choice of which OS to boot.

2 the generic drivers ubuntu installs will proberly be fairly good for your hardware(normaly supporting 1024 or even higher resolutions), and the restricted(official, but closed source) drivers found will let you know once your installed and booted into ubuntu.

---

### Post by SunnyRabbiera on 2008-07-26
Dont worry, Ubuntu can be very easy if you are lucky.
Some stuff is harder then others but you have plenty of folks to help you out.

---

### Post by halitech on 2008-07-26
welcome to the world of linux, I'm sure you will get frustrated at first with some things but it is worth it :)

far as dual booting, check out this link [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

most of your hardware should be detected automatically. For software, there is add/remove and synaptic.

---

### Post by Pro-reason on 2008-07-26
Dual booting is easy.  Just install Ubuntu and the installer will set up GRUB (the bootloader than handles dual-booting).

Most basic drivers are included with Ubuntu.  Once you've installed, you should be able to find more in Synaptic (which is the program you should you for 99% of what you need to install on Ubuntu).  If you have something rare, then you might have to search the Web for a driver and follow the instructions that come with it. 

If you don't say what your hardware is, there is no way I can be more specific.

---

### Post by Sef on 2008-07-26
> 1. How difficult is it to dual boot between the two operating systems? Do I just install Ubuntu on the second hard drive and it'll be good to go?

Not hard.  Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").


> Where can I find drivers for my specific hardware and how do I install them? I tried installing some programs on Ubuntu through VMware but I'll be damned if I could figure it out.

Most drivers are installed with Ubuntu.  A few restricted drivers may need to be added.

---

### Post by Yannick Le Saint kyncani on 2008-07-26
Hi shrewsbury and welcome to ubuntu, you should check [https://help.ubuntu.com/](https://help.ubuntu.com/) for some basic help. Enjoy ubuntu (I hope).

---

### Post by shrewsbury on 2008-07-26
Wow everyone replies really fast. Busiest community of any forum I've ever been a member of. I love it.

Anyways I run an 8600GT graphics card, Intel DG9650T motherboard and I assume I wouldn't need drivers for stuff like my hard drive and DVD burner? I don't really care about the card readers and such. Though my 1TB seagate external drive would be nice to have up and running.

Anyways, I will look into this dual booting and if I have anymore questions I will let you guys know. 

Thanks for everyone's help so far :)

[edit] Also, I have a Core 2 Duo processor which I'm pretty sure is 64 bit compatible. Is it worth it to install 64bit Ubuntu or is there really any advantages?

---

### Post by SunnyRabbiera on 2008-07-26
Yeh most DVD burners should work with ubuntu without trouble though there might be some troublemakers out there.
The best way to see if your hardware will work with ubuntu is with the live CD, a live CD is like a demo without installing a thing unless you tell it to.

---

### Post by scragar on 2008-07-26
your graphics card will definatly work with the generic drivers, however there are a few reports the restricted driver not working on the release from 1 year ago(feisty), no reports from later than that though, so it looks good to go. No drivers needed for hard drives or DVD drives(burners or whatever).

EDIT: clarify first sentence.

---

### Post by steveneddy on 2008-07-26
The Ubuntu CD installer will ask you where to install Ubuntu. Just tell it the second hard drive and all should be good.

Usually I partition my hard drives first, but I believe the new installer will take care of that for you.

---

### Post by Pro-reason on 2008-07-26
> **shrewsbury said:**
> 
Anyways I run an 8600GT graphics card, Intel DG9650T motherboard and I assume I wouldn't need drivers for stuff like my hard drive and DVD burner? I don't really care about the card readers and such. Though my 1TB seagate external drive would be nice to have up and running.

That all sounds like standard stuff that should work "out of the box" without even looking for drivers in Synaptic (which is incredibly easy).

---

### Post by ad_267 on 2008-07-26
When you install Ubuntu you can go to System - Administration - Hardware Drivers to enable the nvidia drivers for 3D support.

---

### Post by shrewsbury on 2008-07-26
Wow all seems pretty easy. I'm in the process of downloading Ubuntu now. One thing I forgot is that I'm using Marvell Topdog 802.11n wireless adapter. Is that going to work with an 'out-of-the-box' (I guess you could say) installation of Ubuntu?

---

### Post by SunnyRabbiera on 2008-07-26
Eh, wireless is still touch an go I am afraid. Thus why its good you are dual booting, so if you need windows to help get wireless drivers you can.

---

### Post by shrewsbury on 2008-07-26
> **SunnyRabbiera said:**
> Eh, wireless is still touch an go I am afraid. Thus why its good you are dual booting, so if you need windows to help get wireless drivers you can.
Okay awesome. I figured something like that might come up so I would keep my Windows installation around. Also, I'm a fairly big Steam fiend so Windows is gonna have to stick around for some time to come :P

---

### Post by ad_267 on 2008-07-26
> **shrewsbury said:**
> Okay awesome. I figured something like that might come up so I would keep my Windows installation around. Also, I'm a fairly big Steam fiend so Windows is gonna have to stick around for some time to come :P

I've got steam and counter strike source running in Ubuntu using wine, but I don't use it that much and it runs better in Windows.

---

### Post by scragar on 2008-07-26
> **shrewsbury said:**
> Okay awesome. I figured something like that might come up so I would keep my Windows installation around. Also, I'm a fairly big Steam fiend so Windows is gonna have to stick around for some time to come :P

steam games run very well in wine actually, [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554) according to almost all users it's support is actually better than windows :P

your wireless card can be made to work according to other threads on the forums, although it looks to be a bit of fiddling.

---

### Post by duckfeet on 2008-07-26
Hi: I'm a few weeks ahead of you, but wanted to tell you welcome!  A large part of my positive reaction to Linux, has as a result of this forum.  I have had several problems, from initial installation, to getting my mouse wheel to quit spinning the pages, and *every* problem was solved by people on this forum, and I myself was even able to help somebody, as new as I am, in using his USB stick to load Ubuntu, which tickled the hell out of me, as I'm usually on the receiving end of help...and just got thru--finally,, of solving my mouse-wheel problems, with as usual somebody on here helping out......

And I also have two HD's, one for Windows, and one for Ubuntu, and once you get the installation done, you'll find they work fine, and Windows will be handy, so you can find out when  you have problems--like I did w/the mouse, and w/my DVD, and w/sound--whether these problems are strictly in Ubuntu, or hardware...

So again, welcome, and any problems, post on here, very helpful people, make all the difference...

---

### Post by bushda on 2008-07-26
> **shrewsbury said:**
> Also, I have a Core 2 Duo processor which I'm pretty sure is 64 bit compatible. Is it worth it to install 64bit Ubuntu or is there really any advantages?

(Let me start by saying I hope this doesn't start a flame war.)

For a newbie, I'd suggest going with the 32 bit version of Ubuntu. My rationale for that recommendation is because getting some things to work like Flash can be something of a pain. 

I'm not sure if your wireless card is going to require the use of ndiswrapper or not, but if it does then you'll be forced to look for the 64 bit drivers for that too. (Don't worry - chances are someone else has already blazed this trail for you.) 

I've dabbled with 64 bit Ubuntu, and for what it's worth I went back to 32 bit Ubuntu for now. I do plan on going back to 64 bit Ubuntu in the future though.

---

### Post by AnonCat on 2008-07-26
The Ubuntu installer will make installation very easy.  I have Ubuntu installed on a separate hard drive and it automatically setup the grub menu which allows you to choose between Windows and Linux at bootup.

---

### Post by scragar on 2008-07-26
> **bushda said:**
> (Let me start by saying I hope this doesn't start a flame war.)

For a newbie, I'd suggest going with the 32 bit version of Ubuntu. My rationale for that recommendation is because getting some things to work like Flash can be something of a pain. 

I'm not sure if your wireless card is going to require the use of ndiswrapper or not, but if it does then you'll be forced to look for the 64 bit drivers for that too. (Don't worry - chances are someone else has already blazed this trail for you.) 

I've dabbled with 64 bit Ubuntu, and for what it's worth I went back to 32 bit Ubuntu for now. I do plan on going back to 64 bit Ubuntu in the future though.

there are no problems with flash on 64 bit anymore, the only problem I can see with going for the 64 bit version would be the wireless card, since it will almost certainly be a proprietary driver, which from lots of sources will only come in 32 bit releases, which for drivers does cause a few problems.

---

### Post by HotCupOfJava on 2008-07-26
I am a user of the 64-bit version myself. If your processor is 64-bit, you would be wise to take advantage of the 64-bit operating system. It will use the capabilities of your processor much better than the 32-bit version. I have had no problems at all with mine - it is lightning fast! (I'm on an AMD 64 dual-core).

---

### Post by bushda on 2008-07-26
Good to know guys. I may have to give 64 bit a try again.

---

### Post by newbuntuxx on 2008-07-26
hey shrewsbury...nice to see you trying ubuntu...

i am fairly new as well, however, i have something that i think is good for a beginner to know.

Since most linux software is either open source or free, the linux communities decided to put all of that software (drivers, graphic applications, office applications, games etc...) into one huge place, which they call the "Repositories". 

You can access the "respos" either using synaptic, which is in:

System-Administration- Synaptic Package Manager 

or using the following command in terminal:

sudo apt-get install "name of program you want to install without the quotes"


This way, you can ensure that all the software that you download has been properly tested and is bug-free, spyware-free etc...Also, you can update all the software that you have installed at once from one place with a single click. 

This is of course a brilliant mechanism...thats why you dont see it in windows...

You can find more info here: 

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

thats my 0.02 cents and i hope you found it useful.

enjoy ubuntu

---

### Post by steveneddy on 2008-07-26
> **scragar said:**
> 
your wireless card can be made to work according to other threads on the forums, although it looks to be a bit of fiddling.

Just search the forums for your card and model and if there is something on it you will find it.

You might try Google for that wireless adapter, also.

---

### Post by MatthewPlanchard on 2008-07-26
Hello Shrewsbury,

Welcome! You're now officially in Linux, so feel free to poke around, check out what's in where, and use anything that you think is interesting! We'll always be here to help if your run into trouble, which you may if you poke around too much! There's some nasty creatures tucked away in some of the deeper, darker places around here . . . of course, mostly you'll be up here where everything's breezy, easy, and well lit! I trust you won't run into too much trouble, and do remember all you need to do is ask and we will help you get yourself out of whatever mess you've gotten into.

Here's a few things to help get you started, now that you've finally arrived:

[Here]("http://www.psychocats.net/ubuntu/index") is psychocat's famous guide. It will teach you mostly everything you need to get comfortable and settled.

[This]("http://ubuntuforums.org/showthread.php?t=790485") is ZabiGG's *excellent* n00b guide to Ubuntu.

[Here]("http://ubuntuguide.org/wiki/Ubuntu:Hardy") you will find the official Ubuntu Hardy Heron (that's what we call our current version, of course) wiki, with information on pretty much anything you can think of.

Well that's just some basic information, but most of us find that the real joy of being here is taking off and exploring for yourself! You really never know what you'll find, and everyone who comes here has a completely different experience. You are welcome to stay as long as you like, and keep an open mind and an open ear. There are folks who have been around this place a lot longer than I have, and you never know what interesting stuff you might pick up along the way.

Good luck, and remember, you can always find us here if you need anything at all!

---

### Post by sandysandy on 2008-07-26
have a look at this link

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

also here is a thread on Free Linux and Ubuntu Books Online

[http://ubuntuforums.org/showthread.php?t=484846](http://ubuntuforums.org/showthread.php?t=484846)

regards

---

