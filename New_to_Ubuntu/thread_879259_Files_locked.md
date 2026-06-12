---
title: "Files locked"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by richg on 2008-08-03
I am using Ubuntu 8.04. Today I was working with some JPGs and O.O. files and some how ended up putting a lock icon next to at least eighty percent of my personal files. When I check Properties, I find the locked files are read only. While in Properties I can change each one to read and write. The lock goes away. Any idea how this could have happened? Is there a simple fix to change all the files to read and write in one or two steps? Thanks.
I am not one to play with the operating system. I just run applications. Apparently Ubuntu still has some gotchas.

Rich


Rich

---

### Post by spiderbatdad on 2008-08-03
there are a number of commands that will work to change the permissions on a number of files at once. You can chomd with the -R flag or chmod /directory/* and so on. What is more important, perhaps, is a more clear understanding of linux file permissions and what they mean. In other words, do you simply +w as your chmod option, or are you more careful and use something like chmod 600?

[http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)

That is one link from a google search. There are many others. It is important to understand how the permissions are assigned and set for owner/group/others.

---

### Post by richg on 2008-08-03
Thanks but that is quite complicated. I have been using Linux for four years, starting with Linspire, then Freespire and now Ubuntu 8.04 for about five months. I use the Ubuntu defaults, a user name and password. Nothing fancy. I have never messed with any kind of permissions. Ubuntu 8.04 is giving me trouble with some of my files but never to this degree. Today I was using Gimp. Kolour Paint and Open Office. Again, nothing fancy. I must have done something simple to lock most of my files. There must be a simple unlock procedure without having to use command line. I stopped using command line with W3.1. I am only interested in User permissions as no one else uses the files. I can change the User permissions in Properties. But that is a lot of work, one file at a time. There must be a simple way to unlock the files since I did nothing that I can think of to lock the files.

Maybe someone else can help me. Thanks.

Rich

I just realized in File manager my Home folder has a lock on it and my External hard drive for backups is also locked.
Since I use removable hard drives, I pulled the Ubuntu hard drive and inserted the Freespire 2.0.8 hard drive and all my files on the external hard drive are unlocked.
If no solution, I will go back to Freespire and wait for Ubuntu 8.10. I cannot have Ubuntu messing with my files. Since all my files in the external hard drive are built using Freespire with Root access and some that were built with W98SE, I suspect Ubuntu does not like that.

Rich

---

### Post by perlluver on 2008-08-03
> **richg said:**
> Thanks but that is quite complicated. I have been using Linux for four years, starting with Linspire, then Freespire and now Ubuntu 8.04 for about five months. I use the Ubuntu defaults, a user name and password. Nothing fancy. I have never messed with any kind of permissions. Ubuntu 8.04 is giving me trouble with some of my files but never to this degree. Today I was using Gimp. Kolour Paint and Open Office. Again, nothing fancy. I must have done something simple to lock most of my files. There must be a simple unlock procedure without having to use command line. I stopped using command line with W3.1. I am only interested in User permissions as no one else uses the files. I can change the User permissions in Properties. But that is a lot of work, one file at a time. There must be a simple way to unlock the files since I did nothing that I can think of to lock the files.

Maybe someone else can help me. Thanks.

Rich

You can run the mouse over all of them at once, right click select properties, and then change all of them at once.  Had to do it with my music collection.

---

### Post by spiderbatdad on 2008-08-03
Yes. Or, open the directory containing the files you want to change permissions on, go to the Edit menu and choose "Select All," then go to the File menu and choose "Properties." In the properties dialog, go to permissions, and select the permissions you want from the drop down menus.

---

### Post by richg on 2008-08-03
> **spiderbatdad said:**
> Yes. Or, open the directory containing the files you want to change permissions on, go to the Edit menu and choose "Select All," then go to the File menu and choose "Properties." In the properties dialog, go to permissions, and select the permissions you want from the drop down menus.

Thanks, that works but I have about 2 GB of files, directories in directories and it will still take some time but if I muddle along I might be able to do more in a swipe. It definitely is a issue because I was running as Root in Freespire and Ubuntu must be trying to protect me.
I wonder if this has happened to others? I will have to search the archives.
Apparently Ubuntu wants you to start new files using the OS and not importing the files.
Thanks again.

Rich

---

### Post by richg on 2008-08-03
> **spiderbatdad said:**
> Yes. Or, open the directory containing the files you want to change permissions on, go to the Edit menu and choose "Select All," then go to the File menu and choose "Properties." In the properties dialog, go to permissions, and select the permissions you want from the drop down menus.

Thanks, that helps also.

Rich

---

### Post by spiderbatdad on 2008-08-03
> **richg said:**
> Thanks, that works but I have about 2 GB of files, directories in directories and it will still take some time but if I muddle along I might be able to do more in a swipe. It definitely is a issue because I was running as Root in Freespire and Ubuntu must be trying to protect me.
I wonder if this has happened to others? I will have to search the archives.
Apparently Ubuntu wants you to start new files using the OS and not importing the files.
Thanks again.

Rich

Kind of why I encouraged use of cli. A very powerful tool for file manipulation. For example if I wanted to change the permissions to read/write for me only of everything in my /home/username/Documents directory, including sub-directories and files in there, one command can do it all:```
chmod 600 -R /home/spiderbatdad/Documents/*
```

Running the command ls -l while in a directory shows me the owner and permissions. So for Documents, I open a terminal:```
cd Documents
ls -l
```

output:
```
:~/Documents$ ls -l
total 16
-rw------- 1 hedwig hedwig    3 2008-08-03 20:48 file1
-rw------- 1 hedwig hedwig    0 2008-08-03 20:45 file1~
-rw------- 1 hedwig hedwig    4 2008-08-03 20:48 file2
-rw------- 1 hedwig hedwig    0 2008-08-03 20:45 file2~
drwxrwxrwx 2 root   root      4096 2008-08-03 21:54 new1
-rw------- 1 hedwig hedwig    5 2008-07-20 20:17 test.txt
-rw------- 1 hedwig hedwig    0 2008-07-20 20:16 test.txt~

```Here I see a problem. The directory new1 is owned by root and has read write execute permissions for all groups and users. It is a directory as denoted by the d at the beginning of the line. The others are files. So I run the command:
```
sudo chown hedwig:hedwig -R new1
```This changes the ownership of the root owned directory in my home folder, and everything in new1
```
cd
```to get back to /home/hedwig.
Then:```
chmod 600 -R /home/hedwig/Documents/*
```

Now the output is:
```
:~/Documents$ ls -l
total 16
-rw------- 1 hedwig hedwig    3 2008-08-03 20:48 file1
-rw------- 1 hedwig hedwig    0 2008-08-03 20:45 file1~
-rw------- 1 hedwig hedwig    4 2008-08-03 20:48 file2
-rw------- 1 hedwig hedwig    0 2008-08-03 20:45 file2~
drw------- 2 hedwig hedwig 4096 2008-08-03 21:54 new1
-rw------- 1 hedwig hedwig    5 2008-07-20 20:17 test.txt
-rw------- 1 hedwig hedwig    0 2008-07-20 20:16 test.txt~

```Including everything inside new1.

---

### Post by richg on 2008-08-03
Another thing. On the desktop is my external Maxtor hard drive. There is a small lock icon aside of the Maxtor icon. I selected the Icon and then clicked Properties. I get a message that properties cannot be determined.
That lock showed up today after I worked with some JPGs and O.O. documents this afternoon.

Rich

---

### Post by richg on 2008-08-03
> **spiderbatdad said:**
> Kind of why I encouraged use of cli. A very powerful tool for file manipulation. For example if I wanted to change the permissions to read/write for me only of everything in my /home/username/Documents directory, including sub-directories and files in there, one command can do it all:```
chmod 600 -R /home/spiderbatdad/Documents/*
```

Thanks but that is what I call running an OS. I do not do that. Been in trouble doing that. I will get all the files unlocked some day. The mystery is how did it happen?
I can see my user name has read/write but the Groups which is Root is read only. I tried to change Group to read/write but Ubuntu would not let me.

Rich

---

### Post by spiderbatdad on 2008-08-03
to change the permission of anything owned by root is going to require the cli, even if it is simply to launch your graphical file browser with administrative permissions:```
gksu nautilus
```will open your file browser, but as root. You would then be able to change the group permissions for root...graphically, of that folder in your home directory.

---

### Post by richg on 2008-08-03
> **spiderbatdad said:**
> to change the permission of anything owned by root is going to require the cli, even if it is simply to launch your graphical file browser with administrative permissions:```
gksu nautilus
```will open your file browser, but as root. You would then be able to change the group permissions for root...graphically, of that folder in your home directory.

Thanks but I will go the long route. At least I know what I am doing.
Hopefully Ubuntu is aware of this kind of issue and 8.10 will not do this to Root files. Most of the time Ubuntu is better than Freespire.
Cheers

Rich

---

### Post by spiderbatdad on 2008-08-03
> **richg said:**
> Thanks but I will go the long route. At least I know what I am doing.
Hopefully Ubuntu is aware of this kind of issue and 8.10 will not do this to Root files. Most of the time Ubuntu is better than Freespire.
Cheers

Rich

Ubuntu 8.10 is not going to allow users to manipulate root files without the use of cli to launch nautilus as root, nor allow any other type of regular-user to make root file changes. That is the whole point of sudo and gksudo...to protect us from ourselves. We are required to acknowledge that we are about to make a change to a file that is not owned by the logged in user. And we are required to have an administrative password.
This is not an issue. It is a protection. If you import files from other linux systems, they will have permissions.  Depending on how the were saved or packaged, the permissions sometimes require changing. It isn't rocket science to learn how to use the cli for basic file operations. It's part of using linux. And if all you have to do is type: gksu nautilus. That's pretty simple.

---

### Post by richg on 2008-08-03
Do you mean to open the command line and just type gksu nautilus
and hit Enter? Will that do all my PC files and external hard drive files is one swoop?
I am paranoid because some time ago someone gave me what I thought were complete instructions. Messed up the OS. I was then told, I thought you knew to do this first and then something else. In other words, assumption.

Rich

---

### Post by spiderbatdad on 2008-08-03
> **richg said:**
> Do you mean to open the command line and just type gksu nautilus
and hit Enter? Will that do all my PC files and external hard drive files is one swoop?
I am paranoid because some time ago someone gave me what I thought were complete instructions. Messed up the OS. I was then told, I thought you knew to do this first and then something else. In other words, assumption.

Rich

Opening a terminal and simply typing that command, launches your file browser as system administrator. You are right to be cautious and even worried. But if you carefully navigate to file system>>home>>yourusername>>somefile_in_your_home_directory you would be able to graphically edit the permissions of a file owned by root, the same way you can edit the permissions in user space with the file browser, on files you own.

I'm not totally sure what happened earlier. Because if you owned the file, but group was set to root, you should have been able to make the change with the user properties>>permissions tool.

---

### Post by richg on 2008-08-04
Ok, I opened a terminal window and typed gksu nautilus, hit enter and here is what I got.

lexon@lexon-desktop:~$ gksu nautilus
Initializing nautilus-share extension

** (nautilus:5842): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///

(nautilus:5842): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:5842): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
lexon@lexon-desktop:~$ 

When I powered up the PC this morning, all the files I had unlocked manually last night are locked again.

Rich

---

### Post by richg on 2008-08-04
Hi All
Thanks for trying but I can live with this. If I have to, I will unlock the file first if there is any modifying that has to be done. 

Rich

---

### Post by v1ncent on 2008-08-11
I'm having the same problem right now... I don't know how it happens, first of all, my user is in the root group, but i never have problems.

This is what i did:
I opened nautilus whit sudo, create a symlink of /etc, copy that symlink to my home folder and change the permissions of THAT '/etc link' from the root group to my group, then i apply changes to enclosed files.

Then nautilus (normal one, without sudo) icons change, like if the theme disappear... And i realize i couldn't access to my home folder anymore, 'Access was denied' it said.

I tried changing permissions from nautilus (opened whit sudo), but IT DIDN'T WORK, how can it be? if you change the permissions and apply to all enclosed files, it must do exactly that, but it didn't work...
What the hell means this permission: drwxrwxrwx?

I'm using Ubuntu 7.10

---

### Post by v1ncent on 2008-08-11
Please help, now my user have all kind of problems.
What makes me confuse is that i don't know how it happend, and worst, evwn if i make changes, it doesn't apply.
Doing this by heand, 1 by 1, doesn't change 'drwxrwxrwx' permission.

---

