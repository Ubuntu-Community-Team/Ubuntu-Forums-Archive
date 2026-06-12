---
title: "PHP Session cookies -- where are they stored?"
date: 2008-02-02
forum: Programming Talk
---

### Post by Sarteck on 2008-02-02
Hello, all,

I've got a question just out of morbid curiosity rather than anything going wrong with my scripts.

You see, I've got a site on a shared host, but use my Kubuntu box here at home for testing.  After researching about sessions a while back, I learned that it's generally a **Good Idea** (TM) to set your *session.save_path* to something other than the world-readable **/tmp**, particularly if it would be a **Bad Thing** (TM) for other users on the shared host to be able to read your files.

So, I've got a include file with a global variable called at the beginning of each script.  The variables in the 'ini_set' key of the array are all set through the **ini_set()** function in a *foreach* loop.  Here's an edited example:```

$TheGlobal['ini_set']['upload_tmp_dir'] = '/home/sarteck/thesite/temp/';
$TheGlobal['ini_set']['upload_max_filesize'] = '500000000';
$TheGlobal['ini_set']['post_max_size'] = '500000001';
$TheGlobal['ini_set']['memory_limit'] = '500000002';
$TheGlobal['ini_set']['session.save_path'] = '/home/sarteck/thesite/sessions';
$TheGlobal['ini_set']['session.cookie_path'] = '/home/sarteck/thesite/sessions/cookies';
$TheGlobal['ini_set']['session.gc_maxlifetime'] = '86400'; // One Day max lifetime
$TheGlobal['ini_set']['session.use_cookies'] = '1';
$TheGlobal['ini_set']['session.use_only_cookies'] = '1';
$TheGlobal['ini_set']['session.cookie_lifetime'] = '0';
foreach ($TheGlobal['ini_set'] as $ini => $set) {ini_set($ini, $set);}
```

Using this setup, everything works fine and dandy, like I want it to.  Session variables are saved for a sufficient amount of time, and things are seemingly secure.  Everything works...

...but, I can't seem to find the actual cookie file anywhere!  I've looked in **/home/sarteck/thesite/sessions**, **/home/sarteck/thesite/sessions/cookies**, in the "Master value" of **/var/lib/php5** from my regular ini file, and even in **/tmp**, but can't find where the session cookie is stored on the server!

Granted, I don't really need to know--like I said, everything works fine.  But it's just bugging me...  I can find the cookie stored client-side (in the /home/sarteck/.mozilla/RANDDIR/sessionstore.js files, surprisingly, and not the cookies.txt file like I thought it would be), but not the server-side cookie.  Anyone know where I should be looking?

---

### Post by ThinkBuntu on 2008-02-02
I imagine that it would be tough to find this data on your server for privacy reasons. You may want to see how apache and mod_php work with the data.

---

### Post by smartalecks on 2008-02-02
Ah, the magik of sessions :D

[IMG]http://img517.imageshack.us/img517/6348/screenshotsessionsfilebpw2.png[/IMG]

```

<?php
ini_set('session.save_path', '/home/alecks/sessions');
session_start();
?>

```

is just the test script I made

---

### Post by Sarteck on 2008-02-02
@ThinkBuntu: Nah, the reason I want to -change- it on the shared server is for security reasons--I don't want my session cookies in a world-readable /tmp directory.  If I left it at it's default, other users on the shared host could potentially access my site's users' sessions and hijack them (a remote possibility, but still a possibility).

Also, I like a little structure in dealing with my data, and storing each subdomain's sessions in their respective folders (for example, *foo.sarteck.com* would store it's sessions in */home/sarteck/foo/sessions*, *bar.sarteck.com* would store it's session variables in */home/sarteck/bar/sessions*, etc.) is ideal for me, as I can better control the security -and- keep the data sorted (and appease my curiosity all at once.  :)



@smartalecks:  That is pretty much what I have in my code (except I am setting a bunch of ini directives through an array with a foreach loop).



**Solution?**
In playing around with it for the past few hours, I finally broke down and set the save_path via the **.htaccess** file.  And... It worked?  Yes, yes it did.  It -seems- that the cookie was getting stored at **/var/lib/php5** (though I'm not exactly sure why it did not show up there earlier when I looked).  My **phpinfo()**, when called after my set of "ini_set" declarations, looked thusly:```
Directive	Local Value	Master Value
session.name	PHPSESSID	PHPSESSID
session.referer_check	no value	no value
session.save_handler	files	files
session.save_path	/home/sarteck/fpj/sessions	/var/lib/php5
session.serialize_handler	php	php
session.use_cookies	On	On
session.use_only_cookies	On	Off
```So, obviously, it was indeed getting the session.save_path I passed via the "ini_set" command, as you can see under the "Local" column.

For some reason unbeknownst to me (but hopefully beknownst to you, the gurus, who can tell me what's going on), PHP basically said a big "F-U" to that Local directive, and just proceeded to happily use the Master value.  Using the .htaccess file, I -forced- PHP to use the value I wanted... But I don't understand why the .htaccess would have precedence, and why it wouldn't work with ini_set in the first place.

Anyone with ideas is welcome to share them.





Side-note, on the shared server, the use of the .htaccess file for PHP value manipulation is unnecessary (though I use it for other things).  So again, it's no huge deal--just my curiosity.

---

