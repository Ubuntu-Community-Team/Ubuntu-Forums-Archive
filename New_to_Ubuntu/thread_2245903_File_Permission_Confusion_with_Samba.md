---
title: "File Permission Confusion with Samba"
date: 2014-09-26
forum: New to Ubuntu
---

### Post by AwaitingUserInput on 2014-09-26
I'm using a MATE desktop, but I don't think that matters.

I just got Samba up and running on a clean install. I told Samba to make my ~/Public directory readable and writeable by all users. For my home directory, I have the permissions so that only I can read/write, and I have to provide my password.

To test it, I grabbed my Android tablet and copied a bunch of files to ~/Public over the network.

Here is an example of ls -l

```
drwxr-xr-x 2 nobody nogroup   4096 Sep 26 23:01 ChromeSnapshots
-rwxr--r-- 1 nobody nogroup 531821 Sep 26 23:27 foo.pdf
```

"ChromeSnapshots" is apparently a folder that Chrome put in my tablet at some point.

```
~/Public$ ls -l ChromeSnapshots/
total 140
-rwxr--r-- 1 nobody nogroup 135418 Sep 26 23:01 receipt.pdf
```

So for everything, user is "nobody" and group is "nogroup." Remember that I did not need to log in or provide credentials to copy files into this directory.

If I do: rm foo.pdf, I get:
```
rm: remove write-protected regular file ‘foo.pdf’?
```

I say "yes" and the file is removed. How can this be when I do not own the file or have write access according to the ls -l command? I would have thought that I'd need "sudo" to delete it. How is the file "read only" yet, it still lets me delete it just by saying "yes?"

Also, if I do a rm -r on ChromeSnapshots:

```
$ rm -r ChromeSnapshots/
rm: descend into write-protected directory ‘ChromeSnapshots/’? y
rm: remove write-protected regular file ‘ChromeSnapshots/receipt.pdf’? y
rm: cannot remove ‘ChromeSnapshots/receipt.pdf’: Permission denied

```

I also got similar messages when trying to move / delete files from the GUI file manager.

So my questions:
1) Why are the files in the ~/Public/ChromeSnapshots directory treated differently than files in the ~/Public directory?
2) What sort of permission will tell me that a file is write-protected, but let me delete it anyways even without using Sudo or typing a password?

I'm somewhat familiar with permissions and ownerships and have often had to change owners or permissions when transferring files between systems. I've never seen anything like this before, though.

---

### Post by TheFu on 2014-09-27
The directory permissions controls which users can add , move or delete files inside it.
Samba doesn't care what the Linux permissions are. It runs as root and you've allowed the world to do stuff inside your HOME. I wouldn't do that. I would setup storage outside /home for everyone to read/write, assuming that was the desire. Honestly, that just freaks me out. I want authenticated users, period.

Having layers of samba shared folders is a bad idea, IMHO.  I won't have a samba share inside another samba share.

---

