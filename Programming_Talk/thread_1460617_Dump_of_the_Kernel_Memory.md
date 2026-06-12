---
title: "Dump of the Kernel Memory"
date: 2010-04-23
forum: Programming Talk
---

### Post by DBQ on 2010-04-23
Hi everybody. How can I create a dump of the kernel's memory? I just want the kernel memory, not the user space.

I am using Ubuntu 9.10.

Thank You

---

### Post by gzarkadas on 2010-04-23
Maybe (as root with sudo, of course) this will suit your needs (though I'm not sure, I don't do that kind of stuff yet :)):

```

cat /proc/kcore > <enter your dump destination file>

```From kernel's sources | fs | proc | kcore.c header:

>  [COLOR=Blue]*    fs/proc/kcore.c kernel ELF core dumper[/COLOR]


---

### Post by DBQ on 2010-04-25
Thank You! I will give it a try!

---

### Post by DBQ on 2010-04-25
I done some reading about /proc/kcore. However, it appears that this file contains both, the kernel and userpsace memory. I just want the kernel memory.

---

### Post by gzarkadas on 2010-04-26
Have a look then at the Redhat crash analysis utility: 
-- source/rpm: [http://people.redhat.com/anderson/](http://people.redhat.com/anderson/)
-- documentation: [http://people.redhat.com/anderson/crash_whitepaper/](http://people.redhat.com/anderson/crash_whitepaper/)
I feel its the right tool for you.

You may also want to take a look in this link that describes kdump: [http://www.mjmwired.net/kernel/Documentation/kdump/](http://www.mjmwired.net/kernel/Documentation/kdump/)

You can also generate a list of user processes addresses with this script:

```

#!/bin/bash

#License GPLv3+: GNU GPL version 3 or later <[http://gnu.org/licenses/gpl.html](http://gnu.org/licenses/gpl.html)>.
#This is free software: you are free to change and redistribute it.
#There is NO WARRANTY, to the extent permitted by law.

cd /proc

# generate ~/smaps.view with low-high address list of user processes
: > ~/smaps.view
for i in $(ls | grep -P '[[:digit:]+]') ; do
    cat ${i}/smaps | awk '(NR-1) % 12 == 0 {print $0}' | cut -c1-17 >> ~/smaps.view
done
# collapse contiguous address entries to one
awk 'BEGIN {
    FS = "-"
    OFS = "-"
}
NR == 1 {
    m_start = $1
    m_end = $2
}
NR > 1 {
    if ($1 == m_end)
        m_end = $2
    else
      {
        print m_start OFS m_end
        m_start = $1
        m_end = $2
      }
}
END {
    print m_start OFS m_end
}'  ~/smaps.view > ~/smaps.reduced

```and use it as an exclude guide when examining the kcore file. 

This is not exactly accurate, since during taking the dump and executing the commands above processes may be added or deleted depending of system's activity, but may be an alternative if the crash tools don't fit your needs.

Hope, something of these helps :).

---

