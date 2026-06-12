---
title: "Folder security"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by domoappo on 2012-05-31
I was looking to password protect a folder, so I followed what this guy said on his website to create a protected folder >[http://www.liberiangeek.net/2012/04/create-a-private-password-protected-folder-in-ubuntu-11-10-12-04/](http://www.liberiangeek.net/2012/04/create-a-private-password-protected-folder-in-ubuntu-11-10-12-04/)

It created a folder called Private, but when I open the folder it doesn't ask me for a password, it just opens up and displays everything inside. Now it won't even let me delete the folder, or even uninstall the program. Can you help me either get it work, or get rid of it? Thanks :  )

---

### Post by Cheesemill on 2012-05-31
The folder that you have created is encrypted and password protected, it's just automatically unlocked with your user password when you log in.

Anyone else trying to access the contents won't be able to, even if they have root access to your machine or boot from a Live CD.

To remove this folder just follow the instructions given by:
```
ecryptfs-setup-private --undo
```

---

### Post by domoappo on 2012-05-31
Okay, so the folder can be accessed only when I'm logged on? Is there any way to make the folder require a password even when I'm logged on? Because that's what I was trying to do. And thanks so much for the help!

---

