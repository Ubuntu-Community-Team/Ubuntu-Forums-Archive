---
title: "Best language for this kind of string work?"
date: 2009-06-28
forum: Programming Talk
---

### Post by Kerry_suds on 2009-06-28
So I am a --total-- newbie to all of this, just started.  And this is the question whats the best language to use and any hints you on howto would be super cool too. TIA.  The problem I have is this I need to do a lot of search and replaces. But they are kinda different. Let me explain.  Two files, a & b. What I want to do is do a search for "xxx" but the replace is from each consecutive line of file b.  eg file a peter_xxx john_xxx james_xxx  file b 090 070 020  after search and replace... peter_090 john_070 james_020  so is it php, perl, python or scripting..told you i was a newbie :-)))). Many thanks K

---

### Post by pokerbirch on 2009-06-28
I would say Python. It's easy to use and has some nice string functions built into it. File input/output is also easy and you can read files line by line. The main string functions you'll need will be find() and replace(). 

[http://docs.python.org/tutorial/inputoutput.html](http://docs.python.org/tutorial/inputoutput.html)
IGNORE THIS: [http://www.python.org/doc/2.3/lib/module-string.html](http://www.python.org/doc/2.3/lib/module-string.html)
USE THIS INSTEAD: [http://docs.python.org/library/stdtypes.html#string-methods](http://docs.python.org/library/stdtypes.html#string-methods)



EDITED due to my stupidity...

---

### Post by Can+~ on 2009-06-28
> **pokerbirch said:**
> I would say Python. It's easy to use and has some nice string functions built into it. File input/output is also easy and you can read files line by line. The main string functions you'll need will be find() and replace(). 

[http://docs.python.org/tutorial/inputoutput.html](http://docs.python.org/tutorial/inputoutput.html)
[http://www.python.org/doc/2.3/lib/module-string.html](http://www.python.org/doc/2.3/lib/module-string.html)

Whoa, the string module? That's deprecated, now all strings have it as methods:

[http://docs.python.org/library/stdtypes.html#string-methods](http://docs.python.org/library/stdtypes.html#string-methods)

---

### Post by pokerbirch on 2009-06-28
> **Can+~ said:**
> Whoa, the string module? That's deprecated

Yes, sorry. I always use the built-in string methods. I've never used the string module. I didn't even know it existed. That'll teach me to read Google's answers before i post them...

---

### Post by wojox on 2009-06-28
php command line.

or

perl Practical Extraction and Report Language.

But you're gonna half to learn regular expressions.

---

### Post by soltanis on 2009-06-28
Use Perl. Python is way out of its league for this task.

---

### Post by Can+~ on 2009-06-28
> **wojox said:**
> But you're gonna half to learn regular expressions.

"Some people, when confronted with a problem, think "I know, I'll use regular expressions." Now they have two problems."

-[Jamie Zawinski]("http://en.wikiquote.org/wiki/Jamie_Zawinski")

> Use Perl. Python is way out of its league for this task. 

why?

---

### Post by pokerbirch on 2009-06-28
I wouldn't recommend Regular Expressions to a complete noob who's never programmed before. It should be an easy task in Python...unless i've totally misunderstood the task?

---

### Post by soltanis on 2009-06-28
Oh come on, first of all, this task takes exactly this much perl:

```

open(A, "<" . $pathA);
open(B, "<" . $pathB);
$acc = '';

foreach (<A>) {
        s/_xxx$/<B>/eg;
        $acc .= $_ . "\n";
}

close(A) and open(A, ">" . $pathA);
print A $acc;
close(A) and close(B);

```

Second that barely took anything in the way of regular expressions, and third regular expressions are only difficult because most people never bother to learn them.

---

### Post by Can+~ on 2009-06-28
[PHP]#!/usr/bin/python

filea = open("a.txt")
fileb = open("b.txt")
filec = open("c.txt", "w")

#For each file of the file A, split and replace the second element.
for line in filea:
	result = line.strip().split("_") # split line
	result[1] = "_"+fileb.readline().strip() # replace rightmost element
	filec.write("".join(result)+"\n") # write

filea.close(); fileb.close(); filec.close()[/PHP]

a.txt:
```
james_xxx
john_xxx
paul_xxx
```

b.txt:
```
010
011
012
```

c.txt (result):
```
james_010
john_011
paul_012
```

That's as simple as it gets. Plus some extra points of being somewhat readable for non-programmers.

---

### Post by Tony Flury on 2009-06-28
> **soltanis said:**
> Oh come on, first of all, this task takes exactly this much perl:

```

open(A, "<" . $pathA);
open(B, "<" . $pathB);
$acc = '';

foreach (<A>) {
        s/_xxx$/<B>/eg;
        $acc .= $_ . "\n";
}

close(A) and open(A, ">" . $pathA);
print A $acc;
close(A) and close(B);

```

Second that barely took anything in the way of regular expressions, and third regular expressions are only difficult because most people never bother to learn them.

Why does the contents of that for loop just look like line noise :-) ?

Perl maybe more efficient in terms of characters used (and maybe even speed), but to be honest i like code i can understand the day i have written - so I would vote for python.

---

### Post by wojox on 2009-06-28
Alien Space Algebra

---

### Post by Kerry_suds on 2009-06-28
Yes to the earlier poster, I have never programmed in perl or python.  I looked at the python, it looks like some for loops and some string work.  It does not too hard (famous last words)  perl i'll look at later today...  I've looked at regular expressions... that to me looks like a world of hurt :)    if i look at can's python example it looks more readable.  I dont get    s/_xxx$/<B>/eg;   $acc .= $_ . "\n";  but i am sure with time i would... but it make me think you have to really be a bit of a master to do that kinda work.  This is day 2 after all :-)  But thanks for all your suggestions... you all are really great. :)  Glad i went with ubuntu :)   K

---

### Post by Shiva88 on 2009-06-28
> **soltanis said:**
> Oh come on, first of all, this task takes exactly this much perl:

```

open(A, "<" . $pathA);
open(B, "<" . $pathB);
$acc = '';

foreach (<A>) {
        s/_xxx$/<B>/eg;
        $acc .= $_ . "\n";
}

close(A) and open(A, ">" . $pathA);
print A $acc;
close(A) and close(B);

```

Second that barely took anything in the way of regular expressions, and third regular expressions are only difficult because most people never bother to learn them.



As someone who knows only a little rudimentary programing, I believe you've stated the case against Perl quite well.

---

### Post by Mirge on 2009-06-28
I think any of the popular interpreted languages will be just fine. Pick one that you are likely to keep using. Perl can do it, Python can do it, PHP can do it, yadda yadda.

---

### Post by ghostdog74 on 2009-06-28
> **Kerry_suds said:**
>  Let me explain.  Two files, a & b. What I want to do is do a search for "xxx" but the replace is from each consecutive line of file b.  eg file a peter_xxx john_xxx james_xxx  file b 090 070 020  after search and replace... peter_090 john_070 james_020  so is it php, perl, python or scripting..told you i was a newbie :-)))). Many thanks K

if words to be replace is the same amount as replacement words and you want to replace them consecutively, 
```

awk 'FNR==NR{for(i=1;i<=NF;i++)repl[i]=$i;next}
{ for(i=1;i<=NF;i++){ 
    if($i ~ /xxx/ ) gsub(/xxx/,repl[i],$i)    
}}1' file2 file1

```

---

### Post by ghostdog74 on 2009-06-28
> **soltanis said:**
> Use Perl. Python is way out of its league for this task.
such statements cannot be made without proper due understanding of languages. OP's task can be done with practically any language that supports string manipulation and file I/O. Even PHP,Java etc can do the job.

---

### Post by soltanis on 2009-06-29
Just as I'm sure any Turing complete language could do this job, which is not to say that OP wants to write his program in brainf*** even though conceivably that could get the job done.

The question is not "can the language do it?" as obviously any language worth calling a language can. The question is how much thinking does it take for the language to do it, which obviously depends on the programmer in question and the facilities supplied by the language.

To be fair the awk is just as incomprehensible to me as I'm sure perl is incomprehensible to...everyone except me apparently (where have all the perl hackers gone? gone to shoot me for my terrible code, that's where).

On reconsideration we can also shorten + improve readability on the perl program:

```

use feature 'say';
open(A, "<" . $pathA);
open(B, "<" . $pathB);
open(C, ">output");

foreach (<A>) {
        s/_xxx$/<B>/eg and say C;
}

close(A) and close(B) and close(C);

```

For anyone who is scared of slashes that regular expression means "find a string at the end of the line which looks like _xxx" and then "replace it with the next line from file B".

Jeez. Python programmers.

---

### Post by viljun on 2009-06-29
perl -pi -e "s/oldtext/newtext/g;" the_folder/*.txt

replaces all oldtext with newtext in all txt-files in folder the_folder. please, be careful.

---

### Post by ghostdog74 on 2009-06-29
> **soltanis said:**
> Just as I'm sure any Turing complete language could do this job, which is not to say that OP wants to write his program in brainf*** even though conceivably that could get the job done.
The question is not "can the language do it?" as obviously any language worth calling a language can. The question is how much thinking does it take for the language to do it, which obviously depends on the programmer in question and the facilities supplied by the language.

so this quote you made is not true then. 
> Python is way out of its league for this task.


> 
To be fair the awk is just as incomprehensible to me 

because its not properly indented and broken down. (also if you are not familiar with awk, of course it will look incomprehensible to you)
```

awk '
FNR==NR{
    #get all replacement text to array
    for(i=1;i<=NF;i++) repl[i]=$i
    next
}
{ for(i=1;i<=NF;i++){ 
    if($i ~ /xxx/ ) gsub(/xxx/,repl[i],$i)    
  }
}1' file2 file1

```
Also, my awk code and your Perl code's output are different.
```

# awk 'FNR==NR{for(i=1;i<=NF;i++)repl[i]=$i;next}{ for(i=1;i<=NF;i++){ if($i ~ /xxx/ ) gsub(/xxx/,repl[i],$i)}}1' file2 file1
peter_090 john_070 james_020

# more test.pl
#!/usr/bin/perl
open(A, "<" . "file1");
open(B, "<" . "file2");
foreach (<A>) {
        s/_xxx$/<B>/eg ;
        print $_ ."\n";
}

close(A) and close(B);

# ./test.pl
peter_xxx john_xxx james090 070 020


```
you will have to amend/add extra Perl code to fit OP's requirement.

---

### Post by ghostdog74 on 2009-06-29
> **viljun said:**
> perl -pi -e "s/oldtext/newtext/g;" the_folder/*.txt

replaces all oldtext with newtext in all txt-files in folder the_folder. please, be careful.

this one too.. doesn't really solve OP's requirement. look at his first post again for his desired output

---

### Post by viljun on 2009-06-29
> **ghostdog74 said:**
> this one too.. doesn't really solve OP's requirement. look at his first post again for his desired output

Oh sorry. Didn't read the post carefully enough...

---

### Post by Reiger on 2009-06-29
> **soltanis said:**
> Just as I'm sure any Turing complete language could do this job, which is not to say that OP wants to write his program in brainf*** even though conceivably that could get the job done.

The question is not "can the language do it?" as obviously any language worth calling a language can. The question is how much thinking does it take for the language to do it, which obviously depends on the programmer in question and the facilities supplied by the language.

To be fair the awk is just as incomprehensible to me as I'm sure perl is incomprehensible to...everyone except me apparently (where have all the perl hackers gone? gone to shoot me for my terrible code, that's where).

On reconsideration we can also shorten + improve readability on the perl program:

```

use feature 'say';
open(A, "<" . $pathA);
open(B, "<" . $pathB);
open(C, ">output");

foreach (<A>) {
        s/_xxx$/<B>/eg and say C;
}

close(A) and close(B) and close(C);

```

For anyone who is scared of slashes that regular expression means "find a string at the end of the line which looks like _xxx" and then "replace it with the next line from file B".

Jeez. Python programmers.

I am not really proficient with Perl (I barely know enough to see what easy code means), but wouldn't it be better to use while(<A>) {} ? I though while(<A>) reads A line by line, whereas foreach(<A>) would read in the entire file at once, split it by line and then return that as an iterable something? 

Thus while(<A>) runs with constant memory whereas foreach(<A>) wouldn't; meaning that the while version would also work on very large files?

---

### Post by gorilla on 2009-06-29
What about bash?

```

$ cat a.txt:
james_xxx
john_xxx
paul_xxx

$ cat b.txt:
010
011
012

$ b=(`cat b.txt`); for i in `cat a.txt`; do echo ${i/xxx/${b[0]}}; b=(${b[@]:1}); done
james_010
john_011
paul_012
```

---

### Post by Kerry_suds on 2009-06-29
you guys amaze me (awk??)  i was expecting here's a url .. bye.  your great because those samples show me what i have to learn in (for lol) each language.  Cheers K      
 
 Edit: Hang on a moment. I think I have learned something, so can you check if I'm right. Thanks    
 
  The python example is flawed compared to the perl possibly even the bash, why?   
 
   because if you add to the lines in a) eg from james_xxx to james_xxx_abc,       
 
  The python example wont work. But the others will, am i right?

---

