---
title: "Writing files in PHP and security"
date: 2010-08-10
forum: Programming Talk
---

### Post by rigao on 2010-08-10
I need a web-based application to write a file with a specific extension (.pgn).

I came across the php instruction 

```

$pgnFile = "torneig.pgn";
$file = fopen($pgnFile, 'w') or die("can't open file");
fwrite($file,$headers2);

```

the problem comes with write permission. It seems that the only way for the program to write this file, is to upload a dummy file with this name earlier and give it permission for everyone to write it (chmod a+w torneig.pgn i think).

I'm concerned about the security of the application with this change in permission.

Is it possible for someone to take advantage of this? If so, is there any way I can make it more secure?

The only thing I need to do is to change a file with .pgn extension so people can download it. If there is a more secure way to do it, I will be very happy to know.

Thanks.

---

### Post by Bachstelze on 2010-08-10
Use mode='w+' instead of mode='w'.

[http://fr2.php.net/manual/en/function.fopen.php](http://fr2.php.net/manual/en/function.fopen.php)

---

### Post by rigao on 2010-08-10
It won't work until I change the permission (wich is what worries me).

This is the error code

```
Warning: fopen(gamesDB.pgn) [function.fopen]: failed to open stream: Permission denied in /home/a3460021/public_html/baixarPGN.php on line 71
```

---

### Post by Bachstelze on 2010-08-10
Obviously, if you want to write to a file, PHP must have permission to write to it. One way around it is suPHP, but it's probably overkill for you. What's wrong with chown :www-data && chmod 775?

---

### Post by rigao on 2010-08-10
> **Bachstelze said:**
> Obviously, if you want to write to a file, PHP must have permission to write to it. One way around it is suPHP, but it's probably overkill for you. What's wrong with chown :www-data && chmod 775?

Hmmm, the first problem is that I don't know what your instructions do :p

If they are equivalent to what I've done (I've gone to the file, right-click it and change permission to everyone to write), my concern is about security, as I don't know how far the everyone has permission to write reach. I mean, if somebody outside the server is able to modify it, it can easily put a virus in it.

As I plan to release it as a patch to a program which is available to download, I'm concerned about the security leaks I can open.

---

### Post by Bachstelze on 2010-08-10
> **rigao said:**
> 
If they are equivalent to what I've done (I've gone to the file, right-click it and change permission to everyone to write)

No. cmod 775 means owner has write permissions, group has write permission, everyone else has read-only permission. chown :www-data defines 'group' to be Apache. Basically, it only gives Apache (and no one else) write permission.

---

### Post by rigao on 2010-08-10
Is it possible to do it with php alone? I mean, I can manually upload a file and change its permission through console (say with your instructions) but then everybody which installs the application will need to do it again. This is kind of a mess.

The ideal would be that php creates its own file, change its permission and then writes the necessary data. Is it possible?

---

### Post by Bachstelze on 2010-08-10
> **rigao said:**
> Is it possible to do it with php alone? I mean, I can manually upload a file and change its permission through console (say with your instructions) but then everybody which installs the application will need to do it again. This is kind of a mess.

The ideal would be that php creates its own file, change its permission and then writes the necessary data. Is it possible?

Depends how you upload it. Only the owner (ot root) can change permissions for a file. If you upload it with FTP for example, the file will be owned by you, so PHP can't change the permissions.

But look at suPHP. [http://www.suphp.org/Home.html](http://www.suphp.org/Home.html) If you really need to do that, you can use it.

---

### Post by rigao on 2010-08-10
The problem is just for php to create it in the first place. Then obviously php would own that file and changes would be allowed. How to create a file with php is what I do not know, this is why I always provide it (via ftp) with the file, but then I need to change its permission. If I was able to create it with php in the first place, then it won't be any need to upload it in the first place.

I will take a look at this suPHP, to see if gets the job done. But yes, at first glance it seems an overkill.

---

### Post by Bachstelze on 2010-08-10
> **rigao said:**
> The problem is just for php to create it in the first place. Then obviously php would own that file and changes would be allowed. How to create a file with php is what I do not know

What I said above, use 'w+' instead of 'w'. However, Apache must still have write permission to the directory where the file is to be created.

---

### Post by rigao on 2010-08-10
> **Bachstelze said:**
> What I said above, use 'w+' instead of 'w'. However, Apache must still have write permission to the directory where the file is to be created.

Using w+ it won't let me create any file :-(

Any reason why?

I'm hosting my web in 000webhost.com (maybe it is a problem with that hosting, dunno).

---

### Post by Bachstelze on 2010-08-10
> **rigao said:**
> Using w+ it won't let me create any file :-(

Any reason why?

Does Apache have write permissions to the directory?

---

### Post by howlingmadhowie on 2010-08-10
in php:
```

<?php

$fp=fopen("myfile.txt", "x");

?>

```
will create a file and fail, if the file already exists.

you can find out more here: [http://www.php.net/manual/en/function.fopen.php](http://www.php.net/manual/en/function.fopen.php)

---

### Post by rigao on 2010-08-10
> **Bachstelze said:**
> Does Apache have write permissions to the directory?

How do I tell?

I normally used filezilla to upload content. Now I'm using a web-application to upload files. I have no direct access to a console AFAIK.

---

### Post by Bachstelze on 2010-08-10
Your FTP client should have a "permissions" panel of sorts when you right-click on a file. However, you probably won't be able to change ownership, so that means you will have no choice but make the files world-writable. suPHP is probably not an option either.

---

### Post by rigao on 2010-08-10
Is it possible to do it with filezilla?

You are write about the options in my file-uploader. I can only choose the categories owner, group and public, but I cannot change the ownership AFAIK.

---

### Post by Bachstelze on 2010-08-10
> **rigao said:**
> Is it possible to do it with filezilla?

You are write about the options in my file-uploader. I can only choose the categories owner, group and public, but I cannot change the ownership AFAIK.

Yeah, I guess you don't really have a choice there.

---

### Post by Hellkeepa on 2010-08-12
HELLo!

Put the files in a folder that's below the web root, so that they can't be reached via a browser. Should help a bit on the security, at least.

Also, I recommend looking into the [file_put_contents ()](http://www.php.net/file_put_contents) function.

Happy codin'!

---

### Post by lisati on 2010-08-12
If you're using PHP to create a file, would writing it to the "/tmp" directory first and then copying/moving it to its ultimate destination be an option?

---

### Post by Hellkeepa on 2010-08-12
HELLo!

PHP would still need permissions to write to the folder. So the end effect is the same, only with one more step.

Happy codin'!

---

### Post by lisati on 2010-08-12
> **Hellkeepa said:**
> HELLo!

PHP would still need permissions to write to the folder. So the end effect is the same, only with one more step.

Happy codin'!

The last time I checked with a simple script on my own machine, it did have permissions set to write to /TMP :D

EDIT: The main advantage of writing a temporary file first is that if something goes wrong with the initial creation of the file, you haven't accidentally over-written an older version.

---

### Post by Hellkeepa on 2010-08-12
HELLo!

Ah, sorry for not specifying. As you said, you have permissions to write to /tmp, but PHP still needs write permissions on the folder to which the file is to be moved. That's why "same result, one additional step".

Though, the way I usually solve this issue on such hosts, is to temporarily make the parent folder "world writable", and then have PHP create the folder. Change the perms back, and you're set. ;-)

Happy codin'!

---

