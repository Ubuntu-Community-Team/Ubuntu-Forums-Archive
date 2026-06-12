---
title: "apt-get interrupted"
date: 2005-02-20
forum: Repositories &amp; Backports
---

### Post by dskloet on 2005-02-20
Hi,

I interrupted (Ctrl-C) apt-get while it was downloading java1.5 and since then, when I run apt-get it says:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

After I do what it says, apt-get seems to work until I reboot my computer. Then problem returns again. Is there a way to fix this?

thanks,
David

---

### Post by az on 2005-02-20
sudo apt-get -f install

---

### Post by Kujane on 2005-02-20
This is a desperate call for help. Sorry to bug you.....HOW do I post a message on this forum. I am completely new to this. There is no "post new message" or  anything like it. I am logged on but this forum tells me nothing.

---

### Post by dskloet on 2005-02-20
[QUOTE=azz]sudo apt-get -f install[/QUOTE]

$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


@Kujane: At the forum-index page of each subforum there is a "New Thread"-link.

---

### Post by madcowsonthewall on 2006-07-01
So, 

sudo dpkg --configure -a

---

### Post by foxiness on 2006-07-05
February 20th, 2005 

:)

---

### Post by pomegranate on 2006-08-27
Sorry to resurrect and old thread, but I'm having this problem too. I've tried following the method above, but the problem is that when I do so, the process (I'm trying to install the MS core fonts) connects to an incredibly slow server, and the install process gives up on some or all of the packages because they're so slow to download. I eventually kill the process by closing terminal. How can I get rid of this, so that I don't keep getting bugged by it? I'm not bothered about installing the fonts.

---

### Post by Petos on 2007-05-28
try this try sudo dpkg --configure -a && sudo apt-get -f install

i am sure it will work

---

