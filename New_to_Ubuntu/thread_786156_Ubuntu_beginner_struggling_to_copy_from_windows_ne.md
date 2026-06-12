---
title: "Ubuntu beginner struggling to copy from windows network share"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by hawse1978 on 2008-05-07
Hi

I am a complete Ubuntu beginner, and recently installed Hardy Heron on my laptop. All was going well until I needed to copy files from the windows network at the office. I can browse network, see the domains and listed servers, but on selecting one I don't see the available shares like I did on XP.

When I try to access a shared folder using the full location i.e. smb://servername/sharename/ sometimes I see an error suggesting that the files/folders cannot be displayed. A reload usually fixes this. The more frustrating part is that I can't copy files over the network. Both drag and drop and copy/paste give me a dialog: "Error while copying". The details state either "Invalid argument" (but doesn't specify what or why) or "Didn't get stream descriptor".

Google hasn't been my friend with this problem. Any suggestions?

Not sure what extra info I can provide to help out, but if you need anything, please ask.

Many thanks,
Mike

---

### Post by Dani Filth on 2008-05-07
I also have a similar thread [here](http://ubuntuforums.org/showthread.php?p=4867618).
Another one is [here](http://ubuntuforums.org/showthread.php?p=4885560)

From what I have seen so far, unlike 7.10, when you just have to type in smb://LAN IP then all the shared stuffs will appear in the screen, in 8.04, you **have** to type in the full path of the specific shared folders/files (e.g "smb://LAN IP/ThisIsTheSharedFolder") in order to access them - which is quite annoying to myself as I use sharing over LAN a lot.

Hope they will get this fixed asap.

---

