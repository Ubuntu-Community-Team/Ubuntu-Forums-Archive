---
title: "i need help with writing an script to synchronize two folder"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by legolas_w on 2008-05-31
Thank you for reading my post.

I have folder A which contains about 100 JPG files and folder B which has 1000s of JPG files.

I want to replace all files which are inside folder A with the same file from folder B. Files which are inside folder A has the same name with files which are inside folder B.

Is there any program which can do this?
Can you give me a hand with writing an script for this?

Thanks.

---

### Post by quelx on 2008-05-31
Are the common files with the same names the same file, eg is **./folderA/foo1234.jpg** the image as **./folderB/foo1234.jpg**?

If so **rsync** can synchronize the folders.

```
rsync -a --progress ./folderA/ ./folderB/
```

And to get **folderA** with the same info just reverse the order

```
rsync -a --progress **./folderB/** **./folderA/**
```

---

