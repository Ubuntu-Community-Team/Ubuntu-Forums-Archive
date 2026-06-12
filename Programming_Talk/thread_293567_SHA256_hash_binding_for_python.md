---
title: "SHA256 hash binding for python"
date: 2006-11-05
forum: Programming Talk
---

### Post by gorded on 2006-11-05
I installed the python-crypto package which is supposed to have python bindings for sha256 but i can't figure out if i need to import sha or another module, and what command  i need to use sha256

Any help would be much apericated

Thanks

---

### Post by Randomskk on 2006-11-05
Going off what I saw a while ago, but I think it's hashlib, check the Python docs for usage but it involves something like:
import hashlib;
m = hashlib.sha512()
m.update("hello, world")
m.hexdigest()

see [http://docs.python.org/lib/module-hashlib.html](http://docs.python.org/lib/module-hashlib.html) for more info!

---

### Post by shortsellyhoonow on 2006-11-05
You might want to try installing gtkpod.

It even has a new feature to find hash collisions in constant time.

---

### Post by Randomskk on 2006-11-05
Update: meh, hashlib isn't available for some very bizarre reason?
python-crypto doesn't seem to have MD5 or SHA.

---

### Post by Randomskk on 2006-11-05
Hashlib is only on python 2.5. Install this:
sudo apt-get install python2.5
Then run it:
python2.5

Then you can import hashlib:
```
adam@wizard ~/Downloads$ python2.5
Python 2.5 (r25:51908, Nov  3 2006, 10:25:39)
[GCC 4.1.2 20061101 (prerelease) (Ubuntu 4.1.1-18ubuntu1)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import hashlib
>>> m = hashlib.sha512()
>>> m.update("hi")
>>> m.hexdigest()
'150a14ed5bea6cc731cf86c41566ac427a8db48ef1b9fd626664b3bfbb99071fa4c922f33dde38719b8c8354e2b7ab9d77e0e67fc12843920a712e73d558e197'

```

---

