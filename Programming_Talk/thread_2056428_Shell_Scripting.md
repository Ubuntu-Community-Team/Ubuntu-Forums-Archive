---
title: "Shell Scripting"
date: 2012-09-11
forum: Programming Talk
---

### Post by rohit verma on 2012-09-11
How can we replace HTML entities with their respective symbols in text file.
eg- "&lt;" with "<" or any other...
Actually i dont want to maintain list.

---

### Post by codemaniac on 2012-09-11
> **rohit verma said:**
> How can we replace HTML entities with their respective symbols in text file.
eg- "&lt;" with "<" or any other...
Actually i dont want to maintain list.

Hello Rohit ,

Can you please post here a snippet of you input file .
So that we can understand your requirement better ?

Regards ,
codemaniac

---

### Post by aromo on 2012-09-11
I'd use sed.  Run:
man sed

---

### Post by SeijiSensei on 2012-09-11
> **rohit verma said:**
> How can we replace HTML entities with their respective symbols in text file.
eg- "&lt;" with "<" or any other...
Actually i dont want to maintain list.

I have no idea what that last sentence means, but I'd use sed, too.

```
sed 's/&lt;/</g' < inputfile > outputfile
```

To do all the symbols you could either pipe the all sed commands together, or apply them one at a time keeping the results in a temporary file.

If you know PHP, you could write a PHP script that runs from the command prompt and uses [htmlentitydecode()](http://php.net/manual/en/function.html-entity-decode.php) to translate from entities to their actual character representations.

---

### Post by rohit verma on 2012-09-12
Thanks buddies!

Codemaniac, below is the sample text from input file :
This is a simple expression 5 &gt; 4 &amp; 3 &#60; 4.

and below is the expected output.
This is a simple expression 5 > 4 & 3 < 4.
  
there can be any html entitiy, thats the complexity....

---

### Post by Lars Noodén on 2012-09-12
You could do it with a very short perl script:

```

#!/usr/bin/perl

use HTML::Entities;

while ( <> ) {
  print decode_entities($_),
}

```

It reads stdin and decodes any HTML entities it finds, sending the output to stdout.

```

./decode.pl < inputfile > outputfile

```

[CPAN](http://search.cpan.org/~gaas/HTML-Parser-3.69/lib/HTML/Entities.pm) to the rescue.

---

### Post by spjackson on 2012-09-12
PHP and Perl have already been mentioned, if you have these. Python also has a function in its cgi package, and I expect many other languages do too. You are spoilt for choice.

Alternatively, there's a standalone program "recode" that will do it, but you would almost certainly need to install it.
```

$ echo 'This is a simple expression 5 &gt; 4 &amp; 3 < 4.' | recode html..ascii
This is a simple expression 5 > 4 & 3 < 4.

```

---

### Post by trent.josephsen on 2012-09-12
Quicker Perl version:

```
$ perl -MHTML::Entities -ne 'print decode_entities($_)' <infile >outfile
```

---

### Post by Lars Noodén on 2012-09-12
> **trent.josephsen said:**
> Quicker Perl version:

```
$ perl -MHTML::Entities -ne 'print decode_entities($_)' <infile >outfile
```


LOL.  That one-liner made my day. :)

---

### Post by trent.josephsen on 2012-09-12
Lol, just thought I'd add it since the original question was about shell scripting and the OP might not be enthusiastic about creating a separate Perl script. Then again, I do love one-liners... :)

---

### Post by rohit verma on 2012-09-12
Thanks a lot buddies... :)

cant belive it could be done so easily..
i mean, such utility are already available....

---

### Post by afulldeck on 2012-09-12
> **trent.josephsen said:**
> Quicker Perl version:
 
```
$ perl -MHTML::Entities -ne 'print decode_entities($_)' <infile >outfile
```
 
Larry Walls invention never ceases to amaze .....

---

