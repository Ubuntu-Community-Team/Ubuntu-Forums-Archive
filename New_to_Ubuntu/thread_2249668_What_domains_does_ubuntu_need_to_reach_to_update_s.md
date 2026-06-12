---
title: "What domains does ubuntu need to reach to update successfully?"
date: 2014-10-23
forum: New to Ubuntu
---

### Post by ben5 on 2014-10-23
I am setting up ubuntu PC's behind a firewall that allows only white listed sites to be reached. 

What all domains do I need to whitelist for ubuntu to be able to update?

---

### Post by grahammechanical on 2014-10-23
You can open /etc/apt/sources.list in Gedit and you will see all the URLs to the repositories that Ubuntu updates from. The URL will change depending upon the mirror that is being used.

Regards.

---

### Post by sandyd on 2014-10-24
> **ben5 said:**
> I am setting up ubuntu PC's behind a firewall that allows only white listed sites to be reached. 

What all domains do I need to whitelist for ubuntu to be able to update?

You can view the domains in /etc/apt/sources.list

Alternatively, some fun with grep and awk produces....

```

cat /etc/apt/sources.list | grep -v '#\|^$' | awk -F "/" '{if (x[$3] == 0) print $3; x[$3]++}'
```

Note that wrongly formatted lines (i.e. lines that produce errors during apt-get update) *may* not work.

---

