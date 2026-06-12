---
title: "chmodding follies"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Dev'olution on 2008-04-25
How do I chmod a folder and all sub-folders and files at one time?

I mean, i know how to chmod 777 /var/www... but i need to chmod all the files below that on my webserver... also i need to make it so that every future file uploaded is 777.

any ideas guys? :confused:

---

### Post by Herman on 2008-04-25
:) How about,
```
sudo chmod -R 777 /pathtofile/filename
```[File Ownership and Permissions]("http://users.bigpond.net.au/hermanzone/p10.htm#File_Ownership_and_Permissions") - fix read, write, execute and ownership issues.

Regards, Herman :)

---

### Post by yaztromo on 2008-04-25
Use the -R option for recursive chmod

e.g. chmod -R 755 /var/www

Read the manual for chmod by typing "man chmod" too.

---

### Post by aaronhall555 on 2008-04-25
> **WestAussieUbu said:**
> How do I chmod a folder and all sub-folders and files at one time?

I mean, i know how to chmod 777 /var/www... but i need to chmod all the files below that on my webserver... also i need to make it so that every future file uploaded is 777.

any ideas guys? :confused:

To change the permissions of files and directories recursively you use the "-R" option.

```

chmod -R 777 /var/www/...

```
or
```

chmod -R a+rwx /var/www/...

```

Make sure you want to give everyone access to read, write, and execute the files and directories that you specify.

I also recommend that you read the manual page or information page about the chmod command. The commands for the manual and information pages are:
```

man chmod

```
and
```

info chmod

```

---

