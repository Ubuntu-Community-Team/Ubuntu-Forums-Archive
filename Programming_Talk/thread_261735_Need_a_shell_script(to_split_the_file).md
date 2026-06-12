---
title: "Need a shell script(to split the file)"
date: 2006-09-20
forum: Programming Talk
---

### Post by carteris21 on 2006-09-20
Hi,
my someone could write sh script, that splitting file in n bytes portions, the same what do split command, but without split command.
I can't find any command which can read some interval of bytes from the file.

---

### Post by LotsOfPhil on 2006-09-20
Why can't you use split? Would it be okay to split it up every *n* lines?

---

### Post by carteris21 on 2006-09-21
It's my task :). I think it would be ok, can you write an example.

---

### Post by amo-ej1 on 2006-09-21
use dd (man dd)

```

dd if=INPUTFILE of=OUTPUTFILE bs=BLOCKSIZE count=CNT skip=SKIP

```

reads CNT blocks of BLOCKSIZE large rom INPUTFILE and write them to OUTPUTFILE skipping SKIP times BLOCKSIZE from the beginning.

---

### Post by TheMono on 2006-09-21
Irrelevant Comment: Nice avatar, amo-ej1... Very cool.

---

### Post by LotsOfPhil on 2006-09-21
> **carteris21 said:**
> Hi,
my someone could write sh script, that splitting file in n bytes portions, the same what do split command, but without split command.
I can't find any command which can read some interval of bytes from the file.

Well, here is what I have. It isn't exactly what you want, but should point you on the right track.

```

#!/bin/sh
#
# Split a file
#
if [ $# -lt 2 ]
then
echo "Syntax is ./lineSplit.sh <file name> <split line number>"
echo "Example: ./lineSplit.sh bp.out 25000"
exit 1
fi
file=$1
split=$2
lineMax=`wc -l $file | awk '{print $1}'`
counter=1
i=1
while [ $counter -lt $lineMax ]
do
  split1=`expr $counter`
  split2=`expr $counter + $split - 1`
  sed -n "$split1","$split2"p $file > fragment."$i"
  i=`expr $i + 1`
  counter=`expr $split2 + 1`
done
                                                                                
sed -n "$counter",\$p $file > fragment."$i"

```

Hmm, what needs explanation... 
You can chuck the if statement at the beginning if you want. Just set "file" and "split" to what you want. 
I think there should be a better way to get the value of lineMax, but I am blanking on it.

If anything is unclear about it, or if you can improve it for me, let me know.

---

### Post by carteris21 on 2006-09-21
Thank you :).

---

