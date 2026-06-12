---
title: "File permissions of /home"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-18
My .dmrc had it's permission changed when I tried to install an external usb 80 gig drive.

I read in this post:

How did the permissions of the .dmrc file change?
[http://ubuntuforums.org/showthread.php?t=898599&highlight=File+permissions+%2Fhome](http://ubuntuforums.org/showthread.php?t=898599&highlight=File+permissions+%2Fhome)

That the poster solved the problem by copying the .dmrc file to a backup, deleting the .dmrc in his /home/username and then copying the backup to where the deleted file came from.

My question is this: how does one work with dot-files. As they are "hidden" will I see a dot-file on my Desktop?

---

### Post by Xiong Chiamiov on 2008-10-18
Nautilus should have an option somewhere for viewing hidden files.  I don't use it, so I can't tell you where, but it's highly unlikely it doesn't.

I believe the root problem here is that the file needs to be owned by you and 644-ed, right?  Instead of doing some other nonsense to do so, you can just change that directly:
```

cd ~
sudo chown [your username]:users .dmrc
chmod 644 .dmrc

```

EDIT: After actually looking at that thread, I see that in the end he has the permissions actually set to 600, and also did a 755 to his home directory, which you may want to try:
```

sudo chmod 755 ~ -R
chmod 600 ~/.dmrc

```
The -R flag is for recursive, meaning that it will apply that change to all files and folders inside your home folder.

---

