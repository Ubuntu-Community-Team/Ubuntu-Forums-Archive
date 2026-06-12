---
title: "Functions you didn't know existed"
date: 2013-04-13
forum: Programming Talk
---

### Post by Mikeb85 on 2013-04-13
Well, today I found something out pretty cool.  I had no idea that Ruby did pattern matching, though I've seen it in OCaml, Erlang and Haskell.  

```

["John", 1, 3, nil, "Jane"].each do |x|
  case x
  when String
    puts "Hello #{x}!!"
  when Integer
   puts x + 2
  else
    puts "Sorry!!"
  end
end

["a", "b", "c", "d"].each { |x|
  case x
  when "a" then puts "A"
  when "b" then puts "B"
  when "c" then puts "C"
  when "d" then puts "D"
  end
}



```

I also learned some cool things about dRuby (also in the standard library), how it can do parallelism and whatnot...

When was the last time you guys discovered something you didn't know about in your favourite language?

---

### Post by MG&amp;TL on 2013-04-13
The fact that C++11 has a *<regex>* header that allows for built-in regular expression matching without a library. Good idea for a thread!

---

