---
title: "PHP and environmental variables"
date: 2011-06-07
forum: Programming Talk
---

### Post by skytreader on 2011-06-07
Hi all. I have a folder in my website that contains "boilerplate" scripts---i.e., scripts that are used by multiple pages, through the include directive. For organization purposes, I put all of them in their own special folder.

So as not to be bothered by the changedir dots (../thats/a/_changedir_/dot), I am trying to set the include_path environmental variable in my code through

```
$_ENV["INCLUDE_PATH"]="C:\xampp\htdocs\path\to\boilerplate\php";
```

But that doesn't seem to work---my code still throws unfound-file related errors. I call phpinfo() after that piece of code above but my boilerplate directory isn't included in include_path. I even tried to change the key to lowercase (i.e., "include_path") but to no avail.

Of course, I can add my directory directly to php.ini but it'd be a hassle for other developers to run my code on their machine (I'm sort of building base codes for a project). Any advice?

Thanks!

---

### Post by Petrolea on 2011-06-07
> **skytreader said:**
> Hi all. I have a folder in my website that contains "boilerplate" scripts---i.e., scripts that are used by multiple pages, through the include directive. For organization purposes, I put all of them in their own special folder.

So as not to be bothered by the changedir dots (../thats/a/_changedir_/dot), I am trying to set the include_path environmental variable in my code through

```
$_ENV["INCLUDE_PATH"]="C:\xampp\htdocs\path\to\boilerplate\php";
```

But that doesn't seem to work---my code still throws unfound-file related errors. I call phpinfo() after that piece of code above but my boilerplate directory isn't included in include_path. I even tried to change the key to lowercase (i.e., "include_path") but to no avail.

Of course, I can add my directory directly to php.ini but it'd be a hassle for other developers to run my code on their machine (I'm sort of building base codes for a project). Any advice?

Thanks!

Have you tried set_include_path function? [http://php.net/manual/en/function.set-include-path.php](http://php.net/manual/en/function.set-include-path.php)

---

### Post by aytech on 2011-06-07
If you're sure the path is correct, try replacing the backslashes with forward slashes.

---

### Post by Petrolea on 2011-06-07
> **aytech said:**
> If you're sure the path is correct, try replacing the backslashes with forward slashes.

He's on Windows, backslashes are used there, so are in PHP that's running on Windows.

---

### Post by aytech on 2011-06-07
> **Petrolea said:**
> He's on Windows, backslashes are used there, so are in PHP that's running on Windows.

Not necessarily, I have Win machine with apache/php 5.2.17 and have to use forward slashes there. Well, probly backslash would work too, didn't check :)

---

### Post by lordadi on 2011-06-07
Wouldn't Apache (and by extension, PHP) be looking only in the /htdocs/ directory and downwards? In that case, your path may need to be relative to the htdocs directory.

---

### Post by skytreader on 2011-06-08
> **lordadi said:**
> Wouldn't Apache (and by extension, PHP) be looking only in the /htdocs/ directory and downwards? In that case, your path may need to be relative to the htdocs directory.

Researching Petrolea's set_include_path, I stumbled upon [this]("http://www.geeksengine.com/article/php-include-path.html"). 

Summary of (a self-inferred) lesson from the link:
Though relative paths are undoubtedly helpful, things may get pretty messy when uploading to your server. It may help to set an absolute include_path, using

```
$_SERVER["DOCUMENT_ROOT"] . "/to/boilerplate/"
```

Thanks for the help guys. Issue closed.

---

