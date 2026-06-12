---
title: "unable to move folders  on the same drive"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by madnomad on 2008-11-12
Hi,

please do not laugh if its a very basic question...:)

Why is it not possible to move files from my folder to the root of the drive?

mv -v /media/disk1/myfolder /media/disk1

I get this following error:

mv: '/media/disk1/myfolder' and '/media/disk1' are the same file

how do I move my data to /media/disk1?

Thank you for any explanation.

Peter

---

### Post by Shwefty on 2008-11-12
I just tried this out myself, to move an item I first navigated to the directory inside of Terminal.

```

mark@mark-laptop:~/Desktop$ cd Test2
mark@mark-laptop:~/Desktop/Test2$ ls
Folder
mark@mark-laptop:~/Desktop/Test2$ cd Folder
mark@mark-laptop:~/Desktop/Test2/Folder$ ls
Document
mark@mark-laptop:~/Desktop/Test2/Folder$ mv Document ~/Desktop/Test2
mark@mark-laptop:~/Desktop/Test2/Folder$ cd ..
mark@mark-laptop:~/Desktop/Test2$ ls
Document  Folder
mark@mark-laptop:~/Desktop/Test2$ 

```

I have a folder named "Test2", inside of "Test2" is a folder named "Folder", inside of "Folder" there is a document named "Document".

To move "Document" up from "Folder" to "Test2", I used the command:

```
mark@mark-laptop:~/Desktop/Test2/Folder$ mv Document ~/Desktop/Test2
```

Essentially, I think you forgot the tilde (~)!

---

### Post by Shwefty on 2008-11-12
I moved the Document "Document", but, you also can move the Folder "Folder" from the folder "Test2" to the desktop by the command:

```
mv Folder ~/Desktop
```

Assuming you're in the correct directory.

---

