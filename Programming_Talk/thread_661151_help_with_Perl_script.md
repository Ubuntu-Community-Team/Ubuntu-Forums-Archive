---
title: "help with Perl script"
date: 2008-01-07
forum: Programming Talk
---

### Post by MustNotSleep on 2008-01-07
I need some help with accomplishing the following:

I have two files:
[LIST]
[*]iso.txt
which contains the ISO-3166-1 country codes in numeric, alpha-2 and full country names, separated by |
[*]iso2.txt
which contains international area dialing codes and ISO-3166-1 alpha-2 country codes, separated by |
[/LIST]
Now, what I need is to add the relevant area codes from the second list, concatenated to the first list in the same format, like so:
20|AD|Andorra|376

The only thing tying together the two files is the 2-digit country code, so I need to perform some loop through file 1 and test file 2 for the occurrence and then tack on the second portion of the relevant line to the end of the line in file 1.

I hope you understand what I mean. I've been banging my head all day trying to figure out a way to do it. And seeing how I recently got into Perl, I thought it would be a good way for me to learn something on the way. Though if you have a suggestion I'm very open to other languages, as well.

Thanks in advance!

PS: I'm attaching the two files so you can see the syntax they have.

---

### Post by pmasiar on 2008-01-07
Perl is OK but Python is more readable.

You need to read one of files to a dictionary (hash), then compare with the other one.

Parsing is easy, I did not grokked details of what you need, but here is general idea:
[php]
names = {}
for line in file('iso2.txt'):
    two, alpha, full, code = line.split('|')
    names[two] = name # or save what you need

for line in file('iso.txt'):
    two, alpha, full, code = line.split('|')
    if two in names:
        # do what you need
    
[/php]

---

### Post by MustNotSleep on 2008-01-07
> **pmasiar said:**
> Perl is OK but Python is more readable.

You need to read one of files to a dictionary (hash), then compare with the other one.

Parsing is easy, I did not grokked details of what you need, but here is general idea:
[php]
names = {}
for line in file('iso2.txt'):
    two, alpha, full, code = line.split('|')
    names[two] = name # or save what you need

for line in file('iso.txt'):
    two, alpha, full, code = line.split('|')
    if two in names:
        # do what you need
    
[/php]
that helps a lot, but i'm still stuck.. though thanks for pointing me to Python.. it is indeed much easier to interpret..

i tried running the following in the interpreter, but received an error..

[php]>>> areacode = {}
>>> alpha = {}
>>> for line in file('iso2.txt'):
...     ac, al = line.split('|')
...     areacode[ac] = ac
...     alpha[al] = al
... 
>>> for line in file('iso.txt'):
...     id, al, full, num = line.split('|')
...     if al in alpha:
...             num = areacode[num]
... 
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
ValueError: need more than 3 values to unpack
>>>[/php]
i've barely started reading tutorials on Python now (mainly those from your sig's link), so i apologize if i sound like a newbie.. :(

can you guide me through the logic of your script? basically i don't know how to refer to the first file's variables while i'm in the second loop... if that makes sense..

thanks again! i'll go back to reading some more.. :D

---

### Post by ghostdog74 on 2008-01-07
> **MustNotSleep said:**
> that helps a lot, but i'm still stuck.. though thanks for pointing me to Python.. it is indeed much easier to interpret..

i tried running the following in the interpreter, but received an error..

[php]>>> areacode = {}
>>> alpha = {}
>>> for line in file('iso2.txt'):
...     ac, al = line.split('|')
...     areacode[ac] = ac
...     alpha[al] = al
... 
>>> for line in file('iso.txt'):
...     id, al, full, num = line.split('|')
...     if al in alpha:
...             num = areacode[num]
... 
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
ValueError: need more than 3 values to unpack
>>>[/php]
i've barely started reading tutorials on Python now (mainly those from your sig's link), so i apologize if i sound like a newbie.. :(

can you guide me through the logic of your script? basically i don't know how to refer to the first file's variables while i'm in the second loop... if that makes sense..

thanks again! i'll go back to reading some more.. :D



that's a classic case of not enough reading ,research and practice. People tend to jump to forums and ask questions that can be solved with just a little bit of reading and practice. Also, if you have started on Perl, then go all the way. Learn all you can about the language. Don't stop halfway. do you have good Perl books to read? If not you can always start where it all began, the Perl documentation.
I do not program Perl nowadays, but once I know the basics, I can code up simple stuff like this without much effort. So i suggest you continue and learn  to the fullest what Perl can do for you. Then slowly proceed on to other languages if you want. 
Here's my take, 
```

#!/usr/bin/perl

my $iso1 = "/tmp/iso.txt";
my $iso2 = "/tmp/iso2.txt";
open(ISO1 ,"< $iso1") or die "Cannot open $iso1: $!";
open(ISO2 ,"< $iso2") or die "Cannot open $iso2: $!";
my %AREAS1 = ();
my %AREAS2 = ();

while ( <ISO2> ){
  my ( $num, $area) = split(/\|/,$_);
  chomp($num,$area);
  if ( $area =~ /,/ ) { 
    @extra = split(",",$area);
    chomp(@extra);
    foreach my $x ( @extra ) {
      $x =~ s/^\s+//;
      $AREAS2{$x} = $num;
    }    
  } else {
     $AREAS2{$area}=$num;
  }
}

while ( <ISO1> ) {
  chomp;
  my @line = split(/\|/,$_);
  $AREAS1{$line[1]} = $_;
}

while ( ($key, $value) = each %AREAS1) {        
        print "$value : $AREAS2{$key} \n";
}
close(ISO1);
close(ISO2);


```
I did not put comments. That's on purpose.

---

### Post by MustNotSleep on 2008-01-07
> **ghostdog74 said:**
> that's a classic case of not enough reading ,research and practice. People tend to jump to forums and ask questions that can be solved with just a little bit of reading and practice. Also, if you have started on Perl, then go all the way. Learn all you can about the language. Don't stop halfway. do you have good Perl books to read? If not you can always start where it all began, the Perl documentation.
I do not program Perl nowadays, but once I know the basics, I can code up simple stuff like this without much effort. So i suggest you continue and learn  to the fullest what Perl can do for you. Then slowly proceed on to other languages if you want. 
Here's my take, 
```

#!/usr/bin/perl

my $iso1 = "/tmp/iso.txt";
my $iso2 = "/tmp/iso2.txt";
open(ISO1 ,"< $iso1") or die "Cannot open $iso1: $!";
open(ISO2 ,"< $iso2") or die "Cannot open $iso2: $!";
my %AREAS1 = ();
my %AREAS2 = ();

while ( <ISO2> ){
  my ( $num, $area) = split(/\|/,$_);
  chomp($num,$area);
  if ( $area =~ /,/ ) { 
    @extra = split(",",$area);
    chomp(@extra);
    foreach my $x ( @extra ) {
      $x =~ s/^\s+//;
      $AREAS2{$x} = $num;
    }    
  } else {
     $AREAS2{$area}=$num;
  }
}

while ( <ISO1> ) {
  chomp;
  my @line = split(/\|/,$_);
  $AREAS1{$line[1]} = $_;
}

while ( ($key, $value) = each %AREAS1) {        
        print "$value : $AREAS2{$key} \n";
}
close(ISO1);
close(ISO2);


```
I did not put comments. That's on purpose.
wow, thanks a lot! with a little bit of modifying, your script did exactly what i wanted.. and by the looks of it, it would've taken me at least another week to get my head around all the concepts you used..

the thing is i have a lot of stuff i want to learn that i've barely begun scratching the surface on them all.. i'm trying to create a database-driven web application, and have so far done a few cool things in JavaScript/PHP.. but the thing is i want to dive in Ruby and RoR and MySQL, and in the meantime i'm getting my feet wet in Perl, bash scripts, regexes and now Python.. it's a lot of different concepts and i'm trying my best to get a firm grip on them all..

the only programming i've done so far is in C and C++ at my college's introductory course.. and with all the different choices in languages out there, you can see why i'm confused..

the thing i wanted to accomplish in this post was simply a small step, that i didn't want to waste a week on, so i wasn't sure how to proceed.. if you hadn't helped me, i'd probably done the thing manually, and it'd still take me less time than learning to script the procedure myself..

so i thank you for the educational post, i'll be sure to keep on reading about Perl.. though Python has certainly piqued my interest.. :)

---

### Post by ghostdog74 on 2008-01-07
> **MustNotSleep said:**
> 
so i thank you for the educational post, i'll be sure to keep on reading about Perl.. though Python has certainly piqued my interest.. :)
Like i said, choose one language and learn all you can about it. No point rushing yourself. In the end, you learn nothing. If you want to learn Python instead (its your call anyway), then go ahead, but this time DON'T GIVE UP HALFWAY. Learn all you can about Python, and be good at it. Then proceed on to other languages. That's the way to learn many languages and be good at them.

---

### Post by MustNotSleep on 2008-01-07
> **ghostdog74 said:**
> Like i said, choose one language and learn all you can about it. No point rushing yourself. In the end, you learn nothing. If you want to learn Python instead (its your call anyway), then go ahead, but this time DON'T GIVE UP HALFWAY. Learn all you can about Python, and be good at it. Then proceed on to other languages. That's the way to learn many languages and be good at them.
i know what you mean.. it's better to excel at one thing, than be mediocre in a dozen different ones.. thanks again for your helpful posts!

---

### Post by ghostdog74 on 2008-01-07
> **MustNotSleep said:**
> i know what you mean.. it's better to excel at one thing, than be mediocre in a dozen different ones.. thanks again for your helpful posts!
That's a different meaning. Its the same as saying, for example, be good at Python, but only mediocre at others. That's not what I mean. You should be good at everything.

---

### Post by pmasiar on 2008-01-07
Sorry I was just leaving when I wrote my my last post, did not have time to do better job.

But you gained important experience in debugging code.

```

# data being split:
20|AD|Andorra|376

# your line 
        ac, al = line.split('|')
# my line
        two, alpha, full, code = line.split('|') 

# You got this error message
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
ValueError: need more than 3 values to unpack

```

What would be guess? Pyton told you that you need "more than 3 values to unpack", you provided only 2. See now?

Do as you want, learn Python or Perl. But let me tell you: I spent a lot of time learning Perl, and Python is not only easier to read, but easier to remember.

---

### Post by ghostdog74 on 2008-01-07
> **pmasiar said:**
> But let me tell you: I spent a lot of time learning Perl, and Python is not only easier to read, but easier to remember.
There are many languages that may be "not easy to read or remember" than Python. However, OP should not stop learning those languages just because of that. 
Not easy to remember? get a reference book then. Not easy to read? then read slowly and understand. Not a problem there.

---

### Post by pmasiar on 2008-01-08
I agree that learning more languages is beneficial. Question is, where to start, and where to focus to become expert? Becoming expert takes 10 years, so plan ahead before investing the time.

Python fits in my brains much easier than Perl or Java does (Perl is too quirky to remember and Java too vast to fit :-) ). Possibly you may say it is problem with my brains, but I don't care - those are last one I have, and I plan to stick with them for a while :-)

---

