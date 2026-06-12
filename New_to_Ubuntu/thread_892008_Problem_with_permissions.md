---
title: "Problem with permissions"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Gorguts on 2008-08-16
I am having a problem with setting my permissions. I am trying to install an aMSN skin to my root directory but there is one problem... it says i do not own the file, therefore it blocks my access when i try to edit the folder and paste my new skin into it. 


here is a Screen shot:
[IMG]http://www.snapdrive.net/files/190310/Grr.png[/IMG]

---

### Post by sisco311 on 2008-08-16
Open the file manager as root.

Press Alt+F2 and run:
```
gksu nautilus
```

---

### Post by Gorguts on 2008-08-16
thank you very much :)

kind of new to ubuntu of course. 
still trying to learn more about it haha.

---

### Post by sisco311 on 2008-08-16
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

### Post by mike1234 on 2008-08-16
> **sisco311 said:**
> Open the file manager as root.

Press Alt+F2 and run:
```
gksu nautilus
```

 Next question. After running gksu don't I need to logout/login? How long would it remain root? (Security issue)? Great tip by the way.

Mike

---

### Post by sisco311 on 2008-08-16
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

