---
title: "Desktop Launcher Permissions"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Mjsch on 2008-10-26
I use Hardy 8.04 LTS. I am trying to set up desktop launchers to a number of folders. Many are on a FAT32 Drive, so linking is not the answer. I create them, using the command line of the location of the folder

ex: Command: "/media/disk/mp3" But whenever I try to use them, I get a permissions error. I have went into nautilus and tried to set permissions for the folder, but it will not let me set group permissions, and setting myself as the owner does not solve the problem.

I am the only user on my computer. Any ideas?

---

### Post by pizzafarmer on 2008-10-26
From the terminal window, what do the permissions for the /media directory look like when you enter this:

ls -lsa

---

### Post by bwhite82 on 2008-10-26
Try giving yourself ownership of the directory that you're linking to:

> sudo chown -R yourUserName:yourUserName /media/disk/mp3

---

### Post by Mjsch on 2008-10-26
This is what I get

16 drwx------ 2 matt root 16384 2008-10-25 22:14 .
16 drwx------ 9 matt root 16384 2008-10-26 10:36 ..

setting myself to owner from nautilus did not work. I will try from terminal get back to you

---

### Post by Mjsch on 2008-10-26
From the terminal I get a "operation not permitted" error

---

### Post by pizzafarmer on 2008-10-26
Do you get the same response from

sudo chmod g+rw /media

?

---

### Post by Mjsch on 2008-10-26
no, but my launchers still don't work

---

### Post by pizzafarmer on 2008-10-26
Maybe the permissions for other have to be changed too:

sudo chmod o+rw /media

Permissions should look like this:

drwxrw-rw-

Make sure the subdirectory mp3 has those permissions as well

---

### Post by pizzafarmer on 2008-10-26
Maybe the permissions for other have to be changed too:

sudo chmod o+rw /media

Permissions should look like this:

drwxrw-rw-

Make sure the subdirectory mp3 has those permissions as well

---

### Post by bwhite82 on 2008-10-26
> **Mjsch said:**
> From the terminal I get a "operation not permitted" error

You made sure to use 'sudo' didn't you?

---

### Post by Mjsch on 2008-10-26
I checked again, I did use sudo. How do I go about changing the permission codes to the ones you gave me before?

---

### Post by pizzafarmer on 2008-10-26
sudo chmod g+rw /media

or to change permission for all:

sudo chmod a+rw /media

---

### Post by Mjsch on 2009-06-30
Found the solution:

FAT32 doesn't support Permissions

reformatted as Ext3

---

