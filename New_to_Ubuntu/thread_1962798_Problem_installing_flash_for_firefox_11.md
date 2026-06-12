---
title: "Problem installing flash for firefox 11"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Guruprasad on 2012-04-21
HI

I am using Ubuntu 10.10
I downloaded and extracted firefox 11.
Then I downloaded flash plugin.
Where should I copy libflashplayer.so file?

---

### Post by oldsoundguy on 2012-04-21
Why so complicated?  Just down load Flash Aid and let it do all of the work including clean up.

[http://linux.softpedia.com/progDownload/FLASH-AID-Download-57355.html](http://linux.softpedia.com/progDownload/FLASH-AID-Download-57355.html)

---

### Post by DJ_Max on 2012-04-21
> **oldsoundguy said:**
> Why so complicated?  Just down load Flash Aid and let it do all of the work including clean up.

[http://linux.softpedia.com/progDownload/FLASH-AID-Download-57355.html](http://linux.softpedia.com/progDownload/FLASH-AID-Download-57355.html)
You dont even have to do that, its in the repositories.
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by oldsoundguy on 2012-04-21
> **DJ_Max said:**
> You dont even have to do that, its in the repositories.
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

The repository install leaves traces behind every time you update .. Flash Aid does not.

---

### Post by lovinglinux on 2012-04-23
Why have you downloaded and extracted Firefox? You should be able to install Firefox from the Software Center.

Do you need a special version or Firefox build? If you do, then see [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

Anyway, Flash-Aid can place the libflashplayer.so in the right place for you. However, if you are using custom firefox installation, you might need to create a symlink to the plugins folder or simply copy the libflashplayer.so to ~/.mozilla/plugins. Anyway, better install Firefox from the repositories.

---

