---
title: "PHP Image Upload Issue"
date: 2007-09-17
forum: Programming Talk
---

### Post by 71fnRVVm on 2007-09-17
Hey everyone,

I'm having an issue with uploading an image through PHP to a specific directory...  I've banged my head on this for a few days, and talked to other people that work on this server... but there is no reason why we can see it's not working.

[php]
// ... already grabs file information, $f_temp is the temporary location of the uploaded file
$target_dir = '/usr/local/apache/htdocs/_images/user_upload/';
$target_dir = $target_dir . basename($f_name);
$moved = move_uploaded_file($f_temp, $target_dir);
			
if ($moved != FALSE) {
   // shows error
} else {
  // continues
}  
[/php]

The directory has been CHMOD'd properly to allow access, PHP isn't spitting out any errors, there's no errors in the apache logs.  It "pretends" like it works, and continues on to the success portion of the code, because move_uploaded_file() doesn't return an error.

I even went so far as to print to screen the temp file info ($f_temp) and the new file info ($target_dir)... both existed, both were correct.

Any ideas why this isn't working?  We were getting an error about SAFE_MODE directory permissions, so we turned SAFE_MODE off... but that didn't help.

Thanks

---

### Post by Thyme on 2007-09-17
Maybe try and increase the "post_max_size" value in your php.ini file. The file you're trying to upload could be over the default limit. Hope this helps...

---

### Post by 71fnRVVm on 2007-09-17
I got excited because that sounded like it might work...

But I increased it to 50M (which is the limit we want), and it made no difference.

Thanks though.

Any other ideas?

---

### Post by Thyme on 2007-09-17
Have you restarted the apache service after altering php.ini?

---

### Post by 71fnRVVm on 2007-09-17
Yeah...

```

apachectl restart
-->httpsd restarted
```

---

### Post by Thyme on 2007-09-17
Ok, I really thought what I suggested would be the solution. Will post if I think of anything useful...

---

### Post by sapo on 2007-09-17
I don't know about the file problem, but your logic here is wrong:

[php]if ($moved != FALSE) {
   // shows error
} else {
  // continues
}  [/php]

Using that you will be displaying errors when the file is moved, you should change it to this:

[php]if (!$moved)
{
  // display errors
}
else
{
  //continue
}
[/php]

Never test a condition like this: $something == TRUE , or $something != FALSE, this is redundant, instead try to use:

if($something), if(!$something), etc.

because if $something is boolean, it is already either true or false, you don't need to test it again.

---

### Post by 71fnRVVm on 2007-09-17
Sorry that was my fault in editing the code to put up on here... I should have doublechecked it.

---

