---
title: "Difficulty with subdirectories using php includes"
date: 2008-10-27
forum: Programming Talk
---

### Post by RobertWaelder on 2008-10-27
I am attempting to create a directory structure using php includes for my website, [www.theinvisibledolphin.com](www.theinvisibledolphin.com), but the includes are breaking some of the image links on pages that are one directory deep. Right now, I am just testing it on my home apache server. I have open_basedir active in my config and set to /var/www. Similarly, my default file in "sites available" is set to /var/www as well. I am trying to create "lyrics" pages in /var/www/lyrics/song.php. The includes load, but none of the links or images work. I am using $_SERVER['DOCUMENT_ROOT'] to refer to /var/www/whatever, for example the images on the site are /var/www/images/logo.png. So basically, I am writing this in the html file:

[PHP]
<?php 
echo '<a class="navln" href="' . $_SERVER['DOCUMENT_ROOT'] . 'index.html">'; ?>
<?php echo '<img src="' . $_SERVER['DOCUMENT_ROOT'] . 'images/home.png" />'; ?>
</a>
[/PHP]

What's going on here?

---

### Post by drubin on 2008-10-27
> **RobertWaelder said:**
> I am attempting to create a directory structure using php includes for my website, [www.theinvisibledolphin.com](www.theinvisibledolphin.com), but the includes are breaking some of the image links on pages that are one directory deep. Right now, I am just testing it on my home apache server. I have open_basedir active in my config and set to /var/www. Similarly, my default file in "sites available" is set to /var/www as well. I am trying to create "lyrics" pages in /var/www/lyrics/song.php. The includes load, but none of the links or images work. I am using $_SERVER['DOCUMENT_ROOT'] to refer to /var/www/whatever, for example the images on the site are /var/www/images/logo.png. So basically, I am writing this in the html file:

[PHP]
<?php 
echo '<a class="navln" href="' . $_SERVER['DOCUMENT_ROOT'] . 'index.html">'; ?>
<?php echo '<img src="' . $_SERVER['DOCUMENT_ROOT'] . 'images/home.png" />'; ?>
</a>
[/PHP]

What's going on here?

This might be what you are looking for. [http://www.php.net/manual/en/reserved.variables.server.php](http://www.php.net/manual/en/reserved.variables.server.php)
[PHP]
<?php 
echo '<a class="navln" href="http://' . $_SERVER['SERVER_NAME'] . 'index.html">'; ?>
<?php echo '<img src="http://' . $_SERVER['SERVER_NAME'] . 'images/home.png" />'; ?>
</a>
[/PHP]
But I would recommend using relative(To the current vhost) urls. ie just using /images/home.php

---

