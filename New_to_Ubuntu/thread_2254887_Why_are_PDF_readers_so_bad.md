---
title: "Why are PDF readers so bad?"
date: 2014-11-30
forum: New to Ubuntu
---

### Post by Aneesh_De on 2014-11-30
Hey all, I've recently started using Ubuntu almost full time, cuz my RoR project work is way easier on Ubuntu. One of the many annoyances I have with Ubuntu is PDF readers. Why are they so bad? Every page I scroll to needs half a sec to one sec to render. Not only that, only a few (around 8?) of them stay in memory at a time, so if I scroll back to a previously rendered page after a while, I face the same delay again. Initially I thought it was only the built in reader that was this slow, but other readers (like qpdfview) are all equally bad. Is this because of extremely aggressive RAM management? Is there any way to fix this? I know this sounds like a tiny thing, but coming from Windows, it's quite jarring. Even my android phone has better performance with pdfs.

---

### Post by mörgæs on 2014-11-30
Which hardware and which version of Ubuntu?

---

### Post by Aneesh_De on 2014-11-30
_**Hardware:**_ 
[HP DV6 6165tx]("http://www.flipkart.com/hp-notebook-dv6-6165tx-laptop-2nd-gen-ci7-4gb-750gb-2gb-ddr5-graphics-win-7-beats-audio/p/itmd2pvecubhfpqv?pid=COMD2PVDWZWH6UDS")
Processor: Core I7 Sandy Bridge
Ram: 4 GB
Not particularly new, but not ancient by any standard.

_**Version:**_
Ubuntu 14.04

---

### Post by grahammechanical on 2014-11-30
My hardware is a lot less specified than your hardware but I notice that pages of PDF documents made out of typed text are rendered quickly but when it comes to pages of PDF documents that are in fact scanned images of pages of books, then the rendering process is very slow. It does not help if the PDF document is based on a large book such as a dictionary. That sort of thing.

It is my guess, that the process is slow because pages are cached in memory and on my machine I only have 1 GB of RAM. I also suspect that the application that created the PDF document plays a part in all of this. How many PDF creator applications are there for Linux? And are these the tools being used to create most PDFs?

I do not expect any PDF document created by an application run on a Windows operating system to produce PDFs optimised for running on Linux. I have even had pages of PDF documents render incompletely because the PDF was created by a certain version of an Adobe product and I did not have the correct version of Adobe reader installed. And this happened when I was using an old version of Windows. Even though the Reader was free to download and install my machine at the time was under specified and would run the newer version of the Reader.

When PDF creator applications allow fancy effects that are not included in the PDF standard to lock in the user to a specific reader application, then of course Linux PDF readers are going to fall short of being efficient because the code in the document is proprietary and not Open Source.

This is life when using Linux. But at least it is free. Even in the sense of not costing any money. We get what we pay for. I am happy.

> [COLOR=#252525][FONT=sans-serif]From 1993-2006 Adobe Systems changed the PDF specification several times to add new features. Various aspects of Adobe's Extension Levels published after 2006 have been accepted into working drafts of ISO 32000-2 (PDF 2.0), but developers are cautioned that Adobe's Extensions are not part of the PDF standard.[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/Portable_Document_Format](http://en.wikipedia.org/wiki/Portable_Document_Format)

Regards.

---

### Post by Aneesh_De on 2014-11-30
> **grahammechanical said:**
> My hardware is a lot less specified than your hardware but I notice that pages of PDF documents made out of typed text are rendered quickly but when it comes to pages of PDF documents that are in fact scanned images of pages of books, then the rendering process is very slow. It does not help if the PDF document is based on a large book such as a dictionary. That sort of thing.

It is my guess, that the process is slow because pages are cached in memory and on my machine I only have 1 GB of RAM. I also suspect that the application that created the PDF document plays a part in all of this. How many PDF creator applications are there for Linux? And are these the tools being used to create most PDFs?

I do not expect any PDF document created by an application run on a Windows operating system to produce PDFs optimised for running on Linux. I have even had pages of PDF documents render incompletely because the PDF was created by a certain version of an Adobe product and I did not have the correct version of Adobe reader installed. And this happened when I was using an old version of Windows. Even though the Reader was free to download and install my machine at the time was under specified and would run the newer version of the Reader.

When PDF creator applications allow fancy effects that are not included in the PDF standard to lock in the user to a specific reader application, then of course Linux PDF readers are going to fall short of being efficient because the code in the document is proprietary and not Open Source.

This is life when using Linux. But at least it is free. Even in the sense of not costing any money. We get what we pay for. I am happy.



[http://en.wikipedia.org/wiki/Portable_Document_Format](http://en.wikipedia.org/wiki/Portable_Document_Format)

Regards.

So there's nothing I can do? I don't have 1GB of RAM, I feel I shouldn't be having such problems.

Maybe it IS time to go Apple...

---

### Post by aspergerian on 2014-11-30
I read many sci PDFs and prefer Adibe Reader on my Ubuntu and W7 machines.

---

### Post by MrSteve on 2014-11-30
have you tried okular pdf reader 
its the default pdf reader in Kubuntu

you can via the setting increase the amount of memory that it can use making pdfs show and run a lot smoother ...

---

### Post by amanchesterman on 2014-12-01
When I used Windows, I used Foxit Reader for PDFs, which I found faster than Adobe Reader. I see that there is a version of Foxit for Linux: I haven't tried it, but you might want to?

---

### Post by Aneesh_De on 2014-12-01
> **MrSteve said:**
> have you tried okular pdf reader 
its the default pdf reader in Kubuntu

you can via the setting increase the amount of memory that it can use making pdfs show and run a lot smoother ...

Can I run it without KDE? I'm on Unity, and have no other reason to switch.

> **amanchesterman said:**
> When I used Windows, I used Foxit Reader for PDFs, which I found faster than Adobe Reader. I see that there is a version of Foxit for Linux: I haven't tried it, but you might want to?

Yeah, I loved Foxit too, but couldn't find it for Linux. Could you give me a link? The only ones I could find were for Windows only.



I gotta ask, am I the only one facing this problem? I think I should keep a poll...

---

### Post by MrSteve on 2014-12-01
link to foxit but its only a 30 day trail
[http://www.foxitsoftware.com/products/sdk/PDFsdk/linux/](http://www.foxitsoftware.com/products/sdk/PDFsdk/linux/)

installing okular will pull in some kde lib files but will not install the kde desktop
it will run from within ubuntu ...

---

### Post by Aneesh_De on 2014-12-01
> **MrSteve said:**
> link to foxit but its only a 30 day trail
[http://www.foxitsoftware.com/products/sdk/PDFsdk/linux/](http://www.foxitsoftware.com/products/sdk/PDFsdk/linux/)

installing okular will pull in some kde lib files but will not install the kde desktop
it will run from within ubuntu ...

An entire PDF SDK just to get a decent reader? This seems like WAY too much work for basic functionality.

---

### Post by MrSteve on 2014-12-01
here is another link i found 
[http://www.foxitsoftware.com/downloads/](http://www.foxitsoftware.com/downloads/)
use the drop down menu to get the linux desktop download 
its a bz2 file ...

---

### Post by /ADM on 2014-12-01
On my Ubuntu machine PDF's are rendered quite poorly sometimes.  If it is a scan or text it is ok but if it's some fancy PDF created using proprietary effects or programs then it gets bad.  I also have a Mac and it simply blows the pants off of Ubuntu in this area.  All pages stay in RAM or render in under half a second.  If you work with PDFs a lot, then maybe Linux isn't for you.  Unless you can get used to slower rendering speeds.  

It's free, has a great community and works well.  But the ultimate choice is up to you.

---

### Post by amanchesterman on 2014-12-01
As a correction to what MrSteve says in post #12, if you go to [http://www.foxitsoftware.com/downloads/](http://www.foxitsoftware.com/downloads/) you can get a version for Linux **and choose the package type**. Just click on the downwards-pointing arrow in the 'package type' field and you can choose a **deb** package which should install easily in Ubuntu. It **doesn't** have to be a bz2 package and there is nothing about it being a trial version either: it looks like the normal Foxit reader tailored for Ubuntu. I hope it works for you. ;)

---

### Post by howefield on 2014-12-01
> **amanchesterman said:**
> As a correction to what MrSteve says in post #12, if you go to [http://www.foxitsoftware.com/downloads/](http://www.foxitsoftware.com/downloads/) you can get a version for Linux **and choose the package type**. Just click on the downwards-pointing arrow in the 'package type' field and you can choose a **deb** package which should install easily in Ubuntu. It **doesn't** have to be a bz2 package and there is nothing about it being a trial version either: it looks like the normal Foxit reader tailored for Ubuntu. I hope it works for you. ;)

5 year old + software and not likely to work on 14.04, at least it didn't on this 14.04 VM.

---

### Post by Aneesh_De on 2014-12-01
> **MrSteve said:**
> here is another link i found 
[http://www.foxitsoftware.com/downloads/](http://www.foxitsoftware.com/downloads/)
use the drop down menu to get the linux desktop download 
its a bz2 file ...

Thanks, I tried it, and while it's still nowhere near as good as it should be, it's quite a bit better.

> **/ADM said:**
> On my Ubuntu machine PDF's are rendered quite poorly sometimes.  If it is a scan or text it is ok but if it's some fancy PDF created using proprietary effects or programs then it gets bad.  I also have a Mac and it simply blows the pants off of Ubuntu in this area.  All pages stay in RAM or render in under half a second.  If you work with PDFs a lot, then maybe Linux isn't for you.  Unless you can get used to slower rendering speeds.  

It's free, has a great community and works well.  But the ultimate choice is up to you.

I get that, and appreciate it both the free part and the amazing community, but yeah, this feels like a little too much work and compromise on basic functionality. And I guess I'm ready to pay the premium to get a better experience.

---

### Post by vasa1 on 2014-12-01
> **Aneesh_De said:**
> ... I get that, and appreciate it both the free part and the amazing community, but yeah, this feels like a little too much work and compromise on basic functionality. And I guess I'm ready to pay the premium to get a better experience.
I think that's the best route. If you find your needs aren't met with one OS, it's best to switch to whatever is appropriate rather than wait and hope for change.

I don't use pdf files a lot but as far as viewing them goes, Google Chrome's built-in PDF viewer (derived from Foxit component) has been more than adequate. For example, I can view the Fullcircle magazine without much problem: [http://dl.fullcirclemagazine.org/issue91_en.pdf](http://dl.fullcirclemagazine.org/issue91_en.pdf). The default "Document Viewer", Evince, doesn't do a bad job either on this pdf file.

Note that my comments are limited to viewing and not to manipulation of the pdf file in anyway.

My Dell Inspiron 1545 laptop has 4GB RAM & is a Core2Duo from 2009 and the OS is 14.04.

If you have an example of a problematic pdf file that you're willing to share please do. Does the link I provided lag for you?

---

### Post by llamabr on 2014-12-01
I don't care for any of the default pdf readers, either.  Try xpdf, available in the repos.  Good keybindings, extremely configurable, and a very small RAM footprint, so that it advances pages quickly.

---

### Post by monkeybrain20122 on 2014-12-01
> **vasa1 said:**
> 
If you have an example of a problematic pdf file that you're willing to share please do. 

+1. I have a lot of PDF documents and books and never have a problem.

---

### Post by oldos2er on 2014-12-01
> **Aneesh_De said:**
> Can I run it without KDE? I'm on Unity, and have no other reason to switch.

Of course. You can install it with the Software Center or ```
sudo apt-get update && sudo apt-get install okular
```

---

### Post by vasa1 on 2014-12-01
> **oldos2er said:**
> Of course. You can install it with the Software Center or ```
sudo apt-get update && sudo apt-get install okular
```
Before that, run ```
apt-get install -s okular
```
That will simulate an install to give you an idea of what okular needs to run on *your* system.
If you feel that a bit too much, include **--no-install-recommends** to lighten things up a bit. By default apt-get and Synaptic install recommends. I don't know what the Software Center does.

---

### Post by monkeybrain20122 on 2014-12-01
No doubt Okular has  a lot more functions, but I don't find it scroll faster than evinve, actually pages load slower even if memory use is set to aggressive.

---

