---
title: "Old computer"
date: 2015-11-05
forum: New to Ubuntu
---

### Post by dbarnowski on 2015-11-05
I have a geeze dunno 10+ year old computer P-4 2.5, 2 Gigs DDR 333, GeForce 6200. You guys think it will run Ubuntu or go with another flavor....

---

### Post by sudodus on 2015-11-05
The CPU and RAM are good enough to run Lubuntu and maybe also Xubuntu and Ubuntu Mate. These are flavours of Ubuntu with lighter desktop environments.

I'm not sure about the graphics card. Some old Geforce cards work, some are no longer supported. [Try several versions and also other linux distros ***live***](http://ubuntuforums.org/showthread.php?t=2230389), before you decide what to install.

See this link for more details: [Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by howefield on 2015-11-05
You might be restricted to the 32 bit version with that processor, but I think it would run, the question is how well ?

Should be easy enough to test with a live medium, although it is not quite the same as installed to the machine, it should give you an idea of how well it would work.

---

### Post by dbarnowski on 2015-11-05
Thnx guys forgot to mention that the GeForce has 528 Megs Ram..

---

### Post by grahammechanical on 2015-11-05
The Nvidia driver web site recommends Linux driver 352.55 for the GeForce GT 620. That is one of the newer Nvidia drivers. I am of the opinion that 528 MB graphic memory is the right side of borderline for Ubuntu's Unity 3D but not by much. Compare the user experience of Ubuntu with some of the other family members by using live sessions.

Regards.

---

### Post by rdb3 on 2015-11-05
I just recently installed Ubuntu 15.10 on my old Compaq Presario (about 7 + years) with 2 GB memory and a 120 GB hdd.  I installed it side-by-side with Windows 7.  It's been running great.
The Firefox default browser runs very fast.  I tried to install a chrome based browser and that one is not so fast.  I opened up a thread on that.  I like Ubuntu so far.  My ubuntu os is 32 bit. The ubuntu partition is 25 GB.

---

### Post by stalkingwolf on 2015-11-05
i just installed mate 13 on a very old dell 512 ram ( it has a cd and floppy )  and it worked fine. granted it is for a youngster that only plays educational games but everything workd when I finished.

---

### Post by leunam12 on 2015-11-05
have you considered upgrading the processor? I'm done dual-booting so I decided to install Windows 8 on an old Dell that had a P4 CPU and use a KVM switch to go from Ubuntu to Windows. But my point is that and I could take that P4 out and replace it with a dual core processor for just a few bucks. Worth a try, it works a lot better.

---

### Post by poorguy on 2015-11-08
> **leunam12 said:**
> have you considered upgrading the processor? I'm done dual-booting so I decided to install Windows 8 on an old Dell that had a P4 CPU and use a KVM switch to go from Ubuntu to Windows. But my point is that and I could take that P4 out and replace it with a dual core processor for just a few bucks. Worth a try, it works a lot better.


better check and make sure what socket your processor is first.
if you have an lga 775 socket it may or may not be possible to install a dual core processor. also make sure your bios will support the dual core processor you plan on installing.
best to check motherboard specs to see what processors are supported and also wat the processors FSB speed is.
if you have a socket 478 i don't believe that a dual core was ever produced for that socket.

good luck.

---

### Post by Sweet_Baby_Jamie on 2015-11-08
I have an old Dell that is fully integrated so you can't upgrade the processor without buying a whole new motherboard.  It has 512 MB of RAM and runs a Lubuntu re-spin called [LXLE]("http://lxle.net") "better than when it was brand new running Windows XP," according to my parents who handed it down to me.  This computer is older than me!  But it runs great on 12.04 32-bit.

---

### Post by Mike_Walsh on 2015-11-08
I'll get 'hounded' for this, but.....you could consider giving 'Puppy' Linux a try.

[http://puppylinux.com/index2.html](http://puppylinux.com/index2.html)

Loads entirely into RAM (which accounts for its astonishing speed). And even the newest releases only occupy around 200 MB. I use it on a 13-yr old Dell Inspiron lappie.....an original 1100. (Which, to be fair, has been upgraded  well beyond its original specs, this last couple of years). It runs a P4, and now has 1 GB of RAM.....and a PATA/IDE interface SSD. 

Runs great. Smooth, snappy.....and responsive.


Mike. ;)

---

### Post by Sweet_Baby_Jamie on 2015-11-09
@Mike_Walsh, Hi!  I have read that Puppy users always have to run as root, and that's supposedly a "high-risk" thing.  Is it true that the user always runs as root?

---

### Post by mastablasta on 2015-11-09
it is. but they have an article explaining why it is OK.

I've been running XP PC as root/admin for over 10 years. risky? yes, but I doubt that it would save me in windows XP to run as user.

anyway, back to puppy: [http://www.puppylinux.com/technical/root.htm](http://www.puppylinux.com/technical/root.htm)

there are other distros for old PCs such as AntiX or Slitaz or TinyCore.

---

### Post by jeffjohn2 on 2015-11-09
Stick with LUbuntu in my opinion; it is clean and stable.  I bought a Dell GX270 on ebay (for £8); upgraded memory to 2GB from scrap-box and installed SATA drive. Works flawlessly and fast enough.

---

### Post by Mike_Walsh on 2015-11-09
> **Sweet_Baby_Jamie said:**
> @Mike_Walsh, Hi!  I have read that Puppy users always have to run as root, and that's supposedly a "high-risk" thing.  Is it true that the user always runs as root?

Hi, Jamie.

Yes, that is absolutely correct. But, as mastablasta says, there is a well-documented article as to why it works OK. This one, to be precise (as mastablasta's link):-

[http://puppylinux.com/technical/root.htm](http://puppylinux.com/technical/root.htm)

But you don't **have **to run totally as root; there **is** the 'Spot' option, which allows all network access to be run in 'user-mode'.

I've been running various Pups for a couple of years now, alongside various of the 'buntus.....and have never had the slightest 'incident' with any of them. It's a great little lightweight distro for rejuvenating many an old, unloved 'puter. It just has a  rather unique way of running, that's all; but you'd be amazed at the number of XP 'refugees' we get..! I'd **thoroughly** recommend giving it a 'test run'.

Most 'Pups' are 'buntu-based, anyway....and the majority of these are 32-bit, which works better for 10+ yr old hardware; Tahrpup, the current release, is based on 'Trusty', and has access to most of the Ubuntu repositories. Of the remainder, many are Slackware-based. It's **no**t hard to get the hang of using it.....and the forum support is nothing short of amazing!

SliTaz is a nifty little thing, too; but it's not quite so easy to get everything working with it.....and the SliTaz forums are a bit patchy at the best of times. You may have to wait some time for a reply, too.....and the advice given is often conflicting. The forum has a total of just three admin staff & moderators.....and the user-base is **not** large.

AntiX is often recommended by many 'Puppians'; it's a solid, small, lightweight distro. 'Nuff said.

TinyCore I can't comment on, as I've never tried it.


Regards,

Mike. ;)

---

### Post by DuckHook on 2015-11-10
> **Mike_Walsh said:**
> TinyCore I can't comment on, as I've never tried it.Abolutely tiny, slick and fast as greased lightning, but not for everyone. It's window manager-based (FLTK); not desktop manager (not even as simple as LXLE). Moreover, it's got a hobbled shell (busybox); not a full-featured one like BASH. We are talking a bare-bones, stripped-down, almost-bare-naked rocket. Some people find the FLTK environment impossible. I sorta like it. It's charming, in a weird retro hobbled way. Something like a three-legged Puppy Linux.

@OP Like all Linuxes, it's free to try. If you don't like it, just nuke it. No harm, no foul. Experiment with it to see if it's right for you.

---

### Post by Sweet_Baby_Jamie on 2015-11-10
I started thinking about Puppy Linux after I got nicknamed [COLOR=#800080]"the puppy"[/COLOR] at school.  I thought I should put it on a jump drive and demonstrate it in computer class.  Just to exploit the nickname thing would be fun!

But now it's like, which Puppy Linux should I use?  I didn't know there were so many until I looked around the web researching it. It sure looks like easy fun though, and it would probably fly even faster than LXLE on this hand-me-down!  And using one of the Ubuntu-based ones sounds easy too.

---

### Post by Mike_Walsh on 2015-11-11
> **Sweet_Baby_Jamie said:**
> I started thinking about Puppy Linux after I got nicknamed [COLOR=#800080]"the puppy"[/COLOR] at school.  I thought I should put it on a jump drive and demonstrate it in computer class.  Just to exploit the nickname thing would be fun!

But now it's like, which Puppy Linux should I use?  I didn't know there were so many until I looked around the web researching it. It sure looks like easy fun though, and it would probably fly even faster than LXLE on this hand-me-down!  And using one of the Ubuntu-based ones sounds easy too.

Jamie, if you let me know what your specs are, I'll put my considering cap on and come up with a shortlist, if you like.

Alternatively, just head on over to the Puppy Forums, at

[http://www.murga-linux.com/puppy/index.php](http://www.murga-linux.com/puppy/index.php)

...join up (it's very easy), and ask on the beginner's forum. We can soon point you in the right direction.

It's certainly easiest to run Puppy from a flashdrive. Many of our members do, permanently. That way, you wouldn't have to mess around with your LXLE install at all.....unless you wanted to, of course. (You certainly sound more than capable..!)  This pre-supposes that your old 'puter will boot from USB, of course.

If not, don't worry; because of the nature of the 'frugal' install option, you can even run Puppy from **inside** LXLE, if necessary! And you'll find that the Grub4DOS bootloader config. tool that comes with every Puppy **as standard** is the easiest thing** ever** to use. There are many, many options..... :D

On top of all this, there's a staggering amount of software available for  the 'Pups'; we have an extremely active developer community, who excel at coming up with novel ideas & workarounds. Do give it a try; I can promise you, you **won't** regret it.

And above all else.....it's just plain fun!


Regards,

Mike. ;)

---

### Post by Al1000 on 2015-11-11
Jamie, FYI:

I have an old laptop which has 768MiB of RAM and I dual boot LXLE 12.04 and Lucid Puppy 5.2.8.6 (frugal) on it. I used to use Grub4Dos but switched to Grub2 some time ago; never could get the proper splash screen to display on LXLE booting with Grub4Dos.

Puppy uses slightly less RAM than LXLE, but slightly more CPU resources. Overall though, Puppy is slightly faster (because it's a tiny OS and loads entirely to RAM).

There are various things you can do with Puppy if you're concerned about security, such as make it not save sessions unless you want it to.

If you like messing around with Linux, you'll love Puppy. :)

---

### Post by Sweet_Baby_Jamie on 2015-11-11
Okay!  I downloaded Tahr Pup 6.0.2 CE and it boots from a USB stick perfectly!  I just played around a bit exploring, made an account on the Puppy forums and stuff.  Running Puppy from the USB key is just a little faster speed-wise than running LXLE installed.  I bet it's faster installed to the HDD, huh?

Anyway I'm going to get to know this Puppy so I can show it off at the computer club at school... and just make the most of that nickname they gave me.  I'm tiny for a 14-year-old on the first day of school this bunch of girls were like, "Oh, look, a little lost puppy!  Isn't he adorable?"  :confused:  I don't know if that's good or not... I'd rather be "sexy" than "adorable" but the nickname stuck because a bunch of upperclass guys were like, "Can we keep him?" and "Wonder if he's housebroken."  :mad:

Since I have to be "the puppy" then, I may as well make the most of it!  Bringing Puppy to school would show I'm a good sport, anyway I guess.

---

### Post by Al1000 on 2015-11-11
> Okay!  I downloaded Tahr Pup 6.0.2 CE and it boots from a USB stick perfectly!

Cool!

> I bet it's faster installed to the HDD, huh?

Only to boot up and shut down. Once up and running it should be the same, since Puppy loads to and runs entirely from RAM, regardless of whether it's on a USB, HDD, CD or whatever. For example, if you use Puppy on a CD, you can remove the CD from the drive after Puppy boots up.

> I don't know if that's good or not...

Yeah, that's good. ;)

---

### Post by nebojsa6 on 2015-11-11
I have a same question,so I'm going to ask it here without rising new thread. I have Toshiba L500D-16k which contains AMD Turion II Dual-Core 500 processor@2.2GHz,4GB RM and ATI Radeon HD 4650 graphical card. Which version of Ubuntu do you recommend?

---

### Post by Mike_Walsh on 2015-11-11
Hey, Jamie.

Good for you! I wasn't exactly the 'runt of the litter' when I was young.....but I've always been the 'black sheep' of our family! :lol:

You'll find Puppy extremely easy to use; Tahrpup especially so, since it uses a newer kernel than Trusty; hasn't got the wi-fi issues for a start. And yes, you're right; they are faster installed to the hard drive.....but not by that much; Puppy's 'working speed' is largely dictated by your CPU speed, and the speed of your RAM.

You should have a lot of fun with it, anyway. Any questions, look me up on the Puppy Forums.....my username is the same.

Enjoy!


Regards,

Mike. ;)

---

### Post by mastablasta on 2015-11-12
> **nebojsa6 said:**
> I have a same question,so I'm going to ask it here without rising new thread. I have Toshiba L500D-16k which contains AMD Turion II Dual-Core 500 processor@2.2GHz,4GB RM and ATI Radeon HD 4650 graphical card. Which version of Ubuntu do you recommend?


you can use anyone you want. try them out see which one works best for you. I would use Kubuntu on that PC, but default Ubuntu is not that bad once you get used to Unity. the GPU should be well supported by opensource drivers.

---

### Post by nebojsa6 on 2015-11-12
> **mastablasta said:**
> you can use anyone you want. try them out see which one works best for you. I would use Kubuntu on that PC, but default Ubuntu is not that bad once you get used to Unity. the GPU should be well supported by opensource drivers.

I was wondering if I can successfully use Ubuntu 12.04.5 LTS,that one could be less resource-hungry for my Toshiba. I will try that one today and keep posted with results. Thank you for your reply.

---

### Post by howefield on 2015-11-12
> **nebojsa6 said:**
> I was wondering if I can successfully use Ubuntu 12.04.5 LTS,that one could be less resource-hungry for my Toshiba. I will try that one today and keep posted with results. Thank you for your reply.

The last version to include Unity 2D, which if I recall correctly, the system will default to if it can't run the 3D version.

---

### Post by mastablasta on 2015-11-12
> **nebojsa6 said:**
> I was wondering if I can successfully use Ubuntu 12.04.5 LTS,that one could be less resource-hungry for my Toshiba. I will try that one today and keep posted with results. Thank you for your reply.

it should be able to run there. 

but if you want less resources take by desktop there are alternatives on 14.04 or even latest 15.10 - look at Ubuntu Mate, Xubuntu. Lubuntu (they are all on 2D deskotps, well mate can have 2D or 3D i think) or just windows managers one can install...

it is however not necessary you would use that much more resources with newer version than with the older one. the question is more how well is the GPU and other hardware supported. and what features are there in newer versions that would make you move form the old one. Personally I stick to LTS editions.

---

### Post by nebojsa6 on 2015-11-12
Just installed it and it works well for me. I have just one problem,and that would be a processor temperature which is too high in my opinion. I had same problem in Windows dists,but temperature was not this high. Anyone having same problem?

---

### Post by poorguy on 2015-11-13
yeah well i just installed tahr pup 6.0 on an emachines T3092 from 2004 and it runs good.
amd athlon xp 3000+ ( 2167 mhz ) / 2.0 gb ddr memory / nvidia fx 5200 8x agp graphics card / 20 gb hard drive.
so far so good / it is very different though.

---

### Post by sudodus on 2015-11-13
Maybe you would like to try ToriOS, which is a re-spin based on 12.04 LTS. You can make a regular installed system, and you can use program packages from the regular Ubuntu repositories. See the following link

[ToriOS - ultra-light distro based on Ubuntu and the window manager JWM](http://ubuntuforums.org/showthread.php?t=2302798)

---

### Post by poorguy on 2015-11-13
> **sudodus said:**
> Maybe you would like to try ToriOS, which is a re-spin based on 12.04 LTS. You can make a regular installed system, and you can use program packages from the regular Ubuntu repositories. See the following link

[ToriOS - ultra-light distro based on Ubuntu and the window manager JWM]("http://ubuntuforums.org/showthread.php?t=2302798")

hey sudodus,

we meet again. i will look in to that as i am really liking tahrpup. it took me a few tries to get it installed right but they say the third time is the one. really runs good on this old desktop and doesn't seem to have a lot of useless crapola in it. another plus was it fit with room to spare on this big ole 20gb hard drive. WOW! i'm liking these lite distros as they are very functional for my PC needs. yeah i am going to check out ToriOS.

life is good.
the poorguy

---

### Post by Sweet_Baby_Jamie on 2015-11-13
The "latest" ToriOS is the daily build, I assume.  I'm enjoying Puppy alot and kinda getting to know JWM.  So a "JWMbuntu" sounds like alot of fun!

---

### Post by Mike_Walsh on 2015-11-13
> **sudodus said:**
> Maybe you would like to try ToriOS, which is a re-spin based on 12.04 LTS. You can make a regular installed system, and you can use program packages from the regular Ubuntu repositories. See the following link

[ToriOS - ultra-light distro based on Ubuntu and the window manager JWM]("http://ubuntuforums.org/showthread.php?t=2302798")

Hi, sudodus.

poorguy might have problems even with ToriOS on his hardware. His problem stems from the lack of SSE2's; and his CPU can't be upgraded to one that does. That's why I suggested he try Puppy; many of our members run it on Pentium 3's....which are also blessed (cursed?) with a lack of SSE2's.

He doesn't have full functionality even in Lubuntu because of this. I've a feeling this might apply to any spins based on Ubuntu, too....even 12.04.5. I've given a brief explanation of the Puppy build process, [here]("http://ubuntuforums.org/showthread.php?t=2302489&page=3&p=13390529&viewfull=1#post13390529").

It can't hurt to try, though..!


Regards,

Mike. ;)

---

### Post by sudodus on 2015-11-14
> **Mike_Walsh said:**
> Hi, sudodus.

poorguy might have problems even with ToriOS on his hardware. His problem stems from the lack of SSE2's; and his CPU can't be upgraded to one that does. That's why I suggested he try Puppy; many of our members run it on Pentium 3's....which are also blessed (cursed?) with a lack of SSE2's.

He doesn't have full functionality even in Lubuntu because of this. I've a feeling this might apply to any spins based on Ubuntu, too....even 12.04.5. I've given a brief explanation of the Puppy build process, [here]("http://ubuntuforums.org/showthread.php?t=2302489&page=3&p=13390529&viewfull=1#post13390529").

It can't hurt to try, though..!


Regards,

Mike. ;)

You are right about that computer. But he wrote about another[ 'not quite that old' computer](http://ubuntuforums.org/showthread.php?t=2294828&page=2&p=13382930#post13382930), where it might work well, and a [whole bunch of them here](http://ubuntuforums.org/showthread.php?t=2294828&page=4&p=13387251#post13387251) :-)

---

### Post by sudodus on 2015-11-14
> **Sweet_Baby_Jamie said:**
> The "latest" ToriOS is the daily build, I assume.  I'm enjoying Puppy alot and kinda getting to know JWM.  So a "JWMbuntu" sounds like alot of fun!

Yes, The "latest" ToriOS is the daily build :-)

---

### Post by mastablasta on 2015-11-14
> **nebojsa6 said:**
> Just installed it and it works well for me. I have just one problem,and that would be a processor temperature which is too high in my opinion. I had same problem in Windows dists,but temperature was not this high. Anyone having same problem?

it could be the GPU that heats up. i believe 3xxx and newer series have a drm switch or something like that in opensource drivers that should enable power management.

to monitor temperature and see what is heating up and how much you can use Psensor: [http://wpitchoune.net/blog/psensor/](http://wpitchoune.net/blog/psensor/)
i think it is a nice frontend to lm-sensors.

---

### Post by nebojsa6 on 2015-11-14
> **mastablasta said:**
> it could be the GPU that heats up. i believe 3xxx and newer series have a drm switch or something like that in opensource drivers that should enable power management.

to monitor temperature and see what is heating up and how much you can use Psensor: [http://wpitchoune.net/blog/psensor/](http://wpitchoune.net/blog/psensor/)
i think it is a nice frontend to lm-sensors.

Yes I'm using that program,and it says temp1 is 55 C doing nothing at all to 69 C when I'm watching a movie,for me that's too high. What I don't know is if that's processor temp or GPU temp.

---

### Post by poorguy on 2015-11-14
> **nebojsa6 said:**
> Yes I'm using that program,and it says temp1 is 55 C doing nothing at all to 69 C when I'm watching a movie,for me that's too high. What I don't know is if that's processor temp or GPU temp.

is your problem with a laptop.
your temps aren't that bad.

the poorguy

---

### Post by poorguy on 2015-11-14
hey nebojsa6,

if it is a laptop use a cooler or raise it off the surface you have it sitting on for more airflow. also make sure your vent openings are free and clear from dust by using compressed air to clean them.
if it is not locking up or shutting down i wouldn't worry to much as mobile processors are made to handle a higher operating temp as they are in such a tight area.

just some thoughts.

the poorguy

---

### Post by mastablasta on 2015-11-15
> **nebojsa6 said:**
> Yes I'm using that program,and it says temp1 is 55 C doing nothing at all to 69 C when I'm watching a movie,for me that's too high. What I don't know is if that's processor temp or GPU temp.

temp1 is either motherboard or GPU. CPU is "core".

check under power management here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

its's DPM not DMR. LOL. anyway try it first in grub menu before making it permanent.

---

### Post by nebojsa6 on 2015-11-15
> **poorguy said:**
> hey nebojsa6,

if it is a laptop use a cooler or raise it off the surface you have it sitting on for more airflow. also make sure your vent openings are free and clear from dust by using compressed air to clean them.
if it is not locking up or shutting down i wouldn't worry to much as mobile processors are made to handle a higher operating temp as they are in such a tight area.

just some thoughts.

the poorguy

well yes he has not been cleaned for a while but that should not be a reason for a high temps. i'm going to doing soon anayway.

> **mastablasta said:**
> temp1 is either motherboard or GPU. CPU is "core".

check under power management here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

its's DPM not DMR. LOL. anyway try it first in grub menu before making it permanent.

seems like temp1 is actually gpu temp,so it's not that high,I was too panic about it. but how to check cpu temp,any idea which program I should use?

---

### Post by mastablasta on 2015-11-16
psensor should show the temp. of CPU

If you do not see it them check package lm-sensors. i forgot but i think you need to run something to actifvate the senors and tell them what to scan for.

also in a bit dumb way - if it feels hot reboot immediatelly and go to BIOS to see the current CPU temp. :)

---

### Post by poorguy on 2015-11-16
i would use xsensors as it runs after install most of the time.

cooling vents blocked up with dust will cause higher temps as there is a lack of good airflow.

anyway try out xsensors it can be installed through synaptic package manager or the software center.

life is good.
the poorguy

---

