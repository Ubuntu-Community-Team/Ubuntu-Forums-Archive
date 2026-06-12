---
title: "How to use python to split master text file into multiple files"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by magischevogel on 2013-02-25
Conf.text contain the following data:
configfile:"/var/etc/config/config.server"
RRRRRRRRRRRRRR
FFFFFFFFFFFFFFFF
NNNNNNNNNNNNNN
configfile:"/var/config/MyConf.cfg"
KKKKKKKKKKKKKKKK
MMMMMMMMMMM
LLLLLLLLLLLLLLLLLL
configfile:"/var/etc/dbconfig/dbcon.conf"
AAAAAAAAAAAAAA
BBBBBBBBBBBBBBBB
CCCCCCCCCCCCCC


How to use a phyton function to split the conf.txt file into multiple files using the "configfile" tag as a spliting string  and the quoted string that come after the tag as path and filename where the splitted sections will be stored.
i.e
the lines
RRRRRRRRRRRRRR
FFFFFFFFFFFFFFFF
NNNNNNNNNNNNNN
will be stored in "/var/etc/config/config.server"
and
KKKKKKKKKKKKKKKK
MMMMMMMMMMM
LLLLLLLLLLLLLLLLLL
will be stored in : "/var/config/MyConf.cfg"
and
AAAAAAAAAAAAAA
BBBBBBBBBBBBBBBB
CCCCCCCCCCCCCC
will be stored in : "/var/etc/dbconfig/dbcon.conf"

PS: The master Conf.text can contain more than the 3 sections mentioned above.so more configfile tag for more config files after the splitting process.
best regards.

---

