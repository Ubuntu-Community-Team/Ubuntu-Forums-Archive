---
title: "newbie: how to install deluge torrent client"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Sudan on 2008-04-24
Ubuntu 7.04

I installed Ubuntu OK.  Have never used it and know very little about Ubuntu.  I'd like to install a torrent client as my first application.  Looking at these forums it appears Deluge is an OK torrent client to use.

I don't know how to find Deluge to install.  I am reading about the package manager and following  directions

[http://monkeyblog.org/ubuntu/installing.html#package_manager](http://monkeyblog.org/ubuntu/installing.html#package_manager)

I have searched the Synaptic Package Manager for "deluge" but it found nothing.

Do I need to download (the windows way) from the deluge web site and then somehow use the package manager to install it?

I'm really lost here.
Thanks for any help.

---

### Post by Bodsda on 2008-04-24
Ok,some background, the Synaptic Package manager is your boxo toys,    but you have to have all the boxes (repositories) enabled. To enable repositories go into synaptic and click preferneces repositories, and tick all boxes along all tabs except maybe the cd and non-free if you dont want that (it is free tho)

next search synaptic again for deluge or transmission which is default in the latest ubuntu

if youhave found it simply click mark for installation then click apply

If youknew it was definately in your repositories you could download and install deluge like this 

in terminal type
```
sudo apt-get install deluge
```

but aswe dont know if its there yet just leave that last part out

Hope this helps

oh, why 7.04 not 8.04?

---

### Post by otrojake on 2008-04-24
Deluge should be in the repositories (Synaptic should be finding it).  My guess is that with the release of Hardy today you're not getting a response from the servers since they're getting hammered.  You could either wait until tomorrow or the next day for the traffic to die down or you could change what servers you're hitting for updates.  To do that System-->Administration-->Software Sources.  Under the "Ubuntu Software" tab look for a "Download From:" dropdown box.  Click "other there" and then "select best server."

But if that doesn't work, my guess is that Deluge isn't in the Feisty repositories.  And then maybe today is the perfect day to upgrade to Hardy. ;)

---

### Post by otrojake on 2008-04-24
Bodsda, that's not the correct package name.  It will be under deluge-torrent.  Like so...

```
sudo apt-get install deluge-torrent
```

---

### Post by wt8008 on 2008-04-24
If all else fails, Deluge has deb packages for download on their site.

[http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by apostate on 2008-04-25
> **wt8008 said:**
> If all else fails, Deluge has deb packages for download on their site.

[http://deluge-torrent.org/](http://deluge-torrent.org/)

Deluge is *absolutely* in the standard Feisty repositories, and the last thing I would suggest is to update to Hardy right now.  The OP is new to Linux, the servers are slammed, and Hardy is still rough around the edges for a lot of people, myself included. I went back to 7.10 it was so rough in fact. A dist upgrade sounds good around...June.

Anyway: Just click on Application -> Add/Remove and search for Deluge. Make sure to change the drop-down box from "Supported Applications" to "All Available Applications".

Have fun!

---

### Post by mivo on 2008-04-25
> **wt8008 said:**
> If all else fails, Deluge has deb packages for download on their site. [http://deluge-torrent.org/](http://deluge-torrent.org/)

This is the best course of action anyway. Deluge's development is relatively fast, so new versions appear quite often and you'll want the latest stable versions for security fixes and other improvements.

---

### Post by Sudan on 2008-04-25
> **mivo said:**
> This is the best course of action anyway. Deluge's development is relatively fast, so new versions appear quite often and you'll want the latest stable versions for security fixes and other improvements.

This is what I ended up doing.  I just stumbled upon doing it that way.  I must say I'm impressed with how easily the install went.

Much thanks to all who responded.  There are multiple ways to do one thing in Ubuntu I see.  I've learned something from each post and appreciate it.

---

### Post by Bodsda on 2008-04-26
sorry bout the wrong package name

---

