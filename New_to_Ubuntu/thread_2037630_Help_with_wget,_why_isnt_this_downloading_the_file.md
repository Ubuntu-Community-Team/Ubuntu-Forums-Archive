---
title: "Help with wget, why isnt this downloading the files?"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by geekyhawkes on 2012-08-05
Hey, so im trying to get a wget download of a bunch of .epub files to work.  I think i must be using the wrong url maybe, but not sure:

im using 

```
 wget -r --level=inf -A epub --http-user=MYUSERNAME --http-password=MYPASSWORD 'http://learn.open.ac.uk/mod/resourcepage/view.php?id=658057'
```

The page linked with the URL is where all of the epub files are listed, but not stored.  They are stored in the following addresses:

[http://learn.open.ac.uk/file.php/8537/!via/resourcepage/109993560/8537/moddata/resourcepage/TU100_b1_p1.epub](http://learn.open.ac.uk/file.php/8537/!via/resourcepage/109993560/8537/moddata/resourcepage/TU100_b1_p1.epub)

[http://learn.open.ac.uk/file.php/8537/!via/resourcepage/109993872/8537/moddata/resourcepage/TU100_b1_p3.epub](http://learn.open.ac.uk/file.php/8537/!via/resourcepage/109993872/8537/moddata/resourcepage/TU100_b1_p3.epub)

As you can see the common part of the URl is as far down as 
[http://learn.open.ac.uk/file.php/8537/!via/resourcepage/](http://learn.open.ac.uk/file.php/8537/!via/resourcepage/) but i have tried this in my wget and it doesnt work. 

If i give a full URL to the exact location of the epub file then it downloads fine, so the server does support wget and the username etc are all fine.  What have i missed?  I thought -r and --level=0 should have taken me all the way through the folders to find the epub files?

Thanks andy

---

