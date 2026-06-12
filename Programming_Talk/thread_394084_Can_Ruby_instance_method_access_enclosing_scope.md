---
title: "Can Ruby instance method access enclosing scope?"
date: 2007-03-26
forum: Programming Talk
---

### Post by Ubuntist on 2007-03-26
Suppose I have a very simple class:

```

class Change
    attr_accessor :size
end
```Then I want a particular instance of this class to have an effect on an instance variable of an enclosing object:

```

class Accumulator
    attr_reader :chg
    def initialize
        @value = 0.0
        @chg = Change.new
        def @chg.size=(amount)
            @size = amount
            @value += amount  # @value intended to be that of instance of Accumulator
        end
    end
end
```In other words, after the following calls,
```

a = Accumulator.new
a.chg.size = 3.0
a.chg.size = -1.0
```I want ```
a.value
``` to return the accumulated values of the calls, 2.0 in this case.  Is there some way I can get to the value attribute of the instance of Accumulator from within the instance method chg.size?

When I try the code as written, Ruby interprets @value in the definition of @chg.size= to be an attribute of chg, not an attribute of the enclosing Accumulator object.

I can think of ways of getting the effect I want (e.g., a global variable), but none of them are very pretty.

Anybody got any ideas?

---

