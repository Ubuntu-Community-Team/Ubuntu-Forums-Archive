---
title: "installing drivers for edimax EW-7128G wireless card"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Xiong Chiamiov on 2008-07-26
So, I received an email from one of our members asking how to go about installing the drivers for an edimax EW-7128G PCI card on Hardy Heron (7.10).  I won't post the contents of the message here to respect their privacy, but it seems like the computer in question has no other method of accessing the internet (always makes it hard, doesn't it?).  A net connection is available on another computer, however, and they can transfer files between the two on CD.

Now, it's been a while since I've used that card, since my computer's now next to my router and thus connected via wire, but I'll see what I can remember.

This card uses the [rt2500 chipset]("http://ralink.rapla.net/"), which should be supported automatically in Gutsy and later.  All you should need is the rt2500 packages, which you should be able to get off of [http://packages.ubuntu.com](http://packages.ubuntu.com) (it's down atm, so I can't check).

However, if it doesn't, there are a few places to look.  One is [the entry on the wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500"), which also provides a few links at the top.  There are [some instructions]("http://ubuntuforums.org/showthread.php?t=563547") on how to use the Windows drivers through ndiswrapper here on the forums (though that's not the first option I'd try), and also some notes at the bottom (very bottom, it's quite long) of [this bug page]("https://bugs.launchpad.net/ubuntu/+bug/34902") on how to compile the newest testing version from source.

Those last options are quite a bit of a challenge for someone who's new, so I'd first try just plugging it in and seeing if it works.  I'd check and see if it shows up in the [network admin]("https://help.ubuntu.com/community/WifiDocs/WirelessNetworking"), and if not, start going down [this list]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") of commands.  Specifically, post the output of lshw and lspci.  The terminal can be found in the menu at Applications menu -> Accessories -> Terminal, then just type these two commands:
```

lshw > lshw.txt
lspci > lspci.txt

```
The > indicates that the output will put to a file called lshw.txt and lspci.txt, respectively.  You can then go ahead and open those files up and copy+paste them in here.

---

### Post by eriqjaffe on 2008-07-27
I have that card in my living room system (mine's got the RT61 chipset), and Feisty had no trouble detecting it, and I was able to set it up without any headache whatsoever.

---

