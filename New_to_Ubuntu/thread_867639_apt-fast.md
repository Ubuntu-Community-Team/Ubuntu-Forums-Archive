---
title: "apt-fast??"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by marine63 on 2008-07-23
i've recently came across this apt-fast thing
[http://www.mattparnell.com/projects/apt-fast-and-axel-roughly-26x-faster-apt-get-installations-and-upgrades.html](http://www.mattparnell.com/projects/apt-fast-and-axel-roughly-26x-faster-apt-get-installations-and-upgrades.html)
and I was wonder how it works and if it works at all...

---

### Post by jordanmthomas on 2008-07-23
It looks like it just replaces wget with a download manager that downloads in multiple chunks?

It asks apt what it would have downloaded, then downloads them with another program, then tells apt to install.  This time, the files apt needs are already in its cache, so it doesn't need to download anything.

I suppose this would be faster, but it is harder on the repositories hosting the debs.  They are probably throttled per connection, and it's probably for a reason

---

### Post by forger on 2008-07-23
they could use multiple servers for it.. then it wouldn't be so hard on one server :)
e.g.
```
axel ftp://ftp.{be,nl,uk,de}.kernel.org/pub/linux/kernel/v2.4/linux-2.4.17.tar.bz2
```


something like a regular expression substitution (with sed?):
```
s/(?:[a-zA-Z]{2}\.)?archive\.ubuntu\.com/\{nl,se,uk,de,us,fr\}\.archive\.ubuntu\.com/
```

---

