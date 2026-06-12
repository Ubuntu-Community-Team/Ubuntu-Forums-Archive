---
title: "perl question -- qr//;"
date: 2009-02-11
forum: Programming Talk
---

### Post by badperson on 2009-02-11
Hi,

I'm having a problem with this code:

```
my $pattern = qr/j.*n/msi;

print $pattern, "\n";

my $string = "my name is jason, yes it's jason";
print $string, "\n";

$string =~ s{$pattern}{anna}mg;

print $string, "\n";

```

it outputs this:

> (?msi-x:j.*n)
my name is jason, yes it's jason
my name is anna



but it should out put:
> my name is jason, yes it's jason
my name is anna, yes it's anna

thanks,
bp

---

### Post by badperson on 2009-02-11
btw, I also tried this:

```
$string =~ s/$pattern/anna/mg;
```
which is normally how I would write it...was just trying the curlies to see if it would make a difference.
bp

---

### Post by unutbu on 2009-02-11
Regexps are "greedy" by default. So the regexp j.*n will match as much of the string as possible. Given the string "my name is jason, yes it's jason", the regexp matches "jason, yes it's jason" since that is the first string that starts with a "j" and ends with an "n". 

To make a minimal (ungreedy?) regexp, use the question mark:
```

my $pattern = qr/j.*?n/msi;
```

---

### Post by badperson on 2009-02-11
thanks...I HATE it when the answer turns out to be some little thing I overlooked...:lolflag:

---

### Post by nvteighen on 2009-02-11
> **badperson said:**
> thanks...I HATE it when the answer turns out to be some little thing I overlooked...:lolflag:
Welcome to Perl :D

---

