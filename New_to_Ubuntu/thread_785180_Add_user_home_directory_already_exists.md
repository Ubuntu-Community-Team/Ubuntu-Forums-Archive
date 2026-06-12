---
title: "Add user: home directory already exists"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by joshedmonds on 2008-05-07
A user that I had setup in 7.10 has been transferred to 8.04, but I can't log them in with their old password. When I go to users and groups, they don't appear in the list, and I can't add them because their home folder still exists. Any help appreciated.

---

### Post by mjwhitfield on 2008-05-07
rename the home directories, create the users then copy the data back into the new folders.

---

### Post by SupaSonic on 2008-05-07
After that, run 
```
sudo chown -R your_username /home/your_username 
```
so that the new user would be the owner of the files, if he isn't already.

---

### Post by joshedmonds on 2008-05-07
I'm not able to edit the folder names using the gui, what would be the appropriate cli commands?

---

### Post by SupaSonic on 2008-05-07
Say your username is **user**
```
sudo mv /home/user /home/user2
```

Create a user called '**user**' (not sure how it is from the terminal, so use GUI)
```

sudo mv /home/user2 /home/user
sudo chown -R user /home/user
```

Log out and login as a **user**

---

### Post by joshedmonds on 2008-05-07
Thanks for that. I did a 
```
gksudo nautilus
```
to rename the folders, created the users, renamed the folders again, and changed permissions with
```
sudo chown -R user_name /home/user_name
```
and it worked perfectly.

---

