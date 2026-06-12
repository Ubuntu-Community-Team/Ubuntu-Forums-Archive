---
title: "mhddfs and Samba issues"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by NRF19 on 2013-06-19
Hey, 

I have installed mhddfs to take advantage of its virtual pooling which I like very much. I have it setup as such

```
sudo mhddfs /media/1,/media/2,/media/TV,/media/Movies media/root/Media -o allow_other
```

I also have installed the samba package which I use to share with my windows HTPC and also main desktop.

I am pretty new to Linux and so don't really understand what is going on and need a simple as possible explanation as to how to solve this,

my problem is that I can create the samba share in the samba app and make it accessible to my user (nathan) with my password, but when I go over to windows and enter this combination I get the following error message

```
\\Tower\Media is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

Multiple connections to a server or shared resource by the same user, using one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again
```

I have changed the ownership/permissions of the directory from root to myself but nothing seems to have changed in being able to access via my windows PC.

Edit:
i found this article [HTML]http://nowhere.dk/post/48105927208/fuse-coolness-with-mhddfs[/HTML] and I am wondering whether the final element is my proble,, however I don't understand how to do/what parts of that code to adapt and how to add it to my /etc/exexports 

please can somebody help,
thanks
NRF19

---

### Post by NRF19 on 2013-06-20
I've tried to figure out what I need to do but I cannot find a file in /etc/exports and as such I'm at a loss. I have no permission to access this folder or any of the subfolders via samba on my windows PC's

---

### Post by NRF19 on 2013-06-20
Solved it by mounting the drives manually via terminal as sudo rather than doing it via sudo palimpsest

---

