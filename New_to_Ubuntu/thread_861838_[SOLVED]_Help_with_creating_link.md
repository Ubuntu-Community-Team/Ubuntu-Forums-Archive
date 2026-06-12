---
title: "[SOLVED] Help with creating link"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by richiewrt on 2008-07-17
Ok, I have my a folder in my home directory that I want to share with my sister who has ftp access to my server, but when I try this:

ln /home/myname/directorytoshare
i get this:
hard link not allowed for directory

if I try this:
ln -s /home/myname/dirctorytoshare
it works, but when trying to browse it through a file browser, it says the link is broken.

so, how do I make it so she can see and use these files.

---

### Post by Rocket2DMn on 2008-07-17
Try the lndir command.

However, there is a problem.  Typically, your home directory should only have permissions for your username to access it.  You can set it to be shared, it just isn't recommended.

---

### Post by jordanmthomas on 2008-07-17
Does she have permission to view /home/myname/directorytoshare ?

Also, it's probably not the problem (as it should still work), but I like to put both paths when making link
```
ln -s /path/to/share /path/to/make/link/at
```

---

### Post by richiewrt on 2008-07-17
probably not, how do i give her permission for that folder?

also when trying the lndir command I got permission denied for everything in the directory, I assume these problems are related

---

### Post by richiewrt on 2008-07-17
Just thought of something, could this be a permissions problem with the ftp server? I have it set to default to a users home folder.

---

### Post by Rocket2DMn on 2008-07-17
It shouldn't be an FTP server problem, it just gets the permissions from the file system.  If you have the link setup correctly and you can use it, then it's a matter of setting permissions that allow other users to access it.  It can be dangerous to have other users writing to your home folder, so I would only give read and execute permissions at most if you are set on taking this approach.
It would be better to setup a shared directory elsewhere on the filesystem.

---

### Post by cariboo on 2008-07-17
If you are going to let your sister browse your home directory, why not let her use your username and password. Or better yet set her up as a user on your computer and create links to the directories you want her to browse, without letting her look at files you want to keep private.

Jim

---

### Post by bodhi.zazen on 2008-07-17
The "problem" is hard vs soft links.

Hard links can not be used for directories (as indicated in your error message) or across (between) partitions.

Here is a brief link:

[http://www.cyberciti.biz/tips/understanding-unixlinux-symbolic-soft-and-hard-links.html](http://www.cyberciti.biz/tips/understanding-unixlinux-symbolic-soft-and-hard-links.html)

---

### Post by richiewrt on 2008-07-17
ok, I chmod 666 the folder that I wanted to share, as I want anyone with access to my server to have access to that folder, that should allow anyone access to that folder right?

also, when I try to cd to the directory with my user, through the link in her home folder, I get a permission denied, when I try with her user I get "can't cd to directory"

when I tried the lndir I get permission denied on every subdirectory.

---

### Post by richiewrt on 2008-07-17
and I am not trying to let her browse my home directory, just a subdirectory that has a lot of files she would want in it.

---

### Post by Rocket2DMn on 2008-07-17
OK stop, please, before anything else breaks.  Let's take this approach:

You should not be changing permissions on your home folder, please reset the permissions to 755 on the /home/<username> directory.

Now, setup the link to the SUBFOLDER which probably has 755 permissions, 644 for files.  PLEASE DO NOT USE RECURSIVE CHMOD or you will screw stuff up.  You shouldn't have to set extra permissions on the files and folders in your home directory since they should default to what you want.  All you need to do is setup the link.

---

### Post by richiewrt on 2008-07-17
I didn't chmod my home directory, just the subfolder.

right now, I can now view the folder through /home/myname/dir2share and through /home/mysister/dir2share

but, when I ftp into the server with her username, the link is there but if you try and click on it, it says the link is broken.

---

### Post by Rocket2DMn on 2008-07-17
Is the FTP using a chroot?  Like, when you login, do you see the initial directory as / or as /home/username ?

---

### Post by richiewrt on 2008-07-17
when she logs in she is in the /home/username
the links shows up there, but says its broke if you click on it

---

### Post by bodhi.zazen on 2008-07-17
What ftp server are you using ? Some ftp servers do not allow following symbolic links ...

To test out your set up, log in on your server as your sister and see if you can navigate to your shares. I assume you can and if so the problem is with your ftp server / configuration.

---

### Post by richiewrt on 2008-07-17
I'm using proFTP. And she is set up to only have access to her /home folder.

---

### Post by bodhi.zazen on 2008-07-17
remove the symbolic link :

```
unlink /home/myname/directorytoshare
```Now mount the directory in your sisters home with mount --bind:

```
sudo mount --bind /home/myname/directorytoshare /home/your_sister/directorytoshare
```

If that works we can add a line to fstab

```
gksu gedit /etc/fstab
```

Add :

```
/home/myname/directorytoshare  /home/your_sister/directorytoshare  none  bind
```

---

### Post by richiewrt on 2008-07-17
Brilliant!!

Works perfect.

Now a question for my future knowlege, can you mount the same dir in more than one place?

---

### Post by bodhi.zazen on 2008-07-17
Well, that is exactly what mount --bind is, mounting a directory in more then one location.

---

