---
title: "How do you access a web page's source with a script?"
date: 2007-06-07
forum: Programming Talk
---

### Post by alalusim on 2007-06-07
Does anybody know of a way to access a web page's source and save it to a text file for manipulation by other scripts?

Keep in mind that I am relatively new to shell scripts.

Thanks in advance.

---

### Post by duff on 2007-06-07
```
# wget http://slashdot.org -O -
# links -source http://slashdot.org
```

---

### Post by alalusim on 2007-06-08
thanks a lot

---

