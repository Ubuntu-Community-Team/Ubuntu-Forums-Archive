---
title: "Partition and its permissions..."
date: 2008-10-21
forum: New to Ubuntu
---

### Post by modano on 2008-10-21
Hello,

Im all new to Ubuntu and linux so bare with me, :)

During installation of Ubuntu 8.0.3 I created a 100GB partition for various file storage, that I did not want to have in /home (i read this on some website a day or two ago about good way to partition for ubuntu)
I chose ext3 as filesystem and set the mount point to be /data

My question is, first of all:
When opening up "computer" in the File Browser, I do not see it as a partition in the sense as windows displays c,d,e etc.
I dug around and finally found my /data partition under File System.
How do I get /data to be its "own"entry under "computer"?

Second is,
I have no rights to create folders or files in my new partition :(
What to do?

grateful for any help!
modano

---

### Post by Duck2006 on 2008-10-21
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by vanadium on 2008-10-21
We need to start with your second question first. You need to grant yourself permissions to write on your data partition.

The most simple way is this:

* Load a nautilus instance with root permissions: at the terminal (Programs - Accessories - Terminal), type "gksudo nautilus". Provide your password and press enter. A file manager window appears with administrator (root) permissions.

* Navigate to / (top directory in the file system, the root directory). Right-click the data dir, select "Permissions". Change the owner from "root" to yourself as user (= select your username from the dropdown).

* Close your nautilus window (for safety)

The second question is how to have it appear in the Places menu.

* Open a "normal" nautilus window. Navigate to /data

* The command Boomkarks - Add bookmarks will add the directory to places.

TIP: to easily access /data from within your home directory, you can create a symbolic link "data" in your home directory.

* Open two nautilus windows side by side
* In the left one, navigate to /
* Leave the right one open in your home directory.
* Middle-click and drag "data" from the left window to the right. On releasing the button, choose "Make link".

---

### Post by modano on 2008-10-21
Thank you vanadium, Did all of your instructions, and now it is exactly as i wanted it! :)

---

