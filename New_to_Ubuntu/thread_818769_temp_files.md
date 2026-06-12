---
title: "temp files"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by chadwit on 2008-06-04
Can all of the folders in /tmp be safely deleted periodically? Are there any other temp locations that can be cleaned as well?

---

### Post by forestpixie on 2008-06-04
AFAIK /tmp is cleared at reboot

---

### Post by sdennie on 2008-06-04
I think they will get cleaned out on reboot.  I wouldn't recommend randomly deleting the files in /tmp though.  If you are looking to save disk space, removing the apt cache would likely save you a lot of space.  I believe the following will clear it out:

```

sudo apt-get clean

```

---

### Post by chadwit on 2008-06-04
oh...ok - thanks guys. 
What's the actual path to the files that "sudo apt-get clean" cleans? I'd like to take a look at those just out of curiosity...

---

### Post by sdennie on 2008-06-04
Have a look in /var/cache/apt/archives.

---

