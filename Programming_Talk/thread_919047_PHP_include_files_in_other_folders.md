---
title: "PHP include files in other folders"
date: 2008-09-13
forum: Programming Talk
---

### Post by tc101 on 2008-09-13
I have a site with folders like this:

[www.sitename/a/b/folder1](www.sitename/a/b/folder1)

[www.sitename/a/b/folder2](www.sitename/a/b/folder2)

If I have a program in folder1, how do I write the include for a file in folder2?   How about for a file in b?

I have tried lots of things.  I don't understand why it doesn't work when I give it the full path

include("http://www.sitename.com/a/b/folder2/include_file_db.php");

which makes me think maybe there is some other problem.

---

### Post by slavik on 2008-09-13
inside phpscripts, you don't have the web structure, you have the local directory structure.

code in folder1/index.php

include("../folder2/index.php"); #includes b/folder2/index.php

and

include("../index.php"); #includes b/index.php

---

### Post by tc101 on 2008-09-13
That works.  Thanks.

---

### Post by tc101 on 2008-09-13
What if I wanted to go one folder up, in the "a" folder?

---

### Post by drubin on 2008-09-13
In php includes are either relative paths. to the current directory or they are absolute. 

../ is up a dir
./ is current dir.
or you can put the FULL path of files ie
include '/var/www/html/site1/index.php';

This method can cause huge issues when trying to move sites/code onto other sites/servers.

**EDIT:** you may also do this. ../../../ This is up 3 dirs.

---

### Post by slavik on 2008-09-13
I would advise against full paths, because you want to keep your PHP code more independent on where it is stored.

---

### Post by drubin on 2008-09-13
> **slavik said:**
> I would advise against full paths, because you want to keep your PHP code more independent on where it is stored.

I always  define('_ROOT',dirname(__FILE__)); in my config file. then 
include (_ROOT.'/inc/file.php');

This way I do not have pathing issues, as well as keeping the project transportable.

**Edit:** But yes I do agree. do not have absolute pathing unless they come from a config file.

---

### Post by tc101 on 2008-09-13
> ../ is up a dir

So does that mean:

.../ is up 2 dirs
..../ is up 3 dirs

and so on?

---

### Post by drubin on 2008-09-13
> **tc101 said:**
> So does that mean:

.../ is up 2 dirs
..../ is up 3 dirs

and so on?

No.  you would have to go up 1 dir then up the next. ie
```
../../ is up 2 dirs
```

---

### Post by lswest on 2008-09-13
> **tc101 said:**
> So does that mean:

.../ is up 2 dirs
..../ is up 3 dirs

and so on?

no, it'd be ../../ for 2 dirs, and ../../../ for 3 dirs.

ah, beaten to it

---

### Post by drubin on 2008-09-13
> **rubinboy said:**
> 

../ is up a dir
./ is current dir.
.........
 you may also do this. ../../../ This is up 3 dirs.

> **lswest said:**
> ah, beaten to it


We were both beaten. I posted this before the question was even asked :)

---

### Post by tc101 on 2008-09-13
Thanks everyone.  I'm understand now.

---

### Post by drubin on 2008-09-13
Remember to mark the thread as solved using the thread tools.

---

