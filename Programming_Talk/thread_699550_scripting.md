---
title: "scripting"
date: 2008-02-17
forum: Programming Talk
---

### Post by vurt on 2008-02-17
Hello, I'm developing a script for school and have a question about the cut command.  I've cut a field and now I need to cut that field into 4 parts, is cut the most efficient way to do this? Or is there an alternative?

What I can't figure out is how to cut those fields and operate on them.

---

### Post by nick_h on 2008-02-17
It depends what you want to do with the output, but *cut* would seem to be a good option.

---

### Post by ghostdog74 on 2008-02-17
> **vurt said:**
> Hello, I'm developing a script for school and have a question about the cut command.  I've cut a field and now I need to cut that field into 4 parts, is cut the most efficient way to do this? Or is there an alternative?

What I can't figure out is how to cut those fields and operate on them.

show your code and a sample of what you are cutting. then describe how you want the output to look like

---

### Post by stroyan on 2008-02-17
Bash can be helpful in parsing fields without running external commands like cut.
You can use a temporary setting of the IFS variable to choose what characters seperate fields.
You can then use array assignment or reading from a 'here string' to assign fields to variables.
You can also use the "${var:start:length}" feature to cut at numbered columns.
```
$ field=one,two,three,four
$ IFS=, parts=($field)
$ echo ${#parts[@]}
4
$ echo "${parts[0]} ${parts[3]}"
one four
$ IFS=, read p1 p2 p3 p4 <<< "$field"
$ echo $p1
one
$ echo $p3
three
$ field="AB123zz"
$ num=${field:2:3}
$ echo $num
123
$
```

---

