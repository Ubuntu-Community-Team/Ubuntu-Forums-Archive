---
title: "how do you grant file operation permissions by command line?"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by anon0 on 2011-12-20
I'm using WinSCP to try to update some files on Ubuntu but I don't have permission to overwrite. What command can I use to grant access? Thanks.

---

### Post by tjoff on 2011-12-20
Use the command 
```
chmod
```
to set permissions on files and folders
Examples:
```
chmod +w file
```
will give all users write access to the file. 
```
chmod u+w file
```
grants write access to the file owner only.

EDIT: when I actually READ your post, I realised that you do not have shell access. Sorry for this irrelevant response

---

### Post by Lars Noodén on 2011-12-20
> **anon0 said:**
> I'm using WinSCP to try to update some files on Ubuntu but I don't have permission to overwright. What command can I use to grant access? Thanks.

There are several ways to solve the problem, but they depend on the context in which they will be used.  So a little more information is needed. Which files and/or directories?

---

### Post by anon0 on 2011-12-20
Thanks. I did chmod +w on the file, and can upload the updated file, but I still get a error message in WinSCP: 

[I]"Upload of file '[filename]' was successful, but error occured while setting the permission and/or timestamp. If the problem persists, turn on 'Ignore permission errors' option.

Permission denied.
Error code: 3
Error message from server: Permission denied
Request code: 9[/I]

Why is this happening?


> **Lars Noodén said:**
> There are several ways to solve the problem, but they depend on the context in which they will be used.  So a little more information is needed. Which files and/or directories?

I'm updating the web server files under /var/www/ and /var/lib/tomcat6/webapps/ROOT/ to test the effects.

You remind me something: is security a concern if I enable write access on these files? The files are actually online.

---

### Post by MartijnNL on 2011-12-20
I would not give write access to the world. Should be save for owner and group. So if you do 'chmod o-w' (o= other = world) you can remove write permissions for the world. To give write permissions to file just to user and group, use 'chmod ug+w'.

---

### Post by Lars Noodén on 2011-12-20
It looks like there might be a typo.  Did you mean 'chmod o=rx' instead of 'chmod o-x' ?

---

### Post by MartijnNL on 2011-12-20
Sorry, I meant 'chmod o-w' and 'chmod ug+w'. Typing too fast.

But 'chmod o=rx' would of course do the job of removing write permissions from the world as well.

Will edit the original post as well, to make sure.

---

### Post by pelle.k on 2011-12-20
Normally you would join a group that has read/write permissions in a particular directory (and subdirs), such as www or what have you. You can also utilize ACL's to expand on that. ACL's can make new files (and folders) inherit permissions from the folder it's in (recursively), instead of files (and folders) being created with your primary user/group id's (as would happen without ACL's).

Personally, i usually make use of the lazy approach with bindfs instead.
> bindfs is a FUSE filesystem for mounting a directory to another location, similarly to mount --bind. The permissions inside the mountpoint can be altered using various rules.
That way you can mount a directory (say /var/www) in /mnt/www (that is not accessible to the web server) and make changes like you are the root user (or whatever user, that depends on how you set bindfs up).
Need i say bindfs should be used with caution? Don't do anything stupid, like mounting the whole system root in a particular folder, just because it allows access to files and directories you normally wouldn't have access to...

---

### Post by anon0 on 2011-12-20
Thanks for the advice about removing write privilege to Other.

After I did chmod o-w, I got the error "cannot overwrite remote file". I did chmod o+w again, now the error message is "Upload of file 'filename' was successful, but error occured while setting the permissions and/or timestamp." It looked like the system treated me as a part of "Other". 

So I used chown username:username filename to give myself ownership, then the problem went away.

This sounds like, to work on these public files, I can chown them while removing Other-privileges. Is this ok?

---

### Post by MartijnNL on 2011-12-20
Instead of changing the file ownership to you, you could add yourself to the group to which the files belong. Setting the ownership to yourself might in some cases prevent the webserver from accessing them. Files in websites should generally be owned by the user and group from the webserver (like www-data). Then you can add yourself to this group to be able to write them. (Of course the group would need to have write permissions.)

---

### Post by anon0 on 2011-12-20
ok, so if I, "username", want to edit the server pages under /var/lib/tomcat6/webapps/ROOT/, a directory owned by "tomcat6" (the default name, I don't know if that's a group or what), what would be a good way to work with the files under ROOT/? (I'm not familiar with group commands so explicit instruction is welcome)

---

### Post by MartijnNL on 2011-12-20
run:

```
ls -dl /var/lib/tomcat6/webapps/ROOT
```

You'll see a libe consisting of permissions (drwx....), two names (tomcat6 xxxxx), some other info and the name of the directory.

The second name (indicated here by xxxxx) is the group name.

You want to add yourself to this group, do this using:

```
sudo usermod -aG xxxxx username
```

Replace xxxxx with the group name and of course replace username with your actual username.

Also make sure the group has all permissions to the ROOT directory as well (it probably already has):

```
sudo chmod g=rwx /var/lib/tomcat6/webapps/ROOT/
```

You may want to set SGID for the directory as well, to ensure that all new files get the right group as well. Or you could use the ACL solution mentioned earlier. But I have no experience with that yet.

```
sudo chmod g+s /var/lib/tomcat6/webapps/ROOT/
```

---

### Post by anon0 on 2011-12-20
Thanks! I was looking up the information and you beat me to it. I ran into the problem of refused access, but I tried logging out and back in, and then file transfer worked.

---

