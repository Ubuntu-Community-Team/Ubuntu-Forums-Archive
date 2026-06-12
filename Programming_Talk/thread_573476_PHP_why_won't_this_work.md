---
title: "PHP: why won't this work?"
date: 2007-10-11
forum: Programming Talk
---

### Post by x1a4 on 2007-10-11
Hi,

Can someone please have a look at my code and tell me what I'm doing wrong?

```

<span style="font-size: 0.9em;">Shop country: 
<?php  if($_GET['country']=='CA'){  ?>
Canada | <a href="/shop/?country=US" title="USA" target="_top">USA</a>
<?php  }elseif($_GET['country']=='US'){  ?>
<a href="/shop/?country=CA" title="Canada" target="_top">Canada</a> | USA
<?php  }else{  ?>
<a href="/shop/?country=CA" title="Canada" target="_top">Canada</a> | 
<a href="/shop/?country=US" title="USA" target="_top">USA</a>
<?php  }  ?></span>

```

It always goes to the else block even when I have 'country' set in the url.  

Thank you.

---

### Post by nine01a on 2007-10-11
Are you sure that the ?country=XX is actually getting appended to the url properly? .../index.php?country=XX might be more appropriate instead of .../?country=XX

Changing /shop/?country=XX to ?country=XX worked fine for me:

[http://shsu.edu/~zan001/test.php]("http://shsu.edu/~zan001/test.php")
[http://shsu.edu/~zan001/test.phps]("http://shsu.edu/~zan001/test.phps")

---

### Post by x1a4 on 2007-10-13
> **nine01a said:**
> Are you sure that the ?country=XX is actually getting appended to the url properly? .../index.php?country=XX might be more appropriate instead of .../?country=XX

Changing /shop/?country=XX to ?country=XX worked fine for me:

[http://shsu.edu/~zan001/test.php]("http://shsu.edu/~zan001/test.php")
[http://shsu.edu/~zan001/test.phps]("http://shsu.edu/~zan001/test.phps")

The url is formed correctly.  The problem was that the page was in a frame.  It worked fine standalone so I made the appropriate changes and it works fine now.

---

