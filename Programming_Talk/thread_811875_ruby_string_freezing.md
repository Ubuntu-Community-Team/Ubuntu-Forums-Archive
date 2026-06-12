---
title: "ruby string freezing"
date: 2008-05-29
forum: Programming Talk
---

### Post by finer recliner on 2008-05-29
im having trouble with a simple ruby script. I get an error that says:
```
`[]=': can't modify frozen string (TypeError)
```
I dont understand why my string is frozen, since i didnt call that function explicitly.
Here is my code:

```

class String
  #arbritrary function that increments the first character in a 
  #string and adds it to an array. the array is returned
  def stuff
    x = self
    ary = []
    3.times do
      ary << x
      x[0] += 1
    end
    return ary
  end
end


s = ARGV[0]
puts s.stuff


```

I tried changing the line:
```
s = ARGV[0]
```
to
```
s = String.new(ARGV[0])
```
so that 's' would be a copy of the command line argument. it runs, but now i just get the wrong output:
```

$ ruby help2.rb a
d
d
d

```

the expected output should be:
```

$ ruby help2.rb a
a
b
c

```


anyone know whats going on here?

---

### Post by stylishpants on 2008-05-29
Apparently the contents of ARGV are implicitly frozen.  You've already worked around that.


To explain your output, it makes sense if you think about it this way:

Your 3.times loop adds x to the array 3 times.  You are not adding a copy of x to the array 3 times, you are adding x itself.

Every time you modify x, you are updating every object in your array, because they're all the same object.

---

### Post by finer recliner on 2008-05-29
hmmm. well, since i am apparently using variables the wrong way in this case, what is the correct way to achieve the desired output?

---

### Post by stylishpants on 2008-05-29
I'm not sure what you want exactly, your code comment implies that you want an array of sequential single characters, but your code is making an array of copies of the entire string that have the first char modified.  I'll believe the comment.

How about this?

```

class String
  #arbritrary function that increments the first character in a 
  #string and adds it to an array. the array is returned
  def stuff
    ( self[0] ... self[0] + 3).to_a.map {|i| "%c" % i }
  end

  # perhaps this is clearer to read?   
  def stuff2
    Array.new(3).fill {|i| "%c" % (self[0] + i) }  
  end

end


s = ARGV[0]
puts s.stuff

```

Note that this is no longer modifies the original string.

---

### Post by finer recliner on 2008-05-29
thank you for your help. the solution i'm going to use is:

```

class String
  #arbritrary function that increments the first character in a 
  #string and adds it to an array. the array is returned
  def stuff
    x = self
    ary = []
    3.times do
      ary << String.new(x)  #changed this line
      x[0] += 1
    end
    return ary
  end
end


s = String.new(ARGV[0])
puts s.stuff

```

---

