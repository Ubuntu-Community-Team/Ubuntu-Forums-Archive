---
title: "iso reader for ubuntu hardy?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Shnooky on 2008-04-27
is there an iso reader for ubuntu hardy, like virtual clone drive?

help...send a link or give info plz

thx

-shnooky

---

### Post by Tatty on 2008-04-27
I believe you can mount the .iso just as you would a partition:

[https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso)

---

### Post by vishzilla on 2008-04-28
gISOMount is a GUI to mount ISOs you can also do it with the command line as mentioned in the above link

---

### Post by Can+~ on 2008-04-28
You can mount an image just as mounting a Hard disk.

Now that I think about it.. I could build a simple utility for this on python. Now I have something to do :KS. Thanks for the idea.

---

### Post by Shnooky on 2008-04-28
how do i use gISOMount

---

### Post by vishzilla on 2008-04-29
its pretty simple. on starting gISOMount select the ISO file from its location and choose a mount point like /media/iso and click on mount
you have to create the directory /media/iso first using the root privilege

---

### Post by marcusfurius on 2008-05-14
You could try [this application]("http://www.marcus-furius.com/?page_id=14"). It is designed specifically for Ubuntu, installs via a deb installer, has a simple to use GUI and mounts ISO, IMG, BIN, MDF and NRG Images, and doesn't require a password to mount images.

---

### Post by Oldsoldier2003 on 2008-05-14
you can also extract an iso using fileroller/archive manager. Im pretty sure i didn't install any iso specific packages. just right click and extract here from within nautilus.

---

### Post by grifter13 on 2008-05-14
> **Shnooky said:**
> is there an iso reader for ubuntu hardy, like virtual clone drive?

help...send a link or give info plz

thx

-shnooky

I think this is the answer to your question.  Say your iso is called mycd.iso then in a shell:

[COLOR="Blue"]mount -t iso9660 -o loop /some_dir/some_where mycd.iso
[/COLOR]
now its part of the file system.  If its a DVD then you can:

[COLOR="Blue"]xine|mplayer DVD://some_dir/som_where[/COLOR]

and it should play (assuming you have the right packages installed).  Otherwise, use it as any regular file directory (naturally there is no writing in the directory).  I hope this is the answer that helps you.

grif.

---

