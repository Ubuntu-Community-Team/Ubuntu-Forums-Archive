---
title: "map network drive"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by cdmjjp on 2012-03-20
On Windows if you want to add a network drive permanently, you just go to 'My Computer - Map Network Drive' and search. On Ubuntu I can only mount each time I log on. However this does not give media access unless I go through the files. Is there a way around this?

---

### Post by Paqman on 2012-03-20
Yes, but it's a bit messier than on Windows. You'll need to add an entry to the file [/etc/fstab]("https://help.ubuntu.com/community/Fstab"). However, once that's done I find it a lot more reliable than the Windows system.

---

### Post by WasMeHere on 2012-03-20
Yes cdmjjp,

There are several ways. One simple way if you are using 'vanilla' Ubuntu with the file browser Nautilus, is to mount the network partition manually (as you have been doing). And then ***drag its icon to the left panel of Nautilus*** (that is inside the file browser window).

Then this will be a short-cut. If you need a password, you will be prompted for that, next time you want to mount it (after reboot). This will be much more convenient, than to do the whole manual job every time.

There are also command line methods making a line in the file [FONT="Courier New"][SIZE="3"]/etc/fstab[/SIZE][/FONT], but I suggest that you try the Nautilus way. I use that myself for network partitions, and the command line way only for local partitions.

Have fun finding out :-)
Olle

---

### Post by cdmjjp on 2012-03-20
Sorry but I am a user only and have no idea of how to do what you just said.Could you please put that into layman terms, if possible?

---

### Post by WasMeHere on 2012-03-20
> **cdmjjp said:**
> Sorry but I am a user only and have no idea of how to do what you just said.Could you please put that into layman terms, if possible?
Are you asking about /etc/fstab or drag and drop in Nautilus?

---

### Post by cdmjjp on 2012-03-20
either, both, whichever is easier! I'm still learning!!

---

### Post by Morbius1 on 2012-03-20
**Gigolo**: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

It uses the same back-end that Nautilus does to mount the share and it can be used to automount when you log into your machine.

* It's a GUI utility.

* It waits for the remote server to be present before it mounts in case the server machine is not up when you start Ubuntu.

---

### Post by cdmjjp on 2012-03-20
I can't find nautilus. When I go to install it, it says it is already installed. Where do I find it?

---

### Post by Morbius1 on 2012-03-20
Nautilus is your File Manager - Home

---

### Post by cdmjjp on 2012-03-20
Found it. Thanx, but say ' File not supported'

---

### Post by Morbius1 on 2012-03-20
What file is not supported?

What did you do?

---

### Post by WasMeHere on 2012-03-20
> **cdmjjp said:**
> Found it. Thanx, but say ' File not supported'

If you just open the file browser (at home) you should have something similar to the screen dumps, that I have attached to this post.

1-connect-to-server.jpg (the first step)

2-connect-ssh.jpg (actually means sftp, but you can select several connection modes from the menu)

3-add-bookmark.jpg (to get a persistent book-mark in the left panel)

4-rename-bookmark.jpg (if you want a better name)

Once you have the bookmark on the left panel of the file browser, it will be easy next time to mount the network partition. Just click on it (and if necessary enter password).

Good luck :-)

---

### Post by Morbius1 on 2012-03-20
Is this a Samba question or an SSH question?

Do you want to automount or have a bookmark that will mount as needed?

---

