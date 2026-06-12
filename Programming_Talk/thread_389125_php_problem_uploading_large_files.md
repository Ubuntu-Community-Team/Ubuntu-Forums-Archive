---
title: "php problem uploading large files"
date: 2007-03-20
forum: Programming Talk
---

### Post by tocleora on 2007-03-20
Ok, I don't know why this wouldn't be a simple fix but then again it seems everything is right... I'm hoping I'm missing something simple, someone can point out.

I manage a web site that its visitor base are mostly people that aren't computer savvy.  Part of what we do on the site is we allow them to upload pictures, and we want to assume they don't know how to resize the images to a reasonable size before uploading. So I'm testing uploading a 2.7 MB image (this image will be resized to a reasonable size with imagemagick, for clarification). A smaller image works, but when I try this image the file variable is blank.  I'm assuming it relates to file size limitations, however I *believe* I've set all of those correctly.  This is what I've done...

In php.ini I've done this:

```

post_max_size = 20M
upload_max_filesize = 20M

```

In the web page itself I have this:

```

<form name="ciform" enctype="multipart/form-data" action="upload.php" method="post">
<input type="hidden" name="MAX_FILE_SIZE" value="20000000" />
<input type="file" name="wpicture">
</form>

```

and the variable I'm looking for is:

```

$_FILES['wpicture']['tmp_name']

```

if it's '' then I report an error, which it's reporting right now.  It's PHP 4.4.6 and shared hosting so unfortunately can't change that.  Hope someone can help! TIA!

---

### Post by Mirrorball on 2007-03-20
If it's shared hosting, try putting those settings in a .htaccess file.

---

### Post by tocleora on 2007-03-20
It *is* shared hosting, but we have ssh access to change our personal php.ini.  So nothing you can see is wrong?

---

### Post by Mirrorball on 2007-03-20
No. Did you restart the server after you made the changes?

---

### Post by tocleora on 2007-03-20
I solved the problem, sorry I didn't get back and state that sooner.  It's hosted on 1and1.com and apparently the php.ini file for them has to be in every folder the changes need to be in (per their documentation),  I figured it would fall down the tree, but I copied the php.ini file to the folder I was having problems with and it worked.  Thanks anyway!

---

