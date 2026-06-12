---
title: "Permissions on additional harddrive"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by jhulf on 2008-11-02
Hi,

i added a secondary harddrive to my pc, and i had several problems. The drive had HFS+ on it, so i had to format it as a Dos Filesystem (couldn't get the Mac to stop journaling.) With the Dos System, finally i could format it through Gparted.
Now i got the ext2 Filesystem but still i do not have the permission to write on it. I changed that through chmod until everybody can read and write and execute anything on that drive.
Now i am stuck with the fact, that i can read and write single files or folders on this drive, but when i tried to copy a 10GB folder to the drive, i again didn't have the right to do it. ( I managed that through gksudo nautilus .)

Now I am asking you:
1- Why does Ubuntu assumes that a second empty harddrive installed to the system has different rights than the first harddrive and the user who is currently locked in (and can go root when in need)?
2- What would be the correct permissions, so that i as a user and i as a root admin can work with this harddrive (No one else is using this Pc)?
3- Why is it so difficult for Ubuntu to read and write or format foreign File Sytems (HFS+ or NTFS or whatever). Shouldn't that be 'plug and play'?

greetings and thanks
jhulf

---

### Post by taurus on 2008-11-02
Where do you mount that second harddrive?  For now, I will assume you mount it to /media/second and your log in name is john.  Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo chown -R john:john /media/second
ls -la /media/second
```
Now, you can write to it, /media/second, whenever you want without being root or using sudo.

---

### Post by jhulf on 2008-11-06
> **taurus said:**
> 

```
sudo chown -R john:john /media/second
ls -la /media/second
```


Thanks, that did the trick.

---

