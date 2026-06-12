---
title: "I'm taking a stand to invent MACE (Mac Environment for Linux)"
date: 2011-06-22
forum: Programming Talk
---

### Post by MrLinux2011 on 2011-06-22
I feel very bad for all of us who want to run mac os x programs on linux. That is why I am going to step up and try and invent the above program. I want it to be like WINE, except it uses mac os x programs.


Trouble is, I have little to no experience in coding (But I'll try to learn). I don't know where to begin. If you are going to talk about legality, don't please. There are many, many loyal mac users out there. Also, please do not bash me for not being experienced in coding.

If anyone wants to help, it would greatly be appreciated,


MrLinux2011

---

### Post by unknownPoster on 2011-06-22
Specifically what OS X applications are you wanting to run?

---

### Post by maddog39 on 2011-06-22
Well wine works by implementing a native linux version of the Windows API and then providing an executable which understands the windows EXE format to jump into and thus execute a windows program.

I'm really not familiar with the underlying systems in Mac OS other than it's unix and more specifically BSD-like. Taking into consideration that Linux is only unix-like, it has many of its own nuances and slight differentiations from the unix specification. That said, a few good starting points would be to look into how the FreeBSD guys implemented Linux binary compatibility in their system. Though this will be the exact opposite, BSD-like (presumably) binaries running on Linux, rather than the other way round.

Once you have figured that out, you will need to create an exact replica of the Mac OSX SDK, perhaps even parts of the SDK that are entirely undocumented. A good starting place for this would be the OpenStep project which is an open source implementation of NextStep on which Mac OSX is based.

If you can get somewhere on the first starting point, perhaps running only command line Mac executables on Linux, you will be in good shape.

---

### Post by MrLinux2011 on 2011-06-22
> **unknownPoster said:**
> Specifically what OS X applications are you wanting to run?

I wanted to check out Sonicworx by Prosoniq. That application is only for Mac.

---

### Post by MrLinux2011 on 2011-06-22
> **maddog39 said:**
> Well wine works by implementing a native linux version of the Windows API and then providing an executable which understands the windows EXE format to jump into and thus execute a windows program.

I'm really not familiar with the underlying systems in Mac OS other than it's unix and more specifically BSD-like. Taking into consideration that Linux is only unix-like, it has many of its own nuances and slight differentiations from the unix specification. That said, a few good starting points would be to look into how the FreeBSD guys implemented Linux binary compatibility in their system. Though this will be the exact opposite, BSD-like (presumably) binaries running on Linux, rather than the other way round.

Once you have figured that out, you will need to create an exact replica of the Mac OSX SDK, perhaps even parts of the SDK that are entirely undocumented. A good starting place for this would be the OpenStep project which is an open source implementation of NextStep on which Mac OSX is based.

If you can get somewhere on the first starting point, perhaps running only command line Mac executables on Linux, you will be in good shape.


Thank you for the advice.:D

---

### Post by cgroza on 2011-06-22
> **MrLinux2011 said:**
> Thank you for the advice.:D
Reach that kind of functionality and be sure many will join you in the effort.

---

### Post by MrLinux2011 on 2011-06-22
> **cgroza said:**
> Reach that kind of functionality and be sure many will join you in the effort.

That is what I am hoping for. It is time that linux users could run mac os x programs.

---

### Post by BkkBonanza on 2011-06-22
I've read that some users have successfully run OS X under VirtualBox. I haven't tried myself but recall reading some forums posts of people doing that. I recall it not being that easy but with fiddling it worked. 

I'd explore that before getting gung-ho on making a OS X - WINE equivalent since thats bound to be a massive undertaking. Look at how long it took WINE to become adequate, and how many people were involved, and it's a job for low-level systems programmers who really know how to write kernel level code. 

I still much prefer to run Windows under VirtualBox than use WINE and I suspect if OS X can be made to work that way, then it would be a more satisfactory experience.

Here's a link from google but I didn't read it thru - just something to consider, as it should work under Linux too.

[http://lifehacker.com/5583650/run-mac-os-x-in-virtualbox-on-windows](http://lifehacker.com/5583650/run-mac-os-x-in-virtualbox-on-windows)

---

### Post by slavik on 2011-06-23
> **unknownPoster said:**
> Specifically what OS X applications are you wanting to run?
I start with Steam, Source engine, WoW, Starcraft 2. In other words, anything that was developed for Mac OSX but not for Linux ... can you tell that I am a sad puppy?

---

