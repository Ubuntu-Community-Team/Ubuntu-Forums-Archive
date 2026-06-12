---
title: "accept input from shell pipe into php cli script?"
date: 2006-12-11
forum: Programming Talk
---

### Post by oldmanstan on 2006-12-11
so i basically want my php command line script to be able to accept one of its arguments from a shell pipe, like grep, for instance:

```
ls | grep .jpg
```

sorts out all the jpegs in the output from ls

i want to be able to do something similar but instead of grep, with my php script, for instance:

```
ls | grep .jpg | myscript.php
```

or some such business (that's actually accurate since the script resizes jpeg files)

i tried google but i can't think of specific enough search terms, i get a lot of unrelated matches, thanks!

---

### Post by tocleora on 2006-12-12
This page discusses the ability to do command line arguments:

[http://www.phpfreaks.com/tutorials/86/1.php](http://www.phpfreaks.com/tutorials/86/1.php)

What you may have to do is:

you could then use a "dir" in php with the command line argument to pull your ls instead, just call it from the command line in the folder you're wanting it pulled from like this:

```
myscript.php .jpg
```

Make sense?

---

