---
title: "Application for programming a ComGenius remote - Maybe sniffing the windows software?"
date: 2006-11-12
forum: Programming Talk
---

### Post by daller on 2006-11-12
Hi There,

In my company, we are forced to use Microsoft Windows for only one reason:

The software to program the remotes we sell, only work on Windows.

It doesn't work in Wine because it requires IE, .NET etc...

I'm thinking about sniffing the data-stream to the remote. (It's a serial-cable - connected to my laptop through a usb-serial cable.)

Can this be accomplished? - or is there a project for this already?

Please help! - This is the only thing keeping us from the 100% switch to Linux!

---

### Post by lloyd_b on 2006-11-12
Just did a quick search on [SourceForge]("http://www.SourceForge.net"), and found several applications to do what you want.

Just go to that link, and search for "serial sniffer".  Find the one that best fits your situation....

Lloyd B.

---

### Post by daller on 2006-11-12
Hi,

Can't seem to find a Windows sniffer... It's all for Linux...

---

### Post by lloyd_b on 2006-11-13
> Can't seem to find a Windows sniffer... It's all for Linux...

Take a linux (any flavor) box with two serial ports.  Hook up one serial port to the Windows box you normally use to program those remotes.  Hook up the other serial port to the remote.  Then use a linux program to pass messages from on port to the other, recording each message (at least one of the serial sniffers from SourceForge is designed to work with this configuration).

I don't even know where to look for a pure-Windows method of getting the info you're looking for...

Lloyd B.

---

