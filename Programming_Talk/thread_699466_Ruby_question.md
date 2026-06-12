---
title: "Ruby question"
date: 2008-02-17
forum: Programming Talk
---

### Post by Sir Nose on 2008-02-17
Well, I'm kinda tired and need a better solution to this thing:
I need to convert fixnums into binary strings. I've been doing it like this:

```

array = [ value & 255, (value >> 8) & 255, (value >> 16) & 255, (value >> 24) & 255 ]
b = array.pack("CCCC")

```

Looks nasty and needs to be readjusted for each different integer size. Is there a better way?

---

### Post by a9bejo on 2008-02-17
[php]
11.to_s(2)   # => "1011"
[/php]

[Fixnum#to_s](http://ruby-doc.org/core-1.9/classes/Fixnum.html#M001119)

---

