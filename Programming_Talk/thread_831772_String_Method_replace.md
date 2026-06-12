---
title: "String Method replace"
date: 2008-06-17
forum: Programming Talk
---

### Post by Captain_Riker on 2008-06-17
Hello there,

sorry to bother you with a question(the first one) which might be easy to answer:

I'm using the following code to search for lines in a file containing the word 'IDENTIFIER'. If found then it should add a Comment to the first Word of the line(which is known). In short, it should comment out certain lines in a file containing a certain word:

```

readin = open(infile, 'r')
writeout = open(infile, 'w')
lines = readin.readlines()
for line in lines:
    if line.find('INDETIFIER') != -1:
        print line
        writeout.write(line.replace('FIRSTWORD', '#FIRSTWORD'))
readin.close
writeout.close

```

My first Question now is: Can it be that I, in any case, have to use a temp file for output and rename it afterward? That I can not write directly to the input file? As long as I let python write the changes to sys.stdout everything works as supposed. Letting Python write the changes to the same file I read it from, simply deletes every single line in the file.

The second Question would be:

I'm thinking about going another way. If I want to have a module for a more general purpose, the task would be to 'insert' a sign/symbol/char on the first position of a line identified by a keyword where I do not know the first word of the line!

As to iterate over the file, using find on the keyword and increasing a counter. And then insert the symbol to the first position using the line number to identify the line. This way I don't need to know the first word. How to extract the line by number is easy using linecache.getline().

But how to insert (or append) the symbol?

Any help is appreciated, so thanks in advance . . .

---

### Post by ghostdog74 on 2008-06-17
> **Captain_Riker said:**
> 

My first Question now is: Can it be that I, in any case, have to use a temp file for output and rename it afterward? That I can not write directly to the input file? As long as I let python write the changes to sys.stdout everything works as supposed. Letting Python write the changes to the same file I read it from, simply deletes every single line in the file.

check out the fileinput module with the inplace option.

---

### Post by Captain_Riker on 2008-06-17
```

for line in fileinput.input('FILENAME', 1):
	print line
	if line.find('KEYWORD') != -1:
		line.replace('FIRSTWORD', '#FIRSTWORD')

```

Hmm, yes and no. But I guess that I'm missing something. It iterates over the lines and literally replaces the lines. ()
Leaving blank lines where the line was and inserts the line in buffer after the blank one. So it alters the layout of file pretty heavy. But as I said before, I'm missing something. But what . . .? ;-)

Ah, and the replace does not work that way. No clue why either . . .

---

### Post by Martin Witte on 2008-06-17
> **Captain_Riker said:**
> My first Question now is: Can it be that I, in any case, have to use a temp file for output and rename it afterward? That I can not write directly to the input file? As long as I let python write the changes to sys.stdout everything works as supposed. Letting Python write the changes to the same file I read it from, simply deletes every single line in the file.

With a mechanism like this you have to use during the replace operation a different file to write to than the one you read from indeed.
> **Captain_Riker said:**
> The second Question would be:

I'm thinking about going another way. If I want to have a module for a more general purpose, the task would be to 'insert' a sign/symbol/char on the first position of a line identified by a keyword where I do not know the first word of the line!

As to iterate over the file, using find on the keyword and increasing a counter. And then insert the symbol to the first position using the line number to identify the line. This way I don't need to know the first word. How to extract the line by number is easy using linecache.getline().

But how to insert (or append) the symbol?

You could do something like
```
#!/usr/bin/env python
import sys
look_for = 'PATH'
for line in open('.profile'):
    if line.find(look_for) > -1:
        print >> sys.stderr, '#%s' % line
    else:
        print >> sys.stderr, line
```
where you replace sys.stderr by a temporary file open for writing

---

