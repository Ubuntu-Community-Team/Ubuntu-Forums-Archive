---
title: "Awk ?"
date: 2012-04-20
forum: Programming Talk
---

### Post by Leifheit on 2012-04-20
Hello!

I am new to this forum so I hope this is the right place for posting.

I have a problem I am working on but im not sure if I am on the right track for the solution.

Basically speaking I want to extract a string at a certain position in a text file and insert it in another textfile again at a certain position.

I was thinking awk would be the right thing to use, but I am having trouble finding out how to do it :)

Would be really nice if some1 could post an example code for doing this. Other solutions than awk would be welcome, too!

Best regards,

Leif

---

### Post by iponeverything on 2012-04-20
Perl might be better suited for this task.  If I were going to go the awk route -- I extract the field like so:

```
cat first-file | awk '{print $3}' > extracted-field
```

where $3 is the third field.

Then I would use emacs to deposit extracted field into the first or list field position of the second file.Then I would use awk again to print out the fields in desired order..


Assumption:
- Consistent number of fields per line.

---

### Post by r-senior on 2012-04-20
> **Leifheit said:**
> Basically speaking I want to extract a string at a certain position in a text file and insert it in another textfile again at a certain position.
Could you clarify "a certain position"?

Is it one occurrence or multiples, are we talking fixed offsets within a line on specific line numbers or delimited by some text or tag?

Perhaps an example would help?

---

### Post by Habitual on 2012-04-20
```

cat x
Field1 Fielld2 Field3 Field4 Field5

cat x | awk '{print $1}'
Field1

cat x | awk '{print $2}'
Fielld2

cat x | awk '{print $3}'
Field3

cat x | awk '{print $4}'
Field4

cat x | awk '{print $5}'
Field5

```

"$n" are positional tokens.

HTH.

---

### Post by Vaphell on 2012-04-20
unnecessary cat, awk handles files just fine

---

### Post by iponeverything on 2012-04-20
> **Vaphell said:**
> unnecessary cat, awk handles files just fine

unnecessary comment ;)

there is more than one way to skin a cat.

---

### Post by Vaphell on 2012-04-20
true, there are 2: with and without the overhead ;-)

---

### Post by SeijiSensei on 2012-04-20
> **Leifheit said:**
> Basically speaking I want to extract a string at a certain position in a text file and insert it in another textfile again at a certain position.

As others have said, you need to tell us what you mean by a "certain position."  If it's something that can be selected by breaking up the line using a delimiter, then awk will do the job.  For a string at a specific column location, I'd end up using a programming language like Perl or PHP.

The delimiter in awk can be any arbitrary string; just designate it by using -F'string'.  

As for inserting into a new string, the obvious choice is sed, but again, you'll need to figure out how to determine the location.  Can you give us an example of the source and a target string?

---

### Post by Leifheit on 2012-04-24
Hello,

thanks for all the quick answers !
I will try to implement them and then report back :)
If it doesnt work here is an example of what I want to do:

I have on file for example called "Basics" containing information like these:


width 300
surface 1100
length1 200
...

I want to read out the numbers and then insert them into an .m4 file like this:

define(width, 300)
define(surface, 1100)
....

Line number and positioning in the line are always constant.
I want to do this so that i can just insert the numbers once in the file called "Basics" and then have them written into several different files without having to do this for each file.

Sorry I did not clarify this in the beginning ... I am still quite new to the programming stuff :/

Thanks a lot !

Leif

---

### Post by bregma on 2012-04-24
> **Leifheit said:**
> Hello,
I have on file for example called "Basics" containing information like these:


width 300
surface 1100
length1 200
...

I want to read out the numbers and then insert them into an .m4 file like this:

define(width, 300)
define(surface, 1100)
....

Would it be easier to just use a shell script?
```
#!/bin/sh

while read name value; do
  echo "define($name, $value)"
done < Basics
```
Redirect the output of echo above into your m4 file, or if necessary convert it into some sort of wacky **[FONT="Courier New"]sed[/FONT]** script.  Using **[FONT="Courier New"]awk[/FONT]** to parse that input file is overkill.

---

### Post by codemaniac on 2012-04-24
> **iponeverything said:**
> ```
cat first-file | awk '{print $3}' > extracted-field
```


You have just won an useless use of cat award. ;)
[http://www.cyberciti.biz/tips/shellshell-scripting-useless-use-of-cat-award.html](http://www.cyberciti.biz/tips/shellshell-scripting-useless-use-of-cat-award.html)

---

