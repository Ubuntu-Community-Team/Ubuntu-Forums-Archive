---
title: "FTP question"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by DarkSaga70 on 2008-06-29
I have hardy installed and in the repos it says I have lftp installed but i don't know how to launch it. I can not find it in any of the drop down menus. Please help.

---

### Post by hyper_ch on 2008-06-29
```

ps aux | grep ftp

```

what do you get?

---

### Post by DarkSaga70 on 2008-06-29
> **hyper_ch said:**
> ```

ps aux | grep ftp

```

what do you get?

 29105  0.0  0.0   3004   748 pts/0    R+   12:50   0:00 grep ftp

---

### Post by hyper_ch on 2008-06-29
ok, ftp server isn't running then.. is there a reason why you want to run a ftp server and not ssh/scp server?

---

### Post by DarkSaga70 on 2008-06-29
i just want a client like I used on windows. I used cute ftp or bullet proof ftp. thats all i need.

---

### Post by hyper_ch on 2008-06-29
is it only you who shall get access or also others?

---

### Post by DarkSaga70 on 2008-06-29
i wanna connect to my friends ftp that all.

---

### Post by hyper_ch on 2008-06-29
ah, now I get ti... I thought you want to setup ftp on your computer so that you can access it from anywhere...

---

### Post by wrtpeeps on 2008-06-29
> **DarkSaga70 said:**
> I have hardy installed and in the repos it says I have lftp installed but i don't know how to launch it. I can not find it in any of the drop down menus. Please help.

alt+f2. Type in lftp. Tried that?

---

### Post by hyper_ch on 2008-06-29
well, lftp is a ftp client for the command line - I suspect... so you might want to install a graphical one

---

### Post by cariboo on 2008-06-29
You can install gftp-gtk from either Add/Remove Prgrams or Synaptic. If you do a search for ftp in Synaptic you will be given a whole list of choices.

Jim

---

