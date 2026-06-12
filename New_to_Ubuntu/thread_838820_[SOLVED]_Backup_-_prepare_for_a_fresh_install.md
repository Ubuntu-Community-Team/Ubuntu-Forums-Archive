---
title: "[SOLVED] Backup - prepare for a fresh install"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Dani Filth on 2008-06-23
Hi folks,

I've been using Ubuntu since 7.04 and what I did to get the latest version is upgrading. But recently, I was advised that a fresh install would normally work better than an upgraded one. So I think I will try a fresh install on my laptop.

What I want to know is how to back up the stuffs that I need so that I can use them (as the way they are now) in the newly fresh install, like:
- Internet Browser (I use Opera) cache, RSS feeds, bookmarks, etc.
- Pidgin Log (I have 'Logging' enabled), if you want more info, it's my Yahoo account.
- Other packages, tools... which I installed, do I have to re-install all of them again with the fresh install?

Thanks in advance,
Cheers :D

---

### Post by tinny on 2008-06-23
Backing up your /home directory should be enough. For your next install you should look at setting up a home partition ([http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")).

The home dir should have all the personal settings etc... that you need.

---

### Post by Dani Filth on 2008-06-23
Thanks tinny for your reply.

Is /home alone enough for everything? Because I tried to look for "pidgin" in the /home folder (I chose to view the hidden files as well) and I couldn't find it anywhere.

Cheers

---

### Post by tinny on 2008-06-23
I believe the Pidgin config / settings files are located in <your home>/.gaim (this is a hidden folder). So backing up your home folder “should” be fine.

Good luck :-)

---

### Post by Dani Filth on 2008-06-23
Sorry but I couldn't find either ".gaim" or ".pidgin" in the home folder - and I selected "Show hidden files" already
:(

---

### Post by RiceMonster on 2008-06-23
I think pidgin is ~/.purple

---

### Post by Dani Filth on 2008-06-23
Thanks RiceMonster, that's exactly what I'm looking for :D

Cheers for all your helps :popcorn:

---

