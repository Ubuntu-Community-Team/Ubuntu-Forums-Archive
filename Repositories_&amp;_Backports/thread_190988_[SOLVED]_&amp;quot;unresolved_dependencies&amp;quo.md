---
title: "[SOLVED] &amp;quot;unresolved dependencies&amp;quot;"
date: 2006-06-06
forum: Repositories &amp; Backports
---

### Post by Cone on 2006-06-06
I was going to install Enlightenment, so I went to Synaptic and started the install for that while simultaneously searching Google for something along the lines of "enlightenment ubuntu" just in case I had problems.  Well, I found a guide for e17 of it so I decided I would install that instead.

   Once Synaptic was done downloading/install everything Enlightenment E16 related, I highlighted everything and told it to remove them, then added the repository that it told me to to Synaptic and did a reload.

   I then do a search for Enlightenment and see that it now lacks a version number next to it, and promptly remove the repository and reload again, but it still is lacking the version number and when I double click on it I get the following error:

> Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.

[QUOTE]enlightenment:

Package enlightenment has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
[/QUOTE]

:rolleyes: Whoops ](*,) 

Any one know how to help?

Thanks,
~Cone

---

### Post by bluevoodoo1 on 2006-06-06
That happened to me when one of the guides told me to make a /etc/apt/preferences file as found here... [http://ubuntuforums.org/showthread.php?t=20216](http://ubuntuforums.org/showthread.php?t=20216) 

I **deleted** the /etc/apt/preferences file I created, reload synaptic, and then it worked. 


Here's the snippet from the link above that I had to remove...
> 
Add the following lines to /etc/apt/preferences
(If this file doesn`t exist, create it.)
(Don't know how necessary it is, but it worked for me.)

```
Package: enlightenment Pin: version 0.17.0_pre10* Pin-Priority: 999 
Package: enlightenment-data Pin: version 0.17.0_pre10* Pin-Priority: 999
```


Hope that helps.

---

### Post by Cone on 2006-06-06
Oh, hey, that worked.  Thanks. :D :mrgreen: =D>

---

