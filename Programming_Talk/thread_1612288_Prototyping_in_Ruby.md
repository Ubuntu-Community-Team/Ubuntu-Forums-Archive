---
title: "Prototyping in Ruby"
date: 2010-11-03
forum: Programming Talk
---

### Post by nova47 on 2010-11-03
Say you have a series of small classes in Ruby that for convenience's sake you put in one file. (In my case I'm writing an interpreter for a BNF grammar so I've got something like 20 classes.) How do I make it so I can use code anywhere within the file? My current issue is the following

[PHP]
class A
 def initialize
    @instance = B.new
 end
end

Class B
end

[/PHP]

The issue is that this is illegal because when I go to create a new class B the interpreter doesn't know about the Class B below. How do I prototype it so that I don't have to have Class B declared before Class A?

---

### Post by schauerlich on 2010-11-03
I'm fairly new to Ruby, so take this with a grain of salt, but as long as you don't call "A.new" between the definitions of A and B, i think you should be fine. Assuming the flow control doesn't actually move into that class before its definition has been read. Or am I misunderstanding?

---

### Post by nova47 on 2010-11-04
I'm not sure I understand what you mean by between the definitions of A and B. In Ruby you can't have any code that's not part of a class so you wouldn't be able to call A.new between the definitions (unless you inserted another class). But I am positive that the current code will throw an error.

---

### Post by dwhitney67 on 2010-11-04
> **nova47 said:**
> .. In Ruby you can't have any code that's not part of a class ...

That's news to me.

Here's some code I was tinkering with recently:
```

class A
        def initialize
                @b = B.new
                puts 'Instance of class A created.'
        end
end

class B
        def initialize
                puts 'Instance of class B created.'
        end
end


a = A.new

```

---

### Post by schauerlich on 2010-11-04
Basically, when the reader gets to A.initialize, all it says is "something named B will have 'new' called on it." It isn't until A.initialize is actually CALLED (via A.new) that it actually ever looks up what B is, or if it has a 'new' method. That's why dwhitney67's example works (B has been read in before A.new is ever called), while this one does not:

```
class A
        def initialize
                @b = B.new
                puts 'Instance of class A created.'
        end
end

# reader gets here, then flow jumps up to A.initialize above - class B is never read!
a = A.new

class B
        def initialize
                puts 'Instance of class B created.'
        end
end

```

---

### Post by nova47 on 2010-11-04
Ya I just saw what you meant and that does work. I think the moral is just to use the def initialize method. It makes life easier lol. Thanks for the help I got it all sorted out.

---

