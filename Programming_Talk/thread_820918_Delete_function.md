---
title: "Delete function"
date: 2008-06-06
forum: Programming Talk
---

### Post by -grubby on 2008-06-06
OK, well I'm writing stuff to a text file based on user input, but I need a delete function. I was thinking something like this:

[php]
if string.find(var)!=-1
    del var
[/php]

However, I have no idea how I would actually delete the variable (in this case, var). I just used "del" as partly an example to what I'd really need to cut all instances of the var string from the whole file. Any ideas?

Oh, almost forgot. The language is Python

---

### Post by pmasiar on 2008-06-06
you cannot delete from outside text file. Read it in, and write to different text file only parts you want, then delete old and rename.

---

### Post by smartbei on 2008-06-07
I'm not exactly sure what you are looking for, but perhaps this will help:
```

string = 'abcdefghabcdefgh'
new_string = string.replace('ghab', 'WHATEVER')
print new_string

## or, to remove a substring from a whole string:
string = 'abcdefghabcdefgh'
new_string = string.replace('ghab', '')
print new_string

```

---

### Post by -grubby on 2008-06-07
Well, I meant like writing stuff to a text file, and being able to go back later and delete it by : searching for all strings that match it, <deleting/overwriting them somehow>

---

### Post by Can+~ on 2008-06-07
How to edit files in place:
[http://ubuntuforums.org/showpost.php?p=1858479&postcount=7](http://ubuntuforums.org/showpost.php?p=1858479&postcount=7)

In your case, you replace with ""

[PHP]import fileinput

for line in fileinput.FileInput("filename", inplace=True):
	line = line.replace(str(var), "").rstrip()
	print line
[/PHP]

---

