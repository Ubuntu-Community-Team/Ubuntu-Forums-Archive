---
title: "copy question"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by thault on 2014-05-13
I need to use the cp command to copy the contents of a folder that has files and sub folders, to another folder. I don't want to move it, just copy the contents. What's the best way to do this?

---

### Post by Lars Noodén on 2014-05-13
I like tar or rsync for that.  

If you are just going to copy once, then [tar](http://manpages.ubuntu.com/manpages/trusty/en/man1/tar.1.html) is fine.

```

mkdir -p /some/path/to/target
cd /another/path/to/source
tar cpf - | (cd /some/path/to/target; tar xpf -)

```

Otherwise, if you are updating them frequently, [rsync](https://help.ubuntu.com/community/rsync) is even better.

```

rsync -av /path/to/source/  /some/path/to/target/

```

Having the slash ( / ) at the end of the paths is important with rsync.

---

### Post by Danger_Monkey on 2014-05-13
you can use cp -r to recursively copy a directory and everything under it to a new location:

```

cp -r /tmp/dangermonkey /opt/john/dangermonkey

```

There are other parameters as well, just like rsync.

---

