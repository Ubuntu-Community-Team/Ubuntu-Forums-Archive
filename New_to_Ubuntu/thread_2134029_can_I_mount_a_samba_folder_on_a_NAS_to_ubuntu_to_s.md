---
title: "can I mount a samba folder on a NAS to ubuntu to speed up file moving?"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by roseysdaddy on 2013-04-09
I have a TB standalone NAS that I would like to copy the files on that to on my ubuntu server.  When I do copy/paste using windows 7 access to both samba directories (one with the files on the NAS and the destination samba folder on the ubuntu server)  it says it should only take like 8 or 9 years to complete the transfer ( i kid, more like 15 hours ) I was wondering if i can somehow move the files directly as Im pretty positive that the introduction of the third machine (windows) is what is slowing the process down so much.  The same thing happens when copying files from different folders on the ubuntu server through windows, but is 1000% faster when using the mv command from a terminal.  Anyway, is there anything I can do?


im using 12.04 ubuntu server.

---

### Post by papibe on 2013-04-09
Hi roseysdaddy.

First, you need to instal a package:
```
sudo apt-get  install cifs-utils
```
Then to mount a samba share:
```
sudo mount -t cifs //servername/ShareName /path/to/mountpoint
```
Replace servername for your actual NAS network name (or IP in case DNS in not well set up), and ShareName for the actual smaba share. Note that the mountpoint directory must exist.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by roseysdaddy on 2013-04-10
before I do this, what command options are needed to keep file structure when moving?

---

### Post by papibe on 2013-04-10
If I understand correctly you want to copy a directory tree. Is that it?

If so, you could simple use:
```
mv -iv  /path/to/source/  /path/to/destination/
```
When both are directories, it copies everything recursively and then remove the source.

Alternatevely, in case there are changes of the copy faling during the move, or there is big transfer, you could use rsync:
```
rsync -av  /path/to/source/  /path/to/destination/
```
If by any reason it fails, just run the command again (any inconsistensy will be fixed). You would need to remove manually the source since rsync just copy/transfer the data.

Does that help?
Regards.

---

### Post by roseysdaddy on 2013-04-10
thank you sooooo much.  That seems to be working perfectly.

edit: how so i mark this as solved?

---

### Post by roseysdaddy on 2013-04-10
how would I go about mounting this during each boot?

---

### Post by papibe on 2013-04-10
You can create an entry on /etc/fstab.

Edit the file using this command:
```
gksudo gedit /etc/fstab
```
You need to add a line similar to this:
```
//servername/ShareName /path/to/mountpoint cifs  user=yourusername,uid=1000,gid=100  0  0
```
For more details take a look a this [tutorial]("https://help.ubuntu.com/community/Fstab").

Let us know how it goes.
Regards.

---

### Post by docJ on 2013-04-10
> **roseysdaddy said:**
> 
how so i mark this as solved?

 Once you're ready to mark as "solved" you need to go back to your very first post and edit it, you will then be able to "solve the thread'
it is a workaround as they're a bug with the forum skin, or so I've been told...

---

