---
title: "How can i automatically put a file inside the iso and after install?"
date: 2019-07-02
forum: New to Ubuntu
---

### Post by klokkefriken2 on 2019-07-02
So i want to config the ubuntu iso or a Any Linux iso, like i want to put a file inside 
[B]File System > usr > share > x11 > xorg.conf.d 


[/B]
And it needs to be there after install. How can i do that?
The file i want to add is a .conf file, that i need.

Any advice?

---

### Post by wildmanne39 on 2019-07-02
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

---

### Post by cruzer001 on 2019-07-02
I have not done this, but looks doable with mkisofs.

[https://www.techwalla.com/articles/how-to-add-files-to-an-iso-image-in-linux](https://www.techwalla.com/articles/how-to-add-files-to-an-iso-image-in-linux)

[http://linuxpitstop.com/edit-iso-files-using-mkisofs-in-linux/](http://linuxpitstop.com/edit-iso-files-using-mkisofs-in-linux/)

[https://bencane.com/2013/06/12/mkisofs-repackaging-a-linux-install-iso/](https://bencane.com/2013/06/12/mkisofs-repackaging-a-linux-install-iso/)

---

### Post by TheFu on 2019-07-03
Ubuntu has a pre-seed file install capability that is meant for hardware vendors.  I've never used it and can't remember the name. ... [https://help.ubuntu.com/lts/installation-guide/amd64/apb.html](https://help.ubuntu.com/lts/installation-guide/amd64/apb.html)

ISO is a read-only format.  That can't be changed.   You can re-package the ISO using **mkisofs** after you expand it, modify the image directories, then rebuild the ISO.  I haven't don't this since the 1990s, so placement of the file inside the ISO may not get it installed onto the target system. A script might be necessary.

Or if you need to do this for hundreds of systems, then I'd look at a bare metal installation tool like **Cobbler**.  If the systems are all identical, I'd probably setup a **clonezilla** server to stream image backups to 50 systems concurrently.  Cobbler is more flexible.

But since this is just an X11 config file, you can do a normal install, that includes ssh-server and automate pushing the config file over using any dev-ops tool like **ansible** over the network.  I use ansible in this way all the time.  Just be certain that you lock down access to the ssh-server for specific accounts and subnets.  Might want to push over an ssh-key file as the first step to make ongoing maintenance easier for your ansible "deploy" account going forward.

---

