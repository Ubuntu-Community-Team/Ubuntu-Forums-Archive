---
title: "PHP: Find 1st Letter of EVERY word in a string"
date: 2009-03-12
forum: Programming Talk
---

### Post by s.fox on 2009-03-12
Hi,

How would I find the first letter of a word contained within a string using PHP.  

For example

```

$string = "Lots of words in this string";

```

I would want to find L,O,W,I,T,S.  Any thoughts?  I know how to find the very first letter, but this is slightly more complicated.

Many thanks,

Ash R

---

### Post by ghostdog74 on 2009-03-12
split the string up into an array, then use for loop to go through the array, checking the first letter using substring functions.

---

### Post by hastur on 2009-03-12
hi,

stupid idea : with a regular expression and a capturing pattern.
something like

```

preg_match_all("/(\S)\S*/i",$string,$array,PREG_PATTERN_ORDER)

```

then $array[0] or $array[1] should contain all the first letters... hopefully (my regexp may be totally wrong).

but of course exploding the string is simpler :)

---

### Post by lapubell on 2009-03-12
real quick code... debug on your own... probably not the fastest solution by far


```

$string = "Lots of words in this string";
$words = explode(" ", $string);
$letters = "";
foreach ($words as $value) {
    $letters .= substr($value, 0, 1);
}

```

if you want the spaces and commas in there, then put those in the for loop too.

cheers!

---

### Post by s.fox on 2009-03-12
Thanks for the ideas.  I have managed to accomplish my goal by splitting the string into an array.  I just wondered if their was an alternative.

Once again thank you.

-Ash R

---

### Post by jimi_hendrix on 2009-03-12
> **lapubell said:**
> real quick code... debug on your own... probably not the fastest solution by far


```

$string = "Lots of words in this string";
$words = explode(" ", $string);
$letters = "";
foreach ($words as $value) {
    $letters .= substr($value, 0, 1);
}

```

if you want the spaces and commas in there, then put those in the for loop too.

cheers!

who was the smart guy that named the explode function...

---

### Post by s.fox on 2009-03-12
Not just saying this but explode has got to be in my top 3 most used commands in PHP.  

I was only reluctant to use it in this case because I wanted to see if their were any alternatives and wanted to increase my PHP knowledge.

Again,  Thanks to the community :D

---

### Post by myrtle1908 on 2009-03-12
In perl ...

```
my $s = "one two three four";
my @f = ($s =~ m/\b(\w)/g);
print @f;
```

Shouldn't be difficult to convert to PHP.

---

### Post by Can+~ on 2009-03-12
Alternative method: Retrieving each letter after a space character.

---

### Post by s.fox on 2009-03-13
> **Can+~ said:**
> Alternative method: Retrieving each letter after a space character.


Now that is an idea i had not considered.  I know I have already done what I set out to do but that kinda sounds like a fun problem to solve.

Thanks

---

### Post by KingNeil on 2009-03-13
There are probably very fancy one-line ways to do it.

I'd just split it by the SPACE character, and then loop through the array of words, taking the first letter. Doesn't really matter how you do it. It's going to be a near-instant execution of code. It won't slow the thing down.

---

### Post by s.fox on 2009-03-13
Well,  I only had to run the piece of code once so it didn't really matter with speed. :D

EDIT:  Yes, there probably is a "fancy" one liner using regular expressions or something similar.  Thats what I am trying to do at the moment anyway just as an exercise.

---

### Post by wmcbrine on 2009-03-13
> **myrtle1908 said:**
> In perl ...

```
my $s = "one two three four";
my @f = ($s =~ m/\b(\w)/g);
print @f;
```In Python:

```

>>> x = 'this is a long string'
>>> [y[0] for y in x.split()]
['t', 'i', 'a', 'l', 's']

```

---

