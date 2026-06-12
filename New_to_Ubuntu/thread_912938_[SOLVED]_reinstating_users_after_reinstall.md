---
title: "[SOLVED] reinstating users after reinstall"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by gj_clt on 2008-09-07
Haven't yet found anything in the forum. I reinstalled 8.04 after I got in a mess getting my Sound Blaster card to work. Everything is now o.k Except the other users on the system cannot log in and I can't add them as new users using their old names and passwords. I did the reinstall by FORMATTING '/' and swap but not the /home partition. Can I enable these old accounts?

---

### Post by astoltz on 2008-09-07
So we probably need some more info.  Are the files for the other users still present on the /home directory?  Why can't you add the old user names back in (I mean what happens when you try)?  Do you have any other users added (besides yourself) currently?

Would you post the output of "ls -l /home"

---

### Post by gj_clt on 2008-09-07
Yes the other users files are all there in their /home directory. The problem is that when they try to log on they are not recognized and when I try to add them as new users I can't because their /home directory is still there.

---

### Post by gj_clt on 2008-09-07
Sorry I forgot to add this to previous post. The original users I cannot get recognised are clt. mt and dt. The users clare, marie and david are NOT needed as that was just done to see what would happen. So I can add NEW users but cannot get the original users to be recognized although all their files are present
drwxr-xr-x 24 1001 clare  4096 2008-09-07 12:10 clare
drwxr-xr-x 27 1001 clare  4096 2008-09-03 11:20 clt
drwxr-xr-x  2 1003 david  4096 2008-09-07 12:09 david
drwxr-xr-x 32 1003 david  4096 2008-09-06 12:21 dt
drwxr-xr-x 63 gt   gt     4096 2008-09-07 12:45 gt
drwx------  2 root root  16384 2008-08-25 18:37 lost+found
drwxr-xr-x  2 1002 marie  4096 2008-09-07 12:08 marie
drwxr-xr-x 36 1002 marie  4096 2008-09-06 15:51 mt
gt@gt-desktop:~$

---

### Post by sanemanmad on 2008-09-07
> **gj_clt said:**
> Yes the other users files are all there in their /home directory. The problem is that when they try to log on they are not recognized and when I try to add them as new users I can't because their /home directory is still there.
Hi gj_clt~

I cannot say for sure this will work; however this is directly from the --usage command. 

try using one of these options 

*useradd $user -d /home/$user* [COLOR="Red"]and/or [/COLOR]*useradd $user -b /home*

 > 
-b, --base-dir BASE_DIR       base directory for the new user account
                                home directory
 -d, --home-dir HOME_DIR       home directory for the new user account


---

### Post by kpatz on 2008-09-07
First, clean up the groups and home directories of the "test" users you created.
```

sudo delgroup clare
sudo delgroup david
sudo delgroup marie
sudo rm -r /home/clare /home/david /home/marie

```

Then run **ls -ln /home**, to get the uid/gid of the problem users.

Then, to re-add the users,
```

sudo adduser --no-create-home --group --uid 1001 --gid <gid_of_clt_home_dir> clt
sudo adduser --no-create-home --group --uid 1002 --gid <gid_of_mt_home_dir> mt
sudo adduser --no-create-home --group --uid 1003 --gid <gid_of_dt_home_dir> dt

```

Substitute the gids you got in the ls -l for the home directories in the --gid options above.  Once you do this, the users should be added, and their uid/gids will match the ownerships of their home directories, so there shouldn't be any need to chown anything.

---

### Post by astoltz on 2008-09-07
The userid and groupid numbers (the "1001, 1002, 1003" parts) are mixed up.  Looks like kpatz beat me to the solution.

Just be careful with the names when deleting directories because things will look a little mixed up 'till you get everything sorted out.

---

### Post by gj_clt on 2008-09-07
Thanks kpatz that has sorted it out.

---

