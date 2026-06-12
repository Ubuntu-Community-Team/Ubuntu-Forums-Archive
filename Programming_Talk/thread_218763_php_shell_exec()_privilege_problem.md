---
title: "php shell_exec() privilege problem"
date: 2006-07-19
forum: Programming Talk
---

### Post by oldmanstan on 2006-07-19
ok, i think this is a problem with privileges. i need to be able to create a zip file on the server using php. i am trying to do it like this:
```
shell_exec('zip -r /home/glesica/www/thefile.zip /home/glesica/www/somefiles/');
```
it works just fine if i run it manually on the server using ssh, but when i run it from a web browser it just doesn't do anything. no errors or anything, just nothin, this is what makes me suspect permissions.

is there any way around this problem? am i doing something wrong? thanks!

---

### Post by hagen00 on 2006-07-19
The problem is that when you're doing it with ssh, you're logged in as a different user to the one that apache is using. 

The apache user (www-data usually) prob does not have the permissions to execute the command. Easiest test would be to su www-data (or whatever user apache is running as) to see if the command works. If not, then you know it's a permission problem. You could then just chmod or chown the /home/glesica/www/somefiles folder to give it the right permissions.

---

### Post by oldmanstan on 2006-07-19
EDIT: never mind, it works, thank you!

---

### Post by scxtt on 2006-07-19
the www-data user doesn't have much privilege - doubtful it can write to **/home/glesica** - try writing to /tmp just to see if the zip is created ... w/ the way you've got it, every folder up to "compressed" would have to be writable by "other" (i.e. www-data) ...

---

### Post by oldmanstan on 2006-07-19
ok, new question, it seems now that any directory php creates belongs to "nobody", i read about this someplace but i cant seem to find where, is there anything i can do about it? or just live with it? the problem is that i can't delete files it seems if they belong to "nobody" which is obviously a bad thing

---

### Post by ifokkema on 2006-07-20
> **oldmanstan said:**
> ok, new question, it seems now that any directory php creates belongs to "nobody", i read about this someplace but i cant seem to find where, is there anything i can do about it? or just live with it? the problem is that i can't delete files it seems if they belong to "nobody" which is obviously a bad thing
The files/directories created by PHP will be owned by the user your webserver runs under. If you want to change that, you'll need to change the server configuration. However, you could try and make the directories' group owner set to your group, and make the files writable for your group. That should solve your problem.

---

### Post by oldmanstan on 2006-07-20
yeah, it's a joke, the thing won't let me do anything to the files php created, piece o' crap

i'm just getting a virtual host so i can set php up myself

apparently this is a common problem (googled it), i dont understand why web hosts haven't tried to solve it

---

### Post by fluffington on 2006-07-20
> **oldmanstan said:**
> apparently this is a common problem (googled it), i dont understand why web hosts haven't tried to solve it

My host ([DreamHost](http://www.dreamhost.com/r.cgi?117623)) runs PHP as the owner of the file, so there's no difference permissions-wise between me doing something over SSH and my script doing the same thing.

---

### Post by ifokkema on 2006-07-21
> **oldmanstan said:**
> yeah, it's a joke, the thing won't let me do anything to the files php created, piece o' crap
Do you mean you want the files created by PHP owned by you? That would require the webserver to run as your user... Are you sure you want to do that? It's not very secure, you know...

Debian based distros, like Ubuntu, run the webserver as 'www-data'. You can add yourself to the www-data group, allowing you to work with the files created by PHP.

[QUOTE=fluffington]My host (DreamHost) runs PHP as the owner of the file[/QUOTE]
The owner of what file?

---

### Post by fluffington on 2006-07-21
> **ifokkema said:**
> The owner of what file?

The owner of the PHP file. If I were to, say, create test.php with user and group fluffington, it would execute as user and group fluffington, not www-data or whatever Apache usually runs as.

---

### Post by scxtt on 2006-07-21
you can easily set the user/group that apache runs as, just add/edit the following in /etc/apache2/apache2.conf:```
User www-data
Group www-data
```but i would **NOT** change it to run as a "normal" user ... i would just add yourself to the www-data group (tho i'm not sure if there's ---rw---- capabilities by default for that group) ... and really, how hard is it to sudo in-order to do things w/ www-data owned files?

---

### Post by ifokkema on 2006-07-22
> **fluffington said:**
> The owner of the PHP file. If I were to, say, create test.php with user and group fluffington, it would execute as user and group fluffington, not www-data or whatever Apache usually runs as.
Interesting... never heard of this configuration before. I've just done some Googling, is this the Apache suPHP module?

---

### Post by fluffington on 2006-07-22
> **ifokkema said:**
> Interesting... never heard of this configuration before. I've just done some Googling, is this the Apache suPHP module?
I've never set it up like that myself (DreamHost was the first place I saw it, and they don't let you mess with the Apache config files), so your guess is as good as mine.

---

### Post by anthro398 on 2006-07-23
I've had a terrible time with PHP permissions myself.  Installing and PHP applications like gallery2 always generate a lot of files and directories owned by apache. When I want to uninstall those applications I'm always left with a bunch of junk I don't have permission to delete.  Very annoying since I don't have sudo access.  The following PHP script solves this by making the directory you specify world-writable so that you can edit or delete the files and directories within.  I realize that was not the specific problem of the parent poster, but I thought someone might find this as useful as I have.

[PHP]<font size=+2>
Gallery Cleanup Script
</font>
<p>
Because Gallery runs as part of the webserver, any files it creates
are owned by the webserver process.  If you want to modify those
files yourself, you need to get the webserver to change the permissions
on them so that you have access.  That's what this script is for.
Simply enter the path to your albums directory below and this script
will make every file in that path (that it can access) writable
by everybody.  Then, you can do whatever you want to the files.
</font>

<p>

Path (on your filesystem) to a file or directory to fix?
<br>
<font size=-1>(examples: /home/~you/public_html/albums, /usr/www/htdocs/albums)</font>
<br>
<form>
<input name=dir>
<input type=submit value="Go!">
</form>

<?

if ($dir) {
        echo "<hr>";
        fix($dir);
}

function fix($obj) {
        if (is_dir($obj)) {
                status("Directory: ", $obj);
                if ($fd = opendir($obj)) {
                        while (($child = readdir($fd)) != false) {
                                if (!strcmp($child, ".")) {
                                        continue;
                                }

                                if (!strcmp($child, "..")) {
                                        continue;
                                }

                                $fullpath = "$obj/$child";
                                fix($fullpath);
                        }
                        chmod($obj, 0777);
                } else {
                        error("Error reading dir", $obj);
                }
        } else if (is_file($obj)) {
                print "File: <b>$obj</b><br>";
                chmod($obj, 0666);
        }
}

function status($msg, $obj) {
        print "$msg: <b>$obj</b><br>";
}

function error($msg, $obj) {
        print "<font color=red>$msg: <b>$obj</b></font><br>";
}

?>

[/PHP]

---

### Post by oldmanstan on 2006-07-24
> **scxtt said:**
> and really, how hard is it to sudo in-order to do things w/ www-data owned files?

it is very hard (impossible) to do that with my host, thanks ;)

---

### Post by LordHunter317 on 2006-07-24
Except for the part where that's stupidly dangerous, sure.

***Don't make things world writeable in response to a permissions problem.***

If you're running a personal server and you want access to files created by PHP, either make the directory where it's creating files owned by your group and setgid, or add yourself to the www-data group.

If you're using a hosting provider and it's not already setup correctly for you, they're incompetent and probably a huge security risk.  Cancel now and get a new provider.  I'm not remotely joking.

---

