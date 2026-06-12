---
title: "Sharing a folder recursively"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by russbook on 2008-07-01
Hi

I am very new to both ubuntu and unix. I have 8.04 unstalled on an 80gb hard drive and all my media on a separate 250gb drive within the same case (formatted as fat32). Within the the O/S I can access all files fine.

I am attempting to share the whole "media" drive with my media center enclosure ([http://emprex-me1.blogspot.com/]("http://emprex-me1.blogspot.com/")). 

At present I have only been successful at this by by copying folders to my ubuntu/desktop then right-clicking and sharing the folder with users/groups/others using the gui. However I then need to select each individual file and change their permission before they will appear on my media center.

Is there a way to set permissions so that they apply to all sub folders and files within them?

I have tried to share the whole drive in the following way but it did not work.

```
lrwxrwxrwx 1 root  999     6 2008-06-17 23:21 cdrom -> cdrom0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 cdrom0
drwx------ 7 russ root 16384 1970-01-01 01:00 disk
lrwxrwxrwx 1 root  999     7 2008-06-17 23:21 floppy -> floppy0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 floppy0
russ@Herbie:/media$ chmod 777 disk

```

---

### Post by Hospadar on 2008-07-01
```
chmod -R <permissions> <folder to be shared>
```

Also note, if you want to give someone permissions to a folder, but not it's containing folder, you can give the containing folder execute privileges.

let's say I want user bob to be able to see user alice's "Documents" folder:
chmod 777 /home/alice/Documents
chmod uog+x /home/alice

---

### Post by beesthorpe on 2008-07-01
Yes chmod can do it, but doesn't  right clicking on the folder > properties > permissions also have a "Apply Permissions to Enclosed Files" button?

---

### Post by russbook on 2008-07-01
Thanks for the quick response.

However this is what is happening for me:
```
russ@Herbie:/media$ chmod -R 777 disk
russ@Herbie:/media$ ls -l
total 24
lrwxrwxrwx 1 root  999     6 2008-06-17 23:21 cdrom -> cdrom0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 cdrom0
drwx------ 7 russ root 16384 1970-01-01 01:00 disk
lrwxrwxrwx 1 root  999     7 2008-06-17 23:21 floppy -> floppy0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 floppy0

```

The permissions for "disk" do not appear changed.Have I go this wrong? I am logged in as russ.

---

### Post by russbook on 2008-07-01
> **beesthorpe said:**
> Yes chmod can do it, but doesn't  right clicking on the folder > properties > permissions also have a "Apply Permissions to Enclosed Files" button?

Any changes I make revert back to previous settings as soon as I hit the "Apply...." button.

Does this suggest that I am not logged in as the owner of the files? How can I ensure that I am?

---

### Post by russbook on 2008-07-01
I am not intentionally bumping this forum: I did reply twice in a row in quick succession to answer the two different replys above - and noticed that after that there were no additional views of the post. Have I violated any bump rule to cause this, or have people just lost interest in the topic?

Just for future ref.

---

### Post by beesthorpe on 2008-07-02
well what I'd do is try changing the permissions as root - either put "sudo" before the chmod commands or run nautilus as root by hitting alt f2 then typing "gksudo nautilus" in the "run application" dialogue box.

This should work as "root" is allowed to do absolutely anything. If this doesn't work for some reason though, I'm afraid I'm as baffled as you.

AFAIK the forums don't have any special rules on bumping - the reason I haven't replied until now is simply that I was offline :)

---

### Post by stchman on 2008-07-02
> **russbook said:**
> Thanks for the quick response.

However this is what is happening for me:
```
russ@Herbie:/media$ chmod -R 777 disk
russ@Herbie:/media$ ls -l
total 24
lrwxrwxrwx 1 root  999     6 2008-06-17 23:21 cdrom -> cdrom0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 cdrom0
drwx------ 7 russ root 16384 1970-01-01 01:00 disk
lrwxrwxrwx 1 root  999     7 2008-06-17 23:21 floppy -> floppy0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 floppy0

```

The permissions for "disk" do not appear changed.Have I go this wrong? I am logged in as russ.

Try changing the owner to you.

```
sudo chown -R $USER:$USER /media/disk
chmod -R 755 /media/disk
```

Let me know if that worked.

---

