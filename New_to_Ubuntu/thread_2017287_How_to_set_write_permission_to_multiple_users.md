---
title: "How to set write permission to multiple users?"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by gshreya3 on 2012-07-05
While assigning permission I am facing some problem.

I have created a folder 'TEMP' in /home directory, multiple users should access this folder.
I have created a group 'musers' and set the folder permissions as
drwxrwxr-x  2 root musers   4096 2012-06-19 12:18 TEMP

This group should be able to create/delete the folders/files in this folder.

But when any user creates any folder/file the owner and group changed for subfolders. Other group members cannot modify that subfolder or file.

I have changed umask as 002 in .bashprofile still it doesn't work.

As owner changed no one can access that file.

Please help me to set the permission.
Thanks in advance.

---

### Post by prshah on 2012-07-05
> **gshreya3 said:**
> 
But when any user creates any folder/file the owner and group changed for subfolders. Other group members cannot modify that subfolder or file.

You need to look at the command setfacl (set file access control lists).

The whole syntax is very large, so please see ```
man setfacl acl
``` for details.

Please post back if it is not clear or if you want examples.

---

### Post by Morbius1 on 2012-07-05
> I have created a group 'musers' and set the folder permissions as
drwxrwxr-x  2 root musers   4096 2012-06-19 12:18 TEMP>  I have changed umask as 002 in .bashprofile The only thing missing from what you did was to ensure that all new files "inherit" the group:
```
sudo chmod 2775 /home/TEMP
```The "2" is the setgid bit. Every new folder file will have the group: musers.

*BTW, I'm assuming you made everyone a member of the musers group.*

---

### Post by asmoore82 on 2012-07-05
**Step #1:** forget that ACL nonsense; it's not Linuxy enough and not universally supported by *nix filesystems.

**Step #2:** +1 for the setguid bit.

**Step #3:** also consider skipping the groups altogether and making a world writable folder; but you need to use the "sticky" bit which prevents users from trashing other users' files.
```
sudo chown 0:0 /home/temp
sudo chmod 1777 /home/temp
```

**Step #4:** Go to Step #0.

**Step #0:** You might want to take a step (pun intended) back and reconsider the whole scheme. Multiple concurrent users really shouldn't be writing to the same file at the same time unless using some sort of explicit version control system with conflict resolution.

If I may lay some philosophy on you, any possible solution which does not involve root access is often the best solution. Likewise, it's sometimes easy to spot a poorer solution by how invasive it is with root access.

With that in mind, if the original problem is that users need to share files; and your first step in the solution is creating a "common area" at '/home/temp' well you can see that this operation already requires root access. Is it really necessary? Well, users are fully allowed to tweak the permissions on their own folders without root access, so you could simply allow others to see what you want.

Next, users need to be able to make changes to shared files. Well, again, the most "seductive" solution is make up a new group, put the users in it, and set permissions for this group. Again, root, root, and more root. Is this necessary? It helps, for this mental exercise, to think of root in the ancient sense as the mysterious system administrator who's far too busy to be bothered every time users need to work together. I love hacking around this idea because at first glance it does seem to be impossible, unprivileged users cannot make/change groups or transfer ownership of files to other users. The users need root's help, right? Is it really necessary? Well, users can give others read-only access to files; and then those others can copy the files into their own folder space. Those users now have copies of the files fully owned by them, just as if the original user had transfered ownership of the original files. The other key difference, and a key strength of the original UNIX file permission paradigm, is that it fully protects all users involved. Each user maintains a complete, working draft of the file that others are freely allowed to pull changes from, but no one else is allowed to destroy or write changes to. The obvious drawback is that users have to take ownership (so to speak) of properly managing their own file permissions and get comfortable with the general workflow of "checking out" the newest copy of the file from whomever changed it last.

With all of that ancient philosophy under your belt, and keeping in mind the excellent default folder organization pre-populated into your home folder by almost all modern Linux distributions, consider something as simple and unprivileged as this:

```
$ **cd $HOME** [COLOR="Purple"]#go home[/COLOR]
$ **chmod 775 .** [COLOR="Purple"]#allow everyone in[/COLOR]
$ **chmod o-rwx *** [COLOR="Purple"]#allow them no deeper[/COLOR]
$ **chmod 775 Public** [COLOR="Purple"]#except in the aptly named Public folder[/COLOR]
$ **mkdir Public/Dropbox** [COLOR="Purple"]#optionally make a world writable area[/COLOR]
$ **chmod 1777 Public/Dropbox** [COLOR="Purple"]#with proper sticky permissions[/COLOR]
```

After this procedure, one just has to keep in mind that other users can see files laying around in their home folder, which is the default permissions on home folders in Ubuntu anyway. This leads to a stronger need of good computing habits: Private documents should be filed away in the Documents folder and not in the "top-level" of the home folder. :D

---

### Post by GreatDanton on 2012-07-05
@asmoore82
+1. I have to admit very nice tutorial.

---

### Post by gshreya3 on 2012-07-11
Thank you IT WORKS !!!!

---

### Post by gshreya3 on 2012-07-11
> **Morbius1 said:**
> The only thing missing from what you did was to ensure that all new files "inherit" the group:
```
sudo chmod 2775 /home/TEMP
```The "2" is the setgid bit. Every new folder file will have the group: musers.

*BTW, I'm assuming you made everyone a member of the musers group.*


Thanks It works !!

---

