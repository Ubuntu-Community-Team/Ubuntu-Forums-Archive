---
title: "Sed command"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by toad3000 on 2013-02-22
Does anyone know what this sed commands works. I keep looking at the man pages but I can't seem to find any info. 

```
sed -e 'sx/..../..../xx
```

Let's just say .... and .... are some random words. If for say those random words are put in what should this sed command do?

Thanks A lot!:-)

---

### Post by ntzrmtthihu777 on 2013-02-22
> **toad3000 said:**
> Does anyone know what this sed commands works. I keep looking at the man pages but I can't seem to find any info. 

```
sed -e 'sx/..../..../xx'
```Let's just say .... and .... are some random words. If for say those random words are put in what should this sed command do?

Thanks A lot!:-)
The -e is not needed, it is assumed with one expression, and don't forget to close the '. twould be easy to test, just make a bs file with said word and feed it through sed.

---

### Post by DiabolicalClaptrap on 2013-02-22
The sed command replaces text in a file. i.e.:

Basketball + PoI - 2/28 @ 9:00 pm
Other shows + PoI - 3/7 @ 9:00 pm
PoI - 3/14 @ 9:00 pm

If I wanted to change those times, you'd type

sed 's/9:00/10:00/' poi-schedule.txt > poischedule2.txt

This would create another text file called poischedule2.txt, with the specified changes

You can also use this to copy any lines to another text file by typing: sed -n '/Other shows/p'  poi-schedule.txt > other-stuff.txt

Where Other shows is the line you want copied.

---

### Post by Hadaka on 2013-02-22
Hi here is an example ..

sed = stream editor    (data stream)
sed...find and replace

```
find 'substitute/fieldA/fieldB/global' input_file 
```
```
sed 's/fieldA/fieldB/g' input_file > output_file 
```
```
echo toad > toad_file 
```
```
cat toad_file 
```
```
toad 
```
#Find the word **toad** in file **toad_file** replace it with **toad3000** and write it to **newtoad_file**
 ```
sed 's/toad/toad3000/g' toad_file > newtoad_file 
```
```
cat new_toadfile 
```
```
toad3000 
```
hope that helps.

---

### Post by papibe on 2013-02-22
Hi toad3000.

What sed does has been pretty well explained so far. Do you still have questions?

The command you posted has some tricks on it. Basically is equivalent to:
```
sed 's/\/....\/....\///'
```
When your expression contains several slashes, sed allows you to use another character for separating the arguments.

This is the same one but using underscore:
```
sed 's_/.../.../__'
```
And in your case using the 'x':
```
sed 'sx/.../.../xx'
```
The command itself looks for the first expression on a line (/..../..../) and replaces it with nothing (a delete in practice).

Note that '.' means any character. This would be examples of input text that would match the expression:
```
/hola/take/
/ab12/0fg6/
```
Let's take this input file example (input.txt)
```
**$ cat input.txt **
this line/should not/be touched.
if something should be deleted is this /1234/5678/
this not abcd/efgh
this not /0000/12345/
this should be /word/this/, but the 2nd appearance should not /word/this/
a weird example that also should be delete: ///////////

**$ sed 'sx/..../..../xx' input.txt **
this line/should not/be touched.
if something should be deleted is this 
this not abcd/efgh
this not /0000/12345/
this should be , but the 2nd appearance should not /word/this/
a weird example that also should be delete: 


```
Does that help? Let us know how it goes.
Regards.

---

