---
title: "How do I access my C:\ from Ubuntu?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by fckr on 2008-07-29
Thing is that I just started out yesterday, and so far I'm close to getting the overall picture about Linux.
I've got a dualboot laptop.
What I can't figure out is that exactly how do I access/browse my music/pictures/apps etc. that are on Vista through Ubuntu?

Do I really need to mark the C:\\Username\Documents\.. separately as shared in Vista and then mount Vista?

So far I've heard about apps like Samba and Firestarter - one is for sharing and the other for Ubuntu firewall settings? I assume they're useful in my case?


Is there any other way?


In advance, thanks, as I can imagine these kind of questions pop up daily and it might get frustrating for you guys.

---

### Post by cdtech on 2008-07-29
Just create a directory within /media such as /media/vista then add this line to your /etc/fstab file:

```
# Entry for /dev/sdb1 :
UUID=1D8FD5F25AC0301F /media/vista ntfs defaults,umask=007,gid=46 0 0
```

To find **YOUR** block id use the command "blkid" and it will show you the UUID to use for your drive.

Hope this helps......

**P.S.**
afterward just run the command "sudo mount -a" without a reboot and you'll be set

---

### Post by iaculallad on 2008-07-29
Normally when you vista drive is auto-mounted in Ubuntu, you could just navigate to Places->Computer and try to browse the listed mounted drive on the Nautilus window.

If your drives are not auto-mounted, you could post the content of your /etc/fstab file and the output of the command sudo fdisk -l and sudo blkid so we could help you auto-mount those partitions.

On your terminal:
```
cat /etc/fstab
sudo fdisk -l
sudo blkid
```

---

### Post by fckr on 2008-07-29
Thanks!

I'll check it out immediately once this 2003 Server training at work is over :P

I also have some issues (such a MS word..) with a superbadly corrupt install (java6-jre), and removing the file is not possible, since allegedly I don't have the proper access though I think I'm the poweruser.

Anyhow, I'll Google my way to bliss and hopefully grow some brains in the process :P

---

### Post by ad_267 on 2008-07-29
This explains about becoming "root" in Ubuntu: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can use "gksu nautilus" to get a file browser with root privileges.

You should usually remove a package using Synaptic or apt-get from the command line rather than deleting files.

---

### Post by fckr on 2008-07-29
But the thing is, that I already tried apt-get and Synaptic; both displaying a couple of file type specific errors, that I can't really recall now since I'm not on that laptop..

I think I'm just making this difficult for myself, and I need to check out the root link you provided and somehow forcing a deletion or uninstall.

The main problem is, that I have 55 updates waiting to be installed, and the java applet is not on the list (but it was), thus I can't uncheck the box next to it. Every time I start installing, I get the root error and whatnot.

But thanks!

---

### Post by ad_267 on 2008-07-29
There's a few commands you can run to clean up packages and repositories like "sudo dpkg --configure -a", "sudo apt-get update" and "sudo apt-get check --fix-broken"

---

### Post by fckr on 2008-07-29
Will do that, but in the meantime thanks to you people!
Think it's better if I try out the steps provided and we can go on from there, otherwise stuff will start piling up here :)

I'll get back tonite probably.

---

