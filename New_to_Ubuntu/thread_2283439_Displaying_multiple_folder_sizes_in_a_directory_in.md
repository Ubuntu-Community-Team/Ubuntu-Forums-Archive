---
title: "Displaying multiple folder sizes in a directory in megabytes"
date: 2015-06-22
forum: New to Ubuntu
---

### Post by dimethyl on 2015-06-22
Hello,
I have a lot of useless folders in a directory that I would like to get rid of.  However, there are some useful folders in the same directory that I want to keep, so I cannot simply throw all the folders away.  The only way I can tell if a folder is useful to me is by looking its size (the total of its contents) in megabytes.  Is there a way to display the size (the total of its contents) of all the folders in one directory in megabytes?

Thank You

---

### Post by nerdtron on 2015-06-22
I'm not sure of any GUI tools but it certainly possible on the command line:
```
 du -sch /home/folder/to/summarize/* 
```

That will show all contents and folder of the summarize folder into human readable sizes. You can replace the h with m if you want it to show exact megabytes.

Like this:
```
~$ du -sch /var/lib/dpkg/*
232K    /var/lib/dpkg/alternatives
4.0K    /var/lib/dpkg/arch
164K    /var/lib/dpkg/available
4.0K    /var/lib/dpkg/cmethopt
4.0K    /var/lib/dpkg/diversions
4.0K    /var/lib/dpkg/diversions-old
53M    /var/lib/dpkg/info
0    /var/lib/dpkg/lock
4.0K    /var/lib/dpkg/parts
4.0K    /var/lib/dpkg/statoverride
1.7M    /var/lib/dpkg/status
1.7M    /var/lib/dpkg/status-old
44K    /var/lib/dpkg/triggers
4.0K    /var/lib/dpkg/updates
57M    total


```

---

