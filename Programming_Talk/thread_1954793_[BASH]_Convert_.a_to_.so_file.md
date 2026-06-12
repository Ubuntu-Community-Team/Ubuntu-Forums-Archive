---
title: "[BASH] Convert .a to .so file"
date: 2012-04-08
forum: Programming Talk
---

### Post by tcf38012 on 2012-04-08
Hello

I've made a bash script to convert a static library (.a file) to a shared library (.so file)

Here it is:

```

#!/bin/bash
tmp=`echo $RANDOM$RANDOM$RANDOM`
current_dir=`pwd`
args0="$1"
args1="$2"

helpmeplease()
{
echo "a2so <a> <so>"
}

if [ -z $args0 ]; then
#    echo "good" > /dev/null
#else
    helpmeplease
    exit 1
fi

if [ -z $args1 ]; then
#    echo "goodette" > /dev/null
#else
    helpmeplease
    exit 1
fi

mkdir -p /tmp/$tmp
cp -R ${args0} /tmp/$tmp/$tmp
cd /tmp/$tmp
ar -x $tmp
gcc -shared *.o -o $tmp.so
cd $current_dir
cp -R /tmp/$tmp/$tmp.so $args1
rm -R /tmp/$tmp

```ENJOY!!!

---

### Post by roelforg on 2012-04-08
you mean the other way around right?
Right???
Because .a is static and .so is shared

---

### Post by tcf38012 on 2012-04-08
> **roelforg said:**
> you mean the other way around right?
Right???
Because .a is static and .so is shared

Yes thanks

Enjoy!!!:popcorn:

---

### Post by roelforg on 2012-04-08
maybe use mktemp?
outputs a temp file on std out
example for use:
```

temp=`mktemp`
echo $temp
echo "frist line">$temp
echo "scnd line">>$temp
cat $temp
rm $temp

```

---

### Post by tcf38012 on 2012-04-08
> **roelforg said:**
> maybe use mktemp?
outputs a temp file on std out
example for use:
```

temp=`mktemp`
echo $temp
echo "frist line">$temp
echo "scnd line">>$temp
cat $temp
rm $temp

```

That Makes an empty file, not a folder :lolflag:

Any thing else that I should improve?

---

