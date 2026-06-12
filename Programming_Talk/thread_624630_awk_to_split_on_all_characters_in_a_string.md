---
title: "awk to split on all characters in a string"
date: 2007-11-27
forum: Programming Talk
---

### Post by paddl3r on 2007-11-27
Dear Forum,

I am struggling to write a block of awk to take a string such as: 

blah

the split on all characters and print them out:

b
l
a
h

The closest I've got is this:

#!/usr/bin/awk -f
BEGIN {
string="blah";
n=split(string,array,"[A-Z]|[a-z]");
for (i=1;i<=n;i++) {
print(array[i]);
}
exit;
}

It splits on each character but prints a blank line for each of the characters. Any suggestions would be welcome. 

Cheers,
paddl3r

PS I don't have nawk or gawk on this system. My boss has insisted it slots in with an existing suite of awk scripts rather than allowing me to use perl :(

---

### Post by LaRoza on 2007-11-27
I don't know awk, but tried to see how it works, by trial and error.

I found that array[] is not printable, at any index. It is my guess that the characters of the string are not in the array.



```

#! /usr/bin/python

name = raw_input()

for i in name:
    print i

```

You can't use Python either?

---

### Post by paddl3r on 2007-11-27
python, ruby... unfortunately not

---

### Post by LaRoza on 2007-11-27
```

#!/usr/bin/awk -f
BEGIN {
string="blah";
n=split(string,array,"");
for (i=1;i<=n;i++) {
print(array[i]);
}
exit;
}

```

I don't know why it works, but trial and error.

I need to learn awk, I hate being right and not knowing why.

---

### Post by paddl3r on 2007-11-27
Thanks for the post but sorry that prints same as the input string on my system:

blah

I tried "" initially thinking it would work but didn't.

---

### Post by LaRoza on 2007-11-27
```

 ./c.awk
b
l
a
h

```

There is no space in the "". If there is a space, it prints the string.

---

### Post by geirha on 2007-11-27
you can also use sed
```
string="blah"
echo -n $string | sed 's/./&\n/g'
```

Edit: Though reading a bit closer, that's not an option anyway :/

---

### Post by LaRoza on 2007-11-27
> **geirha said:**
> you can also use sed


Unfortunately, the boss wants it the way the boss wants it.

---

### Post by ghostdog74 on 2007-11-27
awk (and sed) are such basic and essential tools in *nix you should get to know them better
```

s="blah"
echo $s | awk 'BEGIN{FS=""}{for(i=1;i<=NF;i++)print $(i)}'

```
or 
```

s="blah"
echo $s | awk 'BEGIN{FS="";OFS="\n"}{$1=$1}1'

```
output
```

# ./test.sh
b
l
a
h


```

---

