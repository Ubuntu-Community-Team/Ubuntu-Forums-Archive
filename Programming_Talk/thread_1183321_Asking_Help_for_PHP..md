---
title: "Asking Help for PHP."
date: 2009-06-09
forum: Programming Talk
---

### Post by qixin1984 on 2009-06-09
in my index.php file I write 
<img border="0" src="img/netquest.jpg" width="569" height="164">
but the image cannot be seen on the webpage.
[http://netquest.gforge.inria.fr/index.php](http://netquest.gforge.inria.fr/index.php)
So why?

Thank you for your attention and help!

---

### Post by escapee on 2009-06-10
Make sure your script has access to that image, because I tested the link and I do not have permission to access it as a visitor.

---

### Post by unknownPoster on 2009-06-10
anything that you need to be "interpreted" by php, you need to surround with php tags.

something like, 

```


<?php 

//code here

?>

```

In your case,

```


<?php 

<img border="0" src="img/netquest.jpg" width="569" height="164">

?>

```

---

### Post by osinghrathore on 2009-06-10
but since its plain HTML one doesn't need to enclose it in php tags, only php code should be enclosed within php tags.

 @qixin: the URL you have posted is giving 500 internal server error.

> **unknownPoster said:**
> anything that you need to be "interpreted" by php, you need to surround with php tags.

something like, 

```


<?php 

//code here

?>

```

In your case,

```


<?php 

<img border="0" src="img/netquest.jpg" width="569" height="164">

?>

```

---

### Post by theDaveTheRave on 2009-06-10
qixin

Not sure if it helps much but ....

Have you tried getting all your page code onto a single computer, and then point the img  tag to the local path of your included image?

Alternatively, put the code into php tags and put a loop structure around it so as you can see if your code is being read, then you can grab any error messages thrown out from PHP also (ie file not found type errors)

do you require some form of setup on the web server to include this type of image?

Is the image being overwritten by something else (either a php code script or a CSS)

these are the sorts of "silly errors" I always make, but then I'm silly ;)

David

---

### Post by tturrisi on 2009-06-10
As was stated above, the image has incorrect permissions.
This dir is accessable:
[http://netquest.gforge.inria.fr/img/](http://netquest.gforge.inria.fr/img/)
but the file netquest.jpg is not world readable.

---

