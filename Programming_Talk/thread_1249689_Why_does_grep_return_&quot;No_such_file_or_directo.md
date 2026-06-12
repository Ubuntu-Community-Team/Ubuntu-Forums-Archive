---
title: "Why does grep return &quot;No such file or directory&quot;?"
date: 2009-08-25
forum: Programming Talk
---

### Post by bostonaholic on 2009-08-25
Here's my find/grep

```
> find . -name "*.*" | xargs grep -in "patch_add"
grep: ./tools/jpd_generator/JPD: No such file or directory
grep: Virtual: No such file or directory
grep: Processes/build.xml: No such file or directory
grep: ./tools/jpd_generator/JPD: No such file or directory
grep: Generation/build.xml: No such file or directory
grep: ./tools/jpd_generator/JPD: No such file or directory
grep: Generation: No such file or directory
grep: Test/build.xml: No such file or directory
grep: ./tools/jpd_generator/JPD: No such file or directory
grep: Runtime: No such file or directory
grep: Support/build.xml: No such file or directory

```
but
```
grep -inr "patch_add" *
```
returns the correct results.  Are they not [effectively] the same search?

---

### Post by Arndt on 2009-08-25
> **bostonaholic said:**
> Here's my find/grep

```
> find . -name "*.*" | xargs grep -in "patch_add"
grep: ./tools/jpd_generator/JPD: No such file or directory
grep: Virtual: No such file or directory
grep: Processes/build.xml: No such file or directory
grep: ./tools/jpd_generator/JPD: No such file or directory
grep: Generation/build.xml: No such file or directory
grep: ./tools/jpd_generator/JPD: No such file or directory
grep: Generation: No such file or directory
grep: Test/build.xml: No such file or directory
grep: ./tools/jpd_generator/JPD: No such file or directory
grep: Runtime: No such file or directory
grep: Support/build.xml: No such file or directory

```
but
```
grep -inr "patch_add" *
```
returns the correct results.  Are they not [effectively] the same search?

I think you have files like "./tools/jpd_generator/JPD Virtual", with spaces in them. The names will fall apart into pieces during the processing.

But you can use the option -print0 with 'find', and -0 with 'xargs', and it will work.

---

### Post by geirha on 2009-08-25
```

find . -name "*.*" -exec grep -in "patch_add" {} +

```

---

### Post by bostonaholic on 2009-08-25
> **Arndt said:**
> I think you have files like "./tools/jpd_generator/JPD Virtual", with spaces in them. The names will fall apart into pieces during the processing.

But you can use the option -print0 with 'find', and -0 with 'xargs', and it will work.

thanks, that seemed to have worked.
```
find . -print0 -name "*.*" | xargs -0 grep -in "patch_add
```

---

