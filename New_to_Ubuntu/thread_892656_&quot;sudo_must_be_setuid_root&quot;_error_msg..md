---
title: "&quot;sudo must be setuid root&quot; error msg."
date: 2008-08-17
forum: New to Ubuntu
---

### Post by harryliddic on 2008-08-17
I get "sudo must be setuid root" when trying to use sudo and when I use gksudo I get "wrong permission for /tmp/orbit-harry" I changed the permissions of the root directory to 777 to get a file written in a program I am trying to run, Is there any way out?
__________________

---

### Post by sisco311 on 2008-08-17
What command did you use to change the permission?

---

### Post by Bachstelze on 2008-08-17
> **harryliddic said:**
> I changed the permissions of the root directory to 777 [...], Is there any way out?

No, you're in for a reinstall.

---

### Post by harryliddic on 2008-08-17
sudo chmod 777 /

---

### Post by Bachstelze on 2008-08-17
Then it shouldn't say this. Sure you didn't add -r ?

---

### Post by fahadsadah on 2008-08-17
Permissions is the reason Linux is more secure than Winblows.

777'ing / is pointless, and breaks apps.


777'ing anything also erases stickies,setuids and setgids.

---

### Post by harryliddic on 2008-08-17
I probably added the recursive

---

### Post by Bachstelze on 2008-08-17
> **harryliddic said:**
> I probably added the recursive

Then yes, I'm afraid you can't avoid a reinstall. You can fix the sudo error with [font="Courier New"]chmod 4755 /usr/bin/sudo[/font], but that will be only a temporary solution. It's almost certain you'll have countless of issues because of this.

---

### Post by harryliddic on 2008-08-17
if I can limp along until I get qdvdauthor to work and not lose all my video files( about 8GB worth) I can put up with my third re-install in four weeks. For a project that was due three weeks ago, Linux has not been all that productive. It has added great bells and whistles, but getting the work out and on the table is more of a chore.


harry@harry-desktop:~$ chmod 4755 /usr/bin/sudo
chmod: changing permissions of `/usr/bin/sudo': Operation not permitted
harry@harry-desktop:~$

---

### Post by sisco311 on 2008-08-17
Reboot in recovery mode and try to run the
command from the root shell.

Also restore the permissions on /etc/sudoers:
```
chmod 0440 /etc/sudoers
```

---

### Post by harryliddic on 2008-08-17
While I have got you here, what is the command to list the names and mount points of all the devices?

---

### Post by sisco311 on 2008-08-17
```
sudo fdisk -l
```
and
```
df
```
or
```
mount
```

---

### Post by ramakrishnankt on 2009-12-05
Hi,
My system also have same problem
node2@node2-prudence:~$ sudo su
sudo: must be setuid root

I am also not allowed to use synaptic or the updater and get "su returned with an error" when I try to use them
please try to remove it.
Thanks
Ramakrishnan

---

