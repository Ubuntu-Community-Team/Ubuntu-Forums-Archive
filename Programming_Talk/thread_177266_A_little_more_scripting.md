---
title: "A little more scripting"
date: 2006-05-16
forum: Programming Talk
---

### Post by musther on 2006-05-16
In the thread:

[http://ubuntuforums.org/showthread.php?t=170129]("http://ubuntuforums.org/showthread.php?t=170129")

I asked for help making a script to do multiple find/replace operations on a text file based on a config file with one line per operation.

The eventual bit of script we came up with was this:

```
for x in `cat ttspd` 
do
        f1=`echo $x | cut -d\' -f2`
        f2=`echo $x | cut -d\' -f4`
        sed -i -e s/\\\<$f1\\\>/$f2/gI text.txt
done
```

The lines in the config file are like this:

```
'foo'='bar'
```

So, I would like to put comments in the config file 'ttspd' in the usual linuxy fasion '# comment', is there an easy way to make this loop ignore lines starting with #?

Cheers!

---

### Post by daneel_olivaw on 2006-05-16
should be something like that:

```
for x in `cat ttspd | grep -v "#"` 
do
        f1=`echo $x | cut -d\' -f2`
        f2=`echo $x | cut -d\' -f4`
        sed -i -e s/\\\<$f1\\\>/$f2/gI text.txt
done
```

assuming your original script works by itself :P

PS: Lol, it states "0" replies while showing this very reply of mine.

---

