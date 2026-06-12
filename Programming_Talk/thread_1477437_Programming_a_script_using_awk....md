---
title: "Programming a script using awk..."
date: 2010-05-08
forum: Programming Talk
---

### Post by Pazzeo on 2010-05-08
Hello guys,

I have a little question for you...I'm starting to write a bash script. The main function of this script is to extract only the rows with a particular string and insert a special char, for example #, in some positions of the string. 

To extract the rows with a particular string I used this:

cat file.log | grep "TEST" > temp.log

So now in the temp.log I have only the string with "TEST", an example is:

2010070514342  TEST   1621232792779200500000

Now I want to create a new file with the same string, but formated in this way:

2010070514342#TEST#1621232792779#2005#00000

I think I have to use awk, but I tried without success. Could someone help me?

Thank you very much,

Paz

---

### Post by trent.josephsen on 2010-05-08
For starters, you're using a useless cat.  grep takes input from files.

```
grep TEST file.log >temp.log
```

but to the real problem... I'm sure it's possible with either awk or sed (or both), but I would use perl (because I'm not familiar enough with either of those to use them for this kind of thing).

```
perl -pe 's/^(\d+) (\w+) (\d+)(\d{4})(\d{5})$/$1#$2#$3#$4#$5/' temp.log >output.log
```

The regex magic going on there depends on a pretty rigid file format, so let me know if it breaks and I'll rewrite it for you.

Edit: If you're using this in a script you might not want to depend on perl.  In that case, wait for some awk-gurus to show up.

---

### Post by Pazzeo on 2010-05-09
Oh thanks very much...I think that I can follow your suggestion...but I try your perl command..but the result is equal to the original file.

Could you help me?

Thanks

Pazzeo

---

### Post by trent.josephsen on 2010-05-09
It works for me with your example line.  Please post some actual input along with the expected output and what you actually got.

---

### Post by Pazzeo on 2010-05-09
Sorry, my mistake...your script works very well, but I wrote a wrong example string. The correct is 

20100507130238 - TEST - 06247231701000100200500000

and I want a result like this:

20100507130238#TEST#06247231701000100#2005#000

Could you explain me how it works? 

Thank you very much

Paz

---

### Post by trent.josephsen on 2010-05-10
Sorry for the late reply.  Here's the amended version:

```
perl -pe 's/^(\d+) - (\S+) - (\d+)(\d{4})(\d{5})$/$1#$2#$3#$4#$5/' temp.log >output.log
```

perl -p tells the Perl interpreter to go through the input line by line, printing each line, just like cat.  The -e <CODE> switch tells Perl to execute <CODE> on each turn through the loop, just before printing the line.  In this case, the code to be executed is the string (single quoted) 's/^(\d+) - (\S+) - (\d+)(\d{4})(\d{5})$/$1#$2#$3#$4#$5/'

Now, that's rather intimidating, but it breaks down fairly quickly.  The s is the start of a **s**ubstitution:  Everything between the following two forward slashes is a regular expression, which if it matches the string will be replaced by all the text up to the following slash.  That is, s/REGEX/REPLACEMENT/ replaces all instances of REGEX in the line with REPLACEMENT before printing it out.

So, the regular expression here is '^(\d+) - (\S+) - (\d+)(\d{4})(\d{5})$'.  The ^ and $ mark the beginning and end of the string (so it will refuse to match only a part of the string).  Parentheses are used for capturing groups of characters to be used in the replacement string.  You can see the " - " which is just a literal match for the text " - " in your input.  \d matches a digit and \S matches a non-whitespace character.  The + modifier says "match that last thing as many times as you can, at least once" and the {5} modifier says "match that last thing exactly 5 times".

This regex will match any string that starts with a group(1) of digits, followed by the literal text " - ", followed by a group(2) of non-whitespace characters, followed by the literal text " - ", followed by another group(3) of digits, followed by a group(4) of 4 digits followed by a group(5) of 5 digits.

The numbers in the paragraph above indicate what parts of the string are captured into groups by the parentheses in the regular expression.  These groups are accessible by the special variables $1 through $5, respectively.  Those variables are used in the next part -- the replacement string.

The replacement string is $1#$2#$3#$4#$5, which is the lazy man's way of mashing together the strings $1, $2, $3, $4, and $5 with hashes in between them.

This script won't match a line if the TEST text contains whitespace (tab or space characters).

I'm sure this all looks and sounds like a horrible mess, but it's generally quite easy to write when you get the hang of it.  If you're interested in Perl, I can strongly recommend the book *Learning Perl* from O'Reilly, which will get you started.

---

### Post by hannaman on 2010-05-11
Sed can accomplish what you are asking as well.
```
sed -ne '/TEST/s/ - TEST - /#TEST#/' -e '/TEST/s/2005/#2005#/p' file.log >> output.log
```
This will search through temp.log for lines with the pattern TEST and then replace - TEST - with #TEST# and replace 2005 with #2005# before saving the result to output.log.  It will ignore any lines that do not contain TEST and only save the lines that have been changed to output.log.

This will do the substitution based on specific text in the file and doesn't depend on that text being a specific location on the line.  Also, this can be put directly into a bash script.

Perl (like in the previous example) will probably do what you want better, but I don't know perl at all.

---

### Post by Pazzeo on 2010-05-14
Thank you so much for your help, I resolve using the perl. 

@trent.josephsen thank you so much for your quickly lesson on perl, it was clear and it helped me more. 

Regards,

Pazzeo

---

