---
title: "Error from viewgit on Xubuntu"
date: 2010-03-24
forum: Programming Talk
---

### Post by paulhurleyuk on 2010-03-24
I'm trying to installa  git repo server on my xubuntu (mythbuntu 9.10 actually) server.  I've followed the guide at [https://help.ubuntu.com/community/Git]("https://help.ubuntu.com/community/Git") and everything worked up to installing the viewgit web frontend.

I configured the localconfig.php file as instructed, but I get an error at the top of the window when i visit [http://myserver/viewgit/](http://myserver/viewgit/)

viewgit/inc/functions.php:84 file_get_contents(/srv/gitosis/repositories/testproject.git//description) [function.file-get-contents]: failed to open stream: Permission denied [2]

Also, I don't see any info in the project I've defined (which I can push and pull commits to/from).  When I click on anything, I get "Invalid Hash"

Anyone have any ideas ?

Thanks

Paul.

---

### Post by lisukorin on 2010-04-20
Hi Paul,
your post was created 3 weeks ago but maybe someone else have the same problem so I decide to write how I resolve it.

I just follow the same instruction , install viewgit and had the same problem.
viewgit/inc/functions.php:84  file_get_contents(/srv/gitosis/repositories/testproject.git//description)  [function.file-get-contents]: failed to open stream: Permission denied  [2]
so go to the directory /srv/gitosis/repositories and see:
```
 
ls -lh
drwxr-xr-x 7 gitosis gitosis 4,0K 2010-04-20 12:26 e-wyklady.git/
drwxr-xr-- 8 gitosis gitosis 4,0K 2010-04-20 12:21 gitosis-admin.git/

```e-wyklady is my test repository
next 
```

ls -lh e-wyklady.git

``` and instead of rights info, owner and group information I saw question marks (?)
```

?????????? ? ? 4,0K 2010-04-20 12:26 branches/
?????????? ? ? 66 2010-04-20 12:26 config
?????????? ? ? 73 2010-04-20 12:26 description
?????????? ? ? 23 2010-04-20 12:26 HEAD
?????????? ? ? 4,0K 2010-04-20 12:26 hooks/
?????????? ? ? 4,0K 2010-04-20 12:26 info/
?????????? ? ? 4,0K 2010-04-20 12:26 objects/
?????????? ? ? 4,0K 2010-04-20 12:26 refs/

```I try 
```
sudo chown -R gitosis:gitosis e-wyklady.git
``` to set owner but it won't help, so I run 
```
sudo nautilus .
```and set owner and rights in nautilus (right click on directory -> properties -> rights(third tab, I have localized ubuntu so I'm not sure it rights maybe permissions) ).
From now everythings works fine.

On my machine I run Ubuntu 9.10, filesystem ext3.

regards

Rafa&#322;

---

### Post by rygar on 2012-02-20
Also, if your repository is a bare (empty) repository, it will not work. commit something, and it might work.

---

### Post by nothingspecial on 2012-02-20
This thread is old.

Closed.

---

