---
title: "Is this an ImageMagick bug or am I doing something wrong? (PHP)"
date: 2008-08-09
forum: Programming Talk
---

### Post by rianjs on 2008-08-09
The directory's permissions are 755. The php script is about as basic as it gets:

```
<?php
$thumb = new Imagick();
$thumb->readImage('image.jpg');
$thumb->writeImage('test.png');
$thumb->clear();
$thumb->destroy();
?>
```

Which results in:

Fatal error: Uncaught exception 'ImagickException' with message 'Permission denied to: test.png' in /home/rianjs/www/whatsth.at/writeImageTest.php:4 Stack trace: #0 /home/rianjs/www/whatsth.at/writeImageTest.php(4): Imagick->writeimage('test.png') #1 {main} thrown in /home/rianjs/www/whatsth.at/writeImageTest.php on line 4

I see [this link](http://pecl.php.net/bugs/bug.php?id=12851), and from what I can tell, I'm having this problem, even though it's supposedly fixed. I just installed ImageMagick and all of its dependencies last night, and that bug is from January...

---

### Post by catchmeifyoutry on 2008-08-09
> **rianjs said:**
> The directory's permissions are 755. The php script is about as basic as it gets:

```
<?php
$thumb = new Imagick();
$thumb->readImage('image.jpg');
$thumb->writeImage('test.png');
$thumb->clear();
$thumb->destroy();
?>
```

Which results in:

Fatal error: Uncaught exception 'ImagickException' with message 'Permission denied to: test.png' in /home/rianjs/www/whatsth.at/writeImageTest.php:4 Stack trace: #0 /home/rianjs/www/whatsth.at/writeImageTest.php(4): Imagick->writeimage('test.png') #1 {main} thrown in /home/rianjs/www/whatsth.at/writeImageTest.php on line 4

I see [this link](http://pecl.php.net/bugs/bug.php?id=12851), and from what I can tell, I'm having this problem, even though it's supposedly fixed. I just installed ImageMagick and all of its dependencies last night, and that bug is from January...

Hi, I'm not sure on how Imagick handles this, but could it be that the script doesn't have permission to write this file on your file system?
If the script is executed by the apache-daemon files that it will create cannot be placed in directories that you created unless you change the permissions.
Similarly, if you run the script from the commandline files will be created in your name. Do you have writing permissions for /home/rianjs/www/whatsth.at/ ? Maybe that directory is owned by root, not by you.

I tested your code and it works fine, unless I remove the write permission of the directory because than it crashes.

---

### Post by rianjs on 2008-08-09
Well, it's my desktop machine, and I created it (not as root), and the permissions on it are 755:

```
drwxr-xr-x 3 rianjs rianjs 4096 2008-08-08 23:34 whatsth.at
```

---

### Post by catchmeifyoutry on 2008-08-09
> **rianjs said:**
> Well, it's my desktop machine, and I created it (not as root), and the permissions on it are 755:

```
drwxr-xr-x 3 rianjs rianjs 4096 2008-08-08 23:34 whatsth.at
```

Hmmm, than it is strange.
You are using php5 and php5-imagick from the repository, and executing the script with "php writeTestImage.php"?
Then a long shot, but there is not already test.png in the dir which has wrong permissions to be overwritten, right?

---

### Post by rianjs on 2008-08-09
Weird. I didn't think of trying it using the CLI php command. I'd been testing it via the browser.

I'm sure this information is significant, but I'm not sure what it means, exactly.

---

### Post by catchmeifyoutry on 2008-08-09
> **rianjs said:**
> Weird. I didn't think of trying it using the CLI php command. I'd been testing it via the browser.

I'm sure this information is significant, but I'm not sure what it means, exactly.

yes it is,
if you watch it through your browser, your running it through the apache daemon (if you're using apache). That's what I meant in my first reply, the daemon has user id "apache", or something, which different from your own username. "apache" cannot write in directories you created with premission "755", only _you_ can write in those directories (and root of course).

---

### Post by rianjs on 2008-08-09
> **catchmeifyoutry said:**
> yes it is,
if you watch it through your browser, your running it through the apache daemon (if you're using apache). That's what I meant in my first reply, the daemon has user id "apache", or something, which different from your own username. "apache" cannot write in directories you created with premission "755", only _you_ can write in those directories (and root of course). That's kind of what I suspected. How do I change this so Apache can r/w to the entire www directory?

Edit: I figured it out.

```
sudo chown www-data www
```

Edit 2: Just kidding. That didn't work, even after restarting Apache.

---

### Post by catchmeifyoutry on 2008-08-09
> **rianjs said:**
> That's kind of what I suspected. How do I change this so Apache can r/w to the entire www directory?

To test it, you might just as well set the dir's permissions to 777 for the moment. Try that, and see if it stopped crashing your code.
If it worked, the apache daemon should have created the file test.png in the same dir. In the terminal use "ls -la" to output a list of the files including their owner and group. Check the name of user/group of test.png.
My guess is that the user is called "apache".

Better solution, don't keep the whole dir in permission 777 (potential security risk) but create a subdir where apache may write the images to.
Maybe just call the dir "images" with 777 permissions, and change the script to output the file "images/test.png" instead.

Best solution: look up your user permissions, and that of the "apache" daemon. You could change the ownership of the "images" subdir on the commandline such that the daemon owns the directory. I guess something like 
[CODE]
mkdir images
chown apache images
[CODE]

Or, you might place apache (and yourself) in a new user group and allow that group to write to the folder.

Sooo, in other words, it's a filesystem permission problem of different users with different tasks. If you don't know what I'm talking about, google for info on file permissions, "chown", "adduser", ... etc.

Good luck.

---

### Post by rianjs on 2008-08-09
Thanks for your help. I ended up fixing it by doing

```
sudo chown www-data -R www/
```

from my home folder. All is now working as expected.

---

### Post by catchmeifyoutry on 2008-08-09
> **rianjs said:**
> Thanks for your help. I ended up fixing it by doing

```
sudo chown www-data -R www/
```

from my home folder. All is now working as expected.

Ok, great (it is indeed "www-data" not "apache", just tested it myself :p).
Still, i would advice you to, at a certain point, output files only to a special directory owned by www-data. This way you'll be certain apache can't accidentally overwrite your code or other files.

Anywat, success.

---

### Post by rianjs on 2008-08-09
> **catchmeifyoutry said:**
> Ok, great (it is indeed "www-data" not "apache", just tested it myself :p).
Still, i would advice you to, at a certain point, output files only to a special directory owned by www-data. This way you'll be certain apache can't accidentally overwrite your code or other files.

Anywat, success.

Yes, this is for very specific testing on my desktop. When this module is made more generic, it will indeed be written to a temporary directory. I just needed to make sure Imagick was working, and that my code does what it's supposed to as quickly and messily as possible. :)

---

