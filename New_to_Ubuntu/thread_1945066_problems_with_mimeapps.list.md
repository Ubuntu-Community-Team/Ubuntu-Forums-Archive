---
title: "problems with mimeapps.list"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by kuckunniwi on 2012-03-22
Hi,

I'm running Kubuntu Oneric 64 bit, and am having trouble with certain issues that I'm guessing are ownership-related.

When I try to change a default program for opening a specific filetype (via properties > Application preference order), upon applying changes, I get the message 

> Configuration file "/home/*username*/.local/share/applications/mimeapps.list" not writable.
Please contact your system administrator

I checked the route, and there is nothing in the folder /home/*username*/.local/share/applications

This problem also applies to other tasks, such as editing or creating items in Kick-off app launcher (changes aren't retained).

What can I do to solve this problem? Many, many thanks!!!

---

### Post by lechien73 on 2012-03-22
Please check and post the the permissions on your ~/.local/share/applications/ directory:

```
ls -l ~/.local/share/
```

Mine is:

```
drwxrwxr-x
```

---

### Post by kuckunniwi on 2012-03-22
Thanks for the quick reply!

```
ls -l ~/.local/share/
total 52
drwxrwxr-x 5 kuckunniwi kuckunniwi 4096 2012-03-22 15:47 akonadi
drwx------ 2 root   root   4096 2012-02-07 13:10 applications
drwxrwxr-x 2 kuckunniwi kuckunniwi 4096 2012-02-06 18:50 desktop-directories
drwxrwxr-x 6 kuckunniwi kuckunniwi 4096 2012-03-20 01:34 focuswriter
drwxrwxr-x 3 kuckunniwi kuckunniwi 4096 2012-02-06 18:50 icons
drwxrwxr-x 5 kuckunniwi kuckunniwi 4096 2012-02-04 21:50 local-mail
drwxrwxr-x 6 kuckunniwi kuckunniwi 4096 2012-02-06 18:50 mime
drwxrwxr-x 5 kuckunniwi kuckunniwi 4096 2012-02-04 21:50 notes
-rw------- 1 kuckunniwi kuckunniwi 2516 2012-02-12 16:25 recently-used.xbel
drwx------ 4 kuckunniwi kuckunniwi 4096 2012-03-22 16:13 Trash
-rw-rw-r-- 1 kuckunniwi kuckunniwi 2287 2012-03-22 15:47 user-places.xbel
-rw-rw-r-- 1 kuckunniwi kuckunniwi 1998 2012-03-22 15:47 user-places.xbel.bak
-rw-rw-r-- 1 kuckunniwi kuckunniwi    0 2012-03-22 15:47 user-places.xbel.tbcache
drwx------ 2 kuckunniwi kuckunniwi 4096 2012-02-05 17:40 vlc
```

---

### Post by lechien73 on 2012-03-22
Ok, for some reason the applications directory is owned by root. Please could you try:

```
sudo chmod 775 ~/.local/share/applications
```

Then try changing the default program again?

---

### Post by kuckunniwi on 2012-03-22
nope. Same problem

---

### Post by Cheesemill on 2012-03-22
Try
```
sudo chown -R kuckunniwi:kuckunniwi ~/.local/share/applications
```
This will return ownership of the directory to you.

---

### Post by kuckunniwi on 2012-03-22
> **Cheesemill said:**
> Try
```
sudo chown -R kuckunniwi:kuckunniwi ~/.local/share/applications
```
This will return ownership of the directory to you.

Problem solved! Thanks, Cheesemill!!!

---

