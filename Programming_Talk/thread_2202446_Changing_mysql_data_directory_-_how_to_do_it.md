---
title: "Changing mysql data directory - how to do it?"
date: 2014-01-29
forum: Programming Talk
---

### Post by daner2 on 2014-01-29
I am trying to change the mysql database directory. I followed the top response here ([http://stackoverflow.com/questions/1795176/how-to-change-mysql-data-directory](http://stackoverflow.com/questions/1795176/how-to-change-mysql-data-directory)), including the comment made by mak. But I am still getting "Job Failed to Start."

I want to change the datadir to /media/sf_data/mysql

I am absolutely new to linux, but I have got to get this up and running. I am familiar with mysql on windows though.

(Does it matter if you end a path without a slash or with one? I followed the examples exactly but they were inconsistent on that point.)

Here is what I do exactly:```


sudo /etc/init.d/mysql stop
```
```
sudo cp -R -p /var/lib/mysql /media/sf_data/mysql

```
```
sudo gedit /etc/mysql/my.cnf

```
I change the datadir line to read:
```
datadir        = /media/sf_data/mysql
```

save, close.

```
sudo gedit /etc/apparmor.d/usr.sbin.mysqld
```

I change the following
```
/var/lib/mysql/ r,
/var/lib/mysql/** rwk,
```
to

```
/media/sf_data/mysql/ r,
/media/sf_data/mysql/** rwk,
```

save, close


```
sudo /etc/init.d/apparmor reload
sudo /etc/init.d/mysql restart
```

The above actions do not work. Same error.

So I also tried mak's comment.

```
sudo gedit /etc/apparmor.d/tunables/alias
```

add a new line: ```
alias /var/lib/mysql/ -> /media/sf_data/mysql/,
```

```
sudo /etc/init.d/apparmor restart
```

```
sudo service mysql start
```

Which also does not work.

The error is always "Job Failed to Start."

Any thoughts?

I should say that I do not mind removing apparmor if that's what it takes. This environment does not need to be secure for my purposes. I actually tried to do it already with various tutorials but got the same result. My feeling is that I am missing something basic. I am running mysql 5.5.35-0ubuntu0.12.04.2 (Ubuntu). 

Thanks for any help here. Please keep in mind that I am very new to linux :)

---

### Post by spjackson on 2014-01-29
Welcome to the forums.

I suggest you check ownership and permissions of /media/sf_data/mysql . What sort of filesystem is it? (e.g. ext3, VFAT, NTFS). Check /var/log/mysql* for more information about startup failure.

---

### Post by SeijiSensei on 2014-01-29
The data directory needs to be owned by user "mysql" and group "mysql".  Here are the permissions on the default /var/lib/mysql directory:

```
drwx------ 5 mysql         mysql         4096 Jan 28 07:37 mysql
```

The directory is owned by mysql:mysql and is readable only by that user.  "mysql" is the username that owns the MySQL server process, mysqld.

```

Seiji@GhostWorld::~$ ps axu | grep mysql | grep -v grep
mysql     1137  0.1  0.1 492540  2540 ?        Ssl  Jan28   1:50 /usr/sbin/mysqld

```
The first column gives the name of the user that owns the process.

So the fix is as follows:

```

cd /media
# make sure the mysql user can see directories below sf_data
sudo chmod a+x sf_data
cd sf_data
# make data accessible only to mysql user
sudo chmod 0700 mysql
cd mysql
sudo chmod ug+rw,o-rw *

```
That gives user/group mysql read and write privileges to the files in this directory and denies them to everyone else ("o"="other").  The lines beginning with "#" are optional comments and are included to be helpful.

---

### Post by daner2 on 2014-01-29
@SejiSensei: Going to try this now and report back, thanks for making it detailed for me. :)

@spjackson: File permissions are new to me. I consistently overlook them. Hopefully that is the case here. I am not sure how to find out my file system quickly, but when I installed ubuntu it told me it was going to create an ext4 drive (I think). I'll try to confirm.

---

### Post by daner2 on 2014-01-29
Got the same error, but it does seem to be a file permissions error, according to the mysql error log mentioned.

I've attached screenshots of the log.

I used your commands exactly Seiji, but received the same error. I performed them after performing the change alias addition and before the final mysql restart in the steps above.

With the df -T command, I found out my file system is ext4, but the data folder (a shared folder between the ubuntu vm and windows host) is of the type, "vboxsf"

Edit: sorry the images are so small, the forums appear to have resized them. The images show the log file from time of the first shutdown until the attempt to restart it.

---

### Post by spjackson on 2014-01-30
> **daner2 said:**
> @SejiSensei: Going to try this now and report back, thanks for making it detailed for me. :)

@spjackson: File permissions are new to me. I consistently overlook them. Hopefully that is the case here. I am not sure how to find out my file system quickly, but when I installed ubuntu it told me it was going to create an ext4 drive (I think). I'll try to confirm.
Er... yes, when you install Linux, it creates its own filesystem for its own purposes (ext4 in your case). However, if you dual boot with Windows and mount your Windows partition, then that part will be NTFS (probably). If you have an external disk (e.g. USB) then it will probably be NTFS or VFAT, unless you reformat it under Linux and then you won't be able to read it from Windows.

Why this matters is because different filesystem types have different concepts of ownership, permissions and other details which are tailored to the operating system that they are designed for. Using chown and chmod will do they right thing on a native Linux filesystem, but what they do on a non-native mounted filesystem is not necessarily what you want - they do the best they can.

The fact that it is mounted in /media suggested to me that it might not be a native filesystem, and you've now revealed that it is vboxsf, that you are running Ubuntu in a virtual machine on a Windows host. Therefore, to address the ownership issue, you don't need chown, you need instead to look at how you mount it. You will need to mount it with mysql as the owner. See [https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders) for some clues. You can find uid and gid for mysql as follows:
```

$ id mysql
uid=117(mysql) gid=124(mysql) groups=124(mysql)

```
If the share is mounted automatically during the boot process, you will need to edit /etc/fstab to achieve a similar effect.

---

### Post by daner2 on 2014-01-30
I'm sorry I didn't mention that to start off with. I was ignorant of its implications and so didn't realize it was a factor. But I am glad you were able to ask the right questions to find out.

Here is id mysql for me:
```
$ id mysql
uid=115(mysql) gid=125(mysql) groups=125(mysql)

```

I tried changing permissions by going to /media/ and right clicking on the sf_data folder to change them via the permissions tab, but it was greyed out. So I used the command "gksudo nautilus" to open the file manager as root to go there and change it, and this time the permissions tab wasn't greyed out but when I tried to change ownership from "root" to "mysql", the gui apparently would not allow this and immediately reset the owner to root (changing it via the drop down selection box was impossible). I also could not change the Group, which was set to "vboxfs." Or anything in the Other part of the dialog, either.

And you supposed right: the share is mounted automatically during the boot process. I guess I need to find a mount command to put in /etc/fstab that gives both my account and mysql privileges? If possible, I would just like to simply give everything privileges to the folder so I don't run into this problem again in different clothes.

---

