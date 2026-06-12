---
title: "Accessing other partitions problems"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by BeMyManikin on 2011-12-17
On my comp I have windows and Ubuntu (Mostly because I wanted to try it out before switching it), and now it won't boot windows (but I don't really care because I can get most of the files from using ubuntu). Now, it seems to have unmounted the rest of my hard-drive and I can't normally access the data on the windows partition. It says this when I go to disk utility to find the partition to access the data:

> (nautilus:3501): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


In disk utility, I've tried remounting it, but I doesn't show up on the dash home or anything. I actually don't know the root password for it, but I was wondering if there was another way to get into root to enable the user sharing? or just forget it all and reformat it all like my brother said?

---

### Post by BeMyManikin on 2011-12-17
Take that back, I do know the pw for root, had some time to think about it. So, now the rest does apply.
Thank you

---

### Post by amjjawad on 2011-12-17
Hello and Welcome to Ubuntu Forum :)

Is this Normal Installation? or Wubi Installation?

---

### Post by BeMyManikin on 2011-12-18
Normal I'm pretty sure, I don't know what wubi is...

---

### Post by spiky001 on 2011-12-18
> **BeMyManikin said:**
> Normal I'm pretty sure, I don't know what wubi is...

wubi is when it is installed within windows as opposed to it,s own partition Dual boot (next to windows)

---

### Post by amjjawad on 2011-12-18
> **BeMyManikin said:**
> Normal I'm pretty sure, I don't know what wubi is...

Wubi:
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
[http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer](http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer))

How to avoid Wubi:
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

### Post by amjjawad on 2011-12-18
I tried to google the error message you got and I found 4 results only, two are from your thread (this one) and a website looks like it's for you too.

Assuming you have a Normal Installation NOT Wubi and Windows Partition is still available, try to boot your machine from the LiveCD or LiveUSB and rescue your files that you need.

Also, check this: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
This will tell us what is where.

---

### Post by BeMyManikin on 2011-12-19
Well, before having to do that, is there a way to enable sharing like one of the prompts says to do on my first post?

---

### Post by BeMyManikin on 2011-12-19
Thank you for all your help, but I accidentally found a way to restart sharing. [URL="https://help.ubuntu.com/community/Fstab"]This is the website that helped me.
[/URL]

---

### Post by amjjawad on 2011-12-21
> **BeMyManikin said:**
> Thank you for all your help, but I accidentally found a way to restart sharing. [URL="https://help.ubuntu.com/community/Fstab"]This is the website that helped me.
[/URL]

Ok, glad you managed to fix it :)

Well done!

---

