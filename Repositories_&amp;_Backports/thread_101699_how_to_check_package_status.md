---
title: "how to check package status"
date: 2005-12-10
forum: Repositories &amp; Backports
---

### Post by Asgaard on 2005-12-10
hello all, i'm looking for a way from the command line to see if a certain package is installed or not. apt-cache seems to list a lot of information sans the single boolean  info i need ^__^

so far the closest i've come is to do apt-get -s to simulate an install and see if anything would be done, but it's clumsy... there must be a better cleaner way

thanks

---

### Post by invalid on 2005-12-10
```
dpkg -l | grep packagename
```

---

### Post by Asgaard on 2005-12-20
that does it, thanks ^__^

---

### Post by angkor on 2005-12-20
Or:

```
apt-cache policy [package-name]
```

---

### Post by jaya28inside on 2010-08-18
the simplest one... 

```

dpkg -s packageName

```

---

