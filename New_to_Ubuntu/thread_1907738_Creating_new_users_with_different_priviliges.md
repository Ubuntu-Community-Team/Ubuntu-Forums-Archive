---
title: "Creating new users with different priviliges"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by madeel2 on 2012-01-12
I have just installed lubuntu 11.10. Now I want to create users but with different privileges.

First user (admin): A
Second user : B
Third user: C

The user A should be able to read. write, install updates as well as new software. But would have status lower than admin. That is, A can view, read, write things for the user B home folder, however user B can't do it for user A, but should be able to do so user C.

So it is A-->B-->C

Thanks in advance.

---

### Post by Rex Bouwense on 2012-01-12
Is this what you are looking for:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

By the way, welcome to the forums.

---

### Post by Double.J on 2012-01-12
You may additionally find [this]("https://help.ubuntu.com/8.04/serverguide/C/user-management.html") useful for adding the users and getting an Idea of user structure in *nix based systems.

The thing to remember is, that whilst the Root user is at the top, the most powerful of all, we never run our home systems as a root user. In Windows you may run as administrator all the time, this isn't done in Linux; the first usable user comes just under the root user level, and when we want to do things such as install things that need permission, we use th sudoers file to get root permission to do it :) Ubuntu doesn't allow user to login as root by default, and this doesn't need to be added.

---

### Post by cortman on 2012-01-12
> **madeel2 said:**
> I have just installed lubuntu 11.10. Now I want to create users but with different privileges.

First user (admin): A
Second user : B
Third user: C

The user A should be able to read. write, install updates as well as new software. But would have status lower than admin. That is, A can view, read, write things for the user B home folder, however user B can't do it for user A, but should be able to do so user C.

So it is A-->B-->C

Thanks in advance.

I'd just remove users B and C from the sudoers file, and then chmod the other users' home folders to -r, and the filesystem as well if you like.
To edit sudoers: [https://help.ubuntu.com/community/Sudoers]("https://help.ubuntu.com/community/Sudoers")
To edit file permissions (you need to be A user to do this):

```
sudo chmod go-rw folder_path
```

---

### Post by Lars Noodén on 2012-01-12
You can do it with group permissions A,B and C must be a member of group C.  A and B should be members of group B.

```

# set group memberships
sudo gpasswd --add usera userc
sudo gpasswd --add userb userc

sudo gpasswd --add usera userb

# set directory permissions
sudo find /home/userc -type d -exec chmod g=rwxs "{}" \;

sudo find /home/userb -type d -exec chmod g=rwxs "{}" \;

```

---

