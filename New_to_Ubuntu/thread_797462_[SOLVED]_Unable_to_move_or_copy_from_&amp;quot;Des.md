---
title: "[SOLVED] Unable to move or copy from &amp;quot;Desktop&amp;quot;"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by jerrallan on 2008-05-17
I usually download images to desktop. I am now unable to copy or move images.  There are two jpg images on Desktop that I have been trying to move to the directory Pictures

usrname@usrname-desktop:~$
usrname@usrname-desktop:~$ cd Desktop
usrname@usrname-desktop:~/Desktop$
usrname@usrname-desktop:~/Desktop$ ls
[shows nothing]
usrname @usrname-desktop:~/Desktop$ ls -a
. ..
I checked the "folder" Pictures and found a folder named Desktop which contained all of the files and images located on my Desktop.

How do I restore functionality so I can move from Desktop to other files?

Thanks

---

### Post by macaholic on 2008-05-17
What are you using to download files? I bet that it is not set to download files to where you think it is.

---

### Post by jerrallan on 2008-05-17
from the browser right click on the image, and save image as. They do go to Desktop

Now, after I rebooted the jpgs are gone. I can't find them anywhere.

I just downloaded a new image and 
ls did show it on Desktop
When I moved it to Pictures, it is gone, no where to be found
mv 123456.jpg /Pictures

---

### Post by freebeer on 2008-05-17
It sounds to me that you saved the files to a different folder... something like /home/Pictures/Desktop.  You tried (and succeeded) to cd to /home/usrname/Desktop.  Which is a different folder.

Perhaps if you issued these two commands from the terminal:
```

sudo updatedb
locate [name of one of the files you saved]

```

You'd get the full path to the file and that way you'd know where it was saved to.

---

### Post by macaholic on 2008-05-17
> **jerrallan said:**
> 
When I moved it to Pictures, it is gone, no where to be found
mv 123456.jpg /Pictures
That will move it literally to a directory on the root of your system called "Pictures" To move it to the pictures fodler on the desktop, remove the '/'.

---

### Post by jerrallan on 2008-05-17
Thanks freebeer and macaholic.  They were in root.

One of the jpgs was named Documents. That happened when I tried to move it earlier to Documents.

Back to the books and more reading on "mv"

---

