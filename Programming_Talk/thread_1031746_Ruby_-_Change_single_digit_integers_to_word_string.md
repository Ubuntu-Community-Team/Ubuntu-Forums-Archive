---
title: "Ruby - Change single digit integers to word strings"
date: 2009-01-05
forum: Programming Talk
---

### Post by rlzyoner on 2009-01-05
Howdy,

What would be the best way, in Ruby, to go about changing a string like 1234 to onetwothreefour.

Should I create a hash that sets {1 => "one"...} ans so on ?

Thanks

---

### Post by Caduceus on 2009-01-06
Knowing Ruby there will be a method already built in to do this, have a look through [http://ruby-doc.org/core/](http://ruby-doc.org/core/) or [http://ruby-doc.org/stdlib/](http://ruby-doc.org/stdlib/)

---

### Post by rlzyoner on 2009-01-06
Got.

Just incase anyone needs it

>> numbers = %w(zero one two three four five six seven eight nine)
 => ["zero", "one", "two", "three", "four", "five", "six", "seven", 
"eight", "nine"]
>> 2009.to_s.gsub(/\d/) { |n| numbers[n.to_i] }
 => "twozerozeronine"

---

