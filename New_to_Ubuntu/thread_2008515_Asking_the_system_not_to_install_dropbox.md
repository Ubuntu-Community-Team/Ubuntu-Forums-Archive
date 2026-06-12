---
title: "Asking the system not to install dropbox"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by analyst2k on 2012-06-22
Hello,

I tried installing dropbox on my Ubuntu 11.10 64 bit using Ubuntu Software Center and after downloading it hanged. 
(The progress bar stopped moving for over an hour)

I shutdown the Laptop as i had to commute and turned it back on later.

Now each time I try installing a package using the terminal, it immediately starts to install dropbox which also never completes.(Stays on 99% sometimes 100 for hours)

How do I ask the system to quit trying to install dropbox. ( Ctrl C doesn't work either) 

I just don't want the system to even try to install it at all.

Thank you.

---

### Post by jmfal on 2012-06-22
Try this to remove dropbox
```
 sudo apt-get --purge dropbox    
```

then this
```
sudo apt-get autoclean    
```

Then try to install something, if you get an error put it in your post.

---

### Post by Nick Burgundy on 2012-06-22
Just ran into this issue as well. This worked for me:

[http://ubuntuforums.org/showthread.php?t=1971123](http://ubuntuforums.org/showthread.php?t=1971123)

Open Synaptic, search DropBox, remove DropBox. Apply changes.

Back into software center, DropBox is officially removed.:popcorn:

---

