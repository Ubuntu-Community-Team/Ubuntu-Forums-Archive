---
title: "Windows with Ubuntu or just Ubuntu?"
date: 2017-10-05
forum: New to Ubuntu
---

### Post by ironman03152000 on 2017-10-05
Hello all of the Ubuntu Community and Linux Community,
 I am somewhat new to Linux and of course Ubuntu and would like to ask you guys what your opinion is on the decision I need to make. Personally I use Windows 10 Pro on my Main Computer which isn&#8217;t going to change. However, I will need to use some type of Linux Distribution on my &#8220;Server&#8221; Computer. By what I mean &#8220;server&#8221; is broadcasting websites, hosting 2LTP VPN&#8217;s and using Visual Studio to program. Now my question is, is Ubuntu the right choice for what I need to do and if it&#8217;s better for me to install Windows and Virtualize Ubuntu or just plain-straight install Ubuntu? Thanks for reading my Thread and hope you guys have a wonderful day.

[LIST]
[*]Alan
[/LIST]

---

### Post by QIII on 2017-10-05
Hello!

Up front -- Visual Studio is a product designed for Windows, so you'll need to keep using that on Windows.  The Mono Project, however, does have a product to allow you to develop in C# in a Linux environment.  See [MonoDevelop]("http://www.monodevelop.com/").

As for the rest:  If I were you and just getting my feet wet, I'd use a virtualization solution to get my head wrapped around how all things Linux work.  Break it, fix it, reinstall it, modify it -- if you blow it, restore it from a snapshot.  When you are ready, you can implement a hardware install and know what you are up to.

When you get to it, a virtualized machine on the hardware OS is not such a bad idea.  Use the virtual machine as your server.  KVM (Kernel-Based Virtual Machine) is a much more robust platform for that than VirtualBox and the like.

---

### Post by ironman03152000 on 2017-10-05
Thanks for the advise, Wasn't sure if visual studio could run on Linux. Virtualization is what I thought of first but wasn't sure because I've heard some people say that Linux (Ubuntu) has everything you need. Which I bet it does but learning it first I guess would be that best choice for right now. Thanks Again.

---

### Post by mastablasta on 2017-10-06
it has everything you need, unless you need specific windows applications (windows games, MS office 100% compatibility, commercial & business windows applications such as an ERP...).

for windows applications it is still better to use windows. however if you are already running mostly opensource applications on windows then they have their equivalent or a good alternative available on linux.

For example i use Firefox, Libre office, Thunderbird, GIMP, Inkscape, Nero, Total commander, Winamp and Windows games on windows. 
Firefox, Libre office, Thunderbird, GIMP, Inkscape - have a linux version.
Nero, Total commander, Winamp - have good alternatives (some are even better ones than in windows)
Windows games on windows - many of the old games i play (can't afford the PC for newer ones) can work in Wine. but not all. 

in short at home i could live with Linux just fine.

at work is another matter. office laptop is filled with MS products, specialised apps for single sign on, VPS, ERP app. again some have alternative or even work on linux. but most don't work on it. the IT locked us in an dwe need windows to work. every few years they supposedly do a test if we could migrate to linux, but they usually find out we can not. the main app ERP has a linux client. i think the issue must be the MS office and CAD/CAM design systems as well as possibly some other applications. over the years they got more and more locked in to MS.

---

### Post by HermanAB on 2017-10-06
Microsoft is busy porting their .Net and its tools to Linux.  Most of it already works.

[https://www.microsoft.com/net/download/linux](https://www.microsoft.com/net/download/linux)

[https://code.visualstudio.com/download](https://code.visualstudio.com/download)

[https://blogs.msdn.microsoft.com/vcblog/2017/04/11/linux-development-with-c-in-visual-studio/](https://blogs.msdn.microsoft.com/vcblog/2017/04/11/linux-development-with-c-in-visual-studio/)

However, an operating system is not an either/or binary decision.  I use Macintosh, Linux, OpenBSD and Windows and multiple version of each.

---

