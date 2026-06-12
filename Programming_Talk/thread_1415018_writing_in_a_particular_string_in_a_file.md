---
title: "writing in a particular string in a file"
date: 2010-02-24
forum: Programming Talk
---

### Post by aceqbaceq on 2010-02-24
really need your help,

i need to read file line by line and check if the line matches the template, if so i want to replace it.

i've read about awk and sed, but don't understand how to set the following rule

the template = word1+any symbols+!word2+any symbols+word3

the string must have word1 and word3 but not have word2 at the same time.

i even can find out the numbers of stings that match the template by grep. but neither awk nor grep can't edit particular lines in the file like 2th line or 25th line.

How to do that?

---

### Post by Some Penguin on 2010-02-24
Looks to be a trivial task in Perl.

Pull in line.  Check word at beginning and word at end.  Use a grouping to capture the characters in the middle.  If the first check passes, run a second match on the captured group  against the excluded word.  No need for anything fancy like backreferences.

Check the 'perlre' manual page for details.

---

### Post by aceqbaceq on 2010-02-25
ok. i'm familiar with perl  a little bit. but i'm surprised whether 
there is no way out other than using such a monster as perl for this task.

thank you anyway

---

### Post by Some Penguin on 2010-02-25
*shrug*  Well, Perl was written for such tasks, and it makes such things easy. 

Like operating line-by-line --


```

my $line = undef;
while ($line = <STDIN>) {
...
}

```


If you wanted to find strings that started with Foo and ended with Bar (and the trailing newline or other whitespace), /^Foo.*Bar\s*$/ does it easily -- although you could make it slightly fancier to handle word boundaries (\b), case-insensitivity, or to capture the symbols in the middle (with parens).

And that lets you evaluate a second check on the middle group.


To do it in a single regular expression would be significantly more complicated.  It's possible, but it wouldn't be pretty.  Just trying to match an arbitrary non-empty sequence of characters that didn't have 'NO' in it, would probably have to look something like

```

  /^(([^N])|(N+[^NO]))+$/

```


and if it were LOLA that were forbidden, *something* like the monstrosity below (not bothering to write down the state machine for proper conversion to the regex -- this is handcoded, the correct answer may be more complicated).

(spaces below thrown in for clarity)

```

  /^(([^L])  | (L+[^LO]) | (L+O[^L]) | (((LO)+L)+[^AOL])$/

```

And it'd be unmaintainable and not generalizable.  So don't do it in one regex -- which means working with something designed to keep variables and captures and the like, for sanity's sake.

---

