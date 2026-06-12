---
title: "chmod a directory with or without / ?"
date: 2015-08-10
forum: New to Ubuntu
---

### Post by FlintL on 2015-08-10
Is there any difference if I chmod or chgrp a directory and keep a / at the end?
   
  ```
sudo chmod 640 -R /etc/my_folder


```  or
  ```
sudo chmod 640 -R /etc/my_folder/


```

---

### Post by dino99 on 2015-08-10
[http://manpages.ubuntu.com/manpages/vivid/en/man1/chmod.1.html](http://manpages.ubuntu.com/manpages/vivid/en/man1/chmod.1.html)

---

### Post by FlintL on 2015-08-10
The man page is not very helpful to me. Can you please point to the section that answers my question? I probably don't understand the part you are referencing.

---

### Post by VMC on 2015-08-10
A trailing slash "/" means its a folder, but it depends on the command. Read here:
[http://unix.stackexchange.com/questions/1910/how-does-linux-handle-multiple-consecutive-path-separators-home-username](http://unix.stackexchange.com/questions/1910/how-does-linux-handle-multiple-consecutive-path-separators-home-username)
or here:
[http://unix.stackexchange.com/questions/50499/when-should-i-use-a-trailing-slash-on-a-directory](http://unix.stackexchange.com/questions/50499/when-should-i-use-a-trailing-slash-on-a-directory)

---

