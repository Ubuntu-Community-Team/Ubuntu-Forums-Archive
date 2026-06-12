---
title: "Parse files with bash?"
date: 2007-09-10
forum: Programming Talk
---

### Post by Krijk on 2007-09-10
I want to parse logfiles which have multiple lines for single entries to single line entries. 
I know how to get the required data with awk, but I don't know how to connect them with each other. The seperate entries are usually seperated by an empty line. Does anybody have some suggestions how to do this?

**Example 1**

something
1	else
2	other
3	first

otherthing
1	apple
2	coconut
3	pear

*to output*

something	else  
something	other
something	first
otherthing	apple
otherthing	coconut
otherthing	pear

**Example 2**

Item1
2007 Sep 10 
Proces 12345
Has done something

Item2
2007 Sep 10 
Proces 12378
Has done something else

*to output *

Item1 ; 2007 Sep 10 ; Proces 12345 ; Has done something
Item2 ; 2007 Sep 10 ; Proces 12378 ; Has done something else

---

### Post by ghostdog74 on 2007-09-10
where's your awk code.?

---

### Post by nanotube on 2007-09-10
starting from the input you have stated (multiline items, separated by empty lines), here's how i'd go about it with python:

```

f = open('yourinputfilename.txt','r')
text = f.read().split('\n\n')
text2 = [item.strip().replace('\n',' ; ') for item in text.split('\n\n')]
f2 = open('youroutputfile.txt','w')
f2.write('\n'.join(text2))
f.close()
f2.close()

```

hope that helps. :)

---

### Post by Krijk on 2007-09-11
> **nanotube said:**
> starting from the input you have stated (multiline items, separated by empty lines), here's how i'd go about it with python:

```

f = open('yourinputfilename.txt','r')
text = f.read().split('\n\n')
text2 = [item.strip().replace('\n',' ; ') for item in text.split('\n\n')]
f2 = open('youroutputfile.txt','w')
f2.write('\n'.join(text2))
f.close()
f2.close()

```

hope that helps. :)

So in bash I can probablyu achieve the same with sed, but then I'll have to replace the /n/n first with an identifier to mark the item-end?

---

