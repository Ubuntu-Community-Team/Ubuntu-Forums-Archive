---
title: "Permissions"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Europa7 on 2008-11-12
Hi everyone.
I just installed the latest version of Ubuntu a few days ago. I am trying to install skins for the music player audacious and getting an error message that I don't have the permissions to do so. I went into the audacious folder settings and it says Root is the owner and I am not the owner. I opened terminal and logged in as root by typing sudu su, left terminal open, and reattempted the process without success. 

How do I sign on as root so I have the permission to add the new skin?

Thanks!

---

### Post by tuxxy on 2008-11-12
You could right click the folder > properties > permissions and add you as group having read/write access should work

---

### Post by Europa7 on 2008-11-12
When I go into folder > properties > permissions, it doesn't allow me to make any changes. It says Owner: root and Group: root and the drop down boxes are greyed out and not accessible. It says "you are not the owner, so you cannot change permissions".

---

### Post by tuxxy on 2008-11-12
ok open a terminal window and type this command

```
sudo nautilus /home/user/
```

Remember to edit the /home/user/ dir with the location of your folder, now you should be able to edit permission on any folders

---

### Post by Europa7 on 2008-11-12
Thanks a lot! Problem solved.

---

### Post by tuxxy on 2008-11-12
hehe np glad it worked for you, you can mark the thread solved now too :)

---

### Post by mister_pink on 2008-11-12
For future reference, the solution to not having permission to something is generally not to give yourself permission - there is, after all, a reason your usual user doesn't have access to the system files.

The correct thing to do would be to run "gksudo nautilus --no-desktop" and use that to copy the files as root. Be careful with that though, you can mess things up. Its safest to use terminal (sudo mv -i source destination) as this is nice and explicit (you can't accidentally do anything).

---

