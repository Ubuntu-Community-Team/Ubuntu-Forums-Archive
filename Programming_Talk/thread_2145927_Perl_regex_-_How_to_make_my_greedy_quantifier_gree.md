---
title: "Perl regex - How to make my greedy quantifier greedier?"
date: 2013-05-16
forum: Programming Talk
---

### Post by cibalo on 2013-05-16
Hello schragge and trent.josephsen,

Thank you very much for your valuable reply.

Both of your suggestions worked for me.

Now, I have the following outputs.
```
$ find testing -type f -name "[a-z]*\.txt"
testing/dir.a/dir_b/dir-c/this-is-testing4_org.txt
testing/dir.a/dir_b/dir-c/this_is_testing3_org.txt
$ ls testing/dir.a/dir_b/dir-c/* | perl -ne 'm{^(.*/)([a-z][^/]*)$} && print'
testing/dir.a/dir_b/dir-c/this_is_testing3_org.txt
testing/dir.a/dir_b/dir-c/this-is-testing4_org.txt
$ ls testing/dir.a/dir_b/dir-c/* | perl -MFile::Basename -ne 'print if basename($_) =~ /^[a-z]/'
testing/dir.a/dir_b/dir-c/this_is_testing3_org.txt
testing/dir.a/dir_b/dir-c/this-is-testing4_org.txt
```

Best Regards,
cibalo

---

### Post by trent.josephsen on 2013-05-16
Can you be a little more clear? What's wrong with what the find command outputs?

Changing the greediness of quantifiers only changes what certain subpatterns will match, and can make a pattern match more or less efficient, but can't change whether the pattern as a whole will match.

Or do you want non-backtracking? I think that's possible by some switch or other. Not the best way to do what looks to be a simple match, though.

---

### Post by cibalo on 2013-05-17
I just want to know if perl regex can get the same result as my find command outputs.
Maybe my regex is wrong.
 However, if you have any idea that make the perl regex works.

---

### Post by schragge on 2013-05-17
As **trent.josephsen** said, preventing backtracking should help here
```
perl -ne 'print $1, " - ", $2, "\n" if /^((?>.*\/))([a-z].*)$/'
```
But then, why not just
```
perl -ne 'print $1, " - ", $2 if m{^(.*/)([a-z][^/]*)$}'
```

---

### Post by trent.josephsen on 2013-05-17
Right, that was exactly what I was going to suggest. Non-backtracking subpatterns are an advanced technique I wouldn't really use for something this simple.

Then again, I'd probably use File::Basename, which makes the intent a bit more explicit:

```
$ ls testing/dir.a/dir_b/dir-c/* | perl -MFile::Basename -ne 'print if basename($_) =~ /^[a-z]/'
testing/dir.a/dir_b/dir-c/This-is-testing2_org.txt
testing/dir.a/dir_b/dir-c/This_is_testing1_org.txt
```

Even better, use /^[[:lower:]]/ for extra portability.

The reason your second pattern behaves the way it does is because you've provided no way to avoid the print statement. If the match fails, $1 and $2 don't get changed, and print displays the same things that matched last time through the loop. That's why both schragge's and my solutions use an if modifier.

TMTOWTDI as usual.

---

