---
title: "Hercules Mainframe Emulator"
date: 2006-01-19
forum: Repositories &amp; Backports
---

### Post by Spyromaniac on 2006-01-19
I want to be able to use the latest version of the mainframe emulator Hercules v3.03 see [http://www.conmicro.cx/hercules/](http://www.conmicro.cx/hercules/) but synaptic package manager only shows an old version v2.17.  How do I install the latest version? 

Thanks in advance.

---

### Post by computer_user_au on 2007-01-21
Hi, 

Try this article from debian admin website: [http://www.debian-administration.org/articles/484]("http://www.debian-administration.org/articles/484")

To install on Ubuntu Edgy Eft, change command: [COLOR="Red"]aptitude install hercules[/COLOR] to command: [COLOR="Red"]sudo apt-get install hercules
[/COLOR]
Then just follow the instructions in the article, e.g:

sudo apt-get install hercules
mkdir /etc/hercules
cd /etc/hercules
......

Enjoy...

---

