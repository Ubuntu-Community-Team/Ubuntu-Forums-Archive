---
title: "Regex Help(easy im just horrible with regex)"
date: 2009-01-30
forum: Programming Talk
---

### Post by cerealtx on 2009-01-30
okay so i have a link and i just want the end of the link
```
http://media.website.com/ca7ae5a12f295a3980b9f0d39ea34cfe/filename.flv
```, i managed to create a regex expression to get the link from a html source now i just wanna cut that link down even further to just get "filename.flv" any one help? a explanation as to whats going on would be awesome 2, the code is great but i want to understand aswell

---

### Post by geirha on 2009-01-30
Since * is greedy, you can remove everything up to the last / fairly easily
```
.*/(.*)
```
group 1 should be filename.flv with the example url above.

```
$ echo 'http://media.website.com/ca7ae5a12f295a3980b9f0d39ea34cfe/filename.flv' | sed -r 's|.*/(.*)|\1|'
filename.flv

```

---

### Post by badperson on 2009-01-30
one of these should work:
```
\/([^\.]+)\.(.*)$
\/([^\.]+)\.(flv|htm|html)$


```

---

### Post by kaibob on 2009-01-30
It's not intended for the purpose but basename is another alternative:

```
$ basename http://media.website.com/ca7ae5a12f295a3980b9f0d39ea34cfe/filename.flv
filename.flv

```

---

