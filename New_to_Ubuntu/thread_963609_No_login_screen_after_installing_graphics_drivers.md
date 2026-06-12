---
title: "No login screen after installing graphics drivers"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by pluekiller on 2008-10-30
I tried posting this question on the hardware subforum, but i didn't get any answers.

After i did an apparently successful install of the 177.80 nvidia drivers, i restarted. Now, after the login screen, the black screen appears, and stays that way.

what should i do?

---

### Post by Nxion on 2008-10-30
Try this, hit CTRL+ALT+F2 or F3 or F5. This will drop you to a command line. Once there, log in with your user name and password, after you are logged in run this command and post what the outcome is.

```
startx
```

---

### Post by timcredible on 2008-10-30
did you try installing the nvidia driver from system -> administration -> hardware drivers?  that worked for my nvidia card

---

### Post by pluekiller on 2008-10-30
i will try a fresh reinstall with some tips i got off another old tread.

If that' fails, i'll run the startx command

thanks for the advice

---

### Post by Nxion on 2008-10-30
It also could be that even though you installed the drivers, they are not defined in the xorg.conf file.

---

