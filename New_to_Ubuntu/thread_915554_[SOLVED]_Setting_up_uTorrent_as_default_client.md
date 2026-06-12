---
title: "[SOLVED] Setting up uTorrent as default client"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by RussW210 on 2008-09-10
I am trying to set up uTorrent as the default client for torrents.  When I click to download a torrent I get the option to "Open with utorrent.exe" however it doesn't actually open it with utorrent... it just deposits it in a tmp folder as a .torrent file.  In order for me to open it with uTorrent, I have to manually go into uTorrent, click open file, locate the file, and run it that way.

The first option I get actually when I click to download the torrent is to "Open with: Transmission BitTorrent Client (default)" which works fine.  But I would like to use uTorrent and for some reason it says Transmissing is DEFAULT.

I even tried clicking the button when uTorrent first opens, to set it as default, and that doesn't do anything.

Can someone help?

---

### Post by Zzl1xndd on 2008-09-10
I assume your using Wine to run uTorrent? I think you would have to download a torrent file right click go to properties, then go to openwith, then custom command, then browse into your Wine folder then select uTorrent.

For the Record I would Advice against using a windows program for this when there are a number of good Linux programs, I like Deluge myself.

---

### Post by RussW210 on 2008-09-10
Oddly, when I locate the utorrent.exe in my home folder and click to open with under custom, it says: Could not find application.  Could not find '/home/russell/Desktop/utorrent.exe' even though it is there.

---

### Post by Zzl1xndd on 2008-09-10
I wasn't sure if that would work, I would really suggest using a native Linux Application rather then a Windows one.

---

### Post by mewithafez on 2008-09-10
Yeah, the problem is that uTorrent is a program for windows so it won't work in Ubuntu without this thing called WINE you don't really want to try yet.

**Transmission** is the included torrent client in Ubuntu and is an easy to use lightweight program. I'd say give Transmission a shot and if you want to try another torrent client there are some more in Add/Remove Programs.

---

### Post by hyper_ch on 2008-09-10
why don't you use a native linux torrent client?

GUI ones:

Transmission
Deluge
KTorrent
Azureus


Cli:

rtorrent

--> P.S.: rtorrent just rules ;)

---

