---
title: "Volume Randomly Fluctuates on certain applications"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by Zerp64 on 2013-11-20
This is a pretty crazy - and annoying - problem. With some applications, usually games, my volume will start to fluctuate rapidly and randomly all on its own after about a dozen seconds spent running the program. This has happened on every *buntu install since 11-point-something, multiple editions of Linux Mint (including LMDE), and other distros, all fresh installs or liveCDs. And the weird thing is I can't find any connection between the applications. Katawa Shoujo, XBMC, certain WINE games, other applications I can't recall. Flash stuff seems fine, in and out of the browser. Music players like Cinnamon, Banshee and Rhythmbox are okay; I haven't seen any problems with those.

This problem has been bothering my for years, and it prevents me from using the applications this problem affects. When I first encountered the problem there was a workaround I found on google, using a terminal command (xset, something like that? A X.org utility, anyways) to disable the volume slider on my laptop. It was inconvenient, but it worked for a while, until some new ubuntu version came around and suddenly that fix didn't help anything. I haven't been able to try this workaround on recent installs though, since I can't find the fix any more. It took hours to find the thing the first time around.

There must be some shared library, or more likely audio driver issues, causing this problem. It doesn't happen on Windows 7, so I don't think it's hardware. I'm just at a total loss as to how I should fix this, or what the problem could be.

lshw shows my audio device as "5 Series/3400 Series Chipset High Definition Audio". This also happens when I use a DAC through USB. I'm convinced this is a software issue, not hardware. Right now I'm in the process of downloading Linux Mint 15 KDE to see if there's some weird DE bug that's causing this issue, something that I might be able to dodge by switching to KDE.

I'd be happy to provide any other info you might need. The bug has been bothering me for years, and it's incredibly frustrating when it suddenly pops up when I'm testing out new programs.

---

