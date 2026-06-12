---
title: "File Permissions problems"
date: 2019-06-15
forum: New to Ubuntu
---

### Post by diegoatravesar on 2019-06-15
Hello Everyone,

I am experiencing some issues with file permissions. I have created a group called "serv" which I want to use as the group to access a couple of folders.
I need both my login, 'media' and a second login 'plex' to have access to those folders, so I have added both 'media' and 'plex' to the 'serv' group. However, 'plex' can only access the folders if I set the user owner to 'plex', it doesn't seem to care that it belongs to 'serv'.

Output of 'members serv':
```
media plex
```

Output of 'id media':
```
uid=1000(media) gid=1002(serv) groups=1002(serv),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),117(lpadmin),1000(sambashare)
```

Output of 'id plex':
```
uid=121(plex) gid=1002(serv) groups=1002(serv),44(video)
```

Output of 'ls -la' for one of the directories in question:
```
drwxrwxr-x 79 plex serv 4096 Jun 13 16:03  **.**
drwxrwxr-x  9 plex serv 4096 Jun 13 16:03  **..**
drwxrwxr-x  5 plex serv 4096 Jun  6 09:56 **'First Vacation'**
drwxrwxr-x  9 plex serv 4096 Jun  9 23:25  [COLOR=#5620f4]**Home**[/COLOR]
drwxrwxr-x  2 plex serv 4096 Jun  4 18:09 **'Up North'**
drwxrwxr-x  2 plex serv 4096 Jun  4 18:09 [B]'Vacation 2019'
[/B]
```[COLOR=#222222][FONT=Verdana]

In the above case, 'plex' can access everything just fine, however if I change the user owner to 'media', 'plex' can no longer access the folders or anything in them.


This has been especially frustrating as I had at one time figured out the permissions to resolve this, however I have since wiped the system and lost all of that information.[/FONT][/COLOR]

---

### Post by TheFu on 2019-06-15
How to have multiple users work together on the same files - this is from some classes I taught.
```

    Put everyone into the same group.
    Create a directory where they can share files.
    Make the group on that empty directory have rws permissions
           $ sudo gpasswd -M  user1,user2,user3  ourgroup
           $ mkdir -p /tmp/Workspace
           $ chmod g=rwxs Workspace
           $ ls -lF Workspace
              drwxrw[COLOR="#FF0000"]s[/COLOR]---   user1    group    Workspace/ 
           $ chgrp ourgroup Workspace
           $ ls -lF Workspace
              drwxrws---   user1    [COLOR="#FF0000"]ourgroup[/COLOR]    Workspace/
```
If this is all about plex, then I'd just use the plex group and not create a new group.
For areas where you don't want plex to have access, only there would I use a different group.

The users - user1, user2, user3 - need to either logout and login again or use the newgroup command to refresh the current groups. newgroup only works in the current session, so that would be limited to the current terminal.  The logout/login process would refresh the group list in the entire session.  When there are large number of groups, something over 20, then some tools might not see them without the newgroup being run to make the primary group the require one.  The limit on group count is documented somewhere.

If you have already setup directories, then every directory will need the permissions and group to match the above.  A recursive 'find' is probably the easiest solution.  It is fine if "other" has r-x access on the directories and/or files.  Files only need to be in the group to share.  Above, that would be "ourgroup".

---

### Post by diegoatravesar on 2019-06-18
So if I run ```
groups
``` I don't actually have a plex group, just the default linux groups and the 'serv' group that I created.

In order to follow the steps you have above, I created a group called 'server' to test from a fresh group.
I then ran the 'gpasswd' line which added the new group to each of my users. I verified this by running 'id media' and seeing the new group listed as a secondary group.

As I already have my directory structure in place, I skipped the 'mkdir' line.

I then ran 'chmod -R g=rwxs /PATH' to recursively set the permissions to all of the sub-directories as there are a good number of them.
I ran 'ls -lF /PATH' to confirm the perimssions showed 'drwxrwsr-x' for the directory.
I ran 'chgrp -R server /PATH' and then the 'ls lF /PATH' again to verify the directory(and subdirectories in turn) were using the new group.
The only user I can log in / out with is 'media' as 'plex' is a non-login user tied to the Plex Media Server software. My solution for this was to reboot the entire server, hoping that this would forcefully log all users out and then log them in upon starting up.
I did try running 'newgrp' as 'media' but it didn't appear to change anything, and logging out of the terminal and logging back in stills shows the new 'server' group as a secondary group and not the primary one.

I did run a recursive find as well, after a bit of research. ```
sudo find /PATH/ -type d -exec chmod g=rwxs {} \;
``` on both the directories and then the files. I didn't find that this resolved anything either. 

So my users are still using their original primary group, but do have the secondary group correctly, and my directories have the group set correctly, however I am still having the issue where the permissions only appear to respect the user permissions, not the groups.

---

