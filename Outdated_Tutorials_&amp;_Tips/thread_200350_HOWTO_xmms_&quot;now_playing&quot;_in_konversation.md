---
title: "HOWTO xmms &quot;now playing&quot; in konversation 0.19"
date: 2006-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by MetaMorfoziS on 2006-06-20
There are 2 ways to do it, the first is sometimes not work for me.

I,
 - Download the latest /media script from SVN [http://websvn.kde.org/trunk/extragear/network/konversation/scripts/]("http://websvn.kde.org/trunk/extragear/network/konversation/scripts/")
- sudo apt-get install python-xmms
- sudo mv /usr/share/apps/konversation/scripts/media /usr/share/apps/konversation/scripts/media_old
- sudo cp <pathtoyoursvnmedia> /usr/share/apps/konversation/scripts/
- Restart konversation, and enjoy.

II,
It's 100% work, for all time:
- sudo apt-get install logjam-xmms (If you haven't got it, you need to add some repost to your sources.list for ex: [http://www.ubuntu-nl.org/source-o-matic]("http://www.ubuntu-nl.org/source-o-matic"))
- Start konversation, go : Settings -> Configure Konversation -> Command Aliases
- Add: /exec cmd echo "XMMS: `logjam-xmms-client`" to any alias that you want...

It is not the best professional way, but it works:)

---

### Post by shag on 2008-01-22
Version 1 works great for me.

---

