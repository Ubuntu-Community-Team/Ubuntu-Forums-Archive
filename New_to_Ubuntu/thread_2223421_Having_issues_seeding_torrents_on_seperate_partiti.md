---
title: "Having issues seeding torrents on seperate partition"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by NA3OH on 2014-05-11
I'm still working out bugs in my Ubuntu installation which is dual booting with Win7 Ultimate. 

I'm using the Deluge 1.3.6 and it looks like I can't seed anything that isn't on my Ubuntu partition.The first one on the list is seeding perfectly fine because, I suspect, it's saved onto my Ubuntu partition. All of the other ones are on my Media partition and therefore come up with an error. Force rechecking doesn't work either. What happens when I start up the client is that they all begin downloading for about 10 seconds and then it turns up as error 0%

 [ATTACH=CONFIG]253053[/ATTACH]

Any simple way to make this work?


EDIT: Just found this out. So I downloaded a torrent and set the files to save on the partition that I've been having trouble with. After choosing to save it there, all my other torrents that previously read "Error" started downloading and I just force rechecked them and now they're seeding. Weird.

---

### Post by Drone4four on 2014-05-11
If you boot into Ubuntu, separate partitions aren't mounted automatically.  I experience this to.  Like if I were to reboot and start Vuze, it wouldn't be able to access my separate partitions until I activate them.  To get my torrent client to access my torrents, I'd have to open Nautilus and select the partition in the left hand pane to mount them.  There has gotta be a way to have the partitions mounted at boot.  I'd guess that this would involve tinkering with /etc/fstab.  I'm not sure if I am being very clear describing the real problem.  That's because I'm still a noob. :)

---

### Post by NA3OH on 2014-05-11
I'll look into auto-mounting it. So far the best way I've found is to right click one of the torrents that I've already downloaded using the "move storage" option, but I just keep the download location where it is. After that it is then able to detect all my other files on that partition.

---

### Post by Vladlenin5000 on 2014-05-11
> **NA3OH said:**
> I'll look into auto-mounting it. So far the best way I've found is to right click one of the torrents that I've already downloaded using the "move storage" option, but I just keep the download location where it is. After that it is then able to detect all my other files on that partition.

That happens because when you do the first one it forces the system to mount the partition, obviously.
You have two options: Either you mount the partition - clicking it in the file manager will do it - before starting the torrent client or you make all the necessary changes in order to have that partition auto-mounted.

---

