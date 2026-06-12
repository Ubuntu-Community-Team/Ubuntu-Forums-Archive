---
title: "restricting users from viewing the partitions..."
date: 2012-09-26
forum: New to Ubuntu
---

### Post by visitnag on 2012-09-26
Hi,

I have created a /usr2 partion in my ubuntu 10.10. At the time of installation i have created a user mike and later one more user nelson. These both users can access the /usr2 partition without any restrictions. But, they are unable to write or delete thru GUI. How can I restrict the users not to access the /usr2 partition? I am working through user mike and keep my personal files in /usr2. Please help me.


Thank you,

---

### Post by bab1 on 2012-09-26
> **visitnag said:**
> Hi,

I have created a /usr2 partion in my ubuntu 10.10. At the time of installation i have created a user mike and later one more user nelson. These both users can access the /usr2 partition without any restrictions. But, they are unable to write or delete thru GUI. How can I restrict the users not to access the /usr2 partition? I am working through user mike and keep my personal files in /usr2. Please help me.


Thank you,

Why did you even create /usr2?  The directory /usr is for Unix System Resources (usr).  Although you certainly can use /usr2 there is no real reason to do so.  Typically each user has a directory under /home (i.e. /home/mike or /home/nelson.  These only need to have the permissions of each home directory changed to 700 to keep others out.

Did I miss something here?  Is there some reason that you want to use /usr2 for your users home directories?

---

### Post by visitnag on 2012-09-27
when i have created /usr2 I wanted this partition to be used for all (50GB)...but later I wanted to restrict it as there is enough space in /home to other users. I have changed permission to 700. Now I am facing the problem to open myself. It is giving warning msg as "You do not have the permissions necessary to view the contents of "usr2"" through GUI. How can I see the contents through GUI? I can see the files through sudo ls -ltr /usr2 command.

Problem 2: 

I have used the command chmod -R 700 /usr2, and when I am unable to open again I have executed chmod -R 777 /usr2 command. Now what happend I could open the files in /usr2 but not directories. The /usr2  is showing all the contents as files only (the folder Icon is missing). The type of directory is showing as  "Microsoft Help Attribute Definition File (application/octet-stream)". HOw to recover my stuff?

---

### Post by bab1 on 2012-09-27
> **visitnag said:**
> when i have created /usr2 I wanted this partition to be used for all (50GB)...but later I wanted to restrict it as there is enough space in /home to other users. I have changed permission to 700. Now I am facing the problem to open myself. It is giving warning msg as "You do not have the permissions necessary to view the contents of "usr2"" through GUI. How can I see the contents through GUI? I can see the files through sudo ls -ltr /usr2 command.

The GUI is running with you as the user.  You need to set the permissions of the directory /usr2 to be owned by you.  When you use **sudo** you are running the **ls** command as root (admin).

What are the permissions of /usr2?  Post the CLI output of```
ls -ld /usr2
```

Is the /usr2 a mount point for a separate partition?  You mention "*there is enough space in /home*".  Is the /home on a separate partition?

---

### Post by bab1 on 2012-09-27
> **visitnag said:**
> 
Problem 2: 

I have used the command chmod -R 700 /usr2, and when I am unable to open again I have executed chmod -R 777 /usr2 command. Now what happend I could open the files in /usr2 but not directories. The /usr2  is showing all the contents as files only (the folder Icon is missing). The type of directory is showing as  "Microsoft Help Attribute Definition File (application/octet-stream)". HOw to recover my stuff?

How is Ubuntu installed?  WUBI maybe?  If this is an NTFS partition then you can't use chmod.  NTFS does not accommodate EXT file system commands.

---

### Post by visitnag on 2012-09-27
When I have installed ubunut 10.10. I have created following,

/
/home  20gb   ext3
/usr2  50gb   ext3
/boot
/var
swap

the ls -ld /usr2 shows:

drwxrwxrwx 4 root root 4096 2012-09-15 15:07 /usr2

when I have used the ls -ld command the /usr2 is appearing in green color.

inside /usr2 i have one dir called movies. sample output 
ls -ltr /usr2/movies/

d????????? ? ? ? ?                ? Braveheart (1995)

is there any problem with the "?" signs? I want my stuff back pleeeeeeeease!!

---

### Post by bab1 on 2012-09-27
> **visitnag said:**
> When I have installed ubunut 10.10. I have created following,

/
/home  20gb   ext3
/usr2  50gb   ext3
/boot
/var
swap

the ls -ld /usr2 shows:

drwxrwxrwx 4 root root 4096 2012-09-15 15:07 /usr2

when I have used the ls -ld command the /usr2 is appearing in green color.

inside /usr2 i have one dir called movies. sample output 
ls -ltr /usr2/movies/

d????????? ? ? ? ?                ? Braveheart (1995)

is there any problem with the "?" signs? I want my stuff back pleeeeeeeease!!

Post the output of```
df -h
```...post the output of```
ls -l /usr2/movies
```

---

### Post by sandyd on 2012-09-27
```

#set owner to mike
sudo chown -R mike:mike /usr2
#change perms to allow r,w,x for only the owner
chmod -R rwx------ /usr2

```

---

