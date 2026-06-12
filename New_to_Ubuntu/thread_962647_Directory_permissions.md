---
title: "Directory permissions"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by randysparks on 2008-10-29
Please read through this entire post before making a reply -- it's a little complicated :)

Let's say a directory called "test" has the following ownerships/permissions:

drwxrw-rw- john john

I thought this means that any other user on the system is able to write/rename/delete files in the directory (assuming the individual files have the correct permissions), and get a file listing, but not switch into it because the execute permission for others isn't set. 

But it seems other users can't create or modify files in the directory, even though write permissions are set. They can list the files, however, which makes sense because read permissions are set. 

The only way other users can write or modify files is if the execute permission is set. If you don't believe me, try it. I've tried it under Ubuntu 8.10 and 8.04. 

Am I going crazy here?

---

### Post by Titan8990 on 2008-10-29
Does not sound right but I have not tested it.


Booting Ubuntu on my laptop now to test.

---

### Post by earthpigg on 2008-10-29
can other users modify, etc, as root?

```
sudo nautilus
```

---

### Post by randysparks on 2008-10-29
> **earthpigg said:**
> can other users modify, etc, as root?

```
sudo nautilus
```

Yes, but surely that doesn't prove anything? Root can always do anything, anywhere.

---

### Post by Titan8990 on 2008-10-29
Tested and confirmed. I now just lost all my understanding of "read" and "write" permissions....


Edit: Also, to OP, I am sure that if it is like this in Ubuntu it is like that on all EXT3 filesystems not dependent on the OS.

---

### Post by randysparks on 2008-10-29
> **Titan8990 said:**
> Tested and confirmed. I now just lost all my understanding of "read" and "write" permissions....

I'd like to hear what others have to say, but I'm reasonably sure that Ubuntu is doing things different from other Linuxes here. I hesitate to say but this might even be a bug.

EDIT: Nope, same thing happens on my OS X system.

---

### Post by bhadotia on 2008-10-29
Heck, I have always avoided reading the chmod man page. ..
And now I see this ...

So may be I will have to read it anyway.

Sorry can't be of any help now .. But will return soon (I hope).:)

---

### Post by Titan8990 on 2008-10-29
> I'd like to hear what others have to say, but I'm reasonably sure that Ubuntu is doing things different from other Linuxes here. I hesitate to say but this might even be a bug.

I would check my Slackware laptop but I lost my AC adapter...

---

### Post by Titan8990 on 2008-10-29
> Heck, I have always avoided reading the chmod man page. ..
And now I see this ...

I just read the chmod man page and the info page that it told me to read at the bottom of the man page (they were both identical, yet formatted differently).

There is no in-depth description over what each permission does.

---

### Post by randysparks on 2008-10-29
> **Titan8990 said:**
> I just read the chmod man page and the info page that it told me to read at the bottom of the man page (they were both identical, yet formatted differently).

There is no in-depth description over what each permission does.

I found this over at a BSD documentation page ([http://www.freebsd.org/doc/en/books/handbook/permissions.html):](http://www.freebsd.org/doc/en/books/handbook/permissions.html):)

> Directories are also treated as files. They have read, write, and execute permissions. The executable bit for a directory has a slightly different meaning than that of files. When a directory is marked executable, it means it can be traversed into, that is, it is possible to “cd” (change directory) into it. This also means that within the directory it is possible to access files whose names are known (subject, of course, to the permissions on the files themselves).

In particular, in order to perform a directory listing, read permission must be set on the directory, whilst to delete a file that one knows the name of, it is necessary to have write and execute permissions to the directory containing the file.

This might a rare example of Unix/Linux not being entirely logical, although I'm sure the reasoning behind it will be very sound.

---

### Post by Titan8990 on 2008-10-29
Really, I have never understood why Linux is still using EXT3 when there are better filesystems out there such as XFS.

---

### Post by bhadotia on 2008-10-29
I got it!

Its pretty  simple actually. The permissions simply mean that everyone can read and write the directory and this applies to the files in the directory if the premissions are applied recursively (the -R option in chmod).> (subject, of course, to the permissions on the files themselves)

This seems confusing at first - doesn't it?:)

---

### Post by randysparks on 2008-10-29
> **bhadotia said:**
> I got it!

Its pretty  simple actually. The permissions simply mean that everyone can read and write the directory and this applies to the files in the directory if the premissions are applied recursively (the -R option in chmod).

This seems confusing at first - doesn't it?:)

I'm not sure I understand you. 

In my tests, even if the files were set to be read and write for ugo, it was still impossible to modify them (or write new files to the directory) unless the execute permission was set for the directory. 

Maybe I misunderstand you. Can you try explaining it again? :)

---

### Post by drakeman007 on 2008-10-29
> **randysparks said:**
> I'm not sure I understand you. 

In my tests, even if the files were set to be read and write for ugo, it was still impossible to modify them (or write new files to the directory) unless the execute permission was set for the directory. 

Maybe I misunderstand you. Can you try explaining it again? :)

Im with you, i think that he try to say that if you make a chmod with the -r option you changes the permissions to the folders and all the files or folders under the principal hehehe
thats what i understand! 

Regards

---

### Post by bhadotia on 2008-10-29
Actually really got it this time!:)

The first time was just a theory and this time its backed with experimentation.:popcorn:

I created a directory in my Desktop dir as root (called what):
```
 ls -l
total 4
drwxrw-rw- 2 root root 4096 2008-10-30 00:07 what
```

Now look:
```
$ Please enter your command (no.=3) here : cd what/
bash: cd: what/: Permission denied
User                                     : abhishek
Host                                     : freeze
Working Directory                        : ~/Desktop
Time                                     : 12:13 AM
$ Please enter your command (no.=4) here : mkdir what/me
mkdir: cannot create directory `what/me': Permission denied
User                                     : abhishek
Host                                     : freeze
Working Directory                        : ~/Desktop
Time                                     : 12:14 AM
$ Please enter your command (no.=5) here : sudo mkdir what/root
User                                     : abhishek
Host                                     : freeze
Working Directory                        : ~/Desktop
Time                                     : 12:14 AM
$ Please enter your command (no.=6) here : nano what/root/root
User                                     : abhishek
Host                                     : freeze
Working Directory                        : ~/Desktop
Time                                     : 12:15 AM
$ Please enter your command (no.=7) here : sudo nano what/root/root
User                                     : abhishek
Host                                     : freeze
Working Directory                        : ~/Desktop
Time                                     : 12:15 AM
$ Please enter your command (no.=8) here : less what/root/root
what/root/root: Permission denied
User                                     : abhishek
Host                                     : freeze
Working Directory                        : ~/Desktop
Time                                     : 12:15 AM
$ Please enter your command (no.=9) here : sudo ls what/root 
root
User                                     : abhishek
Host                                     : freeze
Working Directory                        : ~/Desktop
Time                                     : 12:16 AM
$ Please enter your command (no.=10) here : sudo cat what/root/root
I write as root!

```

For the users to be able to write in a directory they should first be able to change to it to able to modify the files that belong to them - if they not able to do that than what's the point in the write permissions. On the other hand if the directory would have been empty all the users could delete it because they had the write permissions to it. 
Watch:
```
$ Please enter your command (no.=13) here : sudo ls -l what/root 
total 4
-rw-r--r-- 1 root root 17 2008-10-30 00:15 root
User                                     : abhishek
Host                                     : freeze
Working Directory                        : ~/Desktop
Time                                     : 12:21 AM
$ Please enter your command (no.=14) here : sudo rm what/root/root
User                                     : abhishek
Host                                     : freeze
Working Directory                        : ~/Desktop
Time                                     : 12:22 AM
$ Please enter your command (no.=16) here : sudo rmdir what/root
User                                     : abhishek
Host                                     : freeze
Working Directory                        : ~/Desktop
Time                                     : 12:22 AM
$ Please enter your command (no.=17) here : ls -l what/
total 0
User                                     : abhishek
Host                                     : freeze
Working Directory                        : ~/Desktop
Time                                     : 12:22 AM
$ Please enter your command (no.=18) here : rmdir what/
```
```
 ls -l
total 0

```


All this is only my understanding and should not at all be taken authoritatively. But I guess its right to some extent:popcorn:

EDIT: I advice you to read through the commands above carefully coz I'm not at al in a mood of explaining ;)
> Please read through this entire post before making a reply -- it's a little complicated 

---

### Post by bodhi.zazen on 2008-10-29
> **randysparks said:**
> In my tests, even if the files were set to be read and write for ugo, it was still impossible to modify them (or write new files to the directory) unless the execute permission was set for the directory. 

That is it exactly. Permissions for directories and files are different.

See [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Or to be exact :

[http://www.zzee.com/solutions/linux-permissions.shtml#zzee_link_9_1077830297](http://www.zzee.com/solutions/linux-permissions.shtml#zzee_link_9_1077830297)

(that second link has a nice "Table")

---

### Post by randysparks on 2008-10-29
I think this is starting to make sense the more I research. 

The execute permission is about ACCESS to a directory. If the execute permission for a directory isn't set then you can't access files within it, regardless of what the read or write permissions for the directory are. 

Read and write permissions are separate from execute permissions, and for a reason.

Say that the permissions on a directory mean that your user account can read it, and execute it, but not write to it (r-x). 

You'll still be able to modify files in the directory, provided you have write permissions for the individual files. You just won't be able to delete the file, or create new ones within that directory. 

Permissions of rw- are illogical, but they have to exist for situations like the above to be possible. This might be why GNOME terminal colors the directory dark green. Maybe it's indicating an impossible situation.

---

### Post by randysparks on 2008-10-29
> **bodhi.zazen said:**
> That is it exactly. Permissions for directories and files are different.

See [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Or to be exact :

[http://www.zzee.com/solutions/linux-permissions.shtml#zzee_link_9_1077830297](http://www.zzee.com/solutions/linux-permissions.shtml#zzee_link_9_1077830297)

(that second link has a nice "Table")

Thanks but I think you misunderstand because that doesn't answer the question. Did you read the first post in this thread?

---

### Post by bodhi.zazen on 2008-10-29
> **randysparks said:**
> Thanks but I think you misunderstand because that doesn't answer the question. Did you read the first post in this thread?

:lolflag:

Yes I did. It seems there is misunderstanding as to what the read, write, and execute permissions mean on a directory. You allow access to a directory be setting the execute permission on the directory.

---

### Post by bhadotia on 2008-10-29
> **randysparks said:**
> Thanks but I think you misunderstand because that doesn't answer the question. Did you read the first post in this thread?

So are you satisfied? Has your problem a started looking solvable (if not solved yet- Come on man give a clear cut answer:))

---

### Post by randysparks on 2008-10-29
> **bodhi.zazen said:**
> :lolflag:

Yes I did. It seems there is misunderstanding as to what the read, write, and execute permissions mean on a directory. You allow access to a directory be setting the execute permission on the directory.

Yes, that's right :) 

I used to think that the execute permission was about who can switch into a directory. A surprising amount of documentation says this too, and it's inaccurate.

What the execute permission is actually about, as you say, is who can ACCESS a directory. That includes switching to it, but it also includes reading/writing files there. 

In other words, if the execute permission isn't set, then it's access denied: you won't be able to do anything inside the directory, regardless of what the read/write permissions for the directory are set as.

EDIT: To understand all this it helps if you realize that a directory is simply a file containing a listing of the directory contents, plus technical information (remember too that, in Linux, everything is a file). If the execute permission on the file isn't set, then you can't access or change the info in that directory, and that includes accessing files inside the directory.

---

