---
title: "Batch renaming files"
date: 2013-12-26
forum: Programming Talk
---

### Post by willzhigaylo on 2013-12-26
For me to be able to upload pics to eBay I have to change all the images from .JPG (upercase) to .jpg (lowercase). Becuase I list alot on eBay, I need to do this often, is there any way I can do this faster? Any help is apprectiated.

---

### Post by mikewhatever on 2013-12-26
Here you go [http://stackoverflow.com/a/8167105](http://stackoverflow.com/a/8167105)

---

### Post by sisco311 on 2013-12-26
You can use one of the GUI tools like:

gprename
 purrr 
 pyrenamer 
 gwenrename 
thunar (file manager)
gnome-commander (file manager) 
 krename

Or if you want to do it in the CLI, then in Ubuntu, you can try the Perl based rename utility:
```

cd path/to/dir
prename --no-act 's/\.JPG$/.jpg/' *.JPG

```

If you are looking for a more portable code or want to rename files recursively, then check out BashFAQ 030 (link in my signature).

---

### Post by willzhigaylo on 2013-12-26
Thanks that helped!

---

