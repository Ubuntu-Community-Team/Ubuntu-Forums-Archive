---
title: "find files or folders excluding certain directories"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by BDNiner on 2008-05-20
is is possible to search for directories or files but exclude certain directories? I am looking for rsync config files on my rsync server but i also have a lot of other directories that are named rsync that store the actual backups. This is using the find command.

---

### Post by quelx on 2008-05-20
append -prune to the command

[http://www.liamdelahunty.com/tips/linux_find_exclude_multiple_directories.php](http://www.liamdelahunty.com/tips/linux_find_exclude_multiple_directories.php)

and ```
man find
```

---

### Post by bumanie on 2008-05-20
I suspect you are looking for the grep command. Look at this for help. [http://www.scit.wlv.ac.uk/cgi-bin/mansec?1+grep](http://www.scit.wlv.ac.uk/cgi-bin/mansec?1+grep)

---

### Post by BDNiner on 2008-05-20
Thank you, this really helps. I figured out what the issue is.

---

