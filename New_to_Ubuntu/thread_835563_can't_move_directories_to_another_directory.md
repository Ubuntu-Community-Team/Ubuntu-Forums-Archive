---
title: "can't move directories to another directory"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by gotquestions on 2008-06-20
Hi,
I downloaded this binary and extracted that .tgz file and I got a folder full of files and subfolders. We can call it "FolderExtractedABC"

So I want to move that folder into /usr/bin/, it won't let me. Why? 

happy@happycloud:~/Desktop$mv FolderExtractedABC /usr/bin

(I also placed sudo in front of it and that didn't do the job)

---

### Post by tjwoosta on 2008-06-20
hmmm... 

thats odd, it should work

what error does it return?


you could try to cp instead of mv

```
sudo cp -Rp FolderExtractedABC /usr/bin
```

then just delete the old one after


EDIT:   Wait I see the problem now! ( i think)

maybe it should be 
```
sudo mv FolderExtractedABc /usr/bin/FolderExtractedABC
```


let me know if that works

---

### Post by yragrelluf on 2008-06-20
in terminal type sudo mv "extracted file path" /usr/bin

---

### Post by gotquestions on 2008-06-20
> **tjwoosta said:**
> 

EDIT:   Wait I see the problem now! ( i think)

maybe it should be 
```
sudo mv FolderExtractedABc /usr/bin/FolderExtractedABC
```


let me know if that works

So I just did that from above and it moved the whole folder over to /usr/bin/. Now I new problem:

When I cd...I see 2 FolderExtractedABC :(

/usr/bin/FolderExtractedABC/FolderExtractedABC/...

How do I get rid of that extra FolderExtractedABC folder?

In the future, if I ever move folders to another place, do you know if there is any flag that can warn me that there is such dir?

---

### Post by tjwoosta on 2008-06-20
hmm..

you might have better luck working with a GUI

in the terminal type ```
gksudo nautilus
```

this will open a filebrowser with administrator rights

you can then visually navigate to /usr/bin and you can drag and drop or copy and paste or whatever you need to do to sort things out

---

### Post by gotquestions on 2008-06-20
Well, I want to learn how to do it via command line. Don't want to rely on GUI all the time incase something happens you know?

---

### Post by yragrelluf on 2008-06-20
try this
1. sudo rm -R /usr/bin/FolderExtractedABC

when you moved it to /usr/bin you shouldn't have added folderextractedabc to the end

---

### Post by ruffEdgz on 2008-06-20
If there is information in the /usr/bin/FolderExtractedABC/FolderExtractedABC/, copy that information from that directory down one:

```

mv /usr/bin/FolderExtractedABC/FolderExtractedABC/* /usr/bin/FolderExtractedABC/

rm -Rf /usr/bin/FolderExtractedABC/FolderExtractedABC/

```

mv = move files/directorys

rm = remove files/directories

That should do it :D

---

### Post by nanikusasaki on 2009-04-06
> **ruffEdgz said:**
> If there is information in the /usr/bin/FolderExtractedABC/FolderExtractedABC/, copy that information from that directory down one:

```

mv /usr/bin/FolderExtractedABC/FolderExtractedABC/* /usr/bin/FolderExtractedABC/

rm -Rf /usr/bin/FolderExtractedABC/FolderExtractedABC/

```

mv = move files/directorys

rm = remove files/directories

That should do it :D


No wonder gotquestions never came back to the thread, she couldn't! The above quoted command contains rm -rf which wiped her computer. If any n00bs read this thread do not abide by the above directions, they are most likely malicious. Gotquestions, if you come back to this thread please send me a message.

---

### Post by SuperSonic4 on 2009-04-06
now that's what I call a bump.

As it happens ruffEdgz's command will delete that folder and all it's subdirectories. It doesn't bork your system. I've used it 100s of times without problem

For deleting an empty directory there is always rmdir

---

### Post by tjwoosta on 2009-04-06
> **nanikusasaki said:**
> No wonder gotquestions never came back to the thread, she couldn't! The above quoted command contains rm -rf which wiped her computer. If any n00bs read this thread do not abide by the above directions, they are most likely malicious. Gotquestions, if you come back to this thread please send me a message.

um actually no..

> 
rm -Rf /usr/bin/FolderExtractedABC/FolderExtractedABC/


if you read the command you would see that he was removing only one folder  (FolderExtractedABC and its contents)   

the reason for removing this file was becase it was inside another FolderExtractedABC 

(there were two folders with the same name with one inside the other)

> So I just did that from above and it moved the whole folder over to /usr/bin/. Now I new problem:

When I cd...I see 2 FolderExtractedABC

/usr/bin/FolderExtractedABC/FolderExtractedABC/...

How do I get rid of that extra FolderExtractedABC folder?

do you understand now?


this is not a malicious command


rm is not malicous  (it simply means remove)

any time you remove files from anywhere using the command line you would use rm


the only time it becomes dangerous is when you remove stuff that you need

---

