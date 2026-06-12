---
title: "Converting a C# project to Java"
date: 2016-10-04
forum: Programming Talk
---

### Post by lads on 2016-10-04
Dear all,

In recent weeks I have tried to revive an old project coded in C#, way back in the day I still used Winblows at work. I use Eclipse, so I went out first for some C# plug-in; while at some point there were three active plug-ins, those projects have all been abandoned. Right now it seems there is only one C# friendly IDE around: MonoDevelop. I thus gave it a go, just to find out [it can not cope with projects coded on Winblows]("https://bugzilla.xamarin.com/show_bug.cgi?id=44864") (and that its scant developers are not really worried about it). In face of all this I must conclude this language is to all matters and purposes dead; time to move on.

Since C# is hugely inspired on Java, I would thought it not so hard to automatically convert between the two. However, so far I could only find a single conversion tool: [cs2j]("https://github.com/twiglet/cs2j"), that unfortunately does not compile on Ubuntu.    

Any advice or experiences to share on this? At this stage a manual conversion to Java seems the only option, but that is a huge load of work...

Thanks.

---

### Post by mcgbb on 2016-10-20
The easy way would be to try MonoDevelop again.. 
I've been using MonoDevelop to test some C# apps running on a Linux platform for an embedded system, it opens my VS2013 projects up and builds them without any issues.
Using MonoDevelop 5.10 on Xubuntu 16.04.  Working great for any VS2010/VS2013 project I import into it.

---

### Post by virgosun on 2016-10-22
It will not work. I have tried lot of tools. Converted code is just worth as a reference, not to mention .NET has no equivalent in JAVA.
I have to rewrite all code in JAVA.
Let's take a look at [this app in C#]("http://sonvirgo.github.io/live-wallpaper-sync/index.html") and [JAVA rewritten ]("http://sonvirgo.github.io/live-wallpaper-sync/Posix.html")[URL="http://sonvirgo.github.io/live-wallpaper-sync/index.html"]
[/URL]

---

### Post by trent.josephsen on 2016-10-23
So... your only problem is that MonoDevelop won't open the Visual Studio project file? Bit drastic to go to rewriting the whole darn thing, right?

I won't pretend to know anything about C# or .NET, but... the actual *source files* still exist, right? Don't C# source files end in .cs usually? I mean, I looked up "what is a visual studio solution file" and they just contain some kind of VS-specific metadata. Surely you could create a blank project (or "solution", whatever the difference may be) in MonoDevelop and just copy the C# source files. As far as I know, Mono is pretty close to feature parity with .NET. At least, that's what people always say when the topic of Microsoft's control over the platform comes up.

Correct me if I'm way off base but rewriting over this seems a bit like replacing your car because you locked the keys inside.

---

### Post by virgosun on 2016-10-23
If the main project references some library project, some also in VB#. Some require NuGet packages, WCF, etc, the matter is more complicated than a rewrite.
Further more you are misleading, the original question is to migrate from c# to java, not from VS.Net to Mono-Develop for c#
Or may I recommend Wine?
Am I not right?

---

