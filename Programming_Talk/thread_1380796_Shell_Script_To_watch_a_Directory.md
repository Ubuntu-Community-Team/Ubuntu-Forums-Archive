---
title: "Shell Script To watch a Directory"
date: 2010-01-14
forum: Programming Talk
---

### Post by ivikas on 2010-01-14
Hello all,

         I have a windows share mounted on network to a linux computer,on which i am working.In there, i have got a folder called "inbox" and new messages will be put inside it or in a sub directory.All i need is a shell script that will watch my inbox for a new event and display a popup window showing "Pls check your inbox Now" through xmessage or gxmessage or any other variants.

So, i want to know how can i monitor my inbox or it's sub directories for new event?

Thanks in advance

---

### Post by MadCow108 on 2010-01-14
extremely primitive version:
```

prev=`du -s folder`;
while [ 1 ]; do
  cur=`du -s folder`;
  if [ "$cur" != "$prev" ]; then
    #do something
  fi;
  sleep 5
done

```

I remember a pretty niffty python script which this kind if thing in a much better and more flexible way somewhere in this forum, maybe search for it.

---

### Post by spupy on 2010-01-14
[http://projects.l3ib.org/trac/fsniper](http://projects.l3ib.org/trac/fsniper)
Monitors a folder and executes scripts for new files.

---

