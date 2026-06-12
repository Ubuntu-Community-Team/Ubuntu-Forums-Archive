---
title: "[SOLVED] VB.NET &amp;amp; C# Programming"
date: 2008-03-15
forum: Programming Talk
---

### Post by EMCGFX on 2008-03-15
I am VB.NET programmer, and learning C# right now. But since I've switched to linux, I am having hard time finding good alternative to Visual Studio and SharpDevelop. The only good IDE I found so far is MonoDevelop. But there is another problem I am using Ubuntu 7.10 x64 edition (AMD64). It looks like Mono only supports x32 at this time.

I think there is at least some VB.NET and C# programmers out here. If you know any good IDE, please post it here. Because I don't want to use VM/Windows for programming all the time ](*,)

Thank you, in advance.

---

### Post by LaRoza on 2008-03-15
Those languages are best used in Windows (especially VB). 

Gambas is a Basic language, with a GUI builder and IDE.

C# can be used in any editor, and you can compile through the command line. MonoDevelop is the IDE it is mostly used with on Linux.

In Linux, languages are not tied to an IDE. .NET is closely tied to the tools and platform of the owner (MS), in Linux, any tools can be used.

I recommend you look at the sticky (I am moving this thread, so you will be in "Programming Talk")

Don't force Linux on yourself, if you are in school, and programming in Windows, Windows is the tools to use.

If you don't have a reason to stick with these languages (VB, not so much C#), I recommend trying another language better suited for Linux development. Python, C, and Java are good bets.

---

### Post by EMCGFX on 2008-03-15
Yeah, I am learning C/C++ But I have many projects that I've done in VB.NET so I want to migrate them to Mono at least. ;-) So I can realease some of this programs on linux as well.

I've never heard of Gambas, will try it thanks.

---

### Post by LaRoza on 2008-03-15
> **EMCGFX said:**
> Yeah, I am learning C/C++ But I have many projects that I've done in VB.NET so I want to migrate them to Mono at least. ;-) So I can realease some of this programs on linux as well.

C and C++ at the same time? That would be hard to do...

You can try Gambas, or MonoDevelop to see if these will work. VB isn't really suited for doing this, it would be like porting a bash script with zenity to Windows.

---

### Post by Wybiral on 2008-03-15
> **LaRoza said:**
> C and C++ at the same time? That would be hard to do...

Perhaps it's some weird hybrid of the two.

---

### Post by EMCGFX on 2008-03-15
No =D C then C++ lol

---

### Post by LaRoza on 2008-03-15
> **EMCGFX said:**
> No =D C then C++ lol

D, C then C++?

Interesting order. (=D may be meant as an emoticon, I can't tell)

---

### Post by CptPicard on 2008-03-15
Oh no, not again the "how do I transfer MSFT programming to Linux" question...

[IMG]http://wasteddomain.com/gallery/d/568-1/picard-sigh.jpg[/IMG]

Seriously, you don't. :| You just don't. It's wrong, get it? Against everything that is good and holy!

Gambas is garbage, as much as I know.

If you want to be crossplatform, use Python or Java. They are crossplatform in the Right Way -- that is, they are a great on Linux and also work on Windows.

I have serious doubts whether any MSFT tech will ever properly work on Linux -- most importantly because of the aversion most Linux coders have to being hooked to Microsoft's stuff -- so porting from Windows to Linux just won't happen like you'd expect...

---

### Post by LaRoza on 2008-03-15
> **CptPicard said:**
> Oh no, not again the "how do I transfer MSFT programming to Linux" question...


Maybe you could get a smaller version of that for your avatar :)

---

### Post by EMCGFX on 2008-03-16
I've installed MonoDevelop it works but the second I try to create GUI it closes, can some one please help ?

After I installed it, it told me that I am missing all this dependencies. But I can't install them over apt-get install. Please help me find this files. thanks.

libbonoboui-2.so.0
libbonoboui_2.20.0.orig.tar.gz
libgailutil.so.17
libglitz.so.1
libgnome-2.so.0
libgnome-keyring.so.0
libgnomeprint-2-2.so.0
libgnomeprintui-2-2.so.0
libgnomeui-2.so.0
libgnomevfs-2.so.0
libnspr4.so
libpanel-applet-2.so.0
libplc4.so
libplds4.so

---

### Post by EMCGFX on 2008-03-16
> **LaRoza said:**
> D, C then C++?

Interesting order. (=D may be meant as an emoticon, I can't tell)

Haha :lolflag:

---

### Post by LaRoza on 2008-03-16
Enable all repositories, update, and try to install again.

---

### Post by CptPicard on 2008-03-16
> **LaRoza said:**
> Maybe you could get a smaller version of that for your avatar :)

Nah, the hamster is cute, and that one picture by no means represents my general feelings about the forum. Sometimes I just can't stop myself from handing out the... trophy.. :p

---

### Post by LaRoza on 2008-03-16
> **CptPicard said:**
> Nah, the hamster is cute, and that one picture by no means represents my general feelings about the forum. Sometimes I just can't stop myself from handing out the... trophy.. :p

I have a couple of "trophies" also always ready also.

---

### Post by themusicwave on 2008-03-16
If you already know C#, then Java is not that big of a switch.  It would be much easier to go from C# to Java than C# to C or C++.

Java and C# are fairly similar.  I would recommend you try learning it.  Also, netbeans has a pretty good Java GUI builder.  It isn't as easy as VB, but it isn;t very hard either.  You can get it from he repos(version 5.5) or version 6 from [www.netbeans.org](www.netbeans.org)

Also you would need all the sun java packages.

Is there any reason you must use VB and C#?  As a progammer who has used Java, C++, VB, C#, Python and a mix of others I can tell you in my opinion VB is the worst langauge out of all I have used.  The only one worse was VBScript.

Today if I am forced to use .Net it is C# or nothing.  Generally i try to use Java instead whenever possible.  Not knowing your situation, I can;t say if this makes sense for you.  Perhaps some context would help.

I also echo Picard's concerns.  .Net was meant to be cross platform, if you platform is Windows.  Microsoft says it's "cross platform" because it works on Windows XP, Windows Vista and sometimes Windows CE.  This is intentional on their part to keep code locked to the Windows platform.

Java is cross platform, python is too.  They work on Windows(All of them), Linux, Unix, Mac, BSD....

---

### Post by pmasiar on 2008-03-16
Reason to switch to Linux IMHO is to use all free software, to participate and share. VB is almost non-existant, C# and .NET/Mono are - less than popular. Linux is it's owl platform and its own world. If you don't want to dive in and use rich free tools available, why bother to switch? Stay on Windows and be happy there, you don't have all the compatibility issues.

I am not saying that you should not switch to Linux: I am saying that if you switch, forget about the old platform! .NET was designed to be incompatible with everyone else. 

It is like coming to party where free BBQ is given away, and you instead of enjoying the free BBQ decided to open spam conserve you brought from your previous place. Of course nobody cares about VB: we have all the free tools!

---

### Post by EMCGFX on 2008-03-16
Like I said before I switched to linux as my main host os. Even If I will use VB.NET for my old projects, I will use vmware. Also the reason I use VB.NET is because its the language I already know, and I did not have time to learn anything new. Even when I was using windows I've released couple of open source GPL (vb.net) projects. Yes, I will learn C# after VB.NET, then after C# I will learn something else. But for now I will learn and use C# and my VB.NET in vmware. Time is money for me. Belive me I know that VB.NET is not the best language, but that what I've learned and used in windows. See I don't want to abendone all my projects in VB.NET and switch to other language so I can recode them, that is time consuming and lots of work. I rather use Visual Studio in VMware ON LINUX and program what I know now. Thank you guys for your opinions on what I should on should'nt use LOL

---

### Post by cprofitt on 2008-03-16
[IMG]http://sfk.game-host.org/images/picsgh.jpg[/IMG]
 
Here is that avatar LaRoza wanted for CptPicard.
 
Decided to give you a few more choices as well after I noticed you said that it does not represent your feelings here...
 
[IMG]http://sfk.game-host.org/images/borg.jpg[/IMG]
 
[IMG]http://sfk.game-host.org/images/picard1.jpg[/IMG]
 
[IMG]http://sfk.game-host.org/images/picpink.jpg[/IMG]
 
[IMG]http://sfk.game-host.org/images/picren.jpg[/IMG]
 
I hope one of them finds your fancy.

---

### Post by CptPicard on 2008-03-16
Hahah... thanks :D

Nice framing, I was wondering about how I'd do it but that's about perfect.

I'm most definitely not Locutus of Microsoft, mind you. (well, it would be great for a little trolling... maybe I'll use that if I ever decide to sing MSFT Monoculture's praises ... once I discover them or something) :)

---

### Post by LaRoza on 2008-03-16
I like the Borg one :)

I may use it someday.

---

### Post by pmasiar on 2008-03-16
Borg is nice. LaRoza, you should swith to it, if in fact you are a bot. 

But maybe you are not, you just want us to believe you are a bot! :-)

---

### Post by LaRoza on 2008-03-16
> **pmasiar said:**
> Borg is nice. LaRoza, you should swith to it, if in fact you are a bot. 

But maybe you are not, you just want us to believe you are a bot! :-)

I will find another borg image, I think I found a good one.

I could be a dog for all anyone knows.

---

### Post by jviscosi on 2008-03-16
> **LaRoza said:**
> I will find another borg image, I think I found a good one.

I could be a dog for all anyone knows.

Okay this is OT, but since we're discussing icons ... LaRoza, is your current icon a black and white posterized-style picture of one or two people reading a book or magazine?  I've been trying to figure it out and it sort of resolved itself into that for me just now.

If it's a secret, you don't have to tell.  ;-)

---

### Post by CptPicard on 2008-03-16
> **jviscosi said:**
> I've been trying to figure it out and it sort of resolved itself into that for me just now.


It's a Rorschach test, and the correct answer is always "breasts". (That's what I've been told, at least).

---

### Post by LaRoza on 2008-03-16
> **jviscosi said:**
> Okay this is OT, but since we're discussing icons ... LaRoza, is your current icon a black and white posterized-style picture of one or two people reading a book or magazine?  I've been trying to figure it out and it sort of resolved itself into that for me just now.


[http://ubuntuforums.org/showthread.php?t=515751](http://ubuntuforums.org/showthread.php?t=515751)

---

### Post by schmendrick on 2008-03-17
AFAIK monodevelop is the only linux-IDE for .NET worth mentioning. 
i think you will have to stick with , but IMHO its a great IDE. 
did you get it to run already?

---

### Post by cprofitt on 2008-03-17
> **CptPicard said:**
> Nice framing, I was wondering about how I'd do it but that's about perfect.

No problem.

I have been making little graphics like this for the web for around 13 years.

---

### Post by cprofitt on 2008-03-17
> **LaRoza said:**
> I like the Borg one :)

I may use it someday.

Give me a request and I can work on a few for you...

---

### Post by LaRoza on 2008-03-17
> **PrivateVoid said:**
> Give me a request and I can work on a few for you...

Thanks! I am as good as I am at image manipulation as I am at...writing VB (can't do it at all)

Could you do this one? [http://www.geocities.com/Area51/Aurora/3491/borgqueen.jpg](http://www.geocities.com/Area51/Aurora/3491/borgqueen.jpg)

I would like all colour removed, and use only greyscale.

---

### Post by EMCGFX on 2008-03-17
I am signing out of this topic, it became avatars topic LOL

---

### Post by LaRoza on 2008-03-17
> **EMCGFX said:**
> I am signing out of this topic, it became avatars topic LOL

Sorry, do you want me to move all the OT posts to a new thread?

---

