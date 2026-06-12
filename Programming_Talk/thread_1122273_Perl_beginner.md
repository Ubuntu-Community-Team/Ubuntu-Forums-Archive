---
title: "Perl beginner"
date: 2009-04-10
forum: Programming Talk
---

### Post by se_landy on 2009-04-10
I need to write a program for web analysis in Perl (it needs to calculate site parameters like [here]("http://tools.pingdom.com/")). the problem is - i don't know anything about that technology. I've been programming in C, C#, JAVA... I have already started to study Perl syntax and learned how to start perl script from terminal. But I don't know what technologies (programs) do I need to use?? Do I need LAMP for localhost?? where do I need to put my scripts for program to work?? 
I need just few links for basic techniques (just to figure out how that stuff work) and also some recommendations like what programs to use...
Tnx for your help:p

---

### Post by ghostdog74 on 2009-04-11
i havn't been to the site, so what does the site do? and what exactly do you want to create? do you want to create a web site similar to that site you mentioned?

---

### Post by se_landy on 2009-04-11
> **ghostdog74 said:**
> i haven't been to the site, so what does the site do? and what exactly do you want to create? do you want to create a web site similar to that site you mentioned?

That is a school assignment, and my professor hasn't specified anything. All I know is that I have to write a program in PERL, that program has to "measure" some site parameters (loading time, is HTML optimized.... stuff like that). I don't think I have to create a web site.... I myself can define what parameters will I include in program. Now the thing is, I'm learning PERL syntax, I think I will be able to write it... But I don't know how do scripts written in PERL work, what programs do I need to use to write and test my program... So if you could help me with that, that would be great! :)
He also mentioned that I can use some already written scripts and that there are a lot of them on the Internet... Is there a web site where I could find those scripts???
Those are basics that I have to learn before I could start writing my program... :)

---

### Post by pmasiar on 2009-04-11
Seems like a procrastinated school project? Check FAQ policy about homeworks.

Seems like you need to write a program which downloads a page and runs some filters/regexes on it, good fit for Perl (please avoid using PERL :-) ). No need for localhost IMHO. You may ask professor which Perl modules s/he recommends for the task and/or are preinstalled.

---

### Post by se_landy on 2009-04-11
> **pmasiar said:**
> Seems like a procrastinated school project? Check FAQ policy about homeworks.

**Seems like you need to write a program which downloads a page and runs some filters/regexes on it**, good fit for Perl (please avoid using PERL :-) ). No need for localhost IMHO. You may ask professor which Perl modules s/he recommends for the task and/or are preinstalled.

I have two months to finish this project, it's a lot of time... Besides, I don't want anyone to do this for me, I am just asking about basic infos... stuff like the bold text... It's easy to learn Perl syntax, but I can't find anywhere what programs could I use for making this program, does everything have to be in one script... those things I can ask only people who have done stuff in Perl :)
All I need is couple advices, links or phrases to search with google to learn how to write scripts and how to check if that what I have written is good (besides to check it in command prompt or terminal) :)

---

### Post by slavik on 2009-04-11
cpan.org is a website that you can search for perl modules.

---

### Post by myrtle1908 on 2009-04-11
To get you started ...

Perl is an interpreted language (unlike C which you mentioned in your original post).  A Perl script requires a Perl interpreter upon which to run.  You most likely already have Perl installed on your linux distribution.  To confirm this, type the following in your console:-

```
perl -v
```

It should output something like the following:-

```

This is perl, v5.8.8 built for i486-linux-gnu-thread-multi
Copyright 1987-2006, Larry Wall
...

```

If it does not, then you need to install the Perl interpreter.

Assuming you do indeed have Perl installed, then creating a basic script is  trivial.  Start up your favourite text editor and type the following:-

```

use strict;
use warnings;

print "Hello World.\n";

```

* Note the use of *use strict* and *use warnings*.  These statements will help you to identify problems with your code.

Save the file as 'hello.pl'.  To run the script, open your console and type:-

```
perl hello.pl
```

This is the most basic Perl script and should get you started.  For dealing with web pages etc you should look at the LWP and/or Mechanize modules.

Finally, here is a simple script that downloads the HTML content from a URL.

```

use strict;
use warnings;
use LWP::Simple;

my $url = "http://www.google.com/";
my $html = get($url);
print $html;

```

Good Luck.

---

### Post by se_landy on 2009-04-11
Tnx guys. this should be enough for the beginning :p :)

---

### Post by yaroto98 on 2009-04-11
If you want to take the cheap way out you can use perl to call other programs and then parse the output they have to get your statistics.

(i don't recommend actually using backtics much, but they're easy to learn)

$output = `wget www.google.com`;

(now run regexes on your $output)

print $results;

---

### Post by slavik on 2009-04-11
> **se_landy said:**
> Tnx guys. this should be enough for the beginning :p :)
I agree.

---

### Post by ghostdog74 on 2009-04-12
> **yaroto98 said:**
> If you want to take the cheap way out you can use perl to call other programs and then parse the output they have to get your statistics.

(i don't recommend actually using backtics much, but they're easy to learn)

$output = `wget www.google.com`;

(now run regexes on your $output)

print $results;
try not to even do that. this makes code not portable.

---

