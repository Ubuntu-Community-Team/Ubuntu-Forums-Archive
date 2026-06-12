---
title: "marco, mate update installation problem"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by ann123 on 2012-10-08
update manager will not download and install marco, mate updates a message appears and states "untrusted site" and has red circle with black line through the circle. Thank you.

---

### Post by NikTh on 2012-10-08
Hi , 

please open a terminal [Ctrl]+[Alt]+[t] and copy-paste from here bellow commands 

```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
```
sudo apt-get update
``` 

Post FULL results and put the results between the brackets **[noparse]```
Here
```[/noparse]** so can be readable.

Thanks

---

