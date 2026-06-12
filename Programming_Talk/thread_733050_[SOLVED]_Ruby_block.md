---
title: "[SOLVED] Ruby block"
date: 2008-03-23
forum: Programming Talk
---

### Post by rye_ on 2008-03-23
```

(1..(str = (2**1000).to_s).length).each {|x| ans = str[x].to_i unless defined? ans #operator# puts ans += str[x] if defined? ans }

```

hi,

ruby experts.  what can I replace #operator# with to make this code work.

Thanks in advance.

Ryan

---

### Post by mssever on 2008-03-23
Wow. That's some write-only code! I can't tell just what you're trying to do, and you didn't say. Let's see...
```
str = (2 ** 1000).to_s
1.upto(str.length) do |x|
  ans = str[x].to_i unless defined? ans #operator#
  puts ans += str[x] if defined? ans
end
```Does this refactoring so far do the same thing?

What are you trying to accomplish? What is #operator# supposed to do?

defined? is not a standard method. If you've created it, then you need to explain what it does. Or are you looking for the Object#respond_to? method?

You're trying to put so much on a single line that your code is nearly impossible to understand. (I'm pretty sure the code you posted contains one or more syntax errors.) You're writing Ruby, not Perl. Don't do so much on one line!

---

### Post by rye_ on 2008-03-23
thanks for the reply mssever.

1) defined?

despite its odd syntax, it is a standard method.  try this in irb;
puts "rye_ is correct, make him the king!" unless defined? b

2) what am I trying to do?
this is [http://projecteuler.net/](http://projecteuler.net/) prob 16 (I think)

what I'm trying to do is add together the individual digits that make up 2**1000. (and do it on one line)

within the code, #operator# is some kind of comma, or list operator (not sure what ruby uses) to let me define to if conditionals on that one line.

---

### Post by Wybiral on 2008-03-23
Is there a summation function?

In Python, it would look like this:
```

sum(int(c) for c in str(2 ** 1000))

```

I'm not sure if Ruby has generator expressions or a summation builtin though.

---

### Post by mssever on 2008-03-23
> **rye_ said:**
> 1) defined?

despite its odd syntax, it is a standard method.
Despite how much I like Ruby (it's usually my language of choice), this is the annoying part. You're right. defined? is part of standard Ruby. But it isn't documented anywhere (I looked in ri and on ruby-doc.org). It's a method that might occasionally come in handy...
> what I'm trying to do is add together the individual digits that make up 2**1000. (and do it on one line)

within the code, #operator# is some kind of comma, or list operator (not sure what ruby uses) to let me define to if conditionals on that one line.

You're probably looking for a semicolon (although it technically isn't one line anymore). But even then, your code has other bugs. For example, strings are indexed beginning with 0.

Also, you don't need to use defined? at all, or test whether your variable is defined; just make sure it is before entering the block. If you feel you must test whether the variable is defined, consider the ternary operator: ```
 a = (condition) ? do_if_true : do_if_false
```

Really, though, trying to restrict yourself to one line is a Bad Thing; it makes your code nearly unreadable (and hard to debug), and you don't gain a single thing from it.

---

### Post by a9bejo on 2008-03-23
> **Wybiral said:**
> Is there a summation function?


No, but in smalltalk-like languages like Ruby, you can use the inject method on an object to do this:
```

sum = [1,2,3,4].inject{|a,b| a+b}

```

---

### Post by mssever on 2008-03-23
> **Wybiral said:**
> Is there a summation function?

In Python, it would look like this:
```

sum(int(c) for c in str(2 ** 1000))

```I'm not sure if Ruby has generator expressions or a summation builtin though.

Good thought. I don't know Ruby's math capabilities very well, since I'm not much of a math person. Where Python uses list comprehensions or generator expressions, Ruby uses blocks.

---

### Post by Wybiral on 2008-03-23
> **a9bejo said:**
> No, but in smalltalk-like languages like Ruby, you can use the inject method on an object to do this:
```

sum = [1,2,3,4].inject{|a,b| a+b}

```

OK, so "inject" is the functional "reduce"?

---

### Post by a9bejo on 2008-03-23
> **Wybiral said:**
> OK, so "inject" is the functional "reduce"?

exactly

---

### Post by rye_ on 2008-03-23
funnily enough inject was my first though too.

something like; (which by the way is still erronous)

puts (0...(str = (2**2).to_s).length).inject(0) {|x, inj| puts x ; inj+=str[x].to_i }

It's just I often like to try out painful ways of doing things as a learning excercise

---

### Post by rye_ on 2008-03-23
thanks for the semicolon suggestion msever.
I don't think I ever knew about that.

---

### Post by a9bejo on 2008-03-23
Edit: ...nonesense....

---

### Post by mssever on 2008-03-23
EDIT: This is wrong; see Wybiral's code, which is a correct version of what I was trying.

---

### Post by Wybiral on 2008-03-23
> **a9bejo said:**
> exactly

OK, does this look like a roughly equivalent Ruby version of the Python code I posted?
```

puts (2 ** 1000).to_s.split(//).inject{|a, b| a.to_i + b.to_i}

```
I didn't know how else to reduce the string, so I split it into an array (I don't program in Ruby, so I'm just going by what I've seen).

EDIT:

I guess technically it's more like this Python code:
```

print reduce(lambda a, b: int(a) + int(b), str(2 ** 1000))

```

---

### Post by mssever on 2008-03-23
> **Wybiral said:**
> OK, does this look like a roughly equivalent Ruby version of the Python code I posted?
```

puts (2 ** 1000).to_s.split(//).inject{|a, b| a.to_i + b.to_i}

```I didn't know how else to reduce the string, so I split it into an array (I don't program in Ruby, so I'm just going by what I've seen).
You're right; My code above is wrong.

---

### Post by rye_ on 2008-03-23
puts (0...(str = (2**1000).to_s).length).inject(0) {|inj, x| inj+=str[x..x].to_i }

That does it 

I like the idea of using  split.  I'll have a play with that.

ps anyone know of any good ruby software whos sourcecode would be good for looking over, and eventually some of US could contribute?

Edit: The reason my previous post's code failed was based on my assumption of how strings behave when accessed as arrays.  it seems array[2..2] is different to array[2] (just thought I'd post this)

---

### Post by a9bejo on 2008-03-23
> **rye_ said:**
> I like the idea of using  split.  I'll have a play with that.


Since Ruby 1.9, you can use each_char instead of split. Same result, but more readable. So Wybiral's version becomes:

```

(2 ** 1000).to_s.each_char.inject{|acc, x| acc.to_i + x.to_i}

```

---

### Post by rye_ on 2008-03-23
nicely done a9bejo.
All hail YARV
where did you come across that one?

---

### Post by a9bejo on 2008-03-23
> **rye_ said:**
> nicely done a9bejo.

where did you come across that one?

Ruby has become a very important tool for me, so I follow the development of the language.  Before 1.9, There were various issues with the string class: For example, you had to use this split(//) - hack to get a list of characters, or 

```

"123"[0]

```

would return 49 (the ascii code of the first char). And, most annoying: Unicode was completely broken. 

1.9 is only an experimental release, but it fixes all these issues.

---

