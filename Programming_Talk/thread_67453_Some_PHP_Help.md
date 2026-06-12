---
title: "Some PHP Help"
date: 2005-09-20
forum: Programming Talk
---

### Post by dk_pa on 2005-09-20
I am pretty new to PHP and am just trying to write a small bit of code that will check for a files exsistence, then if not found create a new folder and write the file in it.  The script will write the folder but doesn't write the file then.  Do these operations just have to be more broken up?  :? 

```

<?php

$user_name = $_POST['user_name'];
$user_email = $_POST['user_email'];
$notes = $_POST['notes'];
$workout_day = $_POST['workout_day'];
$feel = $_POST['feel'];


$filename = "work_outs/$user_name/$user_name.xls";
$file = fopen( $filename, "a+");
$info = "<tr><td>$user_name</td><td>$user_email</td><td>$workout_day</td><td>$feel</td></tr>";

if (file_exists($filename)) {
fwrite( $file, $info);
fclose( $file );
} else { mkdir("work_outs/$user_name");
	fwrite( $file, $info);
	fclose( $file );
}
?>

```

---

### Post by thumper on 2005-09-20
Now I don't know PHP but your logic seems a little flawed.

If the fopen fails (which it would if there was not a directory there), then you don't try to reopen the file once you have made the new directory.

Perhaps test for file exists before fopen?

Pseudo-code:```

if not file_exists:
    mkdir
open file
write data
close file
```

---

### Post by dk_pa on 2005-09-20
Okie dokie.  I'll try that out.  I'm new to programming all together so thanx for helping the noobie =)

---

### Post by ryneezy on 2005-09-20
Usually you can't write into a directory unless you have write permission. Try CHMOD 777 the directory before writing the file.

PHP has a CHMOD method so you can do it from the script.

---

### Post by LordHunter317 on 2005-09-20
[QUOTE=ryneezy]Usually you can't write into a directory unless you have write permission. Try CHMOD 777 the directory before writing the file.[/quote]**No!**.  Never ever do this, even for testing.

Assuming this runs on a webserver, then www-data will need write access to create directories, to whatever directory you want to create directories in.  Having it group-own (and using setgid) or own the directory is probably smart.  ACLs are another alternative.

Also, your script is horribly insecure.  Sanitize your input before using it to create a file.

Also, if the directory doesn't exist, $file won't be valid.  You must test for the directories existence before opening a handle.

---

### Post by thumper on 2005-09-20
[QUOTE=LordHunter317]Also, your script is horribly insecure.  Sanitize your input before using it to create a file.

Also, if the directory doesn't exist, $file won't be valid.  You must test for the directories existence before opening a handle.[/QUOTE]
He did say he was new to programming, so how about an example for "*Sanatize your input*".

Would give examples myself, but really don't know any PHP.

**dk_pa** what **LordHunter317** means by Sanatize is to confirm that the input you are getting matches what you are expecting.  The user might give you some invalid data that would cause your method calls to fail in ways you were not expecting.

If the file is always created when the directory is created, then an explicit directory check is not really needed, but does add a certain feel for completeness.  You do really want to check the file existance before opening the file handle.

---

### Post by dk_pa on 2005-09-20
Gotcha, Hunter. Makes sense now.  Just for clarification, I could write the file no prob.   Wasn't really worried about security either, just getting things to work at first.  Is something I will go back to tho =)  More than willing to listen to anyone on these things tho.  thanx

---

### Post by dk_pa on 2005-09-21
Thanx, Thumper.  I must have replied right when you did cause I missed your post.  Like I said, I was just trying to get the basic stuff to work before I moved on with the details.  Input checking and stuff would be next.  

Basically all I need is for a user to login.  Fill in their data then send it to a file.  If it's a new user, make a directory and then write the file.  Pretty simple.  I'll have more time to work on it tomorrow hopefully.

---

### Post by LordHunter317 on 2005-09-21
To be fair, the Sanitation you need to do isn't terribly complicated.  What you need to watch for is a username of some form that could be used to read something they shouldn't, or overwrite something they shouldn't, or create a directory they shouldn't.  Disallowing '.', among other things would make this rather difficult.

If this is your only app, any practical exploit could be hard.  However, if there's more to the application than just this one script, a vulnerability here could be used to create a file that compromises something else.

My apologies if I seemed alarmist, but I guess it wasn't clear to me this was test code and that you intended to do input validiation later.

---

### Post by dk_pa on 2005-09-21
Alarm away! I really don't mind and I appreciate the help.  I just want you guys to realize I am just trying to get things working first.  I don't mind wearing the noob hat =)  It's only been 3 days of this.  haha. :-P

---

