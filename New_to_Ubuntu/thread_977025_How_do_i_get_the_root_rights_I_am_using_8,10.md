---
title: "How do i get the root rights? I am using 8,10"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by sven_wien on 2008-11-09
Hello all,

i am using the german version of ubuntu 8,10 and i am trying to install openttd but when u try to copy the original files into the games folder then i need the root rights and i dont have them in my user profile!
How do i get those?

Please help 

many thanks

sven

---

### Post by Metaleks on 2008-11-09
If you're using the terminal, just put "sudo" in front of whatever you're trying to do.

If you're trying to do something in nautilus, open up the terminal and type "gksudo nautilus" then do whatever you wanted to do.

---

### Post by drs305 on 2008-11-09
Here's the Ubuntu explanation of Root and the use of sudo/gksudo:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

When you feel you have had your questions answered, please mark the thread solved with the "Thread Tools" link at the top right of the first post.


Welcome to the ubuntu forums sven_wien!

---

### Post by sven_wien on 2008-11-09
well i am trying to get a folder into root but not via terminal if that is possible!
I just need access to the folder /usr/share/games/openttd 
pls just in easy to manage way as i am new to linux

many thanks

---

### Post by drs305 on 2008-11-09
Open nautilus with root privileges:
```
gksu nautilus /usr/share/games
```

That should open the file browser in the games folder and you should see your file or folder. Since you opened it as root, you will be able to move or copy it anywhere you wish. If you are trying to move a folder or file into games, navigate around until you find it.

Right clicking on a file or folder will open the options to cut, paste, etc.

---

### Post by sven_wien on 2008-11-09
many thanks

---

