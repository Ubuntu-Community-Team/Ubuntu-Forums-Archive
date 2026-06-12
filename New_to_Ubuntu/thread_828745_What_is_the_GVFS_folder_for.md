---
title: "What is the GVFS folder for?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-06-14
In my home folder after a clean install of hardy I see a .gvfs folder, which cannot be moved or deleted. I was usually under the impression that EVERYTHING in the /home folder can be edited by the user. Whats this folder for?

---

### Post by iaculallad on 2008-06-14
It serves as mountpoint for GVFS-Fuse.

Excerpt from [http://packages.ubuntu.com/hardy/libs/gvfs-fuse](http://packages.ubuntu.com/hardy/libs/gvfs-fuse)

> gvfs is a userspace virtual filesystem where mount runs as a separate processes which you talk to via dbus. It also contains a gio module that seamlessly adds gvfs support to all applications using the gio API. It also supports exposing the gvfs mounts to non-gio applications using fuse.



---

### Post by abhiroopb on 2008-06-14
Sorry could you dumb that down a little please! I didn't understand that. Its annoying because I have to exclude it from all my rsync backups as it says permission denied. Also is it taking up any space?

---

### Post by iaculallad on 2008-06-14
It's just a mountpoint for non-gvfs applications. With regards to the permission problem, try adding yourself to the "fuse" group.

---

### Post by abhiroopb on 2008-06-14
Seems like I'm alsoa  member of fuse.

Also I was getting an error: something along the lines of:
Users &HOME/.dmrc file is being ignored.

Then a bunch of stuff about not having permissions, this was after login, after I had put all copied my gutsy home folder over my new hardy one.

I used this solution to get rid of the problem:
sudo chmod 644 /home/ricardisimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo

Coould this have caused the issue? I didn't really understand it, I just did it to solve the problem.

---

### Post by iaculallad on 2008-06-14
To better understand the issue on why it prompted you as being ignored in your home directory or to that certain file (either you had used sudo instead of gksudo before), try reading this [page]("http://www.psychocats.net/ubuntu/graphicalsudo").

---

### Post by niteshifter on 2008-06-14
Hi,

Use sudo with rsync.

VFS and GVFS are a bit complex to distill into a paragraph or two:
[wikipedia article virtual file systems]("http://en.wikipedia.org/wiki/Virtual_file_system")
[wikipedia article on GVFS]("http://en.wikipedia.org/wiki/GVFS")

.dmrc - you've got that correct.
/home/user - permissions should be 755. You can change permissions for files / folders you make within /home/user to whatever you like - so long as you created them. IOW not the GNOME (or any other desktop environ) files that it creates. These are the "dot files" or "dot folders": preceeded with a . to hide them.

---

### Post by abhiroopb on 2008-06-14
So instead of this:
sudo chmod 644 /home/ricardisimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo

What should I change it to? There is 644 and 700? what should these be then?

---

### Post by iaculallad on 2008-06-14
Select the best permission which serves your purpose:

644 (-rw-r--r--) If you want the read and write permission only. Others has read-only permission.

700 (-rwx------) If you want read, write and execute permissions.

---

### Post by abhiroopb on 2008-06-14
So, I guess the permissions I set (to allow execution as well is fine).

---

### Post by iaculallad on 2008-06-14
> **abhiroopb said:**
> So, I guess the permissions I set (to allow execution as well is fine).

If that permission can make you feel good then, no problem for me either :)

---

### Post by abhiroopb on 2008-06-14
Thanks! I just wanted to make sure everything worked!

---

### Post by abhiroopb on 2008-06-14
Ok this might be a similar issue. When I view the available space on my hard drive (through gparted) I can see that my /home partition is taking up 43gb of space and there is 38gb of free space. When I look at "free space" in nautilus (status bar), it shows 34GB! So where is the 4 GB dissapearing?

---

