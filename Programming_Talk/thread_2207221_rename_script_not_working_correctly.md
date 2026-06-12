---
title: "rename script not working correctly"
date: 2014-02-22
forum: Programming Talk
---

### Post by rebeltaz on 2014-02-22
I am trying to create a script that will remove extraneous info from a file name and uppercase only the first letter of each word.

I would like - 

AB - THIS IS A TEST FILENAME - EXTRA INFO   NOT NEEDED.EXT

to become - 

This.Is.A.Test.Filename.ext

I have come up with this:

```


rename 's/TZ - //' *.mp3
rename 's/ - .*/\.mp3/' *.mp3
rename 's/([A-Z])/\L$1/g' *.mp3
rename 's/([^A-Z)]/\U$1/' *.mp3
rename 's/ ([a-z])/\.\U$1/g' *.mp3

```

but it doesn't uppercase the first character. I get - 

this.Is.A.Test.Filename.ext

What am I doing wrong? I have tried moving the ^ to before the first [ as well as before the first ( but it still doesn't work. Any ideas? Thanks.

---

### Post by Lars Noodén on 2014-02-22
Be sure to do your experimenting while using -n so that it goes as a dry run and does not change anything.

You'll probably need to do several substitutions.  Maybe something like this?

```

rename -n 's/^[^-]* - //; [color=blue]s/ - .*\././;[/color] s/ /./g; [color=blue]s/\b(\w+)\b/\u\L$1/g;[/color] s/\.(\w+)$/.\L$1/' *.mp3

```

---

### Post by rebeltaz on 2014-02-22
Wow... I didn't know you could combine all of those steps into one. Good to know. 

I am trying to decode that line (which worked great, by the way). Since it is so different from mine, could you help me out and explain each step? I really am trying to learn how to do this one my own. Thanks :)

---

### Post by Lars Noodén on 2014-02-23
Sure.  It is most clear when taken line by line.  It's perl regular expression, the de-facto standard for the net.  

There's a lot online about perl regular expressions.  The perl documentation has [Perl regular expressions quick start](http://manpages.ubuntu.com/manpages/saucy/en/man1/perlrequick.1.html) or you can find a copy of "The Camel Book"  Perl regex and "perl-compatible" regex are really powerful and common and worth knowing.  

```

s/^[^-]* - //; # delete the beginning up to and including ' - '
s/ - .*\././;  # delete from the next ' - ' everything up to but not the period (putting the period back)
s/ /./g;       # swap all spaces for periods in the whole string
s/\b(\w+)\b/\u\L$1/g; # find each word in the whole string and convert it to title case
s/\.(\w+)$/.\L$1/     # find the word after the last period and convert it wholly to lower case

```

Here are the pieces:

[list]
[*]**^** at the beginning of a pattern means the beginning itself
[*]**$** at the end of a pattern means the end itself
[*]**.** means any character  .* means zero or more of any character, .+ means one or more of any character
[*]**\.** means an actual period
[*]**\w** means any character which can be a word (depends on locale, but includes a-z, 0-9)
[*]**\b** means a word boundary, can be a character or zero length
[*]**\u** means force next character to titlecase
[*]**\L** means force all of the next characters to lowercase
[*]**\u\L** together means put the next characters into lowercase, with the first being upper case
[*]**g** at the end of the s/// means apply the regex to the whole string not just the first occurance of the pattern
[*]**()** groups the result of a search and saves it for later, the first result is $1, the second $2, and so on
[*]**[]** means any single one of the characters inside [ and ]
[*]**[^]** means any single one character *except* the one(s) inside
[/list]

---

### Post by Vaphell on 2014-02-23
just for kicks, in pure bash it would go like this

```
for f in *.[mM][pP]3
do
    name=${f#*- }      # trim leftside *-
    name=${name% -*}   # trim rightside -*
    name=${name// /.}  # replace spaces with .
    name=${name,,}     # lowercase everything
    name=${name~}      # flip case of first chars
    ext=${f##*.}       # trim leftside greedy *.
    ext=${ext,,}       # lowercase everything
    mv -- "$f" "$name.$ext"
done
```
docs about parameter expansion
[http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html](http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html)

to prove that these spells work
```
$ f='AB - THIS IS A TEST FILENAME - EXTRA INFO NOT NEEDED.EXT'
$ name=${f#*- }; name=${name% -*}; name=${name// /.}; name=${name,,}; name=${name~}
$ ext=${f##*.}; ext=${ext,,}
$ echo $name.$ext
This.Is.A.Test.Filename.ext
```

---

### Post by rebeltaz on 2014-02-23
Awesome. Thank you very much. That's a little different from th regular expression that I've seen in the past. I'll have to study that a little more :)


@Vapell - Thank you, too... I think I need to learn one thing at a time :D Maybe next week I'll delve into the bash format :)

---

### Post by rebeltaz on 2014-02-27
I'm an idiot... after studying my code, I figured out the problem. Line four should have read [a-z] instead of [A-Z]. D'oh! So in case anyone else needs this:

```

rename 's/AB - //' *.mp3
rename 's/ - .*/\.mp3/' *.mp3
rename 's/([A-Z])/\L$1/g' *.mp3
rename 's/([a-z)]/\U$1/' *.mp3
rename 's/ ([a-z])/\.\U$1/g' *.mp3

```

 -or- (thanks to Lars for the ";" trick :) )
```

rename 's/AB - //; s/ - .*/\.mp3/; s/([A-Z])/\L$1/g; s/([a-z)]/\U$1/; s/ ([a-z])/\.\U$1/g' *.mp3

```


@Lars -> Your code worked perfectly, but I just had to figure mine out for my own knowledge. :) Thanks.

---

