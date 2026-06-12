---
title: "ls command"
date: 2016-01-03
forum: New to Ubuntu
---

### Post by krishna19 on 2016-01-03
Hello All,

I am a newbie to Linux and this is my first post here.

I am trying to learn Linux basics.

When I issue the command 'ls -l' I can see the files and folders and the permissions with that too. It also shows values 2,1. I am wondering what those values are?

krishna@ubuntu:~/Desktop$ ls -l
total 12
drwxrwxr-x _**2**_ krishna krishna 4096 Jan  3 11:43 Krishna
-rw-rw-r-- _**1**_ krishna krishna   56 Jan  3 12:15 mytext
drwxrwxr-x _**2**_ krishna krishna 4096 Jan  3 13:07 Test
krishna@ubuntu:~/Desktop$

Any help would be appreciated.

Krish

---

### Post by Dennis N on 2016-01-03
You can find an explanation of the output of ls -l here:

[http://unix.stackexchange.com/questions/103114/what-do-the-fields-in-ls-al-output-mean](http://unix.stackexchange.com/questions/103114/what-do-the-fields-in-ls-al-output-mean)

---

### Post by krishna19 on 2016-01-03
Hi Dennis,

Thanks for the reply!

I got a fair understanding now.

But still I have a confusion. Why there is executable permission for a folder?

Krish

---

### Post by brian-mccumber on 2016-01-03
> 
**[FONT=arial]Permission Types[/FONT]**

Each file or directory has three basic permission types:

[LIST]
[*]read - The Read permission refers to a user's capability to read the contents of the file.
[*]write - The Write permissions refer to a user's capability to write or modify a file or directory.
[*]execute - The Execute permission affects a user's capability to execute a file or view the contents of a directory.
[/LIST]

Quoted from this link - [https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions)

The execute permission means that without it running a script or a .desktop launcher for a program would not be possible. It also means that without it the user wouldn't even be able to get into the directory to run anything anyway.

---

### Post by Dennis N on 2016-01-03
Hi Krish;

If a folder is executable for your user, then you can open it (with cd). If your user also has read permission, then you can also list the files inside!

---

### Post by malspa on 2016-01-03
> **krishna19 said:**
> When I issue the command 'ls -l' I can see the files and folders and the permissions with that too. It also shows values 2,1. I am wondering what those values are?

The following may explain why you're seeing the value 1 for files and the value 2 for directories:

> Do you ever wonder what is this small number between the file permissions and the owner in the output of ls’s long listing format (its value is usually “1&#8243; for files, or “2&#8243; for directories)? This number is actually the link-count of the file, when referring to a file, or the number of contained directory entries, when referring to a directory (including the . and .. entries).

From: [http://www.giannistsakiris.com/2011/04/15/counting-and-listing-hard-links-on-linux/](http://www.giannistsakiris.com/2011/04/15/counting-and-listing-hard-links-on-linux/)

---

### Post by dave205 on 2016-01-03
> **malspa said:**
> The following may explain why you're seeing the value 1 for files and the value 2 for directories:



From: [http://www.giannistsakiris.com/2011/04/15/counting-and-listing-hard-links-on-linux/](http://www.giannistsakiris.com/2011/04/15/counting-and-listing-hard-links-on-linux/)


AWESOME explanation and kudos for you on not a giving a "rtfm" response.  Yes this is a simple question but we were all new once.  too many forget that. :KS

---

