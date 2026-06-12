---
title: "Mounting Drives"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by .adma on 2008-05-27
Can someone please explain to me exactly how mounting works?  I have a network drive, the DNS-323, which Ubuntu finds perfectly over my network.  I can then access it and play around with files perfectly.  However, I would love for this to be permanently mounted to my computer.  I can't even get F-Spot to recognize it as a drive, because of the SMB protocol maybe?  Any help would be greatly appreciated.

---

### Post by Cypher on 2008-05-27
THe act of mounting basically makes a partition/drive available at a known place (usually a directory). So the directory "/media/cdrom0" is just an empty directory until you put in a CD. At that point "/media/cdrom0" becomes your view to the contents on the CD.

So with your Network drive, to mount it all the time with each boot of your Linux machine, you'd add an entry to the "/etc/fstab" file. Take a look at the current file to see the structure.

---

### Post by lswest on 2008-05-27
Of course, that drive will only be mounted as long as you're connected to the network at which the server is located, or else the correct server is being addressed through the internet.

---

### Post by .adma on 2008-05-27
> **lswest said:**
> Of course, that drive will only be mounted as long as you're connected to the network at which the server is located, or else the correct server is being addressed through the internet.

If I boot up on a different network, will there be issues?  Or will it just show as an empty folder, just like the CDROM example?

Thanks!

---

### Post by lswest on 2008-05-27
Should just show up as an empty folder and maybe pop up once quickly saying it couldn't connect.

---

