---
title: "BASH Scripting"
date: 2009-11-18
forum: Programming Talk
---

### Post by kreggz on 2009-11-18
Hello,

I am sysadmin who isn't that great a bash scripting and I need help

I want to run this command against a list of IP addresses:

snmpget -v1 -c shutF10ke $IPADDRESS sysName.0

The $IPADDRESS variable picks up the ip address line by line in a text file, the command is issued and the hostname is returned, the script then appends the hostname + ip address in another text file.


So how do I do it or does someone already have something like this written?

Thanks

---

### Post by ghostdog74 on 2009-11-18
```

while read -r IPADDRESS
do 
 snmpget -v1 -c shutF10ke $IPADDRESS sysName.0
done < textfile

```

A sysadmin who isn't good at shell scripting is not a real sysadmin at all. :). go read the stuff in my sig to learn bash

---

### Post by kreggz on 2009-11-18
thanks for you help and you are right - I will learn bash

---

### Post by diesch on 2009-11-18
A bit shorter:
```
xargs -i -- snmpget -v1 -c shutF10ke "{}" sysName.0 < text_file
```

---

### Post by kreggz on 2009-11-18
> **diesch said:**
> A bit shorter:
```
xargs -i -- snmpget -v1 -c shutF10ke "{}" sysName.0 < text_file
```

thanks

---

### Post by ghostdog74 on 2009-11-18
> **diesch said:**
> A bit shorter:
```
xargs -i -- snmpget -v1 -c shutF10ke "{}" sysName.0 < text_file
```

but doesn't leave room for extra programming, eg checking status and doing other conditional stuffs.

---

