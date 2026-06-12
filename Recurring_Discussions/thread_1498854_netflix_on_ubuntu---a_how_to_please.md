---
title: "netflix on ubuntu---a how to please"
date: 2010-06-01
forum: Recurring Discussions
---

### Post by chookinator on 2010-06-01
hi everyone.
 
I am new to ubuntu and my friend just gave me a free month of netflix---which i obviously cannot watch with ubuntu.  Any help would be appreciated.  I know windows can run through a virtual player, but i am not computer saavy and need some walk through instructions...
 
thanks!:KS

---

### Post by yamfox on 2010-06-01
Go to a terminal, type:
```
sudo apt-get install wine
```
Then download the windows versions of [firefox]("http://mirrors.ircam.fr/pub/mozilla//firefox/releases/3.6.3/win32/en-US/Firefox%20Setup%203.6.3.exe") and  [silverlight]("http://download.microsoft.com/download/2/2/C/22CABA89-3580-4611-8E0D-56749D2120DF/runtime/Silverlight.exe").
Go to where they were downloaded, right-click on them, go to the third tab, and enable "using as an executable". After you do that to each, right click on each and run with wine. Install them as you would on windows. After that is done, go to Applications>Wine>Program Files and run firefox. Watch netfilx as normal.

---

### Post by aysiu on 2010-06-01
> **yamfox said:**
> Go to a terminal, type:
```
sudo apt-get install wine
```
Then download the windows versions of firefox and silverlight.
Go to where they were downloaded, right-click on them, go to the third tab, and enable "using as an executable". After you do that to each, right click on each and run with wine. Install them as you would on windows. After that is done, go to Applications>Wine>Program Files and run firefox. Watch netfilx as normal.
Netflix does not run in Wine.

If you want Netflix streaming there are several options:
1. Use Windows
2. Use Mac OS X
3. Use Wii
4. Use PS3
5. Use an iPad

---

### Post by Groucho Marxist on 2010-06-13
> **aysiu said:**
> Netflix does not run in Wine.

If you want Netflix streaming there are several options:
1. Use Windows
2. Use Mac OS X
3. Use Wii
4. Use PS3
5. Use an iPad

I have recently discovered that Netflix is also available on Xbox 360 for those who own said peripheral.

---

### Post by kkaldroma on 2010-11-07
Virtual Box.

Install a windows XP VM and stick it in a low graphics mode with nothing on it. This will allow it to boot up in 20-30 seconds instead of the customary Microsoft 8 minutes.

Install silver-light on that and enable 2D / 3D acceleration through the VM.

You can easily watch Netflix that way. Just don't do anything else on your machine while you are trying to watch movies or Netflix goes all Wonky because your "CPU usage" on the VM just jumped to 99% and Netflix will keep trying to slow their stream.

That is what I do.

Additional:
Yes installing a VM with XP is a terrible way to make this work but thanks to the "license agreements" that netflix has with various companies who are partners with or flat out owned by MS it is the only way.
The Roku IS LINUX so we all know nix is completely capable of receiving netflix. It's a money thing. Get a lawyer or work around it.

---

### Post by linuxford on 2010-11-07
They now have an Iphone app as well.

---

### Post by diablo75 on 2010-11-07
I'm of the PS3 persuasion when it comes to Netflix.  It's snappy, doesn't require a disc anymore, provides streams in 5.1 surround sound with HD quality video; it's just far simpler to use Netflix when you have the PS3 working as a fantastic hardware platform that can hook up to anything that accepts an HDMI cable.  No fiddling around with obscure, experimental software, or even "supported" software plugins for a web browser.  If you don't want to spend money on a PS3, there are stand-alone players that do streaming video, including Netflix and Hulu-Plus, among others and they start around $60.  Netflix belongs on a TV screen and you belong on a couch when you watch it... imho.

---

### Post by uRock on 2010-11-07
I have heard a lot of people say that Netflix doesn't work in Windows VMs. I will have to give it a try soon.

Moved to Recurring Discussions.

---

### Post by zefew on 2010-11-07
I don't understand why other linux users suggest using netflix with wii or ps3 or other netflix-compatible consoles with a TV set. This thread is about using netflix *on* linux. 

The easiest (and flawless) way of course is to use VirtualBox and install Windows XP on it. If you have an OS cd, it won't cost you a dime. Believe me, it just runs perfectly and is pretty fast.

---

### Post by uRock on 2010-11-07
Many people connect their PCs to their home theater, which is why they want to run Netflix on it. As soon as Netflix sent me a Wii disk I stopped bothering with it via the PC.

As for laptop users, I doubt running a VBox is worth it either. One good reason to keep that Windows install on Laptops and dual boot them. That's what I do.

---

### Post by zefew on 2010-11-07
> **yamfox said:**
> Go to a terminal, type:
```
sudo apt-get install wine
```
Then download the windows versions of [firefox]("http://mirrors.ircam.fr/pub/mozilla//firefox/releases/3.6.3/win32/en-US/Firefox%20Setup%203.6.3.exe") and  [silverlight]("http://download.microsoft.com/download/2/2/C/22CABA89-3580-4611-8E0D-56749D2120DF/runtime/Silverlight.exe").
Go to where they were downloaded, right-click on them, go to the third tab, and enable "using as an executable". After you do that to each, right click on each and run with wine. Install them as you would on windows. After that is done, go to Applications>Wine>Program Files and run firefox. Watch netfilx as normal.

Did you try it yourself and succeed in watching netflix streaming? If this works without any problem, it would reign as the most recommended method for watching netflix on linux.

---

### Post by zefew on 2010-11-07
> **uRock said:**
> As for laptop users, I doubt running a VBox is worth it either. One good reason to keep that Windows install on Laptops and dual boot them. That's what I do.

There is no doubt. It *is* worth it, provided the resolution is good enough.
I watch netflix streaming all the time on my Ubuntu laptop while working on other coding projects. VirtualBox has a plugin that lets you control Windows XP seamlessly. WUXGA, the resolution on my laptop, is large enough to yield more than several viewable window areas.

---

### Post by uRock on 2010-11-07
> **zefew said:**
> There is no doubt. It *is* worth it, provided the resolution is good enough.
I watch netflix streaming all the time on my Ubuntu laptop while working on other coding projects. VirtualBox has a plugin that lets you control Windows XP seamlessly. WUXGA, the resolution on my laptop, is large enough to yield more than several viewable window areas.

Cool.[IMG]http://www.mikesplanet.net/forums/images/smilies/cool.png[/IMG]

---

### Post by forrestcupp on 2010-11-07
> **Groucho Marxist said:**
> I have recently discovered that Netflix is also available on Xbox 360 for those who own said peripheral.

But only if you pay for a Gold membership to Xbox Live.  That's all I would use Live for, so I can't see paying twice for Netflix.

---

### Post by diablo75 on 2010-11-07
> **zefew said:**
> I don't understand why other linux users suggest using netflix with wii or ps3 or other netflix-compatible consoles with a TV set. This thread is about using netflix *on* linux. 

The easiest (and flawless) way of course is to use VirtualBox and install Windows XP on it. If you have an OS cd, it won't cost you a dime. Believe me, it just runs perfectly and is pretty fast.

It's a lifestyle issue and I personally have a very "zen" notion of what "easy" should be.  I just happen to have an HDTV and a game console.  Lots of people do, but some don't so I can appreciate *their* desire to run Netflix on a computer/laptop if it's their only option and don't want to spend money.  I just like to make sure people are aware of the option to enjoy it on something that was made/built for the specific purpose of home entertainment.

---

### Post by aysiu on 2010-11-07
Running Netflix in VirtualBox Windows is **not** "using netflix *on* Linux." It's using Netflix in Windows.

You can't use Netflix on Linux, which is why some people suggest Windows in VirtualBox and others suggest Wii or PS3.

---

### Post by steve7777777 on 2011-01-02
> **aysiu said:**
> Running Netflix in VirtualBox Windows is **not** "using netflix *on* Linux." It's using Netflix in Windows.

You can't use Netflix on Linux, which is why some people suggest Windows in VirtualBox and others suggest Wii or PS3.

True. I needed to stream Netflix on my Ubuntu HTPC and Virtualbox was the best solution. I had a spare copy of Vista 32bit lying around - never thought I'd use it for anything. Turns out it works great in Virtualbox  under Ubuntu :)

---

### Post by SunnyRabbiera on 2011-01-02
> **zefew said:**
> Did you try it yourself and succeed in watching netflix streaming? If this works without any problem, it would reign as the most recommended method for watching netflix on linux.

It does not work as the latest silverlight is not compatible with wine.

---

### Post by Duplin on 2011-01-04
Hi, a question. If I buy a Roku box will it output my monitor, or must I watch Netflix on a TV? I had rather watch the movies on my monitor rather than my old TV. Thanks for any help.

---

### Post by zccrx91 on 2012-01-05
So what you are saying is there is no way to watch netflix on ubuntu?

---

### Post by aysiu on 2012-01-05
> **zccrx91 said:**
> So what you are saying is there is no way to watch netflix on ubuntu?
Yes.

Unless by "on Ubuntu" you mean "in Windows virtualized inside Ubuntu" or "in Windows dual-booting with Ubuntu."

---

### Post by diablo75 on 2012-01-06
> **zccrx91 said:**
> So what you are saying is there is no way to watch netflix on ubuntu?

Unfortunately, no.  This is the choice made by Netflix; to use a proprietary delivery platform that has no native version available on Linux.  Perhaps this will change someday in the future.  You would think it wouldn't be so hard for such an advent to occur considering the existence of an Android native version of it being available already.

---

