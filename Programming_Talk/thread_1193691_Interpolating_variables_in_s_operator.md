---
title: "Interpolating variables in s/// operator"
date: 2009-06-21
forum: Programming Talk
---

### Post by soltanis on 2009-06-21
I'm trying to find and substitute for a variable expression in perl. Basically, I store $field and $value like this:

```

$field: $value

```

In some text file. Now I want to change the $value under $field, so I open up the file, read it in, and now I want to do something like this:

```

$file =~ s/^$field: (\w*)$/$field: $value/i

```

But I am not sure if I am allowed to simply put the variables in there and expect them to interpolate. Is this allowed in Perl, or do I have to use something different (and if so, what?)

---

### Post by ghostdog74 on 2009-06-21
so why don't you run your code and find out if its workable?

---

### Post by soltanis on 2009-06-22
Yup.

---

