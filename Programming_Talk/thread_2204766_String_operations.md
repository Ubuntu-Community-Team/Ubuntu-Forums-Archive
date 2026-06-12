---
title: "String operations"
date: 2014-02-10
forum: Programming Talk
---

### Post by geohei on 2014-02-10
Hi.

I have a bunch of files, where I would like to truncate the last 2 bytes (0d 0a) and replace them by 0a.
It's basically a string operation, but I didn't find any information on how to do that.

It should be something like ...

newfile = (oldfile,len(oldfile)-2) + "0a"

How shall I do that?

Thanks,

---

### Post by Dave_L on 2014-02-10
There are some packages in the repositories that make this easier:
dos2unix
tofrodos

---

### Post by The Cog on 2014-02-10
Don't know how to do it on only the last line of the file off the top of my head, although I 'm pretty sure you can use sed to only modify the last line. 
But there is a utility called dos2unix that will convert all line endings (0d0a to 0a) in a file.
```
sudo apt-get install dos2unix
man dos2unix
```

---

### Post by Bucky Ball on 2014-02-10
*Thread moved to **Programming Talk**.*

---

### Post by Vaphell on 2014-02-10
```
sed 's/\r$//'
```

> Don't know how to do it on only the last line of the file off the top of my head, although I 'm pretty sure you can use sed to only modify the last line. 

```
sed '[COLOR="#0000FF"]$[/COLOR]s/\r$//'
```

*-i *switch will change files in place

---

### Post by geohei on 2014-02-10
```
root@boxy:/media/raid-main/test# sed '$s/\r$/' < aaa.md5 > test.md5
sed: -e expression #1, char 7: unterminated `s' command
root@boxy:/media/raid-main/test# sed 's/\r$/' < aaa.md5 > test.md5
sed: -e expression #1, char 6: unterminated `s' command
```
Is there any possibility to to string operations more generalized, e.g. left($s,x), right($s,y), len($s), ...

---

### Post by Vaphell on 2014-02-11
my bad, i ate 1 / like a noob. Fixed.

yes, there is
```
$ while read -r ln; do echo "$ln"; echo "${ln: 0:5}"; echo "${ln: -5:5}"; done <<< $'abcdefghijklmnopqrstuvwxyz\nABCDEFGHIJKLMNOPQRSTUVWXYZ' 
abcdefghijklmnopqrstuvwxyz
abcde
vwxyz
ABCDEFGHIJKLMNOPQRSTUVWXYZ
ABCDE
VWXYZ

$ cut -c 10-15 <<< $'abcdefghijklmnopqrstuvwxyz\nABCDEFGHIJKLMNOPQRSTUVWXYZ' 
jklmno
JKLMNO

$ sed -r 's/^(.{5}).*/\1/' <<< $'abcdefghijklmnopqrstuvwxyz\nABCDEFGHIJKLMNOPQRSTUVWXYZ' 
abcde
ABCDE
$ sed -r 's/.*(.{5})$/\1/' <<< $'abcdefghijklmnopqrstuvwxyz\nABCDEFGHIJKLMNOPQRSTUVWXYZ' 
vwxyz
VWXYZ
```

learn 2 bash parameter expansion, cut and regex.

---

### Post by geohei on 2014-04-21
> **Vaphell said:**
> 
```
sed '$s/\r$//'
```
I did a typo. Works fine now. Sorry!

Something else (more bash related than sed).

I'd like to create a list of all *.md5 files with above mentioned modification.
```

root@ganymede:~/# sed '$s/\r$//' < *.md5
-bash: *.md5: ambiguous redirect
root@ganymede:~/# sed '$s/\r$//' < test.md5"
8137b27a378323da97ee0f27023de072 *test.mpg
```
*.md5 doesn't work.
A given filename works!

What's wrong with my line?

BTW ... I'll look later in detail into your reply from 11.02.2014. Thanks!

---

### Post by steeldriver on 2014-04-21
You don't need an input redirect (<) at all - sed will read, concatenate, and process a list of named files (not just standard input)

```

sed '$s/\r$//' *.md5

```

HOWEVER it will almost certainly not do what you want since $ really means 'last line of input' not 'last line of each file' i.e. it will only make the substitution on the last line of the last file in the *.md5 glob expansion. Probably what you need is a loop:

```

for file in *.md5; do '$s/\r$//' "$file"; done

```

**EDIT**: just realized you can use the -s ('separate') switch to make sed interpret $ to mean 'last line of each file'

```

sed **-s** '$s/\r$//' *.md5

```

The loop is probably safer if there are MANY (thousands of) files because of limits on max argument length.

---

### Post by geohei on 2014-04-21
> **steeldriver said:**
> ```

for file in *.md5; do sed '$s/\r$//' "$file"; done
sed **-s** '$s/\r$//' *.md5

```
The loop is probably safer if there are MANY (thousands of) files because of limits on max argument length.
Wow ... I'm impressed! Both methods work perfectly!
And you were right ... the first syntax only deals with the 'last line of input'.
But what do you mean with "... of limits on max argument length"?
Many thanks so far!

Next question. I'd like to ass the result to md5sum. This doesn't work. I don't understand the error message.
```
root@ganymede:~# for file in *.md5; do sed '$s/\r$//' "$file"; done -exec md5sum -c {} \;
-bash: syntax error near unexpected token `-exec'
```
Using an intermediate file works.
```
root@ganymede:~# for file in *.md5; do sed '$s/\r$//' "$file"; done > md5.md5
root@ganymede:~# md5sum -c md5.md5
...
```

... later ...

This works!
```
root@ganymede:~# for file in *.md5; do sed '$s/\r$//' "$file"; done | md5sum -c
...
```
Thanks for the help!

---

### Post by steeldriver on 2014-04-21
AFAIK only the **find **command has a -exec option like that

In this case, I think you can just **pipe **the output from sed to the standard input of md5sum i.e.

```

sed -s '$s/\r$//' *.md5 **|** md5sum -c --

```

---

