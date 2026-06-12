---
title: "[SOLVED] run &amp;quot;sudo apt-get install syslinux mtools&amp;quot; offline"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by bapaknyaAnak2 on 2008-06-13
Guys,

Is it possible to run "sudo apt-get install syslinux mtools" while we are not connecting to internet ??

Please advice.

---

### Post by Grishka on 2008-06-13
> **bapaknyaAnak2 said:**
> Guys,

Is it possible to run "sudo apt-get install syslinux mtools" while we are not connecting to internet ??

Please advice.

nope. you'd have to get the packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and install with dpkg.

edit: but you need to download the packages from internet, of course. so basically there's no way to get packages from the net without being online, you know.

---

### Post by Xiong Chiamiov on 2008-06-13
Actually, you should be able to if said package is included on your Ubuntu cd and you have the CD enabled as a repository.  That said, someone I was trying to help the other day didn't have any success with that, but the command I think is
```

sudo apt-cdrom add

```
followed by a
```

sudo aptitude update

```

---

### Post by Joeb454 on 2008-06-13
It's possible to run it, you'd just get an error ;)

Like the post above - you'd need to download them from that site, or you could check out APTonCD :)

---

### Post by RomeReactor on 2008-06-13
Hi. Another option would be, if these applications are not in the Live CD or the Alternate CD (which you can then install by adding the CD as a repository), then you need an internet connection to download them--though you don't need to necessarily use your system.

Open Synaptic and mark the packages for installation, as you would normally do if an internet connection was available. Then go to 'File->Generate package download script'. Name the file whatever you like and save it. You can then move or copy that script to a USB device, go to another machine with an internet connection, and run the script, which will proceed to download the packages and the necessary dependencies.

Once you have the packages, move them to your Ubuntu system, again open Synaptic, and go to 'File->Add downloaded packages'. You'll be able to install them then. This solution has the added benefit of not having to search for the dependencies yourself.

---

### Post by bapaknyaAnak2 on 2008-06-14
What I mean was something like, we download the file and save it on to hard disk, then execute it afterward without being connected to internet.

I am sending this post from my "neighbor" computer.:(

---

### Post by cariboo on 2008-06-14
Using synaptic just check download files only in the window that pops up after you have clicked apply, then click apply again. When you move the files to your own computer just double click mtools first and gebi should pop up and allow you to install it, then install syslinux.

Jim

---

### Post by bapaknyaAnak2 on 2008-06-15
Guys,

DONE. It was easy. I did what RomeReactor said, just try to get the link of the files requested on internet. Go, to the link and downloaded the files and save it on my USB. After that just simply double click on the downloaded deb files and that's it.

Thank you for help guys :)

---

### Post by Joeb454 on 2008-06-15
Glad you sorted it out :) You can mark your thread as solved from "Thread Tools" at the top of this page

---

