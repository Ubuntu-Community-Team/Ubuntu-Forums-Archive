---
title: "how to locate unzip the images to /usr/local/share/uhd/images"
date: 2015-05-22
forum: New to Ubuntu
---

### Post by nur3 on 2015-05-22
hi 
i am using ubuntu14.04.
i have unzip the image UHD and it is located in the download . How can I move the unzip files to the /usr/local/share/uhd/images.
what can i do?i hope you can help me.

---

### Post by cariboo on 2015-06-18
You need to have escalted privileges in order to move the file. Probably the easiest and  quickest way is via the command line:

```
sudo mv !~/Downloads/<directory> /usr/local/share/uhd/images.
```

where <directory> = the directory name where the files are located.

---

