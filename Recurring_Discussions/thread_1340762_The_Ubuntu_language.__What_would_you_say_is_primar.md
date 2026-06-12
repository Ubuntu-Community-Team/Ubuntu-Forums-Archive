---
title: "The Ubuntu language.  What would you say is primary?"
date: 2009-11-28
forum: Recurring Discussions
---

### Post by CodeBase01 on 2009-11-28
Hey guys,

   I am finally able to put more time back into the Linux community.  I am coming from application development on the Mac (Objective-C) and Windows (C#).  I think the hardest part about moving to application development on Ubuntu/Linux is that most of us look for the "primary" language and set of tools.

   What would you say is that set these days for Ubuntu?  For instance, on the Mac I always know to start-up XCode and Interface Builder to use with Objective-C.  Do we have this nice combination of tools for development?

  Thanks for any replies.  Hope all had a great Thanksgiving break.

PS:  If any of you have found the fix for iMacs not having any sound with 9.10 (and maybe other versions) please post a link.  I've tried several things and even some patches, with no luck.

---

### Post by slavik on 2009-11-29
Whatever the language the project of choice is written in. Could be straight ASM, could be LISP, Haskell ... etc.

Moving this to recurring discussions where this thread belongs.

---

### Post by CodeBase01 on 2009-11-29
Right...That is not exactly the mindset I use on the Mac side.  Here, Objective-C pretty much always "fits" the project.  The language and tools are a bit more standard here, at least for people writing native Mac apps (not java).  

Anyway, the answer is a bit obvious and not really what I was looking for.  Thanks though.

---

### Post by ve4cib on 2009-11-29
Usually the "best language" for a project is whatever you feel comfortable working with.  Given your Objective-C background C++ may be a good fit.  Or perhaps you'd be happier working in C# with Mono.

What kinds of projects did you have in mind?  That also influences the choice of language significantly.  If you're going to write kernel modules then C is the obvious choice.  If you're going to be writing Gnome-Do plugins then Mono/C# is the way to go.  A simple GUI front-end for a command-line program could be written in almost anything, but Python seems like an obvious first-choice for those kinds of easy jobs.

---

### Post by grayrainbow on 2009-11-29
QtCreator.

P.S. And it is multiplatform if you care for this stuff.

---

### Post by CodeBase01 on 2009-11-29
Thanks for the info.  That is a bit more down the road I was trying to get on.  I understand that certain languages fit certain projects. I've had to make these decisions millions of times on other platforms. I am specifically talking about applications, nothing like kernal modules.

I just want to start spending my evenings working on applications that Linux needs.  This could be anything from a database application to a photo library type application.  I think the problem here is that I am not looking for the "best" as much as I am looking for the standard for these types of applications in Linux.  

For example, all the things I listed above I would already know what tools and language I would use on Windows and the Mac because they have the standards I have mentioned.  I guess I will check out mono, at least it is similar to the environment I am use to at work.  It just doesn't feel native or common enough.

---

### Post by sbrown1992 on 2009-11-29
For desktop applications, either python or C#

---

### Post by grayrainbow on 2009-11-29
> **CodeBase01 said:**
> Thanks for the info.  That is a bit more down the road I was trying to get on.  I understand that certain languages fit certain projects. I've had to make these decisions millions of times on other platforms. I am specifically talking about applications, nothing like kernal modules.

I just want to start spending my evenings working on applications that Linux needs.  This could be anything from a database application to a photo library type application.  I think the problem here is that I am not looking for the "best" as much as I am looking for the standard for these types of applications in Linux.  

For example, all the things I listed above I would already know what tools and language I would use on Windows and the Mac because they have the standards I have mentioned.  I guess I will check out mono, at least it is similar to the environment I am use to at work.  It just doesn't feel native or common enough.
I'm not sure that you know exactly what you are talking...did you here of windows COM programming or everything is just .NET for you? Did you here of DerectX, DirectShow, XAudio, WASAPI, GDI...? It looks to me that there's no just "one standard" set of libs on windows? :)
So do what you just do on win, pick one and use it.
P.S. There's a lot of stuff for Unix world. But what seems accepted as "standard": [http://kde.org/]("http://kde.org/")
[http://www.gnome.org/]("http://www.gnome.org/")
And Mono/C# already existing project which one can contribute if desire(or just to see what people do with it), bare in mind that some people are bit "hysteric" with "sold out" like a stuff and don't like anything related to Mono:
[http://f-spot.org/Main_Page]("http://f-spot.org/Main_Page")
[http://banshee-project.org/]("http://banshee-project.org/")

---

### Post by ve4cib on 2009-11-29
> **CodeBase01 said:**
> I guess I will check out mono, at least it is similar to the environment I am use to at work.  It just doesn't feel native or common enough.

Mono is a relative newcomer, so it doesn't have the same proliferation as Python or C++.  That said there are a lot of very good applications written using Mono (Gnome-Do and Banshee both come to mind).

The other problem with Mono is that some people seem to be rather paranoid about it, and see it as somehow giving Microsoft control over Linux (or something like that -- I admit the exact nature of the paranoia escapes me, but discussions involving how "evil" Mono is pop up with relative frequency).  So if you do decide to go the Mono route you should probably prepare yourself for the more vocally-zealous free software fanatics to avoid your software, and they will likely try to encourage other people to do the same.  But provided your software does what it was designed to do properly people will use it.

---

### Post by CodeBase01 on 2009-11-29
Once again, thank you all for the information.  I understand that there are more options out there besides .NET.  I started in C++ and OpenGL with Windows, it has nothing to do with what is usable on the platform.
 
The fact is Microsoft -wants- developers to use .NET.  If I go to the Windows platform it is extremely obvious what Microsoft prefers me to write my applications in .NET is advertised and pushed to people everywhere.  I simply wanted to know if linux had this same "we WANT you to use this language and these tools, if possible.  If that toolset and language doesn't fit your application needs, here are some other options".
 
And you know Apple is going to shove Cocoa, XCode, and IB at developers as much as possible.
 
That is all I wanted to know.  A simple question that is a bit hard to word and answer.   Hope you all had a great weekend.

---

### Post by danbuter on 2009-11-29
There is no standard "you-must-use-this" language, unless you are going to work on an existing project. Otherwise, choose the language you like (though I'm not sure Obj-C is supported in Linux).

---

