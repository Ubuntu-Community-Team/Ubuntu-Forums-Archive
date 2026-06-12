---
title: "Regular expressions help (sed)"
date: 2011-06-06
forum: Programming Talk
---

### Post by lordhaworth on 2011-06-06
Hi all,

I am rather new to scripting and am only starting to learn as it has become necessary. I am enjoying it, but I am currently having some trouble with the following...

Within a file, I have a line that contains something like "example0004.txt" that I want to have identified and replaced with some other numeric code (0006 or something). What I am having trouble with is locating the "example0004.txt" to replace (the new filename has already been established). I currently have:
> 
sed -e  "s/example*.txt/$filename/g" foo.txt > bar.txt



but this doesn't pick it up when the script runs.

Does anyone have any suggestions or advice?

Cheers

---

### Post by Vaphell on 2011-06-06
in regexes used by sed * does not consume chars by itself like it does in bash, it adds an 'any number' modifier to the symbol preceding it. Another thing - dot means 'any char', so in your case you look for exampl[any number of 'e'][any symbol]txt

```
$ x=666; echo 'example111.txt' | sed -r 's/(example)([0-9]*)([.]txt)/\1'$x'\3/g'
example666.txt
```

ignore me using echo to feed the example data to sed. Sed expression will work the same in your case. Dots are troublesome, i usually put them in [ ] as enumeration of allowed chars (which [ ] are used for) strips the special meaning of dot. [0-9]* obviously means any sequence of digits, \1 and \3 return values of capturing groups (parentheses, counting from 1)

---

### Post by lordhaworth on 2011-06-06
Ahhhh,

Thank you!

Much to learn obviously

Cheers again

---

### Post by lordhaworth on 2011-06-06
For those who might be interested, I got it working with the following:


sed -e  "s/example...."."txt/$filename/" foo.txt > bar.txt

which is example[anychar][anychar][anychar][anychar][.txt]. Use of the " " around the . of .txt is to treat it as a full stop rather than a dot wildcard. 

There are probably nicer ways, but this worked for now.

---

### Post by Vaphell on 2011-06-06
read my post earlier, i edited it after you replied (which i didn't see as edit doesn't refresh the thread) to add example of things you can do with sed regexes.

---

### Post by lordhaworth on 2011-06-06
Thanks, your example is very useful

---

### Post by SeijiSensei on 2011-06-06
> **lordhaworth said:**
> sed -e  "s/example...."."txt/$filename/" foo.txt > bar.txt

That will match "example.001.txt" but it will also match "examplexabcetxt".  Here's a way to match only numbers:

```
sed -e 's/example[0-9]+\.txt/something/g'
```

That matches a string that begins with "example" followed by an unspecified number (>0) of digits, followed by ".txt".  Note the use of the "backslash" or "escape" character (\) to tell sed that the following character is to be treated as a literal period and not a placeholder.

You can further limit matches to "example" followed by three digits like this:

```
sed -e 's/example[0-9]{3}\.txt/something/g'
```

Now "example003.txt" will match but not "example02.txt" or "example0004.txt".

The man page for grep ("man grep" at a prompt) gives a quick overview of regular expression syntax.  I recommend searching Google for "regular expression tutorial" to get more help.

---

### Post by lordhaworth on 2011-06-06
Thanks,

It's a heck of a lot more beneficial to look at code segments (that to the beginner can look incomprehensible) when I already know what they *should* be doing

---

