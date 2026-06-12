---
title: "[SOLVED] need help in moving to the right directory"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by imjscn on 2008-07-12
in the File Manageer, if I click my name, I can see there are Desktop and several other folders of mine. Now I want to move FolderX from /data into /myname, in the /data directory, I typed:
sudo mv FolderX /myname

it tells me no such a file or directory. 

If I type in: sudo mv FolderX /home
then, the FolderX goes to /home instead of /myname

How can I move it to /myname? Thanks!

---

### Post by meindian523 on 2008-07-12
what directory are you in while issuing the first command?

EDIT:
Note to all others,I want the OP to learn more about directory structure and the terminal,or I could have just told him to use the graphical sudo nautilus.

---

### Post by boblemur on 2008-07-12
sorry your post is a little confusing??

can u tell me what

pwd gives u...

as well as the full paths of the things you are trying to move...

---

### Post by brian_p on 2008-07-12
> **imjscn said:**
> 
How can I move it to /myname? Thanks!

```
sudo mv FolderX /home/myname
```

---

### Post by imjscn on 2008-07-12
oh my god, thanks a lot, this code moved it to /myname

when I first went wrong, I was in /data directory. It's really tricky...you never know when the file goes to /home, or to /myname, or to /Desktop 

thanks very much!

---

### Post by meindian523 on 2008-07-12
Well,you know where you are by typing either ```
pwd
``` which translates to Present Working Directory or by looking at the path before the prompt,for example:
```
easwarh@l1nuxr0cks:~/Documents/Research Wing/Linux/06.Misc$
```
In this segment,I'm in the directory which has the path ```
~/Documents/Research Wing/Linux/06.Misc
``` where ~ translates to /home/<username>
Please mark your thread solved.

---

