---
title: "rename files using path to file as new filename"
date: 2009-07-24
forum: Programming Talk
---

### Post by monkeyking on 2009-07-24
HI igot alot of files like

[PHP]
path1/res/file.txt
path2/res/file.txt
path3/res/file.txt
[/PHP]

Is there some easy way of renaming these to

[PHP]
path1.file.txt
path2.file.txt
path3.file.txt
[/PHP]

thanks

---

### Post by ghostdog74 on 2009-07-24
i will assume those are in a file, not the actual file names, because "/" is illegal for a file name.

```


awk '{gsub("/","."}1 ' file

```

---

### Post by smartbei on 2009-07-24
After you rename them, where do you want them to be?

@ghostdog - the /is in the file path.

---

### Post by monkeyking on 2009-07-24
Well actually I want to move them,
to a different folder.

so what I want to do is a command like


```

mv path1/res/file.txt /out/path1.file.txt
etc

```

---

### Post by monkeyking on 2009-07-24
I ended up doing something like

```

for i in $(ls /path/to/*.txt); do
 bas=`basename $i`
    pre=`ls $i |cut -f2 -d'/'`
    newnams=$pre.$bas 
    mv $i $newnams

done


```

this uses the second dirname as prefix for the files

---

