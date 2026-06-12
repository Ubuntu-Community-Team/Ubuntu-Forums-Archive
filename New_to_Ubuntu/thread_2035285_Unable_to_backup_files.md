---
title: "Unable to backup files"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by peterson43 on 2012-07-30
I use Deja Dup for backups of my home directory. I have it set to automatically backup every day, and every day I get an error message saying that two of the files failed to back up. The message says
> Could not back up the following files. Please make sure you are able to open them.
One of these files is a place where I hide some password information. Sometime after my initial backup of my home drive I realized that file was readable by all users so I changed it to only be accessible by root. After I made this change I started seeing this file on the list of files that doesn't back up correctly. 

The other files that don't backup correctly are in the ```
HOME/.config/nautilus-actions
``` directory. When I check the permissions of this folder, I am listed as the owner but with the permissions are set to "no list, create/delete, access." Is this the standard/normal permissions setting for this folder or should it be something different. I don't ever remember changing the permissions for this folder. 

Also, one thing I tried to do to keep getting the error messages from Deja Dup was to add the .config/nautilus-actions folder to the list of folders to NOT backup in the Deja Dup settings. For some reason this doesn't seem to work since I still get the same error message every time.

---

### Post by NikTh on 2012-07-30
Hi , 

it seems you are affected by this bug [https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/1000543](https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/1000543) . 

So the solution for now might be  to change the permissions with chmod command . 

```
chmod -R u+r .config/nautilus-actions
```

Thanks

---

### Post by peterson43 on 2012-08-01
Your suggestion to change the file permissions for the .config/nautilus-actions folder seems to have worked. I didn't get the error message today when the backup took place. Also, to avoid getting the error message for the file with my passwords I created a new folder just for this file and then instructed Deja Dup to ignore backing up this folder. Seems to have worked.

---

