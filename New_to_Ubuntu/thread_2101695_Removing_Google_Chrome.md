---
title: "Removing Google Chrome"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by Robert1305 on 2013-01-05
I have an edition of G/C that was installed by a terminal command, I don’t know how cos I haven’t  done it.

What I need is the terminal command to UN-install it completely.

Thank you, Regards Bob.

---

### Post by vasa1 on 2013-01-05
```
sudo apt-get purge google-chrome
```should do it. If you still have a functional G/C, run ```
 dpkg --get-selections | grep "chrome" > ~/Desktop/temp.txt
``` and post the output of that file here.
Once you've purged G/C, go into **~/.config** and delete the folder called **google-chrome**. That will remove files created by G/C in your home folder.

---

### Post by Robert1305 on 2013-01-05
Thanks Vasa1, I had solved the problem by using Synaptic manager.

Will the commands you gave me do for removing any programs. I would have to substitute G/C of course.

Thanks again, Regards Bob ):P

---

### Post by vasa1 on 2013-01-05
> **Robert1305 said:**
> Thanks Vasa1, I had solved the problem by using Synaptic manager.

Will the commands you gave me do for removing any programs. I would have to substitute G/C of course.

Thanks again, Regards Bob ):P

Most of the common apt-get commands are here: [https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet)

Worth a look.

---

