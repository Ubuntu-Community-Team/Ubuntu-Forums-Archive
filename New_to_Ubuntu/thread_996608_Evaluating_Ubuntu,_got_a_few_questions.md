---
title: "Evaluating Ubuntu, got a few questions"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by blira on 2008-11-29
Hi,

I have been becoming more and more interested with computers, and in my experimentation I have really started to enjoy and prefer free and open source software.  So I am really wanting to make a move to linux, from what I can gather Ubuntu is generally considered the best distribution for first time linux users.

My main concern is with hardware compatibility.  I currently have a Sony VAIO SR 190 (not the current 290, I got my laptop right when it was released).  My basic hardware setup is as follows:

Intel P8600, Hitachi 7k200, 4GB memory, Bluetooth (Not sure about the specifics), Intel WiFi 5100, ATI HD3400, Synaptics touchpad.

I can't seem to find drivers anyware for these devices.  I am missing something?  Are these devices not compatible with Ubuntu?

I was also wondering about what comes bundled with Ubuntu besides the operating system and system tools?  I looked through the tour, and it listed high-level stuff like Firefox, OpenOffice, Totem, but I can only assume more stuff is included by default.  I generally prefer to install applications myself, so I only have what I want and need, and don't end up loaded with useless crapware (for example, I watch movies, but I don't edit them).  Is there anyway to just install Ubuntu without third party applications?  If not, how is uninstalling under Ubuntu?  Does it uninstall clean, or leave garbage everywhere like Windows?

Thanks!

---

### Post by twiz86 on 2008-11-29
I just switched to ubuntu 2 weeks ago so I can give you some non-pro spin on this..

Ubuntu pretty much detected everything right off the bat, although my bluetooth still doesnt work, everything else...even my fingerprint reader was detected.
You may have a couple hickups but for the most part you will be ok as far as drivers.

secondly I would ask that you get out of the windows mentality. I had it at first and i thought ubuntu sucked because i was thinking of linux as a windows alternative, it isnt. Its a whole new dimension and a way funner adventure.

Ive never felt more accomplished than i do now that i have my ubuntu running at about 90% of what I want it to do.

Back to your hardware. Im guessing you have a 64bit system so to take advantage of the full 4gig of memory you will want to install the ubuntu amd64 instead of the 386. 

The applications you mentioned are right on but include basero(cd writer), Rhythmbox(music player)...and some other stuff. In the end, if you want more apps there is a program called synaptic package manager that has like thousands of approved aps you can easily install in one click.

Anywho, this is all from a newb...for some reason newbs feel more comfortable hearing success stories from newbs. so here ya go.

:guitar:

One more thing...Ubuntu comes with wayyyyyy less third party crap than most distros...trust me, if anything you will be installing more stuff, not uninstalling.

---

### Post by steve_pearce on 2008-11-29
*I can't seem to find drivers anyware for these devices. I am missing something? Are these devices not compatible with Ubuntu?*

Device drivers (providing they are supported) are usually shipped with the Linux kernel. Every distribution of GNU/Linux has its own kernel build but generally if you go with newest distro releases you will be running a good, stable and hopefully well supported kernel.

My advice would be to download an Ubuntu 8.10 32bit or 64bit cd and run it in live mode. You will be able to see what works and what may require care etc without touching your disks.

*I was also wondering about what comes bundled with Ubuntu besides the operating system and system tools? *

Pidgin (messenger), GIMP (photo editing), F-Spot (photo management), Transmission (torrents), Brasero (burning), Rhythmbox (powerful audio management and playback) to name a few. Pretty much *everything you need to get stuff done*.

*I generally prefer to install applications myself, so I only have what I want and need, and don't end up loaded with useless crapware (for example, I watch movies, but I don't edit them). Is there anyway to just install Ubuntu without third party applications?*

Ubuntu has been finely engineered to include what the vast majority of users require to be productive.

There are very smaller Ubuntu netinstallation images and alt images available should you wish to go the bare bones route. And I believe (like Debian's installer) you can specify whether you want a graphical desktop or not. Which would allow you to install what you wish. There are plenty of options available, probably just a google search away. These however are not recommended for those new to the distribution.

*If not, how is uninstalling under Ubuntu? Does it uninstall clean, or leave garbage everywhere like Windows?*

You can use the add/remove graphical application to remove packages. You can also manually remove packages at a console. "sudo apt-get remove meh" for example. Some packages are usually left in place should you wish to reinstall them at a later stage.

So to conclude, fetch a live cd from the Ubuntu site and give it a try. If certain parts seem troublesome the Ubuntu community are always around to offer advice.

---

### Post by NewJack on 2008-11-29
My suggestion is to run the Live CD and see if there are any issues with your VAIO.  Generally if the Live CD works on it, a full install will work.  That way, if you are having any issues (video, audio,etc) you'll know before committing.  I also suggest you try both Hardy and Intrepid Live CD's see which one works better.

BTW, welcome to the Community!

---

### Post by linuxguymarshall on 2008-11-29
First of all let me welcome you to the Ubuntu community. We will all gladly help you out. There are a couple of things you should keep in mind at all times when asking about Linux.

[LIST=1]
[*]Google is your friend
[*]Don't be afraid to ask, we don't bite. Well most of us......
[*]Get used to a terminal. This is not DOS. The terminal is not as freaky here you will learn to love it.
[/LIST]

It sounds as if you have not switched which gives us a few options. First of all there is learning. You can install X-Chat for Windows which will allow you to connect to the Ubuntu chat room and get help. Or you can dowload and burn a Live CD which you can run Ubuntu from (Not full Ubuntu as it does not have rewritable space to do cool things). Then there is the preferred way of most Windows users. Wubi. Google 'wubi' and download it. It is a great way to use Ubuntu and remove it if you don't like it. Read the FAQ.

But for most of your questions most hardware will be auto detected and what is not you can ask on the net for. People will be glad to help.

cheers!

---

### Post by Xiong Chiamiov on 2008-11-29
I believe your hardware should all be fairly compatible, although the ATI drivers haven't yet gotten up to the quality of the NVIDIA ones.  The open-source ones, though, are included in the kernel, I believe.  If not, they are easily installed, and will be installed on Ubuntu by default.

A live cd will allow you to see how things work and what is included, as well as if things work.  However, if you'd like to have more customization of what packages are installed, you'll probably want to use the alternate cd, which uses an ncurses-based install instead of the standard graphical one.

Linux does a pretty good job of cleaning up after itself.  By default, APT will leave configuration files for programs, but if you do a "purge" removal, then it will remove all files associated with the program.

Ubuntu comes with a lot of stuff preinstalled.  Technically, it's **all** 3rd-party (as in, the entire OS is), as Canonical doesn't really develop much software.  All a distro does is pull together lots of applications written by other people, which is why you can use GNOME, for instance, on Ubuntu, Fedora, Mandriva, Gentoo, Slack, etc.

The important thing to realize is that lots of stuff preinstalled means that more things work automatically.  For instance, you won't have to deal much with printers, because CUPS will already be installed and probably running.  This is why many of the "user-friendly" distros are shied away from by more experienced users - they don't want things running that they don't need, and can handle installing and configuring things themselves.  Don't worry, though - it's nothing like Windows.  Linux does a very good job of providing eye-candy and shiny things while maintaining much better performance than Microsoft has been able to provide.

If you ever get to the point where you want more control over what's installed and what's not, I'd recommend you check out [Arch Linux]("http://archlinux.org").  While I love it to death, I would most certainly not recommend it to a first-time Linuxer, as it can be quite a bit daunting.  A few others to keep in mind that are known for similar "do-it-yourself" philosophies are Gentoo and Slackware.

The greatest boon for starting with Ubuntu is these forums.  A search will provide you many answers, and when you actually need to ask something, you will quite often get several responses within a few minutes.  It's also the nicest and most welcoming community I've ever seen on the internet.  Even though I no longer use Ubuntu, I still come hear to ask questions about generic Linux-y things.

Welcome to the forums, and I hope your journey fairs well!

---

