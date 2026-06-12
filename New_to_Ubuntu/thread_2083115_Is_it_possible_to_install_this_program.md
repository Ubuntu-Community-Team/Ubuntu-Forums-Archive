---
title: "Is it possible to install this program?"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by Psychomax on 2012-11-11
My girlfriend got this slick program to organize her MtG collection on the windows 8 appstore called UrzaGatherer. It is an open source program--I found the source code [here]("http://urzagatherer.codeplex.com/SourceControl/changeset/view/100271")--what is the best way to get it running on my ubuntu machine?

---

### Post by roger_1960 on 2012-11-11
Mmm.... dual boot with windows8?

---

### Post by offgridguy on 2012-11-11
> **Psychomax said:**
> My girlfriend got this slick program to organize her MtG collection on the windows 8 appstore called UrzaGatherer. It is an open source program--I found the source code [here]("http://urzagatherer.codeplex.com/SourceControl/changeset/view/100271")--what is the best way to get it running on my ubuntu machine?

I looked at this site, couldn't see anything about linux compatibility here.  So
presumably since it is a windows app. the only way to run it would be using wine.
       Since I have never had success using wine, i can't advise on that.
I'm inclined to agree with the prior reply.

---

### Post by COMECON on 2012-11-11
It's made with Visual Studio and C#, so it maybe would work with Mono.NET... Otherwise, try it with Wine.

---

### Post by D_E_H0987 on 2012-11-12
> **Psychomax said:**
> My girlfriend got this slick program to organize her MtG collection on the windows 8 appstore called UrzaGatherer. It is an open source program--I found the source code [here]("http://urzagatherer.codeplex.com/SourceControl/changeset/view/100271")--what is the best way to get it running on my ubuntu machine?

Now I can't guide you threw it, I'm not much on programing, but with source code, you should be able to compile the app to run under Linux.  You may need certain library files to do this.  So basically you need more info about UrzaGatherer's code and libraries.

On the other hand since looking at the site link you mention, we find "UrzaGatherer is a WPF 4.0 client application to handle Magic The Gathering cards collections." 

A simpler way, mite be to just ask if there are any Linux APP's to organize a Magic the Gathering card collection.

A search on Google finds this APP with versions for Windows, Linux, and Mac
[http://sourceforge.net/projects/mtgbrowser/](http://sourceforge.net/projects/mtgbrowser/)

I haven't messed with magic since they sent me the first version many moons ago, so I can't tell you if this APP is good or not, but since it was one of the first couple of links to popup most likely its pretty decent.


Anyway a couple of ideas.

---

### Post by Mark Phelps on 2012-11-12
The WPF 4.0 should have been a clue that this is Windows-only.  WPF is the Windows Presentation Foundation -- a graphical subsystem for rendering interfaces in Windows applications.

For this to work in Linux, you would require Linux libraries that handle all the WPF library calls -- much the same that the Wine DLLs handle Windows system calls.

MS Silverlight is a similar concept -- and it does NOT run in Wine.

---

### Post by squakie on 2012-11-12
> **D_E_H0987 said:**
>  ....with source code, you should be able to compile the app to run under Linux.  You may need certain library files to do this.  So basically you need more info about UrzaGatherer's code and libraries.....


Programming to the Windows API is much different than programming the API's in Linux.  It's not that simple.  The entire program would have to be converted to use something like GTK.

Hummmm......open source, convert to GTK - sounds like something I might play with, but don't look to me for the app to run in Linux.  If I play with it and eventually actually get something working, I'll let you know.

---

### Post by directhex on 2012-11-12
Just because the code is available, doesn't mean you can just run it on Linux. This app's pretty tightly tied into Windows-only libraries.

---

