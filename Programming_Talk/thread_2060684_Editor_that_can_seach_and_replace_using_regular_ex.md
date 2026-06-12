---
title: "Editor that can seach and replace using regular expressions needed"
date: 2012-09-20
forum: Programming Talk
---

### Post by sefs on 2012-09-20
Hi there,

Does anyone know of an editor that can search and replace with regex?

I've tried both bluefish and geany but they can only search with a regex but not replace with a regex.

Bluefish seems to support groups, while geany does not.
But can't get bluefish to work with regex in replace field.


I want to search for this:

```

(?'prefix'[<][t][i][n][>][0-9]{6})(?'dash'[-])(?'suffix'[0-9]{4}[<][/][t][i][n][>])

```

and replace with:

```

${prefix}${suffix} 

```

or

```

$1$3

```

Thanks.

---

### Post by MG&amp;TL on 2012-09-20
I think the obvious answer is one of the command-line editors. My personal favourite is vim. But I daresay the original vi and all of the emacs varieties has what you want. In vim, you have a Perl-like syntax for find/replace.

```
:%s/old/new/
```

will do what you're after.

---

### Post by trent.josephsen on 2012-09-20
Vim.

What kind of regex syntax is that? Does surrounding a single character in brackets (which usually means a character class) serve any purpose, or is this basically (Perlish)

```
s/(<tin>[0-9]{6})-([0-9]{4}<\/tin>)/$1$2/g
```

---

### Post by sefs on 2012-09-20
Bluefish supports Pcre,

So my codes were wrong.

I had to use,

Search:
```

(?P<prefix>[<][t][i][n][>][0-9]{6})(?P<dash>[-])(?P<suffix>[0-9]{4}[<][/][t][i][n][>])

```

Replace:
```

\1\3

```

---

### Post by sefs on 2012-09-20
> **trent.josephsen said:**
> Vim.

What kind of regex syntax is that? Does surrounding a single character in brackets (which usually means a character class) serve any purpose, or is this basically (Perlish)

```
s/(<tin>[0-9]{6})-([0-9]{4}<\/tin>)/$1$2/g
```

I am a newbie so I will use yours instead. :)

---

### Post by sefs on 2012-09-20
> **trent.josephsen said:**
> Vim.

What kind of regex syntax is that? Does surrounding a single character in brackets (which usually means a character class) serve any purpose, or is this basically (Perlish)

```
s/(<tin>[0-9]{6})-([0-9]{4}<\/tin>)/$1$2/g
```

Some questions 

1/ why did you escape out "/", I don't think it's a special character, is it?

2/ Does your circle brackets indicate grouping? and the /$1$2/g is the naming?

Bluefish did not recognize this form of group naming.

It does however work with this modification:

```

(?P<prefix><tin>[0-9]{6})-(?P<suffix>[0-9]{4}</tin>)

```

Love how you were able to compress it into a small elegant way like that.

---

### Post by trent.josephsen on 2012-09-21
> **sefs said:**
> 1/ why did you escape out "/", I don't think it's a special character, is it?
Maybe not when you're typing a regex into a box. In Perl/sed/Vim/I don't know what else, s/PATTERN/REPL/ is the construct for search-and-replace. The / must be escaped to prevent the parser mistaking it for the end of the PATTERN.

> 2/ Does your circle brackets indicate grouping? and the /$1$2/g is the naming?
Bingo! Well, almost. The slashes are just part of the s/PATTERN/REPL/ syntax. 'g' is a pattern modifier, short for "global" -- it says, "do this replacement everywhere PATTERN occurs on the current line", as opposed to only the first occurrence. This wouldn't matter if you only ever see one instance of <tip>whatever</tip> on a given source line.

Group naming is something I've never felt my regexes were complex enough to warrant. I'm surprised if Bluefish doesn't support numbering.

---

### Post by sefs on 2012-09-21
> **trent.josephsen said:**
> Maybe not when you're typing a regex into a box. In Perl/sed/Vim/I don't know what else, s/PATTERN/REPL/ is the construct for search-and-replace. The / must be escaped to prevent the parser mistaking it for the end of the PATTERN.


Bingo! Well, almost. The slashes are just part of the s/PATTERN/REPL/ syntax. 'g' is a pattern modifier, short for "global" -- it says, "do this replacement everywhere PATTERN occurs on the current line", as opposed to only the first occurrence. This wouldn't matter if you only ever see one instance of <tip>whatever</tip> on a given source line.

Group naming is something I've never felt my regexes were complex enough to warrant. I'm surprised if Bluefish doesn't support numbering.

Thanks a mil, that helped!

---

### Post by Vaphell on 2012-09-21
> The / must be escaped to prevent the parser mistaking it for the end of the PATTERN.
actually / is not a fixed part of the 's/pattern/replace/occurence' syntax in sed (haven't tested other tools)
First symbol after s is to be treated as a delimiter and by using something else than / you avoid the problem with let's say file paths completely
```
$ echo /a/c/b/c/b/c/b/c | sed 's[COLOR="Red"]a[/COLOR]/[COLOR="Red"]a[/COLOR]X[COLOR="Red"]a[/COLOR]g'
XaXcXbXcXbXcXbXc
```
/ is needed only in regex patterns filtering lines.
```
sed '[COLOR="Red"]/[/COLOR]pattern[COLOR="Red"]/[/COLOR] s_pattern_replace_'
```

---

### Post by trent.josephsen on 2012-09-21
> **Vaphell said:**
> actually / is not a fixed part of the 's/pattern/replace/occurence' syntax in sed (haven't tested other tools)
First symbol after s is to be treated as a delimiter and by using something else than / you avoid the problem with let's say file paths completely
Quite right, thanks for mentioning it. Actually I originally used # but I figured that was unnecessary. Although if I'd realized it could be cause for confusion I probably would have left it. One grows accustomed to reading regexes in // after a while.

---

