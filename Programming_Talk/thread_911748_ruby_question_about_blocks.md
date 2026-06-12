---
title: "ruby question about blocks"
date: 2008-09-05
forum: Programming Talk
---

### Post by finer recliner on 2008-09-05
the following code:

```

letters = ['a','b','c','d']


letters.each do |x|

  x.upcase!

  if x == 'B' then
    x = 'z'
  end

end

puts letters

```
produces this output:
```

$ ruby test.rb 
A
B
C
D

```


how come inside the "each" block, the upcase! method worked, but the assignment operator inside the "if" statement did *not* work?

if it was as simple as "x" is a local variable in the "each" block, then wouldn't both the upcase! method and the assignment operator not stick when you exit the loop?

how can i make the the assignment operator stick even after exiting the loop?

thanks guys.

---

### Post by CptPicard on 2008-09-06
This is one of these pass-by-value vs. pass by reference and "what is exactly being set by =" questions :)

The reason why the uppercase thing works is that x.uppercase! takes the object *referred to* by the variable x and mutates it to being uppercase. When you do x = 'z', what it actually does is that it *rebinds the name x* to a new value 'z'. What you're doing with '=' is just simply making the parameter name x "mean something else" inside the block.

Some ruby guru (mssever) can answer the how to make it stick question :)

---

### Post by stylishpants on 2008-09-06
Essentially what you're trying to do is use a closure to create a little function that modifies each element in your array.  You can use the 'map!' function to modify your array in place.

```

letters = ['a','b','c','d']

letters.map! { |x|
  x.upcase!

  if x == 'B'
    'x'
  else
    x
  end
} 

puts letters

```

Note that each array element is being set to the final value in the closure, which is why the values within the 'if' statement need not be explicitly assigned to a variable. 

Type "ri Array.map" for more information.

---

### Post by finer recliner on 2008-09-06
thanks guys, the map! method was just what i needed

:guitar:

---

