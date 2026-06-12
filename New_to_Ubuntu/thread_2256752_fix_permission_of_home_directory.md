---
title: "fix permission of /home directory"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by raj10 on 2014-12-14
[[TABLE]
[TR="bgcolor: transparent"]
[TD="class: postcell, bgcolor: transparent"][/TD]
[TD="class: votecell, bgcolor: transparent"][CENTER][COLOR=#777777]
0[/COLOR]down vote[favorite]("http://askubuntu.com/questions/561369/resetting-home-permission/561381#")
[/CENTER]
[/TD]
[TD="class: postcell, bgcolor: transparent"]I changed the permission of /home folder to 777 and now I cannot access my account and login only as a guest (Ubuntu 14.04) with no sudo support.
Permission in home folder is as follows:
drwxr-xr-x 134 root root 12288 Dec 14 11:47 etc
d---------   4 root root  4096 Dec 14 09:50 home
drwxr-xr-x  24 root root  4096 Dec 11 23:04 lib
drwxr-xr-x   2 root root  4096 Dec  4 18:05 lib32
drwxr-xr-x   2 root root  4096 Dec  4 18:05 lib64
drwx------   2 root root 16384 Nov 30 23:42 lost+found
I will appreciate if there is a fix other than reinstall.


[/TD]
[/TR]
[/TABLE]

---

### Post by nerdtron on 2014-12-14
You can boot into Live CD (or USB) and change the permissions there.
The /home folder is owned by root.
```
sudo chmod 755 /home
sudo chown root:root /home
```

Next you home folder and everything inside it is owned by your username.
```
sudo chown -R username:username /home/username
```

After those, I think we need to see the permissions of the folder so you may need to post the output here:
```
ls -lah /home/username
```

---

### Post by Lars Noodén on 2014-12-14
You should be able to get to a console by pressing ctrl-alt-f1 and then log in.  You won't get your home directory until you fix the permissions but it should let you work in the shell anyway.  

Then set the permissions to the original default:

```

chmod u=rwx,g=rx,o=rx /home

```

Then when you are done, press ctrl-alt-f7 to get back to the graphical interface.  

Or if you can boot into recovery mode, you can use that.  Otherwise a live system like the Desktop DVD would work.

---

### Post by nerdtron on 2014-12-14
Edit: just realized my question :)

---

### Post by raj10 on 2014-12-14
Thanks, but I cannot do sudo becasue I can log in only as guest. I tried to log off as guest and login as regular user (raj) but it is not accepting my passowrd! I dont get any error message - the screen goes blank and then comes back with the login screen.

---

### Post by nerdtron on 2014-12-14
That's why we suggested you boot using a Live DVD or Live USB.

Or as Lars Nooden suggested: > You should be able to get to a console by pressing ctrl-alt-f1 and then log in.

---

