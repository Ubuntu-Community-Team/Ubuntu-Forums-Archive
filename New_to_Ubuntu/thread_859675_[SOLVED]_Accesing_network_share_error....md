---
title: "[SOLVED] Accesing network share error..."
date: 2008-07-14
forum: New to Ubuntu
---

### Post by mingle on 2008-07-14
Hi,

(Anyone have ANY suggestions?)

I 'm having trouble when trying to access my Windows share.

I have Samba installed and I connect to the windows share using the "Connect to Server" option under the "Places" menu.

Now, I can read and write to the share WITHOUT any problems using the file manager. There is also an icon for the share on the desktop and everything seems fine.

However, when I try and add a bookmark for the share and then access the bookmark I get the following error:

Could not open location 'smb://hp-d530s/data/'
The specified location is invalid

I also get similar errors when (from within the file manager) I double click on a picture-file, or MP3 on the Windows share. It's as if the local apps don't have authorisation to access the files on the share.

Any comments or help would be greatly appreciated!

Cheers,

Mike.

---

### Post by mingle on 2008-07-15
Hi,

Sorry to bump this again, but I really need to find an answer to this and my searching and googling haven't helped.

If not, I'm going have to stick with windows (again!)

Cheers,

Mike.

---

### Post by iaculallad on 2008-07-15
> **mingle said:**
> Hi,

Sorry to bump this again, but I really need to find an answer to this and my searching and googling haven't helped.

If not, I'm going have to stick with windows (again!)

Cheers,

Mike.

On your terminal:

```
sudo apt-get install smbfs
```

Then try to use the procedure I posted in this [thread]("http://ubuntuforums.org/showthread.php?t=847837").

---

### Post by mingle on 2008-07-15
Hi iaculallad,

Thanks for being the first to help me out!

Is there a simple way to automount the shares when I boot up?

Cheers,

Mike.

---

### Post by mingle on 2008-07-15
Hi,

After much searching I appear to have found a solution to my issues with mounting Windows shares.

Check out the following VERY helpful thread:

[http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba](http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba)

Cheers,

Mike.

---

