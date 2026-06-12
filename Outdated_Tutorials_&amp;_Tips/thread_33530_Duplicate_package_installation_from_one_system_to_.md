---
title: "Duplicate package installation from one system to another"
date: 2005-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by gmc on 2005-05-11
Hello Folks,

In my travels, I came accross this little tip that I thought you might find useful. Let's say you install Ubuntu onto a system and you want to setup another system with exactly the same packages installed. Try this

Create a list:

System1# dpkg --get-selections \* >installed-packages.txt

Use that list to install it on another computer:

System2# cat install-packages.txt | dpkg --set-selections
System2# dselect install remove

You could copy the "installed-packages.txt" onto a floppy/usb drive or even use ssh and scp/sftp the file to the new system.

Hope someone finds this useful. I did when I setup to identical servers for my home network.

G.

---

### Post by Zelut on 2005-05-11
That does sound like something useful.  I have a dell box (I didn't buy it, dont blame me!) and a notebook that both should have roughly the same packages.  That'd be a much quicker way than installing manually.  

Thanks!

---

