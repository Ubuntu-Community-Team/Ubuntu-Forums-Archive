---
title: "Can't install 7-Zip ;("
date: 2008-09-13
forum: New to Ubuntu
---

### Post by holbe094 on 2008-09-13
I have ticked Z-zip from the Ad/Remove programs list and clicked on Apply.Now it says that it's installed,but I can't use it.When I rightclick a file,there is no option to extract the archive,also in the applications menu,it doesn't appear!
Please help.Thanks.

---

### Post by mikewhatever on 2008-09-13
7-zip for Linux has no GUI, hence no icon in the menu. The right click option should be 'Extract Here'. The lack of GUI doesn't mean you can't use it. 7-zip integrates with the default archives application, FileRoller, allowing you to archive and extract 7-zips.

---

### Post by holbe094 on 2008-09-13
I hope I got you right....
what i want to do is extract a RAR file and when I open it in the Archive manager,it says:
[IMG]http://img3.imagebanana.com/img/82koli8e/Screenshot.png[/IMG]

---

### Post by belda on 2008-09-13
try installing rar.

bring up the console and type

```
sudo apt-get install rar unrar
```

---

### Post by cozmicharlie on 2008-09-13
Try this for installing 7zip - works for me.
[http://tombuntu.com/index.php/2008/07/21/add-7z-7-zip-file-archive-support-to-ubuntu/](http://tombuntu.com/index.php/2008/07/21/add-7z-7-zip-file-archive-support-to-ubuntu/)

---

### Post by mikewhatever on 2008-09-13
> **holbe094 said:**
> I hope I got you right....
what i want to do is extract a RAR file and when I open it in the Archive manager,it says:
[IMG]http://img3.imagebanana.com/img/82koli8e/Screenshot.png[/IMG]

7-zip doesn't support rar archives. You'll need to install unrar.

---

