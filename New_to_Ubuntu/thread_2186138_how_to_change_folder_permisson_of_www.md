---
title: "how to change folder permisson of www"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by vamshikrishna072 on 2013-11-06
im trying to create file in www folder but im not having permissons to create so . 

my www folder rights
drwxrwxr-x  2 root root     4096 Oct 22 18:39 www

i tried this command still no change 
sudo chmod u+x www


please help me how to change this folder permission?

---

### Post by nerdtron on 2013-11-06
You need to be familiar on understanding permissions, such as user/groups/others. Please read [http://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](http://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions)

```
sudo chmod u+x www
```
Nothing will happen on this command. It just says that the user/owner (which is the root user) will be able to execute (enter) the www folder.

You can try:
```
sudo chmod a+w www
```
This will allow all users to be able to write on the www folder. 

The previous command will allow everyone, but what if you just want your self to be the owner and be able to write on the folder? Change the ownership of the folder:
```
sudo chown -R user:user www
```

---

### Post by vamshikrishna072 on 2013-11-06
thanks
 that worked for me .. :D

---

### Post by Lars Noodén on 2013-11-06
This one can cause trouble:

```

[s]sudo chmod a+w www[/s]

```

It really does allow any account to write to that directory, including the web server process.  That can cause lots of trouble by removing a layer of protection.  The web server processes should not have write access.  You can set it back this way:

```

sudo chmod o=rwx,g=rwx,o=rx www

```

If you are the only user on that system you can gain write access simply by taking ownership of the directory.

```

sudo chown vamshikrishna072 www

```

That's the much safer way.

---

