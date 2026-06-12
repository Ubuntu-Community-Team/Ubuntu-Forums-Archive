---
title: "how can i make a back up of my home folder"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Kedster on 2008-05-11
Hello umm i i really want to make a copy of my home so that i can format my drive and send it away to get fixed. i really want to have a copy so that when i reinstall i have can get all my personal setting and files back. It is about 125 MB but when i tryed to burn it to a dvd it had to deep of folders. also after i make a copy how can i get it back to my my partition when i reinstall. It will be on its own patition too so.   please help:(:):guitar:

---

### Post by Monicker on 2008-05-11
You could create an archive of it, and burn that.

```
tar czvf HomeBackup.tar.gz /home/username
```

Use /home, if you need to backup files for multiple users in that directory.



After redoing your partitions, just copy the file to your new /home folder and do

```
tar xzvf HomeBackup.tar.gz
```


Note: You do not have to use the terminal commands.  It can be done through the File Browser.  Just right click your home folder and select Create Archive.

---

### Post by Malta paul on 2008-05-11
You could also use Quickstart this worked well for me.
[http://quickstartdownload.pbwiki.com/QuickStart+Help](http://quickstartdownload.pbwiki.com/QuickStart+Help)

The download file link is:
[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)
 
Have fun:)

---

### Post by philinux on 2008-05-11
When I did this I made two. One to a cdrw and another to a ext3 formatted usb stick using the cp command.

---

### Post by Kedster on 2008-05-11
ok umm id think that will work but i just came upon somthin really displeasing, a few weeks ago (in pure stupidity) i accidentally copied a folder into it self and well it wont let me delete it and i was wondering if there is a  way (in cl or gui) to delete it it u don't understand say so and ill try to describe better what is wrong

---

