---
title: "&quot;requires installation of untrusted packages&quot;"
date: 2015-12-18
forum: New to Ubuntu
---

### Post by houmingc on 2015-12-18
I want to install a recording application onto my ubuntu. i chose ardour
But using Ubuntu Software Centre, an error occurs saying "requires installation of untrusted packages"

---

### Post by ian-weisser on 2015-12-18
That seems unusual.
That error is there for a reason. You are right to come here and ask.

What release of Ubuntu are you running?
Are you following instructions from the internet?
Or did you just discover ardour in the Software Center?

---

### Post by v3.xx on 2015-12-18
Maybe missing a key.  Please run the following command in terminal and post any "GPG Errors" you may get.

```
sudo apt-get update
```

---

