---
title: "Shell variable in Linux is reset after while loop"
date: 2010-06-04
forum: Programming Talk
---

### Post by huangyingw on 2010-06-04
Hello,
	I had following code:
```

	#! /bin/bash
check_file=/root/disk_list.txt
result=1
cat $check_file | while read file ; do
	result=0
  echo ${result}
done
echo ${result}

```
	the variable result is expected to be set to value 0 in while loop, while after the while loop, its value is reset to the original value 1.
	While if I use for loop instead of while loop, the curious reset phenomenent would not occur.
	Could someone explain this?
	What's the difference between for and while loop?

---

### Post by geirha on 2010-06-04
[http://mywiki.wooledge.org/BashFAQ/024](http://mywiki.wooledge.org/BashFAQ/024)

---

### Post by huangyingw on 2010-06-04
> **geirha said:**
> [http://mywiki.wooledge.org/BashFAQ/024](http://mywiki.wooledge.org/BashFAQ/024)

thanks first, I am reading.

---

### Post by gmargo on 2010-06-05
Taking the first suggestion (useless use of cat) from that helpful FAQ, the simplest fix is probably:

```

#! /bin/bash
check_file=/root/disk_list.txt
result=1
while read file ; do
        result=0
        echo ${result}
done < $check_file
echo ${result}

```

---

### Post by huangyingw on 2010-06-10
> **gmargo said:**
> Taking the first suggestion (useless use of cat) from that helpful FAQ, the simplest fix is probably:

```

#! /bin/bash
check_file=/root/disk_list.txt
result=1
while read file ; do
        result=0
        echo ${result}
done < $check_file
echo ${result}

```
Yes, I have tried this simplest fix, and it works, thank you.

---

