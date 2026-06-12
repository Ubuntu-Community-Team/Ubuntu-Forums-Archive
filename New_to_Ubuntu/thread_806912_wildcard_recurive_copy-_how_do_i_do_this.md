---
title: "wildcard recurive copy- how do i do this?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Rob Hodge on 2008-05-25
here's what i'm trying to do. i want to copy all mp3's from a cdrom archive to a usbdrive. but i can onlyget the recursive to work, or the wildcard, but not both. here's what i'm trying to do

 cp -r /media/cdrom/*.mp3 /media/USB\ DRIVE/

granted, this isn't correct, but might give anidea exactly what i'm trying to do. 

i want to climb the directory tree and copy over any mp3's found, maintaining the same directory structure. 

any ideas?

Rob Hodge

---

### Post by gerben1 on 2008-05-25
You could do this:

```

cd /media/cdrom ; find . -name "*.mp3" -print | cpio -pvdum  /media/USB\ DRIVE/

```

---

### Post by hyperair on 2008-05-25
Copy this code into the terminal:
```

find "/media/cdrom" -name '*.mp3' -print | cpio -pavd "/media/USB DRIVE"

```

This code is adapted from this tutorial: [http://www.askdavetaylor.com/how_do_i_selectively_copy_files_from_a_directory_structure.html](http://www.askdavetaylor.com/how_do_i_selectively_copy_files_from_a_directory_structure.html)

When in doubt, Google is your friend.

---

