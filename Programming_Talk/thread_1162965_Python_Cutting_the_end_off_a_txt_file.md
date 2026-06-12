---
title: "Python: Cutting the end off a txt file"
date: 2009-05-18
forum: Programming Talk
---

### Post by gazmac on 2009-05-18
Hi,

Lets say I have a text file that looks like this 

```
interesting
interesting
very interesting
not interesting
not at all interesting
not even needed at all
just garbage

```

What I would like to do is read the text file and when I get to the line that starts "not interesting" it just deletes the rest of the file.

I can find the "not interesting" line using...

```

sourceText='[content]'				
for line in fileinput.FileInput("text.txt",inplace=1):
	line=line.strip()
	if line.startswith(sourceText):
		DO SOMETHING HERE TO CUT THE FILE
	else:
		print line
```

Any suggestions how I could delete everything from the found line to the end of the text file?

---

### Post by MeLight on 2009-05-18
exit the loop using the **break** statement

---

### Post by ghostdog74 on 2009-05-18
just another option
```

awk '/not interesting/{exit}1' file>newfile; mv newfile file

```

---

### Post by gazmac on 2009-05-18
Thanks guys,

I tried the break and it worked fine, here's the code for anyone even more of a beginner than me.

```

sourceText='not interesting'
for line in fileinput.FileInput("text.txt",inplace=1):
	line=line.strip()
	if line.startswith(sourceText):
		break
  	else:
     		print line
```

---

### Post by Bodsda on 2009-05-18
> **gazmac said:**
> Thanks guys,

I tried the break and it worked fine, here's the code for anyone even more of a beginner than me.

```

sourceText='not interesting'
for line in fileinput.FileInput("text.txt",inplace=1):
	line=line.strip()
	if line.startswith(sourceText):
		break
  	else:
     		print line
```

Interesting to see how other people achieve things. I would have gone about this a bit different. Heres what I would have done

```

count = 0
lines = open("infile").readlines()

for i in range(len(lines)):
    if lines[count].startswith("not"):
        break
    else: 
        print lines[count].strip()
    count += 1

```

Same result, different approach.

Bodsda

EDIT: TO the beginner this line may be confusing ```
if lines[count].startswith("not"):
``` 
So, an explanation for the beginners. The if statement will evaluate the conditional and if it returns True then it will execute its block of code e.g. break. but if it returns non-true, which it would if the line startswith anything other than not then it will run the else block

---

### Post by bobbocanfly on 2009-05-18
> **Bodsda said:**
> Interesting to see how other people achieve things. I would have gone about this a bit different.

Bit simpler/more Pythonic way of doing the same:

```

for line in open("infile"):
    if line.startswith("not"):
        break
     else:
        print line
```

---

### Post by Bodsda on 2009-05-18
> **bobbocanfly said:**
> Bit simpler/more Pythonic way of doing the same:

```

for line in open("infile"):
    if line.startswith("not"):
        break
     else:
        print line
```

bah, looks like my python-ic-ee-ism is off ever since i started learning C++

---

### Post by ghostdog74 on 2009-05-18
> **Bodsda said:**
> Interesting to see how other people achieve things. I would have gone about this a bit different. Heres what I would have done

[code]
count = 0
lines = open("infile").readlines()


except that it would be memory intensive when operated on a big file....therefore, to avoid such issues, using line by line iteration is still the "flexible" choice as it fits both situations.(small & big size files)

---

