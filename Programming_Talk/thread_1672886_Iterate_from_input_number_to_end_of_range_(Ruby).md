---
title: "Iterate from input number to end of range (Ruby)"
date: 2011-01-21
forum: Programming Talk
---

### Post by liquidfunk on 2011-01-21
I'm hoping to get my Ruby script to start at an inputted number, say 100, and itterate all the way up to the end of the range; 1000. Having all the numbers in between saved to a file.

This is a code I have so far:

```
#!/usr/bin/env ruby

if ARGV.length ==0; 
 puts "Enter the start number"
 else puts ARGV.size  
ARGV.each do |a| 


for i in 0..1000 do
 puts i;

     end  
 end
end
```

To run it I'm typing:

```
ruby increment.rb 100 > increment.txt 
```

However, it ignores the input number and starts at 1 regardless.

What am I doing wrong?

---

### Post by schauerlich on 2011-01-21
```
#!/usr/bin/env ruby

n = ARGV[0].to_i

for i in n..1000 do
    puts i
end

```

---

### Post by liquidfunk on 2011-01-21
Thanks for your reply!

---

### Post by ghostdog74 on 2011-01-21
this a more rubyish
```

n = ARGV[0].to_i
n.upto(1000) do|x|
    puts x
end

```

---

### Post by krazyd on 2011-01-23
> **ghostdog74 said:**
> this a more rubyish
```

n = ARGV[0].to_i
n.upto(1000) do|x|
    puts x
end

```

Or even:
```

(ARGV[0].to_i..1000).each { |x| puts x }

```

Ruby's flexibility is great! :D

---

### Post by schauerlich on 2011-01-24
Well why not:

```
#!/usr/bin/env ruby

puts ((ARGV[0].to_i || 0)..1000).to_a.join "\n"
```

---

### Post by ghostdog74 on 2011-01-24
> **schauerlich said:**
> Well why not:

```
#!/usr/bin/env ruby

puts ((ARGV[0].to_i || 0)..1000).to_a.join "\n"
```

also
> 
ruby -e 'puts (ARGV[0].to_i..1000).to_a'  0  > output


---

### Post by schauerlich on 2011-01-24
Nifty. I've only learned Ruby superficially, more of a Python guy myself. Naturally I assumed it should act like Python. :)

---

