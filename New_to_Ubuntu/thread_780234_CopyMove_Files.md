---
title: "Copy/Move Files"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by spotteddog on 2008-05-03
Nautilus vs Home Folder?

Which one to use? Why? Should I be using something else?  


I have found that I can either go to Places> Home Folder> view hidden folders or run gksudo nautilus> veiw hidden folers to copy and move folders and files. 
Right now I am copying data from my Windows drive to my Hardy drive. Am I on the right track?

Thanks,
Spot

---

### Post by Moop on 2008-05-03
You shouldn't need to use gksudo nautilus to copy anything into your home folder. I would just use Places-Home Folder which is the same as running nautilus without the gksudo.

---

### Post by spotteddog on 2008-05-03
Thanks, Moop. 

Does the same hold true for files such as my FireFox and ThunderBird Profiles?

---

### Post by Moop on 2008-05-03
> **spotteddog said:**
> Thanks, Moop. 

Does the same hold true for files such as my FireFox and ThunderBird Profiles?

The same holds true for everything going into your home folder. You only need to use gksudo nautilus when you don't have permission (it won't let you) to access a file.

---

### Post by master5o1 on 2008-05-03
Any file and folder in your home folder can be 'manipulated' by you.

/home/user/* where * = any file or folder, can be copied, moved or manipulated in any other way by you!

---

