---
title: "calculate usage from file"
date: 2010-07-27
forum: Repositories &amp; Backports
---

### Post by learnbash on 2010-07-27
Hello folks,

i have a file courierimapuiddb that have contents like

```

1 1280206508 4  
1 1280206466.V805I169cM853838.xxx
2 1280207962.V805I16d5M343672.xxx
3 1280208055.V805I16d6M20816.xxx


```

1280206508 above means total size and its decreasing when file added in directory. when total size utilization >= 90% then i got notification that you have how many percent left space. It will read from first line to last line to get how much percent left.

I want to check above things under below all directories where that file "courierimapuiddb" exist.

```

/directory/name/

```

thanks.

---

### Post by RainCT on 2010-08-22
Did I understand you correctly, you want to find all files inside a particular directory which are called "courierimapuiddb"? If so, just `cd' into that directory and there you can run:

```

find -name 'courierimapuiddb'

```

If you want to know how much space a directory uses, you may also use:
```

du -h --max-depth=0 /directory/name

```

Finally, you can also see how much free space the partition inside which a directory resides has using:
```

df -h /directory/name

```

I hope some of this helps. If not, I fear you'll have to explain your problem in a more detailed way.

---

