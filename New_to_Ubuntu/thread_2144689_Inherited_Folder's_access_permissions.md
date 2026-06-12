---
title: "Inherited Folder's access permissions"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by mbnoimi on 2013-05-13
I created "First" folder and edited its permissions to rwx as shown below:
[ATTACH=CONFIG]242546[/ATTACH]

Then I created sub-folder "Second" but it didn't inherit the parent folder permissions as shown below:
[ATTACH=CONFIG]242547[/ATTACH]

How can I activate folder's access permissions inheritance?

---

### Post by dino99 on 2013-05-13
use chown :

sudo chown youruser:youruser /path/to/folder

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Morbius1 on 2013-05-13
Linux doesn't have file permissions inheritance - at least not in the traditional way and at least not in the way you want it to be.

But before you get too far with any non-traditional way you need to ask yourself why it's necessary for you to do this. What you have right now is this:

/First ~ owner = mbnoimi , permissions = 700 
[COLOR=#0000cd]*Only mbnoimi  will gain access to that directory*[/COLOR]

/First/Second ~ owner = mbnoimi, permissions = 775

A given directory can only be accessed through the path to that directory so the only user that can access /First/Second is mbnoimi even if permissions on Second were 777 since /First won't let anyone else through.

---

### Post by mbnoimi on 2013-05-13
> **dino99 said:**
> use chown :

sudo chown youruser:youruser /path/to/folder

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I don't want apply permissions manually whenever I created a new folder or file

---

### Post by mbnoimi on 2013-05-13
> **Morbius1 said:**
> Linux doesn't have file permissions inheritance - at least not in the traditional way and at least not in the way you want it to be.

But before you get too far with any non-traditional way you need to ask yourself why it's necessary for you to do this. What you have right now is this:

/First ~ owner = mbnoimi , permissions = 700 
[COLOR=#0000cd]*Only mbnoimi  will gain access to that directory*[/COLOR]

/First/Second ~ owner = mbnoimi, permissions = 775

A given directory can only be accessed through the path to that directory so the only user that can access /First/Second is mbnoimi even if permissions on Second were 777 since /First won't let anyone else through.

Hmm you want to whole story behind my question :)

I'm sharing my files over the network through SAMBA so whenever I created a sub-folder in the main shared folder the users can't see it because I've to change the permissions manually as the main folder's permissions. Same problem happen when network users add a new folder to my shared folder, I can't access it until I modify the permissions manually.

PS
I know this must be SAMBA's quesiuon but I face same issue with FTP shared folders too.

---

### Post by bab1 on 2013-05-13
> **mbnoimi said:**
> Hmm you want to whole story behind my question :)

I'm sharing my files over the network through SAMBA so whenever I created a sub-folder in the main shared folder the users can't see it because I've to change the permissions manually as the main folder's permissions. Same problem happen when network users add a new folder to my shared folder, I can't access it until I modify the permissions manually.

PS
I know this must be SAMBA's quesiuon but I face same issue with FTP shared folders too.

You can set a folders inheritance with the SUID and SGID bits.  You set the default permissions with UMASK.

---

### Post by mbnoimi on 2013-05-13
> **bab1 said:**
> You can set a folders inheritance with the SUID and SGID bits.  You set the default permissions with UMASK.

How can I do it?

I tried to apply it for the main folder as following:
[ATTACH=CONFIG]242550[/ATTACH]

but the default permissions of sub-folders (created after applying the new permissions for main folder) is:
[ATTACH=CONFIG]242551[/ATTACH]

---

### Post by bab1 on 2013-05-13
Permissions are not inheritance ownership.

Tip: don't set the UID on these folders.  The user is not important if all the users are in the same group.  Just use SGID and put all the users in the group *users *.  Then create a sub folder and see if the group is still *users*.  If so we can set the permissions in the next step.

Where in the file system tree are you creating this Samba share (/srv or /data or ...)?

---

### Post by Morbius1 on 2013-05-13
> I'm sharing my files over the network through SAMBA so whenever I  created a sub-folder in the main shared folder the users can't see it  because I've to change the permissions manually as the main folder's  permissions. Same problem happen when network users add a new folder to  my shared folder, I can't access it until I modify the permissions  manually.

Since /First is set to owner = mbnoimi , permissions = 700 none of your samba clients can add to or even access the share unless they are coming in as mbnoimi but for the sake of argument one solution is to make everyone look like mbnoimi:

Add the following line to /etc/samba/smb.conf:
```
force user = mbnoimi
```
[COLOR=#0000cd]*Where you put that line depends on how you created the samba share. If  you want it to apply globally to all your shares then add it under the  "workgroup = " line. If you want it to happen only to a specific share  then add it to the share definition.*[/COLOR]

Then restart samba:
```
 sudo service smbd restart
```

After the samba client gains access either as a guest or as a credentialed user he will be converted to mbnoimi. Everything they do they will do as mbnoimi - at least for your samba share.

*[COLOR=#0000cd]**EDIT**[/COLOR]:[COLOR=#0000cd] This post: [/COLOR]*
> I'm sharing my files over the network through SAMBA so whenever I  created a sub-folder in the main shared folder the users can't see it  because I've to change the permissions manually as the main folder's  permissions. Same problem happen when network users add a new folder to  my shared folder, I can't access it until I modify the permissions  manually.

*[COLOR=#0000cd]Is just the opposite of what you originally described as your requirement: You wanted all subfolders to have owner = [/COLOR][COLOR=#0000cd]mbnoimi and permissions of 700.[/COLOR]*

---

### Post by mbnoimi on 2013-05-22
> **Morbius1 said:**
> Since /First is set to owner = mbnoimi , permissions = 700 none of your samba clients can add to or even access the share unless they are coming in as mbnoimi but for the sake of argument one solution is to make everyone look like mbnoimi:

Add the following line to /etc/samba/smb.conf:
```
force user = mbnoimi
```
[COLOR=#0000cd]*Where you put that line depends on how you created the samba share. If  you want it to apply globally to all your shares then add it under the  "workgroup = " line. If you want it to happen only to a specific share  then add it to the share definition.*[/COLOR]

Then restart samba:
```
 sudo service smbd restart
```

After the samba client gains access either as a guest or as a credentialed user he will be converted to mbnoimi. Everything they do they will do as mbnoimi - at least for your samba share.

Thanks, this works for SAMBA :)

> Is just the opposite of what you originally described as your requirement: You wanted all subfolders to have owner = mbnoimi and permissions of 700. 
I'm still missing it. I want to inherit the parent folder permissions and owner too... Any suggest?

---

### Post by bab1 on 2013-05-23
> **mbnoimi said:**
> Thanks, this works for SAMBA :)


I'm still missing it. I want to inherit the parent folder permissions and owner too... Any suggest?

In post #6 and in #8 I gave you the answer.  It appears that you can't set it GUID using the GUI interface.  This doesn't make much sense but it appears to so.  The use of the SGUID bit is the correct way.  You will have to do this using the terminal (CLI).  Are you doing this on a test share without too many files?  Do we need to do this recursively over many subdirectories of files?

---

### Post by Morbius1 on 2013-05-23
> **mbnoimi said:**
> Thanks, this works for SAMBA :)
I'm still missing it. I want to inherit the parent folder permissions and owner too... Any suggest?
Unless you use something like bindfs you cannot inherit ownership since the setuid bit on a directory has no meaning in Linux - only in BSD.

Through a combination of umask and the setgid bit you can cause new child files and folders to inherit the group ID and group permissions of the parent. 

The only problem with setgid in this topic and something that still baffles me is that the parent folder whose permissions you want to inherit always starts off the same way:

Owner =          mbnoimi

Owner permissions = read / write / execute
Group permissions = none
Other permissions = none
In octal mode these are permissions of 700. Why do you want all child files and folders to have permissions of 700?

You want just the opposite to happen. Maybe if I restate bab1's posts a different way it will help:

** Change ownership of the parent folder to include a new group ( I'm going to use plugdev since it already exists ):
```
sudo chown mbnoimi:plugdev /parent-folder
```
** Change permissions to 770 instead of 700 and add the setgid bit to the parent folder:
```
sudo chmod 2770 /parent-folder
```
** Add all the users you want to access that folder to the plugdev group:
```
sudo gpasswd -a user-name plugdev
```
** Since you are using Kubuntu 12.10 the umask is already set at 002 so no change is required to that.

Any new file copied to or created in but not moved to the parent folder will have group = plugdev and permissions of 664. All members of the plugdev group will be able to read and write to that file.

---

### Post by bab1 on 2013-05-23
> **Morbius1 said:**
> Unless you use something like bindfs you cannot inherit ownership since the setuid bit on a directory has no meaning in Linux - only in BSD.

The suid bit has the same meaning in both Linux and BSD.  Namely: setuid and setgid is short for "*set user ID upon **execution***" and "*set group ID upon **execution***".   Inheritance is not an explicit function of the suid or sgid bit with UNIX or Linux.  Setting the primary group is the only method that I know of to explicitly set group inheritance.

---

### Post by Morbius1 on 2013-05-23
> The suid bit has the same meaning in both Linux and BSD.
At a file level we are in agreement but I was specifically talking about how setuid in BSD differs from Linux on directories. In BSD:
> (the setuid bit).
Executable files with this bit set will run with effective uid set to the uid of the file owner. 
[COLOR=#0000cd]*So far this is exactly the same as Linux.*[/COLOR]

Directories with this bit set will force all files and sub-directories created in them
to be owned by the directory owner and not by the uid of the creating process.
*[COLOR=#0000cd] In Linux the setuid bit on directories is ignored.[/COLOR]*
> Setting the primary group is the only method that I know of to explicitly set group inheritance.         
With the exception of bindfs we are in agreement which is why all I did was take your previous posts and rearrange the words a bit ;)

---

