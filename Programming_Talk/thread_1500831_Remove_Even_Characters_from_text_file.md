---
title: "Remove Even Characters from text file"
date: 2010-06-03
forum: Programming Talk
---

### Post by mbstrlbstr on 2010-06-03
I have a list with random characters inserted in between each relevant character. I need to remove the random characters. I have limited experience with scripting and such, so go easy on me!
Thanks,
Shaun

---

### Post by stylishpants on 2010-06-03
Here's a little ruby one-liner that throws out every second character on each line.
```

bob@cob:~$ echo -e "a1b2c3\nd4e5g6\n\nh7i8j9" > file
bob@cob:~$ cat file
a1b2c3
d4e5f6

g7h8i9
bob@cob:~$ ruby -e 'ARGF.readlines.each do |line| line.chars.each_slice(2){|arr| print arr[0]}; end' file
abc
def

ghi

```

Whether this is a usable solution for you depends on your input data, it would be useful if you posted a representative sample.

---

### Post by mbstrlbstr on 2010-06-03
Thanks for that. I don't know if I have ruby installed on here or not. I have run some python and perl scripts recently, but not ruby. Below is an example of what I'm talking about

```
sahdatuhnemycwac
adnhdornexwz
jpulidlweqthtbex
```

If the script was run, I would want it to look like

```
shaunmca
andrew
juliette

```

Thanks!

---

### Post by trent.josephsen on 2010-06-03
```
sed -e 's/\(.\)./\1/g'
```

I didn't post it immediately because it treats newlines differently from other characters, but that seems to be o.k.

---

### Post by mbstrlbstr on 2010-06-03
Is that python?

---

### Post by kaibob on 2010-06-03
I put the words from your post in a file named wordlist.txt and used bash parameter expansion:

```
#!/bin/bash

while read word ; do
  for (( i=0 ; i<=${#word} ; i=i+2 )) ; do
    echo -n ${word:${i}:1}
  done
  echo
done < wordlist.txt
```

---

### Post by mbstrlbstr on 2010-06-03
@trent.josephsen
I tried that, and it removed the wrong characters?
Maybe if I inserted a character in front of every line, it would work then?

@kaibob
I entered it like this in my console

cat file.txt | wordscript

and it ins't sure what to do with the wordscript file?

---

### Post by mbstrlbstr on 2010-06-03
Never mind, I changed the code to start at bash script to start at 1 instead of 0. It worked great!

---

### Post by kaibob on 2010-06-03
> **mbstrlbstr said:**
> @kaibob
I entered it like this in my console

cat file.txt | wordscript

and it ins't sure what to do with the wordscript file?
I have modified my earlier post to make things clearer. The words being manipulated are in the file named wordlist.txt. This text file has to be in the current directory, or you have to provide a path to this file. Then, in a terminal, just enter the name of the script and nothing else.

---

### Post by mo.reina on 2010-06-04
python 3:
```

f = open('worldlist.txt').readlines()
print([x[::2].replace('\n', '') for x in f])
```

for version 2.6 or below:
```
f = open('worldlist.txt').readlines()
print [x[::2].replace('\n', '') for x in f]
```

---

### Post by wmcbrine on 2010-06-04
> **mo.reina said:**
> print [x[::2].replace('\n', '') for x in f]I don't think that does quite what you want.

How about this?

```
for line in file('worldlist.txt'):
    print line.rstrip()[::2]
```

---

### Post by mo.reina on 2010-06-04
```
>>> f = open('wordlist.txt').readlines()
>>> print [x[::2].replace('\n', '') for x in f]
['shaunmca', 'andrew', 'juilette']
>>> 

```

isn't that what the OP wanted?

```
mo@mo-laptop:~/python/gui$ cat wordlist.txt 
sahdatuhnemycwac
adnhdornexwz
jpulidlweqthtbex

```

---

### Post by wmcbrine on 2010-06-05
> **mo.reina said:**
> isn't that what the OP wanted?I think the OP wanted

```
shaunmca
andrew
juilette
```


not

```
['shaunmca', 'andrew', 'juilette']
```

---

### Post by schauerlich on 2010-06-05
```
>>> print "\n".join(x.strip()[::2] for x in open("wordfile.txt", "r").readlines())
shaunmca
andrew
juilette

```

Also: obvious homework is obvious

---

### Post by wmcbrine on 2010-06-05
Yeah, I kinda assumed homework, which is why I didn't answer initially. Then again, the OP didn't specify a language.

I think .strip() might be overzealous here (what if there are lines with leading spaces to preserve?), readlines() is not needed, and mode "r" is not needed.

```
print '\n'.join(line.rstrip()[::2] for line in file('wordfile.txt'))
```

---

