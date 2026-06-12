---
title: "Basic Perl text substitution"
date: 2012-05-21
forum: Programming Talk
---

### Post by hailholyghost on 2012-05-21
Hello,

I would like to combine these two Perl substitutions

```
my $name = $file;
$name =~ s/.out$//;
$name =~ s/^nmr//;
```

into a single command, just like sed can do:

```
sed -e 's/^nmr//g' -e 's/out$//g'
```

I know that Perl was meant to mimic the way that sed works, but it doesn't work *exactly* the same.

The program I have now works, but I would like to make it better.

Thanks very much!

---

### Post by trent.josephsen on 2012-05-21
Like this?

```
perl -pe 's/.out$//; s/^nmr//'
```

---

### Post by wallaroo on 2012-05-21
How about ..
```
$name =~  s/.out$|^nmr//g;
```

---

### Post by hailholyghost on 2012-05-22
Hi wallaroo,

Yep that worked!

Thanks so much!

and to trent.josephsen, I should have specified that I meant with a perl text file.  My bad!

-Dave

---

### Post by shawnhcorey on 2012-05-22
> **hailholyghost said:**
> Hello,

I would like to combine these two Perl substitutions

```
my $name = $file;
$name =~ s/.out$//;
$name =~ s/^nmr//;
```

into a single command, just like sed can do:

```
sed -e 's/^nmr//g' -e 's/out$//g'
```

I know that Perl was meant to mimic the way that sed works, but it doesn't work *exactly* the same.

The program I have now works, but I would like to make it better.

Thanks very much!

Why? Doing so makes your code harder to understand. Avoid micro-optimization; it never improves the code.

---

### Post by trent.josephsen on 2012-05-22
shawnhcorey is correct; combining the two into a single substitution is not an improvement (and will probably hurt your performance rather than the reverse).

Also, I'd like to observe that . matches any character, so your first substitution will change 'about' to 'a'. If you want to match a literal ., escape it.

---

### Post by David Andersson on 2012-05-22
> **hailholyghost said:**
> 
I would like to combine these two Perl substitutions

```
my $name = $file;
$name =~ s/.out$//;
$name =~ s/^nmr//;
```

into a single command

All the answers above are *correct* and *works*. My answer is a *different* approach.

If we look at it as *idioms*, the above is basically "*remove things we don't want*" so at the end "*what remains is what we want*". I'll suggest "*pick out what we want*" and in this case "*express what we want by its context*".

```
if ($file =~ m/^nmr(.*)\.out$/) { 
  $name = $1;
}
```

The thing in parenthesis is captured in variable $1 (and $2 etc).

This *pick things* behaves slightly different in certain cases, compared to the *remove things*. If *$file* does not match, *$name* will be unset, instead of being a copy of *$file*. If that is good or bad depends on the rest of the program. For example, if it would be an error for *$file* not to have "nmr" and ".out" in it the code could be extended like this:

```
if ($file =~ m/^nmr(.*)\.out$/) {
  $name = $1;
} else {
  die "file name didn't contain a name\n";
}

```

Another example (where both context and content matters): if *$name* must be a number, then change the pattern to **^nmr(\d+)\.out$** .

---

