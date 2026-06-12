---
title: "[SOLVED] basic python question - check if a string contains some text?"
date: 2008-01-18
forum: Programming Talk
---

### Post by ryanVickers on 2008-01-18
I am aware that in bash you can go
```

if [[ $var =~ "value" ]]; then

```and this will check for if the variable "var" _contains_ the text "value".  How would one go about doing this in python?
so far, I have
```

if var == value:

```but that is of course to check if it is solely *equal* to it - I want to detect if it *contains *it :confused:

---

### Post by Mr.popo on 2008-01-18
```

var = "value"
if "value" in var:
    print "True"

```

Do you mean that?

---

### Post by ryanVickers on 2008-01-18
with the exception of the fact that "var" will be ever changing user input, I believe this will do quite nicely :D

---

