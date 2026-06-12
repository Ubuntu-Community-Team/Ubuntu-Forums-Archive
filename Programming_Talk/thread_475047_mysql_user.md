---
title: "mysql user?"
date: 2007-06-15
forum: Programming Talk
---

### Post by adza on 2007-06-15
Hi there, when i want to get my webscript to update files on the server, the web user needs write access to it's directory. My question is how do i determine what the 'web' user is? I don't want to chmod 777 on the directory as that gives everyone access, how can i just add the write access to that web user (and what is the web user)?

---

### Post by kidders on 2007-06-16
Hi there,

To find out who your web server is running as, get it to run **whoami** in a shell. How to do that varies, depending on what (if any) scripting engines you have available, but a simple PHP version would be...```
<?php
echo "<p>Hi there, I'm ".`whoami`.".</p>";
?>
```Another way to find out what's what is to take a look through the various (Ubuntu has quite a lot of them!) Apache config files for "User" and "Group" directives ... assuming, of course, you're even using Apache. For instance...```
$ grep -i '^\s*user' /etc/apache2/*
/etc/apache2/apache2.conf:User www-data
```As you mentioned, **chmod 777**-ing things is silly, but depending on how security-conscious you are, granting a script write access to the directory it itself is stored in can be equally dangerous. You see, it is always possible that, either through a bug in your web server, or a glitch in your own code, a script could be manipulated into modifying itself, which would be catastrophic.

My best suggestion would be to do this...[LIST]
[*]Where possible, have your web server write to a location outside the web root. For instance, if your server lives at /var/www/htdocs, grant write access to /var/www/tmp, for example. That way, it would be impossible for someone to manipulate a script into creating a file with malicious content, and call it by visiting its URL (ie because it wouldn't have one).
[*]Where that's not possible, use a subdirectory below the script that'll be doing the writing. So, if your script lives at /var/www/htdocs/admin/writestuff.php, grant write access to /var/www/htdocs/admin/tmp, for example. Note however that this often equates to **chmod 777**, since there is not always a way to stop a server serving content that it has permission to access, if you know what I mean.[/LIST]To actually grant write permission, you can...[LIST]
[*]Make the web server itself the owner of a file or directory & **chmod** it accordingly.
[*]Set a file/directory's group to the web server's primary group & **chmod** it accordingly.
[*]Add your web server to someone else's group, allowing it access to everything that group can access.
[*]Etc...[/LIST]... It all depends on the subtleties and specifics of the effect you're looking for.


I hope that helps.

Question: What's the connection to MySQL? :confused:

---

