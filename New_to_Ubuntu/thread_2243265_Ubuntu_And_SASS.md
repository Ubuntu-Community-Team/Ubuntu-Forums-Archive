---
title: "Ubuntu And SASS"
date: 2014-09-07
forum: New to Ubuntu
---

### Post by khan3 on 2014-09-07
Hi 

This is the first time i am using Ubuntu i have it setup on a virtual machine.

I have everything installed/setup, i am now watching my scss file to my css file. After the first time it writes to my css file it doesent after that. It says watching for changes, but it doesent update.

Can someone help me troubleshoot this?

Sass: Sass 3.4.3 (Selective Steve)


thanks,
KHAN

---

### Post by grahammechanical on 2014-09-07
Is there anything in the SASS documentation that might explain this? For example, the changes to the scss file being cached before being converted to css and written to a file?

[http://sass-lang.com/documentation/file.SASS_REFERENCE.html](http://sass-lang.com/documentation/file.SASS_REFERENCE.html)

Regards,

---

### Post by khan3 on 2014-09-08
> **grahammechanical said:**
> Is there anything in the SASS documentation that might explain this? For example, the changes to the scss file being cached before being converted to css and written to a file?

[http://sass-lang.com/documentation/file.SASS_REFERENCE.html](http://sass-lang.com/documentation/file.SASS_REFERENCE.html)

Regards,

I believe it does something like this, but it should still listen to changes in the .scss files and write to css file after.

For this reason i have tried deleting the cache folder as on other forums its a solution to many issues. Though, it did not solve mine.

KHAN

---

### Post by khan3 on 2014-09-08
It's a known issue

[https://github.com/sass/sass/issues/1393](https://github.com/sass/sass/issues/1393)

I reverted back to older version and it's fixed the problem.

---

