---
title: "Using symbolic links with PHP"
date: 2006-03-07
forum: Programming Talk
---

### Post by Ahriman on 2006-03-07
I have a few files on my machine that I want to let others download, and so I have written a script that will allow them to download it from a PHP generated page off my server.

The only problem, is that the script won't reference the files, because they live in /usr/dump and the script/server pages are all in /var/www

Could I make symoblic links to the files in /usr/dump and still have visitors to the webpage be able to download the files, without having to copy the files into the web root?

---

### Post by dabear on 2006-03-07
Yes, I've done it my self. You could do it through the cli:
```

sudo ln -s  /media/hda1/ /var/www/share

```
(makes a symlink called share in /var/www which points to /media/hda1)

Or you could do it through nautilus by left-and-right-click-dragging /media/hda1 to /var/www (if you have the right permissions)

---

