---
title: "why use  // in web deisgn?"
date: 2010-03-04
forum: Programming Talk
---

### Post by kapi on 2010-03-04
have just come across some code while in work and wondered why the browser has used two forward slashes in the code to state failure to connect or open a document.

Warning: include() [function.include]: Failed opening 'C:/www//includes/rangenav.inc.php' for inclusion (include_path='.;C:\php5\pear') in C:\www\zone_new\aura-oak-granite-collection\index.php  on line 69

---

### Post by Hellkeepa on 2010-03-04
HELLo!

That's not the browser's doing, but the PHP's error reporting coupled with the settings in the "php.ini"/apache config file.
What's been done here, is that the person who set up PHP used a trailing slash on the htdocs root folder, and when PHP concatenated this with the include path (which starts with a slash) you got two slashes follow eachother.

This has no effect, neither negative nor positive, and can safely be ignored.

Happy codin'!

---

