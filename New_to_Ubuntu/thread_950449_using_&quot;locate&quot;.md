---
title: "using &quot;locate&quot;"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by stereomuffin on 2008-10-17
Hi, i have a few windows shares i access threw mount.cifs (for example i have my /home/user/Music mounted to a windows share on a remote server).

I'm doing this threw some lines in my /etc/rc.local

However when i run updatedb it doesn't seem to include my mount, when i do a "locate <some mp3>" it doesn't give me any result.

Can someone share some light or a fix on my problem?

Cheers! :)

EDIT: i did search the forum, and found: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=697468](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=697468) however i'm not sure if this relates to mount.cifs aswell? I tried the symbolic links part, but it doesn't work.

---

### Post by kpkeerthi on 2008-10-17
Perhaps not a direct solution for your query, but this might be handy:
```
find ~/Music -iname "<pattern>.mp3"
```

If you are confortable using regular expressions, you could use
```
find ~/Music -regex '<pattern>'
```

**Example:** To find all files begining with 'A' or 'a'
```
find ~/Music -regex '^[Aa].*\.mp3'
```

---

### Post by stereomuffin on 2008-10-17
> **kpkeerthi said:**
> Perhaps not a direct solution for your query, but this might be handy:
```
find ~/Music -iname "<pattern>.mp3"
```

If you are confortable using regular expressions, you could use
```
find ~/Music -regex '<pattern>'
```

**Example:** To find all files begining with 'A' or 'a'
```
find ~/Music -regex '^[Aa].*\.mp3'
```

Thanks kpkeerthi, that works great. :)

---

