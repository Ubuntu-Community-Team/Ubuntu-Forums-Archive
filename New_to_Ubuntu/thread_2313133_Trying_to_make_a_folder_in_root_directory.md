---
title: "Trying to make a folder in root directory"
date: 2016-02-09
forum: New to Ubuntu
---

### Post by tyler91 on 2016-02-09
Ok, so I just got this OS like a couple hours ago. I'm loving it btw. It has all the great things that windows makes you search for or purchase! Anyways back to the topic. So I went to download Tor browser for Linux and I did it. (Getting used to all the stuffz for linux) But I put it in my desktop and its just sitting there looking all ugly like a folder and shiz. So I thought I would just drag and drop it into some directory where all the programs reside but I couldnt find one so I thought I would just put it in the main computer directory. Well I dont know how to do this. I tried sudo mv commands but that all told me there was no such directory or files. Could you guys tellz me how I can move my Tor folder into the default programs location for ubuntu? Thnx a bunchez

---

### Post by Vladlenin5000 on 2016-02-09
Hi and welcome.

Although you can create directories outside your userspace, such action is really not recommended. And really that just your Windows mentality still making the rounds.
The package I think you downloaded is the TOR Bundle, right? If so, it's a self-contained program (Firefox with special settings and tweaks) and a configuration script which is what you use to actually run the TOR browser. I suggest you extract it somewhere inside /home/your_username instead of the Desktop (again, a bad practice coming from Windows which even in that OS is a bad practice). You can also create a desktop shortcut for the aforementioned script for your convenience or otherwise just open the folder and double-click it. DO NOT PUT IT ANYWHERE ELSE!!!

---

### Post by grahammechanical on 2016-02-09
> into the default programs location for ubuntu?

There isn't one. It is part of the many reasons why Linux is superior to Windows. And it means we have to stop thinking like a Windows user. We have to determine exactly what it is you have sitting on the desktop. Is it an icon for the Tor browser or is it a compressed file that contains the Tor browser? Is it the stuff that you downloaded but not yet installed?

In Ubuntu it is often best that we look in the Ubuntu Software Centre for the stuff we want to install. Especially if we  are new. And in the software centre I see 2 packages that might have been a better option. This is what is said about them

> Tor Browser Launcher is intended to make the Tor Browser Bundle (TBB) easier to maintain and use for GNU/Linux users. torbrowser-launcher handles downloading the most recent version of TBB for you, in your language and for your architecture. It also adds a "Tor Browser" application launcher to your operating system's menu.

When you first launch Tor Browser Launcher, it will download TBB from [https://www.torproject.org/](https://www.torproject.org/) and extract it to ~/.local/share/torbrowser, and then execute it. Cache and configuration files will be stored in ~/.cache/torbrowser and ~/.config/torbrowser. Each subsequent execution after installation will simply launch the most recent TBB, which is updated using Tor Browser's own update feature.

In Linux an application is installed not to its own folder but the several system folders and then there most likely will be a configuration in the users home folder.

The software centre takes care of all that.

Regards.

---

### Post by tyler91 on 2016-02-09
Well I searched Tor in the Software Center and only got a 2 star vadlia option whereas when I went to the actual website I got the 5.5.1 version for linux

I wanna cut to the chase and start using Terminal as much as possible though. Is there some way I can just configure it in terminal and it will go where it is supposed to?

---

### Post by Vladlenin5000 on 2016-02-09
What you downloaded is fine. Just follow the instructions I already posted because the bundle isn't to be installed. As the name implies it's a self-contained software meant to be used "as is", directly from the contained folder. You can even use it from a USB stick if you want.

---

### Post by tyler91 on 2016-02-09
I suppose I could just make a folder for it..

How do I change folder icons?

---

### Post by Vladlenin5000 on 2016-02-09
You aren't listening/reading, are you?
Please tell me what exactly you don't understand:
1. Download the compressed file *.tar.xz for your arrchitecture, 32-bit or 64-bit
2. Double-click and extract it to anywhere of your choosing inside your user's area -> /home/your_username
3. Find the extracted folder and inside double-click "Start..."

---

### Post by Geoffrey_Arndt on 2016-02-11
Tyler91,

OK, you're going to totally "hose" your "new OS" . . . . . because you don't seem to have the inclination to learn the ABC's of Linux.   It's not at all like Windows . . . . why not take just 2-3 days and view some youtube tutorials on linux (not how to install it, but how to use it).   Use the youtube search feature to narrow things down . . . like "using Ubuntu OS" or similar.

Otherwise, you'll easily break Ubuntu, and won't have a clue as to why, or how to fix it.

---

### Post by Vladlenin5000 on 2016-02-11
Tyler91,

The advice above is golden. Please try to understand its scope and implications.
Meanwhile please don't PM me saying I had too much coffee. OK, it's funny and I know at times I sound as grumpy as my avatar, but it's also quite puerile and uncalled for.

---

