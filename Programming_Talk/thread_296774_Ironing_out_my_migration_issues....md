---
title: "Ironing out my migration issues..."
date: 2006-11-10
forum: Programming Talk
---

### Post by casperiv on 2006-11-10
I have been developing software for several years now, and although I am working on migrating to Ubuntu for just about everything I do (Gaming, side projects, surfing....).  I really need to be able to use Visual Studio and a GOOD SQL interface, any ideas?  How well does Visual Studio work with wine, or does it work at all?  Also, are there any web dev applications open source that are comparable with Dreamweaver?

I am getting closer to being able to only use my Ubuntu HD in my laptop, but still have a few loose ends.  Any help?

---

### Post by 23meg on 2006-11-10
> How well does Visual Studio work with wine, or does it work at all? I wouldn't rely on it working, even if it does seem to work (I don't think it will, but try and see). > Also, are there any web dev applications open source that are comparable with Dreamweaver?There's NVU and Bluefish, but most find them lacking in features compared to Dreamweaver. Anyway, if you're doing CSS-heavy design the lack of features may be a trivial matter for obvious reasons. Check them out and see if they work for you. Older versions of Dreamweaver are also supposed to work with WINE, but since I get lots of crashes in Dreamweaver even in its native environments, I'm leaning towards open source alternatives which are more stable.

Hope your migration goes well.

---

### Post by casperiv on 2006-11-10
I hope so too.  I would like to find a solution for everything I do in windows, but I doubt it will happen.  With the lack of professional software in linux distros at the present time, I will have a really hard time getting a good base of tools.

I use pretty much all the functions of Dreamweaver, which is why I have such a hard time finding a replacement.  As far as Visual Studio goes, I don't think it will work.  MS makes it as hard as possible to make big apps like that work with anything other then  windows.... if nothing else the .NET frame work definatly won't work for compiling projects.

I'm too tired to type, let along thing about this right now.  I need to go take a break from the computer :)

---

### Post by 23meg on 2006-11-10
> I hope so too. I would like to find a solution for everything I do in windows, but I doubt it will happen. With the lack of professional software in linux distros at the present time, I will have a really hard time getting a good base of tools.Do look around and check out the existing tools anyway; you may be positively surprised. If nothing works you can keep your Windows installation in a dual-boot environment, or run Windows in a virtual machine.> I use pretty much all the functions of Dreamweaver, which is why I have such a hard time finding a replacement.Then your best bet is to run it via WINE or in a virtual machine. Try it, it's very likely to work somehow.
> As far as Visual Studio goes, I don't think it will work. MS makes it as hard as possible to make big apps like that work with anything other then windows....I'm not sure they make any such deliberate effort, but in the case of VS there seems to be a point in it not working, since it's designed from the ground up to build and compile apps that run on the Windows platform; I wouldn't expect a program that does such a low-level job to run on an alien API when most apps *made on *that program aren't working themselves.
> 
if nothing else the .NET frame work definatly won't work for compiling projects.Welcome to [Mono]("http://www.mono-project.com/")..

---

### Post by po0f on 2006-11-10
casperiv,

I second 23meg's suggestion of keeping Windows around, if only just for VS/Dreamweaver, *especially* if you use these tools for money.  There is no reason to sabotage yourself financially just to see if it will work.

---

