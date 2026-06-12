---
title: "Command Line Back Up with Tar"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by gray123 on 2012-08-17
hi,      having got my system setup. I want to back up the system there are various graphical ways but command line tar is easy enough. I found these commands online     tar cvpzf backup.tgz --exclude=/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt /     tar xvpfz backup.tgz -C     works well enough haven't had to restore yet of course but my question is why would it be set up to exclude the system file tree.  Cheers, G

---

### Post by Wim Sturkenboom on 2012-08-17
/proc is dynamic, so no need; same probably applies to /sys (not sure)
/mnt can have mounted devices (e.g. an external HD) so why include it; same would apply to /media, by the way.

There should not be anything in lost+found, so why backup. And if there is anything in there and you have not recovered it yet, it was obviously not that important.

---

### Post by Lars Noodén on 2012-08-17
You'll probably want to also skip /dev and /run

---

### Post by mapes12 on 2012-08-17
I backup my system with [Remastersys]("http://www.remastersys.com/"). The only thing I keep in /home are my application system files. All my other stuff goes onto a separate partition. That way the Remastersys custom .iso comes in at about 2GB. Easy to install onto a DVD-R or thumb drive and I can then have my setup on any machine that has supported hardware in no time at all.

I've tried the tar option but it didn't restore properly for me.

Good luck :guitar:

---

### Post by newb85 on 2012-08-24
> **mapes12 said:**
> I've tried the tar option but it didn't restore properly for me.

It probably didn't.  It's a widespread oversight not to use the -g option when backing up a system with tar.  If the -g option isn't used, the restore will *not* remove files that don't belong.

I'm in the process of creating a howto on backing up with tar that will include this.

---

