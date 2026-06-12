---
title: "cronjob to delete"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by AnLGP on 2008-07-08
I'd like to set up a cronjob to delete unnecessary files.  Where is the trash bin located in the file directory and are there any other directories that store temporary stuff (besides the /tmp folder and any download folder I created)?

What can I set to delete that won't fry the system besides user created files?

---

### Post by drs305 on 2008-07-08
User trash in hardy is stored in /home/username/.local/share/Trash/files

Previous versions stored trash in ~/.Trash

Use a bit of caution about deleting the tmp folder as the files could be in use during a session. You wouldn't want to set a cronjob that ran at a specific time unless you were sure none of the information from the tmp files was still in use.

---

### Post by ibuclaw on 2008-07-08
The trash is located in **~/.local/share/Trash**

A nice script to remove and recreate the directory would be
```

for i in /home/*
do cat /etc/passwd | grep $i
   if [ $? -eq 0 ]
   then rm -rf /home/$i/.local/share/Trash
        mkdir -p /home/$i/.local/share/Trash/files/../info
        echo "removed trash folder for $i"
   else echo "$i not a user"
   fi
done

```

Other things you can search and destroy are flush/temp files such as **foo~** and **#foo#**.

```
find /home -type f -iname "*~" -exec rm "{}" \;
find /home -type f -iname "#*#" -exec rm "{}" \;

```

other possible temp files include ***.bak** ***.tmp** and ***.log**, but whether or not you want to delete them too is arguable.

Two other folders that are safe to remove (usually not needed/not used) are:
```

~/.cache
~/.thumbnails

```
Although, they have now been fixed to have a small footprint on your hard drive space (.thumbnails in Gutsy would take up 300MB+ after 3 months) so they are probably worth ignoring now.

Other than that, there really isn't much more that you can remove.
Are you really struggling to keep hard drive space?

Regards
Iain

---

### Post by AnLGP on 2008-07-08
I'm not struggling in the least (300 gigs about using only 2.something) I just want to automate deleting stuff.  Thanks.

---

### Post by Inxsible on 2008-07-08
I would advise against deleting stuff using crons. Deleting often requires user input...and that is supposed to be read and understood by the user and then take appropriate action.

No point in having the cron screw up a system.

That being said, if you are only going to use cron to delete user data...you may as well use Shift + Del while deleting stuff as opposed to a simple Del

---

