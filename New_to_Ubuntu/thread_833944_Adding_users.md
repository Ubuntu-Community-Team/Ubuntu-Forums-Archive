---
title: "Adding users"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by ub007 on 2008-06-19
Hi,

This is my first post & its great using Ubuntu.
I added few users using both 'adduser' & 'useradd' commands.Also created groups and added the users to it.Now, how do i view the users which i just added.eg...I have added 3 users (james,mark,john) to a group 'beginners'.which command will list me the group -'beginner' & the users in it?

Secondly,how do i assign admin rights to one of the users in that group?

I've just started off with Linux and sorry guys,if I ask somethin really naive or stupid.

Cheers,
David

---

### Post by hyper_ch on 2008-06-19
```

cat /etc/group | grep beginner

```

---

### Post by iaculallad on 2008-06-19
You could use the **id** terminal command to list the groups of where a user belongs.

```
id username
```

---

### Post by cariboo on 2008-06-19
You could also use System-->Administration-->Users and Groups

Jim

---

### Post by ibutho on 2008-06-19
To add a user to the admin group
```
sudo gpasswd -a user admin
```
Change "user" to the username of the person you want to add to the admin group.

To check for the users in a group, you could try
```
grep -i group /etc/passwd
```
You can further refine the output using something like awk.

---

### Post by ub007 on 2008-06-19
Thank you so much!that helps....

---

