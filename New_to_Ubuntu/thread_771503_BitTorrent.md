---
title: "BitTorrent"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by WBL on 2008-04-27
I just got my Inspiron 1525N fully configured running Ubuntu 8.04.  Everything works great!  :)

Anyways, I have some embarrassingly simple questions:

1.  What is BitTorrent?
2.  How can I get it on my Ubuntu 8.04 system and use it?

Thanks in advance.

-WBL

---

### Post by kamitsukai on 2008-04-27
Well im not very good at explaing things but there are many people that already have, so here is some reading material

Ubuntu community help page:
[https://help.ubuntu.com/community/BitTorrent](https://help.ubuntu.com/community/BitTorrent)

and a forum post:
[http://ubuntuforums.org/showthread.php?t=136032](http://ubuntuforums.org/showthread.php?t=136032)

hope this helps a little bit

---

### Post by LaRoza on 2008-04-27
BitTorrent is a very good way of sharing files. 

The default BitTorrent application in Ubuntu is called Transmission.

Instead of a single server, BitTorrent allows many people to serve pieces of files, which makes for very fast downloads without burdening a single server.

---

### Post by hums07 on 2008-04-27
Default torrent application for Hardy is **Transmission**. Previous Ubuntu releases (such as Gutsy) uses BitTorrent. All application perform similar task, just different way to display things. If you still want BitTorrent, you can install it from Synaptic I think.

---

### Post by nofrendo on 2008-04-27
Basically what you need to do is download .torrent files from what is called a bittorrent tracker. The largest one currently is called The Pirate Bay. These are pointer files that tell your bittorrent client where to retreive the file that you want.

[www.thepiratebay.org](www.thepiratebay.org)

Of course, you are only going to use bittorrent to download linux distros right?

Edit: And Gutsy used Azureus if I'm not mistaken?

---

### Post by kamitsukai on 2008-04-27
and generally once you have used torrents for a while you work your way up from public torrent trackers such as thepiratebay to somthing like demonoid (which is a low level private tracker) which gradually encourages users to share more of there bandwith via seeding which improves the overal speed of these linux distros which everyone downloads...

---

### Post by michaelharg on 2008-04-28
I upgraded from Gutsy to Hardy but the default Bittorrent client hasn't changed, how do I change this to Transmission? Thanks..

---

### Post by stchman on 2008-04-28
Use torrents cautiously.  A lot of torrents are for downloading illegal or copyrighted software, movies, music etc.  There are many people that think they cannot get into trouble downloading things by use of torrents, but I have read that ISPs are logging IPs when illegal material is downloaded.

A good torrent client for Ubuntu is KDE's KTorrent.  Very nice.

---

### Post by AndyCooll on 2008-04-28
> **michaelharg said:**
> I upgraded from Gutsy to Hardy but the default Bittorrent client hasn't changed, how do I change this to Transmission? Thanks..

I'm assuming that Transmission has installed successfully, it's just not set as the the "default". 

If it isn't displaying under Applications > Internet you can add it to the listings by going to System > Preferences > Main Menu and then selecting Internet. It's likely that it doesn't have a tick against it to display it in the listings, so do so now.

If it isn't set as the default, the easiest way to change this is to right-click on a file (a .torrent in this case), choose "Properties" and then choose the "Open with" tab. You should then be able to choose the default application to open that type of file with.

:cool:

---

