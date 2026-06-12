---
title: "Simple php question"
date: 2012-04-21
forum: Programming Talk
---

### Post by Arachan on 2012-04-21
Hello,

If I use php to create a file with fwrite, what controls the permissions of that file? Also what permissions does php have when creating the file, eg can it create it in somewhere with restricted permissions?

I am very new to php and it'd be great if someone could clear this up for me.

Thanks,
arachan.

---

### Post by Ryan Dwyer on 2012-04-22
PHP is always running as a Unix user. The file it writes will be owned by that Unix user. In Ubuntu, under a standard Apache install, that user is www-data. If you're executing a PHP script from command line it will be running as you.

Files it creates will be owned by itself, readable and writeable by itself, and I think readable by group and other. You can try using PHP's chmod() function to remove read access to group and other after writing the file.

You could also try Googling "unix directory umasks". I don't know much about them, but I believe they set limitations or defaults for newly created files.

---

### Post by Bachstelze on 2012-04-22
> **Arachan said:**
> 
If I use php to create a file with fwrite, what controls the permissions of that file?

Actually the file is created when you call fopen(), not fwrite(). There is a mode parameter to fopen() that you can use to specify the permission of the file, within the limits of the umask for the directory where the file is created.

---

### Post by SeijiSensei on 2012-04-22
The simplest place to write work files with PHP under Apache if privacy doesn't matter is /tmp.  Files written to /tmp will be deleted if the system is rebooted, and they can be read by all users on the system.  If they are truly temporary files, you should probably delete them at the end of your script.  Give the files names that won't cause a collision like this:

```

<?php
$tempfile="/tmp/php_".time();
$fp=fopen($tempfile,"w+");
fwrite($fp,$stuff);
fclose($fp);
[...]
exec("rm -f $tempfile");
?>

```

If you need a place to write persistent, private files, you need to create a directory that is writable by the www-data user and group.  For maximum privacy use 700 permissions on the directory, and chmod() the file to 600 after running fclose().  

```

sudo mkdir /path/to/new/directory
sudo chown www-data.www-data /path/to/new/directory
sudo chmod 700 /path/to/new/directory

```

If you want to create files that you can read and modify, add yourself to the www-data group and use 770 and 660 permissions on the directory and files respectively rather than 700 and 600.  To add yourself to the group, edit (as root with sudo) the file /etc/group and add your username after the trailing colon in the line that begins "www-data".  Or use the GUI users and groups management tool in Ubuntu.

---

### Post by Bachstelze on 2012-04-22
> **SeijiSensei said:**
> and they can be read by all users on the system.

Not necessarily. If you create a file in /tmp and chmod it 600, it will only be readable by you.

---

### Post by SeijiSensei on 2012-04-22
Sorry, I wasn't thinking clearly.  You're right, of course.

Here's a modification to the code I wrote above that implements 600 protections on a file in /tmp:

```

<?php
$tempfile="/tmp/php_".time();
$fp=fopen($tempfile,"w+");
[color=blue]chmod($tempfile,600);[/color]
fwrite($fp,$stuff);
fclose($fp);
[...]
exec("rm -f $tempfile");
?>

```

---

