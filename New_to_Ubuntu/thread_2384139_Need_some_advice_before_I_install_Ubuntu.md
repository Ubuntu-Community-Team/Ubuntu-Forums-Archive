---
title: "Need some advice before I install Ubuntu"
date: 2018-02-02
forum: New to Ubuntu
---

### Post by dracolunellc on 2018-02-02
I have some unique situations to address with my Ubuntu installation.  I am a quadriplegic user and so I have to use several adaptive devices in order to operate my computer efficiently.

I use a device called a Quad Stick to replace the mouse (it goes by that name if anyone else would find a game controller/mouse useful) that device appears as a standard mouse so there will be no problem with it under Ubuntu.

Another thing that I use frequently (heck I used it to write this email,) is Dragon naturally speaking.  As of this juncture I do not believe they make a Ubuntu compatible version.  When I use something like Wine I am curious if I will only be able to use Dragon in the Windows environment.

I know just enough about what I want to do to understand it might be possible, but I need to talk to people with more experience than I.

Thanks,
Jacob

---

### Post by #&amp;thj^% on 2018-02-02
No first hand experience with Dragon but copy and paste seem s to work.
From Wine: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=2077](https://appdb.winehq.org/objectManager.php?sClass=application&iId=2077)
> Dragon Naturally Speaking  is high accuracy, full speed voice recognition software. Originally developed by Dragon Software was bought by ScanSoft now called Nuance. It can deliver up to 98% accuracy at full speed dictation.

Dictation works only within the wine environment. _Users should expect to use the application primarily for text recognition into wine's Notepad or NatSpeak's DragonPad.  **Text can be cut and pasted into any application.**_e
Anyway Best of luck to you, hopefully someone that has used it daily will chime in.

---

### Post by QIII on 2018-02-02
Hello!

The WineHQ database only shows test results through version 10 of Dragon Naturally Speaking.  That's obsolete.  But judging from the dismal test reports for earlier versions, I suspect version 13 would be a bust.

It is possible you might be able to use it in a Windows virtual machine guest on a Linux host, but that might be more trouble than it is worth.

You might be able to find a Linux alternative, but I wouldn't expect much love.

Have you considered running Ubuntu in a virtual machine so you can get your fix of that without giving up what you have already developed some skill with under Windows?

---

### Post by oldfred on 2018-02-02
Ubuntu has a variety of Accessibility options.

[https://help.ubuntu.com/community/Accessibility](https://help.ubuntu.com/community/Accessibility)

Not sure if any of those settings may help or not.

If you are able to contribute:
[https://wiki.ubuntu.com/Accessibility](https://wiki.ubuntu.com/Accessibility)

---

### Post by dracolunellc on 2018-02-02
Actually the virtual machine idea is one I might look into.  Considering the machine I am building is a X 299 Asus board with an I-9 processor, and 128 GB of RAM, I am not worried about having enough processing power for what I want to do.  (In case you could not tell this is not the first time I have built a computer ;))

I also intend to look into doing auto CAD and some 3D work on this machine as well.  So with my situation I need to explore the options available to me.  I have been running Windows 10 Pro for quite a while but it has become increasingly unstable in my applications, so I am looking at all the options and trying to touch base with you to figure out what I can do with reality.

Thanks,
Jacob

---

### Post by mastablasta on 2018-02-05
for autocad you will want to stay on Windows or perhaps Mac OS will have something.

---

### Post by leunam12 on 2018-02-05
I have Dragon Naturally Speaking 12 working with WINE, the hard part was to install the .NET 4.0 environment that is required for the program to run, but now it works fine, it only works with Microsoft Word and other WINE programs, though. Version 13 is a lot better than version 12, I have it on Windows, and I have never tried to install it on Linux with WINE, but it is worth trying because it is way more accurate. I can dictate a 12-page document with very little corrections with my heavy spanish accent. With version 12 I have to do a lot of corrections.

---

