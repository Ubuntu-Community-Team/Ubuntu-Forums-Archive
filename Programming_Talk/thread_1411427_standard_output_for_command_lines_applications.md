---
title: "standard output for command lines applications"
date: 2010-02-19
forum: Programming Talk
---

### Post by vincentberenz on 2010-02-19
Dear all,

When running a command line application, usually the output can be caught using | or redirected to a file using > or >>.
But sometime it is not. As an example, if you use the application "dict" like :

```
dict coach >> foo.txt
```then "foo.txt" contains definitions of "couch" and so on.

But if you use a word that is not in the dictionary :

```
dict coah >> foo.txt
```then nothing is printed in foo.txt and other information are displayed in the console.
(in that particular case : 
"No definitions found for "coah", perhaps you mean:
gcide:  CoA  Corah  coach  Noah  COOH  cosh  Coag  Coak  Coal  Coat  Coax
wn:  coach  noah  cosh  coal  coat  coax")

It turns out it is this output I am trying to catch in a file.

Is there any way I can redirect this output ? (for running into scripts).

Many thx

---

### Post by falconindy on 2010-02-19
This is because there are two different methods of output, stdout and stderr. I won't get into details about how they differ, but you have a few options as to how to capture it:

Capture only output sent to stderr
```
dict coah 2> foo.bar
```

Capture output from stderr and stdout in different files
```
dict coah 2> foo.bar > foo.baz
```

Capture output from stderr and stdout in the same file
```
dict coah > foo.bar 2>&1
```

And in Bash only, this shortcut exists for the above
```
dict coah &> foo.bar
```

In any of the examples above, you can freely replace a single > with a double >> to append.

---

### Post by vincentberenz on 2010-02-19
that's working great ! thanks a lot

---

