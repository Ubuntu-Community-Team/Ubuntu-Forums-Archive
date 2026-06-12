---
title: "Transferring &quot;home' via cd/dvd without &quot;locked files&quot;."
date: 2008-11-23
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-11-23
I hope that made some sense:confused:

I usually do transfers with a usb hard drive using Partimage but I just did a transfer using DVD's (because I didn't have an external drive with me), but I had to right click each file and correct the "read/write" properties to "get-r-done"!

Anyone understand:confused:

I did get it done, but since different files in /home have different properties unlocking each one was time consuming.

So, in the future, how can I copy /home and have the files in an unlocked state?

I used Brasero and then selected NOT to exclude .mozilla and .opera which worked flawlessly otherwise!

---

### Post by kansasnoob on 2008-11-25
Thought I'd give this a bump!

As an afterthought: I see when I mount this dvd that when I click on "folder name" > properties > permissions, it says "You are not the owner, so you can not change these permissions".

No urgency as the project is done, but I know there must be a way of transferring all "home" files via cd or dvd without having to change permissions of each individual file and/or folder.

---

### Post by Paqman on 2008-11-25
I don't think it's the permissions you want to change, but rather the ownership.

To take ownership of everything inside a folder using the CLI:
```
sudo chown -R *username*:*username* /foldername
```

Using Nautilus, you can launch Nautilus as root by Alt-F2 then:
```
gksu nautilus
```

Right click on folder > Properties > Permissions > change the owner > click "apply to all enclosed files".

If you mess about with the actual permissions you might find you can't log in. By default the /home should be 755 (except for /home/.dmrc which should be 644)

---

### Post by CatKiller on 2008-11-25
CDs and DVDs are inherently read-only media, so the files on there are naturally read-only. They inherit this characteristic when you copy them back to the hard drive. It is fairly trivial to highlight all of the files and give them write permissions all in one go in the file manager, or you can do it with one command; ```
chmod -R u+w .
``` ought to do it, I think, although it's not something I've tried.

It's possible to change the permissions in the same action as copying the files across. If you're doing it graphically, you'll still have all the files you've copied highlighted, so you can then select the properties of all the files you've copied across and not the others. If you're doing it from the command line, you can chain that earlier command after your *cp* (or whatever) command with **&&**, which means to do the second command after the second command has successfully completed. There's probably a way to combine the commands in a more clever way to only change the permissions of the files you've copied.

The fact that *root* owns the files on the DVD is an unrelated thing, based on how the DVD is mounted. When a filesystem is mounted, options are available to control how it is mounted, where it is mounted, who has permissions over the files and so on. For a use-once command, these are done through options with the *mount* command. For filesystems that are mounted automatically at startup, these are controlled with the */etc/fstab* file. I'm not sure where the options are set for the new-fangled automatic mechanism for mounting of removable media.

---

### Post by kansasnoob on 2008-11-27
Hmmm, after trying several things I've now accomplished the goal of not being able to copy anything from anywhere to somewhere else!

Really! I'm now denied the privilege of copying a file to the desktop!

I have no idea what happened!

It's fun learning though!

---

