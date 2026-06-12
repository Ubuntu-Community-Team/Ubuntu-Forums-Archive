---
title: "how to set up local shared folder for swapping files between local users?"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by dancingLoki on 2011-10-26
this seems like it should be easy - 

how can I set up local shared folder in Ubuntu 11.10 for swapping files between local users on same computer?

---

### Post by audiomick on 2011-10-26
Easy indeed, if all goes well. 

Create a new folder wherever you want to have it. Logical for me in this instance might be in /home but not in any of the /home/username folders. Or on a data partition somewhere else. Anyway...

When you have the folder, right click on it in the file manager, and choose preferences. There is a tab in there called "permissions" on which you can change the permissons of this folder so that anyone or no-one can read it and write into it.

If you want to change the owner, you can do that by starting Nautilus (the file manager) via a terminal with super user priviliges.

```
gksu nautilus
```

Enter your password when asked. The instance of Nautilus that now opens has super user priviliges, so be very careful what you do in there, and shut it down again as soon as you have finished what you want to do. In there, you can also accidently erase system files and what have you with the system asking if you really want to do this... ;)

In this super user instance of nautilus, the permissions tab in the properties of the folder allows change of ownership.

---

