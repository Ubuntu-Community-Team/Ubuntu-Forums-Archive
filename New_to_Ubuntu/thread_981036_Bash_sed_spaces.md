---
title: "Bash sed spaces"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-11-13
Why does the following code produce spaces.

```
#!/bin/bash

b=1
for ((a=1;a<7;a+=1));do
	c=`echo $b| sed 'a.png' | sed 's/ .png/.png/'`
echo $c
let "b=$b+1"
done
```

It makes the output

```

1 .png
2 .png
3 .png
4 .png
5 .png
6 .png

```

Why isn't it
```

1.png
2.png
3.png
4.png
5.png
6.png

```

---

### Post by porchrat on 2008-11-13
actually looks like a.png introduces a space or something.  If a is numeric you could try something like this instead:

sed 's/[0-9] .png/[0-9].png/g'

alternatively if that space is a tab you could try sed 's/[\t].png/.png/g'

Just suggestions, I'm not very knowledgable with sed and I'm not in front of a linux machine to play around with this.

---

