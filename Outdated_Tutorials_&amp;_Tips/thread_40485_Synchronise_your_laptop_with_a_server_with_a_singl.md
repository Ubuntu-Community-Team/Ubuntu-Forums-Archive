---
title: "Synchronise your laptop with a server with a single click"
date: 2005-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by jonny on 2005-06-09
Do you need to keep a laptop synchronised with a server or a mounted filesystem, such as a removable storage device?  If so, read on.

At work, I use ubuntu on a laptop for most tasks.  I'm not always connected to the office network, so I keep all my documents on the local hard drive.  But keeping important files on a laptop is a bad idea – backups are difficult, and my colleagues can't easily share my documents.  So I also keep a copy of my data on an office server.  

Sometimes, though, I need to work collaboratively on a document.  That means that the master copy is on the server – but I also like to keep a copy on my laptop for when I'm working offline.  This creates a problem for me: which files do I need to copy to or from the server?  Sometimes I get muddled up, and I've lost work by overwriting new documents with older ones.  So, in a moment of exasperation, I wrote a brief script to help me.

This script synchronises my laptop with the server.  If the local file is newer, it copies it to the server.  If the remote file is newer, it copies it to my laptop.  If both files are the same, it ignores them.  I've been using the script for a few months and it works flawlessly for me, so I thought I'd share it.

First, you need to decide which directories you want to synchronise.  I keep my local files in a directory called /home/jonny/Briefcase, and I mount the remote files in a directory called /home/jonny/RemoteBriefcase (visit [www.ubuntuguide.org](www.ubuntuguide.org) for advice if you don't know how to mount a network drive).

Next, you need to create a script.  Open Text Editor and enter this code```
#!/bin/bash
cp -rpuv ~/RemoteBriefcase/* ~/Briefcase/
cp -rpuv ~/Briefcase/* ~/RemoteBriefcase
```Save it somewhere, and create a shortcut to it on your Gnome panel.  Now you have one-click synchronisation.

This script comes with a two provisos.

 - First, be aware that makes no attempt to warn you if both the server and the local version have been edited since you last synchronised.

 - Second, some remote filesystems won't let you backdate a file's last edited date.  If you edit a file locally and then synchronise, the server will timestamp it when you synchronise.  That means that the file will then be copied back to your laptop next time you synchronise.  This is harmless, but could cause concern if you aren't expecting it to happen.

---

### Post by nocturn on 2005-06-09
[QUOTE=jonny]
This script comes with a two provisos.

 - First, be aware that makes no attempt to warn you if both the server and the local version have been edited since you last synchronised.

 - Second, some remote filesystems won't let you backdate a file's last edited date.  If you edit a file locally and then synchronise, the server will timestamp it when you synchronise.  That means that the file will then be copied back to your laptop next time you synchronise.  This is harmless, but could cause concern if you aren't expecting it to happen.[/QUOTE]

Thanks for this howto, it will benefit many users hopefully.
Maybe it would be better to use rsync instead of cp, this will only copy over changed files and can handle deleted files on the source too.

--edit, two way syncing will not work with rsync --delete option

---

### Post by thee_walrus on 2005-07-31
I prefer unison. It works extremely well, and addresses both of the problems your script seems to have. 

See the webpage here: [Unison Home Page](http://www.cis.upenn.edu/~bcpierce/unison/)

It's in the universe repository, so just

```
apt-get install unison
```

---

### Post by Cuppa-Chino on 2006-03-03
[QUOTE=thee_walrus]I prefer unison. It works extremely well, and addresses both of the problems your script seems to have. 

See the webpage here: [Unison Home Page](http://www.cis.upenn.edu/~bcpierce/unison/)

It's in the universe repository, so just

```
apt-get install unison
```[/QUOTE]

can this help me with the following problem? I have continue using Window$ and do want to switch back & forth everytime I send some emails (my provider does give my IMAP).

so what I would like to do is everytime I LOG IN or OUT of either Window$ or Ubuntu that my entire Thunderbird folder structure is synchronised - can unison help?

---

