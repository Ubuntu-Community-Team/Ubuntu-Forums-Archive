---
title: "OpenGL and DirectX"
date: 2012-05-23
forum: Recurring Discussions
---

### Post by rasmus91 on 2012-05-23
Hello everyone.

I am a gamer, i have a highend desktop computer i use for gaming, i, however also have this laptop that i use with Ubuntu only. It has always been a mystery to me why there are so many games that do not use OpenGL, but only DirectX.

I understand why Microsoft created it, thats not hard. But i would like to know some of the pros and cons for each. OpenGL is obviously supported on multiple platforms. but other than that im really not all that sure about it. Why does people create their games for DirectX and not OpenGL? wouldn't it be easier to port games if they used OpenGL?

Im a student on Aalborg university, planning to soon start creating the Design document of a game that will be my first RPG (and real computer game) ever created. It will most likely take a long time, as it will be a spare time project. and i would like it to run on my laptop, that is, in Ubuntu.

But say i wanted it to run in windows only, what should i choose, DirectX or OpenGL?

(i know this may not sound very promising, but I'm a quick learner, and only in the beginning of my time here. As i progress with this project i will learn all the things i need to, to make this possible, i might as well add that this is no promise of a free game, not because the game wouldn't be free, but because i am not of the timeframe, or if it will ever be released. if it will be released, it will probably be under some Open Source License to give something back to the community)

---

### Post by roelforg on 2012-05-23
In windows?
DirectX
Because it can take advantage of the "undocumented" api's in the kernel and it'll be updated to support a new win32 api before the api even releases (courtesy of microsoft being behind it), making it always on the bleading edge.
Projects like OpenGL need some time to get a new api implemented and tested, in the mean time people want games that can take full advantage of their system.
It's a logical choice:
More time before new api's/win versions supported = fall behind the rest and lose customers.
Lose a few customers vs. please the users of a minority OS (Linux is still in the minority on the desktop)
And mac osx is so locked down that you need to give a big chunk of your profits to apple to make a game even run on the os! This would impact the profits big time.
It's all about economics

---

### Post by Mikeb85 on 2012-05-23
While Microsoft does make it easy and attractive to use DirectX, OpenGL has plenty of great features (equivalent to the newest DirectX), and in my experience, runs better.  But it does come down to economics - Microsoft provides some great developer tools, and makes it easy to develop for PC/Xbox at the same time, much more easily than for OSX/Linux...

---

### Post by roelforg on 2012-05-23
> **Mikeb85 said:**
> While Microsoft does make it easy and attractive to use DirectX, OpenGL has plenty of great features (equivalent to the newest DirectX), and in my experience, runs better. But it does come down to economics - Microsoft provides some great developer tools, and makes it easy to develop for PC/Xbox at the same time, much more easily than for OSX/Linux...
 
In addition to the fact that companies want to make the most money,
it's the best for the profit to please the biggest group and those are the people on Win/XBox.

---

### Post by Mikeb85 on 2012-05-23
> **roelforg said:**
> In addition to the fact that companies want to make the most money,
it's the best for the profit to please the biggest group and those are the people on Win/XBox.

Yes, it is.  Although, if you're small, pleasing the niche markets can make you a decent sum of money, as you'll get much more attention, albeit from a smaller market.  Look at a game like Oil Rush - it gets 100x more attention from the Linux community than from the Windows community.

---

### Post by roelforg on 2012-05-23
> **Mikeb85 said:**
> Yes, it is. Although, if you're small, pleasing the niche markets can make you a decent sum of money, as you'll get much more attention, albeit from a smaller market. Look at a game like Oil Rush - it gets 100x more attention from the Linux community than from the Windows community.
 
It can make you good money...
If you know where they're the largest and sell your game there, because w/o buyers you could please the most profitable niche with the best product but still don't make a single buck.

---

### Post by forrestcupp on 2012-05-23
A lot of people who ask about this don't really know what DirectX is. OpenGL is only for graphics. DirectX is for graphics, input devices, and 3D/2D audio. If you use OpenGL, you have to find libraries for everything else, too. If you use DirectX, you get everything you need all in one. The different parts of DirectX all work together, making it much easier than using separate libraries that weren't necessarily created to work together. For instance, in DX, if you have an object in your 3D space, it's easy to link that object's 3D audio in the same 3D space. OpenGL just gives you the graphics.

A better comparison to OpenGL would be Direct3D, which is only one part of DirectX. If I were developing a game geared toward Windows, and even all the modern game consoles, I'd use DirectX, too. It's not really worth it to use OpenGL, unless you're specifically developing for Linux. Even the new Wii U will support DirectX 11.

---

### Post by mips on 2012-05-23
It's easier to create games in directx seeing it incorporates video & sound. OpenGL is lacking in this department.

If OpenGL was better &easier to use then developers would use it.

---

### Post by rasmus91 on 2012-05-23
> A better comparison to OpenGL would be Direct3D, which is only one part of DirectX. If I were developing a game geared toward Windows, and even all the modern game consoles, I'd use DirectX, too. It's not really worth it to use OpenGL, unless you're specifically developing for Linux. Even the new Wii U will support DirectX 11.

i find this to be creepy at best. Damn, i wish I or someone else would come up with a solution that tramples DirectX i actually already knew it was used for sound as well as other inputs and stuff, but i didn't think about it when i made this thread.

That however also narrows my question a bit as i am mostly interested in the graphics part.

I have no intention of making a windows only game, as the only thing windows has ever really given me is lots of headaches.

The initial plan is to make the game cross platform, but develop it on Linux. as i will receive help from some of my buddies here, that use windows, it will probably be ported to that as well. The plan is, assuming that we make it that, far to release the code for the game as open source, but at the same time make it easy to mod the game. these are nothing but ambitions and dreams right now, but i hope they will start to take form soon enough. summed up, my plan is just to give any other people who likes developing games and mods, something very nice to work with. in the sense that it will be a fully functioning game, that will be open for editing by the community. I do not plan on earning any money on this, for me the purpose will be to learn, and giveback to the community, and hopefully the game will be put into the Ubuntu software center before 2020 :P

---

### Post by sffvba[e0rt on 2012-05-23
*Thread moved to **Recurring Discussions**.*

... been ages since I saw this debate ... 


404

---

### Post by MG&amp;TL on 2012-05-23
> **rasmus91 said:**
> i find this to be creepy at best. Damn, i wish I or someone else would come up with a solution that tramples DirectX i actually already knew it was used for sound as well as other inputs and stuff, but i didn't think about it when i made this thread.

That however also narrows my question a bit as i am mostly interested in the graphics part.

I have no intention of making a windows only game, as the only thing windows has ever really given me is lots of headaches.

The initial plan is to make the game cross platform, but develop it on Linux. as i will receive help from some of my buddies here, that use windows, it will probably be ported to that as well. The plan is, assuming that we make it that, far to release the code for the game as open source, but at the same time make it easy to mod the game. these are nothing but ambitions and dreams right now, but i hope they will start to take form soon enough. summed up, my plan is just to give any other people who likes developing games and mods, something very nice to work with. in the sense that it will be a fully functioning game, that will be open for editing by the community. I do not plan on earning any money on this, for me the purpose will be to learn, and giveback to the community, and hopefully the game will be put into the Ubuntu software center before 2020 :P

If you want to make a game, I wouldn't suggest using OpenGL directly. Use something like Ogre3D. Just as fast, and much easier to use. Haven't come across any problems using it with the demos.

---

### Post by roelforg on 2012-05-23
> **rasmus91 said:**
> i find this to be creepy at best. Damn, i wish i or someone else would come up with a solution that tramples directx i actually already knew it was used for sound as well as other inputs and stuff, but i didn't think about it when i made this thread.
 
That however also narrows my question a bit as i am mostly interested in the graphics part.
 
I have no intention of making a windows only game, as the only thing windows has ever really given me is lots of headaches.
 
The initial plan is to make the game cross platform, but develop it on linux. As i will receive help from some of my buddies here, that use windows, it will probably be ported to that as well. The plan is, assuming that we make it that, far to release the code for the game as open source, but at the same time make it easy to mod the game. These are nothing but ambitions and dreams right now, but i hope they will start to take form soon enough. Summed up, my plan is just to give any other people who likes developing games and mods, something very nice to work with. In the sense that it will be a fully functioning game, that will be open for editing by the community. I do not plan on earning any money on this, for me the purpose will be to learn, and giveback to the community, and hopefully the game will be put into the ubuntu software center before 2020 :p
 
sdl?

---

### Post by forrestcupp on 2012-05-23
> **MG&TL said:**
> If you want to make a game, I wouldn't suggest using OpenGL directly. Use something like Ogre3D. Just as fast, and much easier to use. Haven't come across any problems using it with the demos.

That's exactly what I was going to say. Another good 3D engine that is cross platform is Irrlicht. 3D/Game engines are much easier to use than straight OpenGL or DirectX. Most game companies use commercial game engines, like the Unreal, Crysis and Source engines. Irrlicht and Ogre3D are a couple of good free, cross platform 3D engines. Irrlicht is a little easier to use than Ogre3D, and you can use a lot more content filetypes. They're both pretty good quality, though. There are other good libraries for audio and physics that connect pretty well with those 3D engines. Irrlicht includes basic gravity, but no physics beyond that.

---

### Post by KiwiNZ on 2012-05-23
The biggest and commanding difference between DirectX OpenGL is......

If you develop a game in OpenGL you have a time consuming hobby with very little ROI.
If you develop a game in  DirectX you have a large target market and the opportunity for high
ROI if you produce a high quality relevant product.

---

### Post by thatguruguy on 2012-05-23
> **KiwiNZ said:**
> The biggest and commanding difference between DirectX OpenGL is......

If you develop a game in OpenGL you have a time consuming hobby with very little ROI.
If you develop a game in  DirectX you have a large target market and the opportunity for high
ROI if you produce a high quality relevant product.

Doesn't Minecraft use OpenGL? I thought (although I may be wrong) that Minecraft was at least somewhat successful.

---

### Post by ExSuSEusr on 2012-05-23
From what I understand it is a money / profit issue.

Someone more literate in programming can correct me if I am wrong, but - as you know - Windows is a closed source OS.  Windows is also the most used OS on the planet.  

Much like the hardware manufacturers, if you don't have the support of MS you aren't going to sell much product.  - I heard once that MS was actually threatening to withhold the code needed by hardware manufacturers to write drivers if they dared write commercial drivers for Linux.  How true that is?  I don't know - but given MS's history it wouldn't surprise me.  

Perhaps the same is true for the gaming industry. 

MS withholding valuable pieces of code if they don't bow down and refuse to incorporate anything but DirectX?

> If you develop a game in  DirectX you have a large target market and the opportunity for high

Don't you also have to have some type of license agreement with MS or at least some of their code as well?

---

### Post by forrestcupp on 2012-05-24
> **KiwiNZ said:**
> The biggest and commanding difference between DirectX OpenGL is......

If you develop a game in OpenGL you have a time consuming hobby with very little ROI.
If you develop a game in  DirectX you have a large target market and the opportunity for high
ROI if you produce a high quality relevant product.

Not true. The Source engine uses OpenGL for MacOS X and PS3. The Quake 3 engine uses OpenGL. There has been a lot of money made from games using OpenGL. It's not like OpenGL doesn't work on Windows. Before DirectX was any good, and after the rocky start with each card having its own proprietary api, everyone was using some form of OpenGL. Remember how the Voodoo cards had their own MiniGL based on OpenGL?

I'm not saying I would go with OpenGL, because I probably wouldn't. But it's not just a hobby library.

---

