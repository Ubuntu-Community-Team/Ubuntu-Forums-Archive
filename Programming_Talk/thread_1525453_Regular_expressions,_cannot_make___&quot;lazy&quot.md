---
title: "Regular expressions, cannot make *  &quot;lazy&quot;"
date: 2010-07-06
forum: Programming Talk
---

### Post by yc2 on 2010-07-06
When I use the * or + to repeat characters, they always include the longest possible match.

How can I make the output of the sed-command below be:
 three two four five
i.e.
how can I make the searchpattern of the substitute command stop at the *first* "two"?

```
$ echo 'one two three two four five' | sed -e 's/^.*two//'
 four five
$ echo 'one two three two four five' | sed -e 's/^.*?two//'
one two three two four five
$ echo 'one two three two four five' | sed -e 's/^.*\?two//'
 four five
```

Thanks a lot.

---

### Post by Reiger on 2010-07-06
Those are “extended” regular expressions so you perhaps the -r flag will do what you need?

---

### Post by Trumpen on 2010-07-06
As far as I know, sed doesn't support lazy operators. You have to make them
manually:

```
$ echo 'one two three two four five' | sed 's/two/\x0/; s/.*\x0//'
 three two four five
```

where '\x0' is a character that is not contained in the input stream.

---

### Post by yc2 on 2010-07-07
Thank you for the information. This became a little more complicated than I first thought.

I found a property of sed/substitute to replace the n:th occurrence of the search-pattern. I think it will also come in useful for me now.

```
$ echo 'one two hello three hello four hello five six' | sed 's/hello/\x0/2;'
one two hello three  four hello five six

```(2:nd occurrence of "hello")

I am sometimes forced to work in different environments (Linux, Windows) where I can't really control what tools are available. I still often think the most straightforward way to solve some editing problems is to make a program. In my situation I have found that writing a PHP-program using preg_replace (basically regex and sed-substitute), explode and other PHP string manipulation tools has sometimes been the easiest way for me. (I have a server where I can always access PHP)

Learning Perl or AWK would open new doors, but for the time being I do not have the time and will stick with sed/regexp and when it fails (= I don't know enough) go to PHP.

I can't really remember any good example now, but with regex/sed I have sometimes felt that I can't get further, but with a programming language there is always a solution, although sometimes including some sweat :)

---

### Post by trent.josephsen on 2010-07-07
You can use perl as a quick-n-dirty sed replacement in cases like this.

```
$ echo 'one two three two four five' | perl -pe 's/^.*?two//'
```

The -p switch just makes perl behave like sed.  No special Perlish knowledge required.  I use this a lot because I tend to use Perl regexes and it's easier just to change the invocation of the program than translate the regex to sed syntax.

---

### Post by yc2 on 2010-07-07
Thanks Trent,

That was a useful one. The lazy star has entered my system.

- - - -

Maybe the following is a topic for another thread, but it is related.

I sometimes (using sed) just put the following text (together with other text) on some lines: "TO_BE_DELETED".

When I have come to a certain point I want to remove all lines containing "TO_BE_DELETED". I therefore do:

```
sed '/TO_BE_DELETED/d'
```

However, before I have deleted them all I sometimes want to work on lines NOT containing this pattern.

Is there any command that can do this. I need the opposite of the code-box above. It would mean:
If the string "xyz.." is NOT present on this line, do ...

In sed there is [^abc] but this, naturally, individual characters. i would need the same thing for entire strings. Is there anything like it?

---

### Post by yc2 on 2010-07-07
I think I found a solution to what I asked. To act on the lines NOT marked one should add an "!"
```
sed '/TO_BE_DELETED/!s/foo/bar/'

```

---

