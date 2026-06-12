---
title: "basic chmod question"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by santiagorf on 2012-11-29
Hi all,
I was playing around with chmod and I found that even files are protected from being written, I can delete them.

In the following example, I create as a root a file named foo and remove all access permissions. However, I'm still able to delete it with a regular user.
  

```
user@user-AO532h ~/dr/N02 $ sudo touch foo
user@user-AO532h ~/dr/N02 $ sudo chmod 000 foo
user@user-AO532h ~/dr/N02 $ ls -l
total 12
---------- 1 root root  0 2012-11-28 23:30 foo
-rw-r--r-- 1 user user 3 2012-11-28 23:11 hh
-rw-r--r-- 1 user user 4 2012-11-28 23:00 hh1
-rw-r--r-- 1 root root  2 2012-11-28 23:15 hhh\
user@user-AO532h ~/dr/N02 $ whoami
user
user@user-AO532h ~/dr/N02 $ rm foo
rm: remove write-protected regular empty file `foo'? y
user@user-AO532h ~/dr/N02 $ ls -l
total 12
-rw-r--r-- 1 user user 3 2012-11-28 23:11 hh
-rw-r--r-- 1 user user 4 2012-11-28 23:00 hh1
-rw-r--r-- 1 root  root  2 2012-11-28 23:15 hhh\

```

Why am I able to delete it if I don't have any permission to this file?

---

### Post by JKyleOKC on 2012-11-29
> **santiagorf said:**
> Why am I able to delete it if I don't have any permission to this file?The permissions for a file apply only to the **content** of that file; the file itself is ruled by the permissions of the directory in which it resides. Even though you created the file as root, via sudo, you created it in your $HOME directory -- and you have write permission to the directory itself. Without it, you could not have created the file. However, removing an empty file from a directory actually involves just erasing the file's entry from the directory itself, and your write permission to the directory allowed you to do so.

It can be, as you've discovered, quite confusing. Just think of it as erasing the directory entry and it will make sense, though.

The full details are a bit more involved, since it's possible for a file to "reside" in multiple directories under different names and permissions. However that's not a "normal" situation and doesn't really matter a lot in the context of your question. If you want to dig deeper into this aspect, search for information about "hard links" starting with the manual page for "ln" -- but be prepared for some mind-boggling complications when you do so...

I hope this helps!

---

### Post by Vaphell on 2012-11-29
because you modify dir contents not file contents

---

### Post by santiagorf on 2012-11-29
Thanks for the prompt replies!!!
Is there any book you can recommend regarding this topic? 


> **Vaphell said:**
> because you modify dir contents not file contents

---

### Post by Pletched on 2012-11-29
> **Vaphell said:**
> because you modify dir contents not file contents

I'm officially confused. [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---

### Post by sisco311 on 2012-11-29
> **santiagorf said:**
> Thanks for the prompt replies!!!
Is there any book you can recommend regarding this topic?

Start here: [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by audiomick on 2012-11-29
> **Pletched said:**
> I'm officially confused. [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

Picture an unlocked garage, or a garage that you have the key to. In there are a heap of boxes that you don't have the key to. You can't look inside the boxes, but you can take them out and throw them away.

---

### Post by sisco311 on 2012-11-29
> **Pletched said:**
> I'm officially confused. [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

Directories (like nearly everything else) are _files_ too. They contain only a list of _files_ and their inode numbers. So, if you have write and execute permission for a directory you can delete any file from it.

---

### Post by deadflowr on 2012-11-29
> **Pletched said:**
> I'm officially confused. [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

It's not that confusing.
The owner of a folder/directory can create and delete the contents of that folder regardless of whether or not the owner owns the files contained within.
What the owner cannot do is manipulate the contents of the unowned file within their folder.
There are however ways to prevent this, such as resetting/changing the attributes of the file. 
If, for example, you  
```
sudo chattr +i filename
```
, you will set the file as immutable, meaning no one, not even root, can change or modify the contents of that file, not even delete it.

You can get more info by running man chmod, or man chattr in a terminal.

---

### Post by bab1 on 2012-11-29
> **deadflowr said:**
> It's not that confusing.
The owner of a folder/directory can create and delete the contents of that folder regardless of whether or not the owner owns the files contained within.
What the owner cannot do is manipulate the contents of the unowned file within their folder.
There are however ways to prevent this, such as resetting/changing the attributes of the file. 
If, for example, you  
```
sudo chattr +i filename
```
, you will set the file as immutable, meaning no one, not even root, can change or modify the contents of that file, not even delete it.

You can get more info by running man chmod, or man chattr in a terminal.

Not to confuse the OP even more, but you can also set the sticky bit to suppress the deletion of files as long as the user is NOT part of the files group ownership. More info [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") and  a quote from that page> "Currently its use is system dependant and it is mostly used to [COLOR="DarkSlateGray"]**suppress deletion of the files that belong to other users**[/COLOR] in the folder where you have "write" access to."

This is how the /tmp directory is set up.

---

### Post by Pletched on 2012-12-16
Thanks guys. I appreciate everbody telling me it's not that difficult. :D

---

