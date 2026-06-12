---
title: "Bash Scripting Help Please"
date: 2014-10-24
forum: Programming Talk
---

### Post by neil-kautzner on 2014-10-24
```

object network ip:webworks.blah.com
 host 111.111.1.111
 description 2013-8-4
object network ip:www.blah.com
 host 111.111.1.111
object network fqdn:blah.blah.com
 fqdn blah.blah.com

```

Above is what I am looking at. What I, IDEALLY, want to see is something like this:

Name: webworks.blah.com
Address: 111.111.1.111

Since some of the information is just showing the FQDN, I need to do NSLOOKUP on these. I would do the NSLOOKUP by hand but, i have probably around 1000 to do. SO, this is why I am thinking a Bash script will be most helpful. I have a script that looks like this; found it on this forum from 2010. ```
for i in `cat epcasa.txt`; do nslookup $i | grep ^Name -A1;echo;done
``` could this be modified to do what I am proposing? Any help would be greatly appreciated. I am in the midst of learning how Bash scripting works and my knowledge is limited at this time otherwise I would takle this on my own.

---

### Post by Vaphell on 2014-10-24
```
#!/bin/bash

while read -r ln
do
  [[ $ln = "object network"* ]] || continue
  host=${ln##*:}
  nslookup "$host" | grep -A1 '^Name:'
  echo
done < nslook.txt
```

```
$ cat nslook.txt
object network ip:www.yahoo.com
 host 111.111.1.111
 description 2013-8-4
object network ip:www.google.com
 host 111.111.1.111
object network fqdn:www.ubuntuforums.com
 fqdn blah.blah.com
$ ./nslook.sh
Name:	fd-fp3.wg1.b.yahoo.com
Address: 46.228.47.115
Name:	fd-fp3.wg1.b.yahoo.com
Address: 46.228.47.114

Name:	www.google.com
Address: 173.194.116.112
Name:	www.google.com
Address: 173.194.116.113
Name:	www.google.com
Address: 173.194.116.114
Name:	www.google.com
Address: 173.194.116.115
Name:	www.google.com
Address: 173.194.116.116

Name:	www.ubuntuforums.com
Address: 91.189.94.12

```


PS. avoid using for loops with files and command outputs, while read is for that

---

### Post by neil-kautzner on 2014-10-24
Awesome!!!
Such a fast response too! Thank you, thank you!

---

