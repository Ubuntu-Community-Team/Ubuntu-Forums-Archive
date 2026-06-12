---
title: "External hard drives are all read only"
date: 2015-08-30
forum: New to Ubuntu
---

### Post by aquinas2 on 2015-08-30
Hi, I'm brand new to Ubuntu, I finally took the plunge after years of being frustrated with Windows and OSX, I love it, and have been able to figure a lot of the basic stuff out, however, for some reason all my external drives are read only and I can't back anything up to them. I saw a couple of other threads on this, but they seemed very specific to the op's drive. Any suggestions?

---

### Post by yancek on 2015-08-30
What is the filesystem type on your external drive partitions?  Generally, you would need root permissions to copy to another drive.  If you were able to write to the external drive partitions previously and now can't, you might need to run a filesystem check with the 'fsck' command.  More details needed.  If you are using a current Ubuntu, you should have access to external drives/partitions under the /media/user directory and can find the owner:group and permissions with the ls command.

Example:  ls -l /media/user/

Change user in the command above to your actual user name.

---

### Post by aquinas2 on 2015-08-30
Hey thanks for the quick reply yancek! Heres what is says when I run that command...
drwxrwxr-x 1 root root 14 Apr 21  2014 My Book
drwxrwxr-x 1   99   99 14 Apr  2  2014 Untitled

Its been 12 years since I've dealt with a terminal and the commands, etc. So to be honest, I'm not 100% sure what this means. Yeah, I know maybe a bit pathetic, but I think you learn fastest by just jumping right in.

---

### Post by yancek on 2015-08-30
You can get pretty much the same information by right-clicking on a directory or file and selecting Properties and then clicking on the tabs at the top of the new window.

The output shows these are both directories (the letter d at the far left of the line), that the owner and group have read (r), write (w) and execute (x) permissions and other have read and execute.  It also shows the owner as root for My Book and the owner:group for "Untitled" is user:group 99.  Don't know what/who that is?  What that means is you as a user do not have write permissions to "My Book" because the permissions for other are read and execute.  Since you are not root user or probably in the root group, you would need to get root permissions.  In Ubuntu that is done by using the command sudo to prefix and other command.  You would then be prompted for the primary user password.  The primary user is the one you created when you installed Ubuntu.  You can change that or add users to give them root permission although that generally is not necessary on a home computer.

I found the site below which discusses user:group 99:99 which I had never seen before if you are interested.  You should be able to change owner:group from briefly scanning the site.

 [http://unixjunkie.blogspot.co.uk/2007/03/user-99-unknown.html](http://unixjunkie.blogspot.co.uk/2007/03/user-99-unknown.html) 

To access the mount point for the My Book partition in a terminal, you would need to use escape character or put it in quotes as there is a space in the name.  Example below.

```
cd "/media/user/My Book/"
```

This doesn't apply if you are in a file manager.  To access the directory with root permissions, it is generally recommended you use gksudo,  gksudo nautilus should open the nautilus file manager if you have a default Ubuntu install.  If you don't have gksudo installed, you will be prompted to install it and will likely be given the specific command to enter.

Change the ownership with the chmod command.

sudo chown -R user:group"/media/user/My Book/"

You need to replace user:group above with your actual user name and group name.

---

