---
title: "PHP scripting question -"
date: 2009-07-13
forum: Programming Talk
---

### Post by AFarris01 on 2009-07-13
I somehow accidentally posted this before finishing the title... Im trying to figure out how i could add a date-last-modified stamp to a page, but in a slightly more complicated way than normal.

I know I can add this to a page by using something similar to the following:
```

<?php echo date(&#8220;F d Y H:i:s&#8221;, getlastmod() ); ?>

```

but my problem is this: my pages are all being dynamically created, using 1 standard header, which includes a menu, a content file, and 1 standard footer, which contains site tracker info, and a copyright notice.  the content of the site is kept in a completely separate area.

for example, my index page looks like this:
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">

<?php require("./includes/header.php");?>

<?php include("./Index/contents.php");?>

<?php require("./includes/footer.php");?>

```
the idea is that I can just update the 'contents.php file on any given page, to update that page.  

The problem is that the 'page last updated' section is located in the copyright area, and I can't move it, due to design restrictions. Is there a way for me to insert a general type function into the footer that will monitor when the appropriate 'contents.php' file has been modified, without adding any extra code to the 'contents.php' files themselves?

---

### Post by michaelzap on 2009-07-13
Looks to me as if it's all running as one script, so you can just add something like

<?php $moddate=date("F d Y H:i:s",getlastmod()); ?>

to your contents script and

<?php echo $moddate; ?>

to your footer script.

---

### Post by AFarris01 on 2009-07-14
Thanks! That looks like its working just fine.  Greatly appreciated!

I gotta brush up my PHP...

---

