---
title: "could not move any files into the new mounted folder in Ubuntu"
date: 2015-03-31
forum: New to Ubuntu
---

### Post by houmingc on 2015-03-31
Did GParted
There is 2 device
1) /dev/sda -secondary
2) /dev/sdb -primary

mount point in GParted is /hdd and /media/SecondDrive
I am able to mkdir in terminal but not inside GUI. 
I could not move any files into the new mounted folder. Why?

 :mad:

---

### Post by yancek on 2015-03-31
Generally on Linux systems such as Ubuntu, an ordinary user has no write permissions outside his/her own /home/user directory.  You can use sudo mkdir and enter your user password  when prompted to created a directory elsewhere on the system.  You can also do gksu nautilus and open a file manager with root/admin privileges.  If you are not using nautilus you will need to use whatever file manager you use.

Linux was designed from the start as a multi-user system which is one of the main reasons for this.  When logged in as root using sudo, you can also change the owner:group for the mount point as well as permissions.  I would expect to see numbers after the /dev; /dev/sda1, /dev/sdb2, rather than just sda or sdb.

---

### Post by Bashing-om on 2015-03-31
houmingc; Hello ;

OK,
> 
I am able to mkdir in terminal but not inside GUI. 
I could not move any files into the new mounted folder. Why?

I bet what we have here is a permissions issue. When you created the directory, you did so with 'sudo' . That made 'root' the owner of the directory, "you" do not have access to "root's" directory.
Now what you need to do is change the ownersip of the directory from 'root' to "you".
That is done with the 'chown' command.
```

man chown

```

If additional assistance is required, provide to us the method you are using to mount the target, the path to the target and the output of an attempt to list files in that directory.
From this we can format the explicit command to change that ownership to "you" .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

