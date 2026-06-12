---
title: "write a function that ignores ',' using Python"
date: 2008-08-30
forum: Programming Talk
---

### Post by s1300045 on 2008-08-30
I am writing a function that will read in a string, dice it according to the commas, and store the result into a list.


```

def read(string):
	a = []
	tmp = ''
	for i in string:
		if i == ',':
			a[len(a):]= [tmp]
			tmp = ''
		tmp = tmp + i
	return a
```

&#12288;&#12288;For now it's only reading things before the first comma into the list, can someone point out what I am doing wrong here? I just started learning Python on my own. It would be great if I can find some tutoring here. Thanks!

---

### Post by Wybiral on 2008-08-30
Why not use the standard split function?

```

print "this,is,comma,separated".split(',')

```

---

### Post by s1300045 on 2008-08-31
I thought reinventing wheels could help me get familiar with Python, but hack, I didn't even know there's a split function! I'd still like to know what I am doing wrong though.

Thanks for answering!

---

### Post by ghostdog74 on 2008-08-31
> **s1300045 said:**
> I thought reinventing wheels could help me get familiar with Python, but hack, I didn't even know there's a split function! I'd still like to know what I am doing wrong though.

Thanks for answering!


without the split function, you can always use string fundamentals. The following use simple slicing and indexing.
```

s="one,two,three"
while 1:
    if "," in s:
        ind = s.index(",")
        print s[:ind]
        s=s[ind+1:]        
    else:
        if s : print s
        break

```

---

### Post by Quikee on 2008-08-31
A little bit modified and it works fine:
[PHP]def read(string):
	a = []
	tmp = ''
	for i in string:
		if i == ',':
			a.append(tmp)
			tmp = ''
		else:
			tmp = tmp + i
	a.append(tmp)
	return a

print read("a,b,c,ddd")
[/PHP]

Add to the end of a list with append.

---

