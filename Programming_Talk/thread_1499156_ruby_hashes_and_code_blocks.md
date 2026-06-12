---
title: "ruby hashes and code blocks"
date: 2010-06-01
forum: Programming Talk
---

### Post by cybo on 2010-06-01
i'm trying to learn ruby but there are a lot of things i can't understand. the book i am reading right now is good but there are few lexical things i don't understand

here is the code i can't figure out

```
@at_callbacks = Hash.new{|hash, key| hash[key] = []}
```

i would really appreciate an explanation of what is happening there.

thanks

---

### Post by stylishpants on 2010-06-01
This code is declaring a new Hash object.  It's stored in the variable @at_callbacks, which is an instance variable because it uses the @ sigil.

The Hash constructor is receiving a closure which will be used when a non-existent key is referenced.  In this case, it is simply specifying that if a non-existent hash key is referenced, then add that key to the hash and give it an empty Array object as its value.



Here we get back "nil" when we request a key that does not exist:
```
bob@cob:~$ irb
irb(main):001:0> h = Hash.new
=> {}
irb(main):002:0> h["one"] = 1
=> 1
irb(main):003:0> h
=> {"one"=>1}
irb(main):004:0> h["two"]
=> nil

```

Here we get back an empty array instead of "nil" when we request a key that does not exist:

```
irb(main):005:0> h = Hash.new { |h,k| h[k] = [] }
=> {}
irb(main):007:0> h["two"]
=> []
irb(main):008:0> h
=> {"two"=>[]}
 
```


You should install the ri package from the repositories and use that to see the documentation on things like this, it will help your ruby learning.  Install "ri" then type "ri Hash.new" for the official documentation on this, with examples.

---

### Post by cybo on 2010-06-02
stylishpants

thanks for the help.

---

