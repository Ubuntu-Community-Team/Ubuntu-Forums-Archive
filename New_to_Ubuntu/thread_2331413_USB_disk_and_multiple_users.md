---
title: "USB disk and multiple users"
date: 2016-07-22
forum: New to Ubuntu
---

### Post by Jorhel on 2016-07-22
Hi,
I have created a separate user account for my kids with restricted privileges. 
I want them to be able to use a USB stick to save their work or take stuff to school. Is there a way to authorise that without giving them admin privileges?
When I try to open the disk from their desktop it does not work, from mine it "mount" automatically.
By the way what's the difference between mounting and opening if any?
I'm sure that has already been answered somewhere but can't find it.
cheers

---

### Post by veddox on 2016-07-22
Hi there,

"mounting" means inserting a file system into the Linux file tree, ready for use - "opening" simply means using it. You'll find more details [here]("https://help.ubuntu.com/community/Mount").

Concerning your question I found [an answer on StackExchange]("http://unix.stackexchange.com/questions/96625/allow-non-superusers-to-mount-any-filesystem") that might help you. Disclaimer: I haven't tried any of those methods myself.

Good luck!

---

### Post by yancek on 2016-07-22
Do you have Ubuntu installed on all the computers?
Are you trying to open by plugging the flash drive into the second computer?  What operating system is installed on this computer and what filesystem is on the flash drive?
Are you trying to access the flash drive while it is attached to your computer from the other computer.   You will need to install and configure networking software.  For Linux systems, this is usually nfs.

---

### Post by ptn107 on 2016-07-23
Don't quote me but I think it has to do with permissions in /etc/group.

Try adding the kids account to the *plugdev* group.
```
usermod -a -G plugdev accountname
```

Maybe?

---

### Post by Jorhel on 2016-07-25
There is only one computer with only xubuntu on it. I have created an account for my kids with restricted permissions so they can't install new programs for example.
We chose which account through log in at the begining of a session.

Thanks that was helpful in understanding(sort of)how the system work.
My problem seems to have sorted itself without any intervention other than restarting the computer....

---

### Post by yancek on 2016-07-25
With just one computer and with several users, you could create a specific group and add your 'kids' users to that group and give them whatever permissions you want for the flash drive mount point.

In the ordinary course of things, one would need to have root (sudo) permissions to install software so as long as they don't have your password, should not be a problem. Anyhow, glad you got it working.

---

### Post by Jorhel on 2016-08-12
Thanks, yes they are in a group and they have permission to use flash drive which is why I was puzzled it didn't work. It seems it has something to do with who logged in first when the computer was started... But as long as we got it working I'm not picky...

---

### Post by Geoffrey_Arndt on 2016-08-13
If you log in first, and then open an already plugged in flash-stick, or plug in the flash stick during your session, you temporarily own that device.   If your son or daughter does the same thing (being the first user), then they own the device and you (even as the admin) can't access the device (without special commands in the terminal).    This applies to usb flash-sticks that have the ms dos file systems (fat32 or ntfs).   For Linux file systems, the rules are different.     As you saw, a restart allows a new "first user" to own the device and access it.

---

