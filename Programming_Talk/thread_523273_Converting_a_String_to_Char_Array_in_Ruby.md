---
title: "Converting a String to Char Array in Ruby"
date: 2007-08-11
forum: Programming Talk
---

### Post by Shack_ on 2007-08-11
I'm just getting started with Ruby, and I was wondering whether there was a simple method to convert a string into a character array. In Java you can do something like:

```

String word = "tomato";
word.toCharArray();

```

Is there a similar method in Ruby? If not, could someone show me how to do it? I'd appreciate the help.

---

### Post by Jessehk on 2007-08-11
In Ruby, at least in the current version, there are no chars. There are only strings.

However, you can split up a string in to an Array of single character strings.
There are several ways you could do this.

For example (an *irb* session):
```

$ irb
irb(main):001:0> "Hello, world!".split(//)
=> ["H", "e", "l", "l", "o", ",", " ", "w", "o", "r", "l", "d", "!"]
irb(main):002:0> "Hello, world!".scan(/./)
=> ["H", "e", "l", "l", "o", ",", " ", "w", "o", "r", "l", "d", "!"]

```

---

### Post by hypexr on 2009-10-05
FYI a quick little test I did showed that the scan method above is 1.6 times faster than the split.

---

### Post by Can+~ on 2009-10-05
> **hypexr said:**
> FYI a quick little test I did showed that the scan method above is 1.6 times faster than the split.

Unfortunately, your post wasn't all that fast.


*looks at date*

---

### Post by Jim_in_Germany on 2009-10-14
I know the thread is ages old, but maybe this will help someone.
You can also do this:

word = "tomato"
word.each_byte{|b| puts b.chr}

This would output:
t
o
m
a
t
o

The method each byte, takes a string apart byte by byte, returning the decimal value for the character at each index location.
You can then do what you want with it, for example convert it back into characters using the 'chr' method, or stick it into an array, or whatever.

---

### Post by celicni on 2010-01-03
> **Jim_in_Germany said:**
> I know the thread is ages old, but maybe this will help someone.
You can also do this:

word = "tomato"
word.each_byte{|b| puts b.chr}

This would output:
t
o
m
a
t
o

The method each byte, takes a string apart byte by byte, returning the decimal value for the character at each index location.
You can then do what you want with it, for example convert it back into characters using the 'chr' method, or stick it into an array, or whatever.

That works only for ASCII characters. Since Ruby strings are unicode, this solution is incomplete (would not work for all strings)

---

### Post by bvsatyaram on 2010-03-30
We can also do this:
```
word = "Nice dog"
word.chars.to_a
=> ["N", "i", "c", "e", " ", "d", "o", "g"]
```

---

### Post by LumbeeNDN on 2010-11-04
> **bvsatyaram said:**
> We can also do this:
```
word = "Nice dog"
word.chars.to_a
=> ["N", "i", "c", "e", " ", "d", "o", "g"]
```

...this looks alot cleaner, but didn't work for me!

```

\sandBox.rb:2: undefined method `chars' for "Nice dog":String (NoMethodError)

```

---

### Post by bvsatyaram on 2010-11-04
May be due to different ruby version.
I have ruby -v 1.8.7 installed on my box.

---

### Post by LumbeeNDN on 2010-11-06
...u'r right, I had v 1.8.6 on one system, and it was failing. Another laptop I have has 1.8.7, and I can use .chars there...

---

