---
title: "Regular Expression Question"
date: 2005-02-13
forum: Programming Talk
---

### Post by gab10 on 2005-02-13
I'm not too good with Regular Expressions... does anyone know the syntax to find all the strings that don't contain a particular phrase? I tried
```
(*somephrase*){0}
```
but that doesn't seem to work.

---

### Post by Koobi on 2005-02-14
[QUOTE=gab10]I'm not too good with Regular Expressions... does anyone know the syntax to find all the strings that don't contain a particular phrase? I tried
```
(*somephrase*){0}
```
but that doesn't seem to work.[/QUOTE]
 This should work.

```

[^somephrase]+

```

---

### Post by ow50 on 2005-02-14
[QUOTE=Koobi]This should work.
```
[^somephrase]+
```[/QUOTE]
Wouldn't that would equal```
[bcdfgijklnqtuvwxyz]+
```which would match lines that have at least one character not in 'somephrase'?


I dont know of a way to match not 'somephrase' with standard regexes. It depends on what app you're using.

Grep: ```
grep -Gv "somephrase" filename
```

Perl script:
```
while (<FILE>) {
    if ($_ !~ /somephrase/ ) { print "$_" }
}
```

Sed seems to have ! as negation operator, but I don't know how to use that.

---

