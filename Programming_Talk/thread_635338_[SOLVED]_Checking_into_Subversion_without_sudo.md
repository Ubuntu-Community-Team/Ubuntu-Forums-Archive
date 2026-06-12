---
title: "[SOLVED] Checking into Subversion without sudo"
date: 2007-12-08
forum: Programming Talk
---

### Post by sillv0r on 2007-12-08
First, I apologize if this is the wrong forum to ask about source control systems.

I've been using subversion 1.4.4 on 7.10 for a while now.  My issue is that whenever I want to check something in I'm required to sudo in order for the command to update the appropriate svn system files.

Q1: **Does this have to do with where I installed it? ** I have a feeling it has to do with permissions on the folder where my repository exists.  I didn't want the repository in any users folder.  I wanted it in a more general folder.  namely: "/usr/local/subversion"  as the root for my source tree.

Q2: **Is it wise to simply change the permissions **on that root folder to allow everyone access?  Or is there a way I can setup permissions based on those with ssh or apache access?

(If i'm not developing using vim on the server, as is the case when I use tortoise on a windows box connecting through apache, it seems to work appropriately.)

I just don't like my repository filled with changes by "root".  

Any information is greatly appreciated!

---

### Post by geirha on 2007-12-08
> **sillv0r said:**
> 
Q1: **Does this have to do with where I installed it? ** I have a feeling it has to do with permissions on the folder where my repository exists.  I didn't want the repository in any users folder.  I wanted it in a more general folder.  namely: "/usr/local/subversion"  as the root for my source tree.

Where you place it is irrelevant as long as all users that should have access to it has access to that path. /usr/local/subversion is an ok place to have it.
> **sillv0r said:**
> 
Q2: **Is it wise to simply change the permissions **on that root folder to allow everyone access?  Or is there a way I can setup permissions based on those with ssh or apache access?

Changing permissions and ownership of the subversion repository is the common way to do it. Basically: 
1. create a group and add all users that should have write access to the subversion repository to that group. (System -> Administration -> Users and groups)
2. in the repository directory, there should be a directory called **db/**. Give the group you created group ownership of that dir and all its subdirectories and files, and give the group write access. You do this either with nautilus as root (sudo nautilus) or with the following commands in a terminal:
```
sudo chgrp -R *groupname* /usr/local/subversion/*repository_name*/db
sudo chmod -R g+w /usr/local/subversion/*repository_name*/db
```

---

