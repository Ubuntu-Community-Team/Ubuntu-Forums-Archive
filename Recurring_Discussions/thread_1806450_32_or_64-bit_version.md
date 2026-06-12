---
title: "32 or 64-bit version?"
date: 2011-07-17
forum: Recurring Discussions
---

### Post by User_ on 2011-07-17
Ok, so on the Ubuntu download site I am given the option of either choosing between the 32-bit and 64-bit versions of Ubuntu with the 32-bit one being marked as "recommended". Does this "recommended" tag play any important role on choosing the right version? In other words, does this mean that the 32-bit version is more stable than the 64-bit one? I am currently running Windows 7 (64-bit).

Thanks in advance.

---

### Post by danyc05 on 2011-07-17
If you are sure that your computer is a 64bit computer then get the 64bit. I had the same issue deciding which one to get and I just went with the 64bit and I havent really had any problems with it.

---

### Post by ikt on 2011-07-17
> **User_ said:**
> Does this "recommended" tag play any important role on choosing the right version?

Nope, it's just for your average user who is unaware what 32/64 bit are and are unsure if their pc is capable of running 64 bit, so 32 bit by default is the safer option for a lot of people.

Have been running 64 bit ubuntu since forever. :)

---

### Post by adempewolff on 2011-07-17
they are both equally stable in terms of the OS.  a few years ago it was a pain to make some commonly used programs (flash and java to name a few) work in the 64 bit version.  Nowadays these types of problems are more and more rare and the workaround for them are easier to find.

I would base your decision on how much RAM your system has.  If you have more than 4 GB of RAM, I would choose the 64 bit version so that you can fully utilize your ram.  Otherwise, the performance differences between the two are negligible for the normal user (as long as you are not an engineer using an expensive CAD or rendering program, etc.) and you could use the 32 bit version without ever noticing a difference.

---

### Post by User_ on 2011-07-17
Thanks everyone for your replies and yes I am sure that my computer is a 64-bit one. I am just going to go with the 64-bit.

---

### Post by User_ on 2011-07-17
> **adempewolff said:**
> they are both equally stable in terms of the OS.  a few years ago it was a pain to make some commonly used programs (flash and java to name a few) work in the 64 bit version.  Nowadays these types of problems are more and more rare and the workaround for them are easier to find.

I would base your decision on how much RAM your system has.  If you have **more than 4 GB of RAM**, I would choose the 64 bit version so that you can fully utilize your ram.  Otherwise, the performance differences between the two are negligible for the normal user (as long as you are not an engineer using an expensive CAD or rendering program, etc.) and you could use the 32 bit version without ever noticing a difference.


What if I have exactly 4GB?

---

### Post by jwbrase on 2011-07-17
> **User_ said:**
> What if I have exactly 4GB?

In *theory* 32-bit should allow you to access all of it.

In practice, 32-bit tends to not see a fairly large chunk of it (often half or three quarters of a gig, but I've heard of more than a gig not being recognized).

Even if you have less than 4 gig, I'd still generally say go with whatever is appropriate for your processor. (64-bit for 64-bit, 32-bit for 32-bit).

---

### Post by adempewolff on 2011-07-17
Well I think 2^32 addresses (the number of addresses that can be addressed by 32 bit programs) is actually a little smaller than how big 4 GB sticks actually work out to be.  But honestly, the difference is academic. Unless you are a performance user (heavy gamer, engineer, video editor, etc.) you will never notice the difference between 3.8 GB and 4GB.

If you are concerned with being on the bleeding edge and utilising every bit of memory/processing power, use the 64 bit.  I've been using it for years and only occasionally have to take some extra steps to make a program work.

---

### Post by ikt on 2011-07-17
> **adempewolff said:**
> Well I think 2^32 addresses (the number of addresses that can be address by 32 bit programs) is actually a little smaller than how big 4 GB sticks actually work out to be.  But honestly, the difference is academic. Unless you are a performance user (heavy gamer, engineer, video editor, etc.) you will never notice the difference between 3.8 GB and 4GB.

If you are concerned with being on the bleeding edge and utilising every bit of memory/processing power, use the 64 bit.  I've been using it for years and only occasionally have to take some extra steps to make a program work.

I go with the opposite, if your cpu supports 64 bit then use it! If you're stuck with a 32 bit limited cpu then :(

---

### Post by adempewolff on 2011-07-17
> **jwbrase said:**
> Even if you have less than 4 gig, I'd still generally say go with whatever is appropriate for your processor. (64-bit for 64-bit, 32-bit for 32-bit).

I'm pretty sure all modern processors are capable of running in 32-bit or 64-bit mode.  I could be wrong...

---

### Post by Dave_L on 2011-07-17
Are there any simple benchmark programs that I could run to compare the performance of the 32-bit and 64-bit Ubuntu editions?

(I installed phoronix-test-suite a while ago, but it looks intimidating and I haven't tried running it yet.)

---

### Post by uRock on 2011-07-17
I have 2 GB RAM and I use the 64bit Ubuntu without any issues. It is fast and makes me smile.:D

---

### Post by User_ on 2011-07-17
So, you suggest that I should use the version that better corresponds to my system's preferences?

> **uRock said:**
> I have 2 GB RAM and I use the 64bit Ubuntu without any issues. It is fast and makes me smile.:grin:

So the RAM really doesn't play any big part in this process..

---

### Post by adempewolff on 2011-07-17
Your system will run either version significantly faster than windows has ever run on that system.***

The 64-bit version will run slightly faster for some applications and will probably allow you to use slightly more of your memory.

However, if you use the 64-bit version, there is the possibility that you might occasionally run into a program that won't work--or, more likely, will need a little extra configuring to work in a 64-bit environment.

If you aren't afraid of every once in awhile having to do a little bit of troubleshooting/research to make something work, by all means use 64-bit.  I've been using it for almost as long as I have been using Ubuntu and it works great for me.


***with the possible exception of if you install 11.04 and your videocard is not up to using the new Unity interface

---

### Post by Paqman on 2011-07-17
> **adempewolff said:**
> I'm pretty sure all modern processors are capable of running in 32-bit or 64-bit mode.  I could be wrong...

Some of the Atoms from a couple of years ago were still 32-bit. A lot of netbooks, for example, are stuck with it.

But generally:
[LIST]
[*]If you have a 32-bit processor run 32-bit
[*]If you have a 64-bit processor, run 64-bit
[/LIST]
Simple, really :)

---

### Post by User_ on 2011-07-17
> **adempewolff said:**
> 
with the possible exception of if you install 11.04 and your videocard is not up to using the new Unity interface


Hmm.. And how do I figure that out?

---

### Post by adempewolff on 2011-07-17
What are you running now? Windows?  If so, you should be able to go into the device manager and find out what your video card is (or maybe just in "about this computer".  Once you find out your video card, google it to find more information.  As long as your video card supports 3d acceleration you should be fine.  Chances are, if your computer came with 4GB of RAM, it also came with a decent video card.

---

### Post by User_ on 2011-07-17
Ok, I will look into it. I think that's it. That's all I needed to know. 

Btw (a bit off-topic), what's up with all these threads about Ubuntu freezing at login screen when the ethernet is not plugged in? I got a bit concerned about that issue and I want to know more.

---

### Post by adempewolff on 2011-07-17
never experienced nor heard of it.  I suppose if ubuntu was configured as a workstation and wanted to login in through a network one might encounter that bug.  I doubt you'd encounter it as a normal user.

The best advice for making sure ubuntu will work for you is downloading an .iso burning a liveCD, and running it off of the liveCD before you install it.

There are very few things that will go wrong with a real installation if they work with the live cd (although there are a few things that will not work with the liveCD (without a bunch of configuring), but will work from a real installation--so don't lose hope if something doesn't work right away)

---

### Post by User_ on 2011-07-17
> **adempewolff said:**
> 
running it off of the liveCD before you install it.


Is this nessesary? I assume it is for testing purposes only.

---

### Post by wildmanne39 on 2011-07-17
> **User_ said:**
> Ok, I will look into it. I think that's it. That's all I needed to know. 

Btw (a bit off-topic), what's up with all these threads about Ubuntu freezing at login screen when the ethernet is not plugged in? I got a bit concerned about that issue and I want to know more.
Hi, that is a rare problem and is just being seen by a few people, it will most likely not effect you.

---

### Post by User_ on 2011-07-17
I see.. Thanks!

---

### Post by wildmanne39 on 2011-07-17
Your welcome!

---

### Post by adempewolff on 2011-07-17
> **User_ said:**
> Is this nessesary? I assume it is for testing purposes only.

No it's not neccesary, but--with Ubuntu at least--the installation cd and the liveCD are one and the same.  So, it's not too much effort to quickly try it out before the full install.  That said, if you are dead-set on using Ubuntu, even if it means fixing any problems that crop up, go ahead and skip booting from the liveCD before installing.

---

### Post by Swagman on 2011-07-18
If you choose to install the 32 bit version on 64 bit hardware you are then classed as a heretic

I am a heretic !!

Yes 64 bit does everything they are saying it does.. plus a few value added extra's... like glitches <-- on my hardware anyway !!

So what is my "unusual hardware" ?

Self build (as always)

Mobo:- Asus M4A87TD-Evo ,---AMD
Cpu: - AMD Phenom IIx4 (965 black edition)
Gpu: - nVidia GT8800 (512mb)
Ram: - 2x2gb corsair
HDD: - 1Tb sata2
Audio  Xonar D2x

sod it.. here's a pic

[[IMG]http://img809.imageshack.us/img809/9059/xonar.th.jpg[/IMG]](http://img809.imageshack.us/i/xonar.jpg/)

So.. Nothing unusual then !!

Now I was on 10:10 (32bit) and wanted to upgrade to 11:04 64 bit
My /Home is on a separate partition.
I fresh downloaded and checked md5 and burnt 3 cd's
11:04 both 32 & 64bit
Peppermint 64

Live booted Peppermint first... Very fast, looks great actually.. Everything worked from the Live environment

Boot 11:04 64
No Unity.. Ok.. That'll be down to no graphics drivers no doubt.

Go for install

Do NOT want updates as system is installing because it'll do that all over again when I switch the backports etc on when installed so **DON'T** tick that box

I also **DON'T** want the codecs installing as I'll do that myself anyway (U-R-E & flash-aid)

Installer bombs out !!

Try again

and again

and again

Burn Iso to USB stick and try again

and again

Last chance for 64 bit.. Tick "download updates whilst installing"

Success ????????????????????????????????

Ok.. Up & running on 11:04-64 

Install all the codecs... flash-aid

Hey.. It's working... Unity is a pain.. Missus hates it.. But if that's the way it's going we'd better get used to it.

But

Menus (Unity) keeps popping out then the screen flashes and kind of resets the desktop.. Freezing whilst it does it, sometimes for up to about 20 seconds.

Then hard freeze

sudo halt

Sod all

Finger of death ***k off !!

reboot... same issues

Bye bye 64 bit... I pondered good and hard about changing to Peppermint 64 but my missus knows Ubuntu and now has *some* experience of Unity so...

Install 11:04-32bit

No issues at all !!

Fancy that !!

---

### Post by overdrank on 2011-07-18
Moved to Recurring Discussions

---

### Post by Swagman on 2011-07-18
See what I mean !!

Topic is moved where it'll be poorly viewed.

As I said... I'm a heretic !!

---

### Post by uRock on 2011-07-18
> **Swagman said:**
> See what I mean !!

Topic is moved where it'll be poorly viewed.

As I said... I'm a heretic !!

This topic has been covered hundreds of times, therefore making it a "recurring" topic, not a "heretic" topic.

---

### Post by ikt on 2011-07-19
> **Swagman said:**
> Install 11:04-32bit

No issues at all !!

Fancy that !!

That sounds very odd to be honest, when the installer bombs are you still able to access the live cd or did it just completely freeze up?

Did you submit a bug report by any chance?

---

### Post by Swagman on 2011-07-19
> **ikt said:**
> That sounds very odd to be honest, when the installer bombs are you still able to access the live cd or did it just completely freeze up?

Did you submit a bug report by any chance?


No.. Requester just said the installer has failed. So I started the whole process again .. Reboot (Live Cd) try again & again etc

Lots of pop ups like this

[[IMG]http://img195.imageshack.us/img195/5351/nattyscreenshot.th.png[/IMG]](http://img195.imageshack.us/i/nattyscreenshot.png/)

Unfortunately I didn't bother screengrabbing the installer failed messages as I have heaps of Natty failures from previous attempts with 64 bit (just into June)

[[IMG]http://img823.imageshack.us/img823/7720/natty5screenshot.th.png[/IMG]](http://img823.imageshack.us/i/natty5screenshot.png/)

Sometimes it worked though.. lol

[[IMG]http://img703.imageshack.us/img703/4325/natty4screenshot.th.png[/IMG]](http://img703.imageshack.us/i/natty4screenshot.png/)


I actually told a bit of a porkie re: 32 bit working ok as I posted in General help an issue today but I appear to have resolved that

---

### Post by uRock on 2011-07-19
Sounds more like you had a bad cd image.

---

### Post by Swagman on 2011-07-19
Plural ?

And don't forget USB stick !!

---

### Post by vehemoth on 2011-07-19
Swagman: you could try it in classic mode or try the alt install.  The 64 bit version uses a bit more ram but I'm not sure how much.

---

### Post by wolfen69 on 2011-07-20
> **vehemoth said:**
> The 64 bit version uses a bit more ram but I'm not sure how much.

RAM is there to be used, not saved for a rainy day. I think it's funny that people get computers with 4gb+ of memory, then try and use as little as possible. <scratches head>

---

### Post by Swagman on 2011-07-20
Ok... got a confession to make.. It would appear that the issues I've been having are down to old bios firmware.. I'm not going to re-write it all out again so hear is a copy & paste from a post I made on our [**ISP's forum**](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473)


> 
I'm not sure if the issue has been resolved yet although a funny thing happened on the way to.....

 

I recently (clean) installed Ubuntu 11:04 (separate /Home partition) but have been getting random Firefox & Chromium crashes so I thought I'd boot into Windows 7.. (Which is extrememly dusty as it's only there for legacy purposes) and use the asus bios updater there (self build computer) which is, just for interest sake an M4A87TD-Evo. Obviuosly I had to wait eleventy billion years whilst the stupid virus definitions (avast) updated, then win updates (not bad for a naughty version huh !!).. Then a reboot need... But don't turn off computer yet.. more updates installing...bah!

 

Back into winblows and try the Asus updater again... But it didn't work .. so manually surf to Asus..

 

Anyway.. successfully updated Bios.. reboot into winodws again... wow.. Now my trackball works again (no.. I don't know why it packed up in Windows, I had to plug in a Ps/2 mouse to use ONLY in windows).

 

But...... ( the point of all this drivel)  No internet connections found !!

 

WTF ?

 

Go through it's "Make new connection hoo har only to be asked "whats my account [email]name@Btinernet.com[/email] and password"

 

eff orf... That info is NOT required just to setup a network connection to my router <--- what's that crock all about ?

People don't honestly enter that info do they ?

 

Anyway. I faffed about a bit before wondering whether the new bios switched off the onboard lan so I rebooted into bios (switched off the stupid expressgate & splash etc and checked settings.

 

Everything as it should be

 

Boot into Linux

 

No problems.. I'm still here as I'm listening to Jono-Bacons live vid-cast

 

[http://www.ustream.tv/channel/at-home-with-jono-bacon&#65279;](http://www.ustream.tv/channel/at-home-with-jono-bacon&#65279;)

 

So I dunno if the network connection in windows is still b0rked



So.. profuse apologies from me to whoever needs it as my machine has been stable since firmware update and most probably would've been on the 64 bit install as well.

---

### Post by Swagman on 2011-07-21
Good Morning. [posting this here temporarily]

Well... This issue has returned with a vengence. Previously it was only browser windows that would close randomly, now any window is !!

I couldn't even fire up synaptic, either from menus or cli


> 
[b]paul@Main-Computer:~$ sudo synaptic
[sudo] password for paul: 

** (synaptic:2330): CRITICAL **: launchpad_integration_add_items: assertion `GTK_IS_MENU (helpmenu)' failed
synaptic: rgmainwindow.cc:1501: void RGMainWindow::buildInterface(): Assertion `widget' failed.
paul@Main-Computer:~$ sudo dpkg --configure -a
paul@Main-Computer:~$ sudo synaptic
[/b]

I've got Synaptic up & running via cli, everything seems ok

**Syslog.1**
> 
Jul 20 15:18:07 Main-Computer kernel: [12986.407394] chromium-browse[2366]: segfault at b86b6f40 ip b5d83c5a sp bfd649c0 error 4 in chromium-browser[b4929000+2e02000]
Jul 20 15:41:42 Main-Computer kernel: [14402.192257] chromium-browse[5022]: segfault at 458c0006 ip b5728482 sp bfd65040 error 4 in chromium-browser[b4929000+2e02000]
Jul 20 15:56:30 Main-Computer kernel: [15289.523328] chromium-browse[5633]: segfault at bef43d0b ip b584d87d sp bfd65020 error 4 in chromium-browser[b4929000+2e02000]


Interesting bit No.2

> 
[b]
Jul 21 07:27:07 Main-Computer kernel: [    0.697425] pnp 00:0c: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Jul 21 07:27:07 Main-Computer kernel: [    0.697427] pnp 00:0c: disabling [mem 0x000c0000-0x000cffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Jul 21 07:27:07 Main-Computer kernel: [    0.697430] pnp 00:0c: disabling [mem 0x000e0000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Jul 21 07:27:07 Main-Computer kernel: [    0.697432] pnp 00:0c: disabling [mem 0x00100000-0xc7efffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Jul 21 07:27:07 Main-Computer kernel: [    0.697472] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved[/b]


Weird
> Jul 21 07:27:07 Main-Computer gdm-binary[1009]: WARNING: Unable to find users: no seat-id found

Weird 2

> Jul 21 07:27:07 Main-Computer kernel: [   10.680182] ioremap error for 0xc7e90000-0xc7e91000, requested 0x10, got 0x0


**KERN.LOG**


> 
Jul 21 07:33:56 Main-Computer kernel: [  419.299840] lsb_release[2266]: segfault at 4 ip 080f2d42 sp bfd29d84 error 6 in python2.7[8048000+1f0000]
Jul 21 07:36:11 Main-Computer kernel: [  554.884034] gnome-system-lo[2394]: segfault at 17171717 ip b6e3fd6e sp bf86334c error 4 in libc-2.13.so[b6e00000+15a000]
Jul 21 07:36:28 Main-Computer kernel: [  571.815270] boincmgr[2408]: segfault at 376bfb14 ip b75f8185 sp bfe089c0 error 4 in libwx_gtk2u_core-2.8.so.0.7.0[b7398000+302000]
Jul 21 07:36:38 Main-Computer kernel: [  581.956839] software-center[2345]: segfault at 978b0d8 ip 0810b9ff sp bfb1fa60 error 4 in python2.7[8048000+1f0000]


**Jockey.log**

> 
2011-07-21 07:49:49,209 DEBUG: nvidia_173 is not the alternative in use
2011-07-21 07:50:04,004 DEBUG: Shutting down
2011-07-21 10:21:19,580 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9dd4aec>
2011-07-21 10:21:20,617 DEBUG: reading modalias file /lib/modules/2.6.38-11-generic-pae/modules.alias
2011-07-21 10:21:20,696 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-07-21 10:21:20,696 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-07-21 10:21:20,754 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-07-21 10:21:20,771 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-07-21 10:21:20,771 DEBUG: Firmware for DVB cards not available
2011-07-21 10:21:20,771 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-07-21 10:21:20,774 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci


Additonal drivers shows driver (185?) is activated but not in use ?

Firefox crashes the most

---

### Post by uRock on 2011-07-21
The OP got his/her question answered.

Thread Closed.

---

