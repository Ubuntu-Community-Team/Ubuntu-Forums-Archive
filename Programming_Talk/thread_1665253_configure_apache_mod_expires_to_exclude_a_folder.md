---
title: "configure apache mod_expires to exclude a folder?"
date: 2011-01-12
forum: Programming Talk
---

### Post by ndefontenay on 2011-01-12
```
#---------------------------------------------------------
# MOD EXPIRE SETTINGS
#---------------------------------------------------------
#Expires Options
ExpiresActive on
<FilesMatch "\.(jpe?g|JPE?G|png|PNG||gif|GIF|swf|SWF|bmp|BMP|js|JS|css|CSS|ico|ICO)$">
ExpiresDefault "access plus 1 month"
</FilesMatch>
```

Hi,

I've used the code above to cache any files with this type of extensions.
It's been added to .htaccess at root level.
So, it's going to affect any files that's in the public folder.

In that public folder, I get a folder that keeps profile pictures. Those are renamed with the user id. So, I don't want them cached because if a user changes his profile picture, he won't see the new one until he delete his browser's cache.

How can I exclude the profile folder?

---

### Post by gmargo on 2011-01-12
Can't you just put another **.htaccess** in the profiles directory, and override the root value?

---

