---
title: "[SOLVED] Copying files over to data partition?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by gabriella on 2008-08-15
I'm slowly learning how to do everything and I'm sold on using a non MS OS even if the learning curve is a little different. But can someone tell me what I'm doing wrong please.

I created a data partition formated as ext3. I have a pile of photo's saved in my /home folder but I cant seem to copy or move them to the other partition. How SHOULD I do this??

Thanks

---

### Post by Elfy on 2008-08-15
The partition needs to be mounted, probably want it to be mounted automatically, in which case you'll need to add it to a file called fstab.

This post goes through it nice and simply

[http://ubuntuforums.org/showpost.php?p=5569475&postcount=6](http://ubuntuforums.org/showpost.php?p=5569475&postcount=6)

Then you should be able to drag them

---

### Post by unutbu on 2008-08-15
This is probably an ownership/permission problem. 


To give yourself ownership of and read/write permission for the data partition:
open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)) and type:
```

export DATA=/path/to/data/partition      # Change the path as necessary
sudo chown -R $USER:$USER $DATA
sudo chmod -R u+rw $DATA

```

---

### Post by gabriella on 2008-08-15
Thanks! there are so many excelent tutorials I just don't have time to read them all at once or find them...but I'm working on it!

---

