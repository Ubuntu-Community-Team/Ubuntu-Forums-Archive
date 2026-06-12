---
title: "Looping problems"
date: 2014-03-28
forum: Packaging and Compiling Programs
---

### Post by Jimics on 2014-03-28
A hello to all the forum I'm new here c:

The very first of all sorry for my english :p It's not the first, the second or the twentieth time I come here but I finally registered c: Congrats and thanks for all to contribute in the forum ;)

Well so the problem is that; I'm starting on /bin/bash and I need to loop inside a loop while looping.\\:D/
What I mean is, the entire code is inside a while, and I need to loop inside a while on there, what I mean is:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]#!/bin/bash

while [ a -ge b ]; do[INDENT]while [ c -eq d ]; do[/INDENT]
[INDENT=2]while [ e -ne f ]; do[/INDENT]
[INDENT=2]done[/INDENT]
[INDENT]done[/INDENT]
done[/TD]
[/TR]
[/TABLE]

When I use only two, I usually do with "[[ ... ]]" and it works, but I cannot find how to loop again.
Thanks~

---

### Post by EddyDreizehn on 2014-03-30
Bash can't nested while loops like this. Other languages can this. In bash you have to create something like that: 

```

while [ ... ]
do 

var=`while [ ... ] ; do ; somestuff ; done`

done

```

Ehm, special note this: ` is not like ' 
The ` means, that the code inside can be run!

 :guitar:

---

### Post by Jimics on 2014-04-03
Well that's a problem...#-o  Then I will try the same on Java ...  Thanks for help \\:D/

---

### Post by steeldriver on 2014-04-03
This works fine for me

```

$ cat looploop.sh
#!/bin/bash

j=0
while [ $j -lt 3 ]; do
  i=0
  while [ $i -lt 5 ]; do
    printf "j = %d, i = %d\n" $j $i
    ((i++))
  done
  ((j++))
done

```

```

$ ./looploop.sh
j = 0, i = 0
j = 0, i = 1
j = 0, i = 2
j = 0, i = 3
j = 0, i = 4
j = 1, i = 0
j = 1, i = 1
j = 1, i = 2
j = 1, i = 3
j = 1, i = 4
j = 2, i = 0
j = 2, i = 1
j = 2, i = 2
j = 2, i = 3
j = 2, i = 4

```

IIRC bash 'while' loops implicitly *do *get executed as subshells - hence why 'exit' doesn't always do what people expect...

---

