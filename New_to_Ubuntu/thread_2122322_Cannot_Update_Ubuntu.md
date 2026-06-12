---
title: "Cannot Update Ubuntu"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by EDLIU on 2013-03-04
Hi,

I changed the default settings in the "Software Sources". I changed the "download from" from the default mirror servers to servers for the US.

The system crashed when I tried to save the changes. And after reopening the Software Sources, the "DOWNLOAD UPDATES" disappered.

I then tryed to change the "download from" settings back to "the best mirror servers", but still cannot update the system.

So, what should I do now? How do I get my system to check for the latest updates, so I can download and install them?

And, what are the differences between a "local server" and "main server", or even "servers for US"?

Thanks.

Ed

---

### Post by ManamiVixen on 2013-03-04
Local server is a server on your network, main server is the one at Canonical's headquarters, and US servers are duh, in the United States.

sudo gedit /etc/apt/sources.list

What does it contain? Print it here.

Also, have you tried sudo apt-get update in terminal?

---

### Post by EDLIU on 2013-03-04
Hi,

I have found the "Software Updater". And the problem is solved.

But there's still one question. How do I "change the download from back to the default local servers"? How do I know which server Ubuntu used at the first time when system is installed.

And, does the software on main, local, and for US, servers all the same? (such as language packs)

Thanks.

Ed

---

### Post by ibjsb4 on 2013-03-04
All servers are not the same.  Some get updated before others and some are way faster than others.  I would take a look at the list of servers for the United States.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by Mikhail.Inspired on 2013-03-04
If you want to, there is an option to "choose best server" in the software-settings.

---

