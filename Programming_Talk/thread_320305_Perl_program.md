---
title: "Perl program"
date: 2006-12-17
forum: Programming Talk
---

### Post by 008325 on 2006-12-17
i have a text file 

in each one line , it include the email address and name

one line = one user , here is example

```


01 ABC aaa@aaa.com
02 CDE bbb@bbb.com ccc@ccc.com
03 FGH 123@123.com 123@456.com 789@123.com


```


each line maybe including many  email

i wrote a perl

```
while (<DAT1>) {

($email)=($_ =~ /([\w\-]+\@[\w\-]+\.[\w\-]*)/);

print $email;

}
```

however , it just get the first email not all the email per line, 

how can i solve this program ?

i tried use array @email , nothing has change :-k :-k

---

### Post by po0f on 2006-12-17
008325,

```
[FONT="Courier New"]#!/usr/bin/python

import sys

email_addresses = []

def main():
    fd = open(sys.argv[1])
    ab = fd.readlines()
    fd.close()

    for contact in ab:
        [email_addresses.append(email.strip()) for email in contact.split() if "@" in email]

    print "\n".join(email_addresses)

if __name__ == "__main__":
    main()[/FONT]
```

Save that to whatever.py and just run it with the text file in the same directory as the script:
```
[FONT="Courier New"]$ python whatever.py file[/FONT]
```

[EDIT]

Was missing a closing parens, only one cup of coffee so far this morning.  :rolleyes:

---

### Post by 008325 on 2006-12-17
> **po0f said:**
> 008325,

```
[FONT="Courier New"]#!/usr/bin/python

import sys

email_addresses = []

def main():
    fd = open(sys.argv[1])
    ab = fd.readlines()
    fd.close()

    for contact in ab:
        [email_addresses.append(email.strip() for email in contact.split() if "@" in email]

    print "\n".join(email_addresses)

if __name__ == "__main__":
    main()[/FONT]
```

Save that to whatever.py and just run it with the text file in the same directory as the script:
```
[FONT="Courier New"]$ python whatever.py file[/FONT]
```

thanks for you replying  :) :) 

it works :cool: 

however , i also want to learn more about perl program 
how can i also work with perl ?
Thanks you

---

### Post by &lt;mawe&gt; on 2006-12-17
Hi!

Just like poOf I would use split instead of a regex. Seems to be much easier ;)
```
while (<DAT1>) {
  ($num, $name, @emails) = split / /;
  print "@emails\n";
}
```

Regards, mawe

---

### Post by 008325 on 2006-12-17
> **<mawe> said:**
> Hi!

Just like poOf I would use split instead of a regex. Seems to be much easier ;)
```
while (<DAT1>) {
  ($num, $name, @emails) = split / /;
  print "@emails\n";
}
```

Regards, mawe


:cool: :cool: :cool: 

Thanks for you replying  
i am so sorry about i dont post the full version of the example :p  

```

900000001 41300 CHAN, Ka Ka K111222(3) kaka@yyyy.com

900000002 41900 LAW, Ming Ming M222333(4) ming@yyyy.com minglaw@gggg.com

900000003 41300 YIP, Keung Keung B333444()

900000004 41303 YEUNG, Wai Wai W55555(5) waiwai@gggg.com

900000005 41303 AU, Yuen Yuen A666777(8)

900000006 41900 HO, Man H888999(0) man@gmail.com homan@yyyy.com

900000007 41300 CHEUNG, Tai Tai John C999000(1) johncheung@gggg.com

```

---

### Post by po0f on 2006-12-17
008325,

I had a feeling there were more than just two fields before the email addresses, that's why my script looks for "@".  ;)

I would post a Perl solution, but it's just yucky to me.

---

### Post by 008325 on 2006-12-17
> **po0f said:**
> 008325,

I had a feeling there were more than just two fields before the email addresses, that's why my script looks for "@".  ;)

I would post a Perl solution, but it's just yucky to me.

Sorry for your inconvenient :D

---

### Post by ghostdog74 on 2006-12-17
just one way in Perl

```

open(DAT1,"test.txt");                                    
while (<DAT1>) {
  @hash_array = split / /;
  for $items (@hash_array) {
   print $items . "\n" if $items =~ /@/   }
}
close(DAT1);

```

In Python, its much more readable
```

for line in open("test.txt"):
 	line = line.split()
 	print [items for items in line if "@" in items ]

```

---

### Post by &lt;mawe&gt; on 2006-12-17
I also prefer Python, but here is my next try in Perl ;)
```
while (<DAT1>) {
  @data = split / /;
  print join(" ", grep /@/, @data);
}
```
or just
```
print join(" ", grep /@/, split / /) while (<DAT1>);
```

Regards, mawe

---

### Post by 008325 on 2006-12-17
> **<mawe> said:**
> I also prefer Python, but here is my next try in Perl ;)
```
while (<DAT1>) {
  @data = split / /;
  print join(" ", grep /@/, @data);
}
```
or just
```
print join(" ", grep /@/, split / /) while (<DAT1>);
```

Regards, mawe


thanks you
but how can i grep it line by line ? i mean ...
how can i print like that



```

print "$. Username : $username Password : $password Email : $email\n";

```

---

### Post by scoon on 2006-12-17
Hey there, 

Here is a good start for you to work from.  Since most people felt obliged to say they prefer python, I feel obliged to say that I much prefer Perl to python any day.  

-scoon

```
#!/usr/bin/perl -w
use strict;
use Data::Dumper;

while (<DATA>){
    chomp;
    next unless length; #-- ignore blanks
    my @line_data = split(/ /);

    #-- since you didn't really specifiy what
    #-- each of the fields are in the data, 
    #-- I used Dumper to illustrate how the "split"
    #-- data looks. 
    print Dumper(\@line_data) . "\n";
}


__DATA__
900000001 41300 CHAN, Ka Ka K111222(3) kaka@yyyy.com

900000002 41900 LAW, Ming Ming M222333(4) ming@yyyy.com minglaw@gggg.com

900000003 41300 YIP, Keung Keung B333444()

900000004 41303 YEUNG, Wai Wai W55555(5) waiwai@gggg.com

900000005 41303 AU, Yuen Yuen A666777(8)

900000006 41900 HO, Man H888999(0) man@gmail.com homan@yyyy.com

900000007 41300 CHEUNG, Tai Tai John C999000(1) johncheung@gggg.com

```

---

### Post by pmasiar on 2006-12-17
> **ghostdog74 said:**
> ... readable in python
+1 for ghostdog74 for readable solution. It can be made even little more readable with better variable names: Ie. in my code names of all lists and dictionaries ends with 's'. So I would have:

```

for line in open("test.txt"):
 	words = line.split(' ') 
 	print [email for email in words if "@" in email ]

```

---

### Post by pmasiar on 2006-12-17
This is real readable solution, as in python should be:

```

for line in open("test.txt"):
 	for word in line.split(' '): 
 	    if "@" in word:
                print word 

```

---

### Post by &lt;mawe&gt; on 2006-12-17
```
for line in open("test.txt"):
```
And how do you close this file? This is bad style, IMO.

---

### Post by po0f on 2006-12-18
[quote=<mawe>]jibber jabber...[/quote]

Gogo Python2.5!

```
[FONT="Courier New"]from __future__ import with_statement

with open(file) as fd:
    for line in fd:
        print line
# end of scope, file descriptor freed for us![/FONT]
```

Oh yeah, sorry for misquoting you.  :)

[EDIT]
I always open files separate from processing the file contents just for the reason you stated.

---

### Post by pmasiar on 2006-12-18
> **<mawe> said:**
> And how do you close this file? This is bad style, IMO.

Destructor will close file. I agree it can bite me (and it did couple times): if you write to file, is better to close it (so buffer is flashed out). OK. so I can close() file at the end, or use "with ... as ..." construct from 2.5. My point was, how readable the solution is, comparing with other "traditional" languages like C. Especially when we have good variable manes and **don't** use list comprehention. :-)

---

### Post by po0f on 2006-12-18
pmasiar,

I agree that the list comprehension I posted isn't that readable, it is kinda busy.  But I hate (explicit) loops more than LC so meh.  (Good LC almost reads like English, I think that was the point.)

---

### Post by shoagun on 2006-12-18
> **008325 said:**
> i have a text file 

in each one line , it include the email address and name

one line = one user , here is example

```


01 ABC aaa@aaa.com
02 CDE bbb@bbb.com ccc@ccc.com
03 FGH 123@123.com 123@456.com 789@123.com


```
each line maybe including many  email

i wrote a perl

```
while (<DAT1>) {

($email)=($_ =~ /([\w\-]+\@[\w\-]+\.[\w\-]*)/);

print $email;

}
```however , it just get the first email not all the email per line, 

how can i solve this program ?

i tried use array @email , nothing has change :-k :-k


if you're wondering why this particular solution doesn't work, it's because the pattern search stops after the first match.  You can find every match in the string by adding a g after the last forward slash.  If you use it in an array context, it will return all the matches in a list.  So, for instance, if I wanted to match multiple emails in a line, I could do:

```
my @emails=($_=~/\S+\@\S/g);
```

If you want a full solution using pattern matching, I could write it up, but I think the other solutions posted, using split, work fine.

---

### Post by ghostdog74 on 2006-12-18
> **<mawe> said:**
> ```
for line in open("test.txt"):
```
And how do you close this file? This is bad style, IMO.

No quite true, in Python 2.2 or later, you can loop over the file object itself. Python will do the implicit close() after iteration.
Here is a reference
[http://www.effbot.org/zone/readline-performance.htm]("http://www.effbot.org/zone/readline-performance.htm")
I have used this syntax very often in my scripts, so no problems.

---

### Post by Wybiral on 2006-12-18
Or you could just use...

```

readfile = open("test.txt")
for line in readfile:
 	for word in line.split(' '): 
 	    if "@" in word:
                print word
readfile.close()

```

I think thats 100% readable...

---

### Post by po0f on 2006-12-18
ghostdog74,

After iteration, or after the script/program exits?  I've never bothered looking into when exactly it happens, but I am curious.  (I always explicitly close my open files.)

---

### Post by ghostdog74 on 2006-12-18
> **po0f said:**
> ghostdog74,

After iteration, or after the script/program exits?  I've never bothered looking into when exactly it happens, but I am curious.  (I always explicitly close my open files.)

hi

until no more lines in the file.
another reference PEP: [http://www.python.org/doc/2.2.1/whatsnew/node4.html]("http://www.python.org/doc/2.2.1/whatsnew/node4.html")

---

### Post by &lt;mawe&gt; on 2006-12-18
[quote="ghostdog74"]No quite true, in Python 2.2 or later, you can loop over the file object itself. Python will do the implicit close() after iteration.[/quote]
AFAIK this is true if you open your file via **file("text.txt")**, but not for **open("text.txt")**.

---

### Post by ghostdog74 on 2006-12-18
> **<mawe> said:**
> AFAIK this is true if you open your file via **file("text.txt")**, but not for **open("text.txt")**.

may i refer you to [http://docs.python.org/lib/built-in-funcs.html]("http://docs.python.org/lib/built-in-funcs.html") under Footnotes, and [http://docs.python.org/lib/built-in-funcs.html]("http://docs.python.org/lib/built-in-funcs.html") for file() .

---

### Post by &lt;mawe&gt; on 2006-12-18
[quote="http://docs.python.org/lib/built-in-funcs.html"]
When opening a file, it's preferable to use open()
[/quote]
[quote="http://docs.python.org/lib/bltin-file-objects.html#bltin-file-objects"]
file() is new in Python 2.2. The older built-in open() is an alias for file().
[/quote]
So I should use *open()*, but it is just an alias for *file()*?

---

### Post by ghostdog74 on 2006-12-18
> **<mawe> said:**
> So I should use *open()*, but it is just an alias for *file()*?

I use open() mostly for "general purpose file operations". It was mentioned somewhere that  file() is used for subclassing and type testing and open() is preferred for use as a
factory function which returns a new file object.  I have not really used file() before so i have no further comments. open() is fine for most of my cases. 

Some reads here.
[http://sourceforge.net/tracker/index.php?func=detail&aid=1094011&group_id=5470&atid=305470]("http://sourceforge.net/tracker/index.php?func=detail&aid=1094011&group_id=5470&atid=305470")

[http://mail.python.org/pipermail/python-dev/2004-July/045931.html]("http://mail.python.org/pipermail/python-dev/2004-July/045931.html")

[http://mail.python.org/pipermail/python-dev/2004-July/045967.html]("http://mail.python.org/pipermail/python-dev/2004-July/045967.html")

---

### Post by &lt;mawe&gt; on 2006-12-18
Thank you for the links. I always use *file()* instead of *open()* :)
[quote="Guido van Rossum"]
Anyway, here's my future-proof distinction: use open() as the factory
function, and file for type-testing.
[/quote]
Hmm, maybe I'll use *open()* now :)

---

