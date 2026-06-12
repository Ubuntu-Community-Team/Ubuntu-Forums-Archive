---
title: "ruby beginner problem"
date: 2008-08-20
forum: Programming Talk
---

### Post by billgoldberg on 2008-08-20
I've hear ruby was the best language to learn first.

I'm following a online crashcourse to learn the basics.

I'm stuck on one of the "tasks".

I'll just copy/paste it.

> Write a Deaf Grandma program.

 Whatever you say to grandma (whatever you type in), she should respond with HUH?!  SPEAK UP, SONNY!, unless you shout it (type in all capitals). 

If you shout, she can hear you (or at least she thinks so) and yells back, NO, NOT SINCE 1938! 

*To make your program really believable, have grandma shout a different year each time; maybe any year at random between 1930 and 1950. (This part is optional, and would be much easier if you read the section on Ruby's random number generator at the end of the methods  chapter.) *

You can't stop talking to grandma until you shout BYE.

The random number stuff can wait, I'll need to get the basic program running first.

This needs to be done using "while" and "if".

The guid explains the "if " and "while" part pretty good, and I think I got it.

But it doesn't mention on how to mix them up.

This is where I'm failing, I've tried a lot of things, but they all give errors.

I've came up with this, but it's not working like it should.

```
width = 60
puts 'Hello, I\'m the granny program'.center(width)
puts 'What do you want to ask me?'
command = ' '
while command != 'bye'
command = gets.chomp
end
if command!= command.downcase
puts 'Speak louder'
else
puts 'Not since 1936'
end
puts 'program terminated'
```

---

### Post by mssever on 2008-08-20
> **billgoldberg said:**
> ```
width = 60
puts 'Hello, I\'m the granny program'.center(width)
puts 'What do you want to ask me?'
command = ' '
while command != 'bye'
   command = gets.chomp
end
if command!= command.downcase
   puts 'Speak louder'
else
   puts 'Not since 1936'
end
puts 'program terminated'
```It'll make your code much more readable if you indent it properly. After any keyword that will eventually require an end, indent your code (Ruby convention is two spaces). I've indented your code above.

You should surround your operators with a space on each side. So instead of command!= whatever, do command != whatever. You've got an error on your if condition. command != command.downcase doesn't do what you're expecting it to do.

EDIT: Oh, and you'll never break out of the while loop unless you enter 'bye', which isn't what you want, either.

P.S.: I hope that by providing hints instead of answers, I'm helping you to learn more.

---

### Post by billgoldberg on 2008-08-20
Got it. *(watched a movie to clear my head)*

I've used this

[PHP]width = 60
puts 'Hello, I\'m the granny program'.center(width)
puts 'What do you want to ask me?'
down = ' '
var1 = (rand(21))
var2 = 1930
year = var1.to_i + var2.to_i
while down != 'BYE'
    down = gets.chomp
  if down != down.upcase
    puts 'speak up'
  else 
     puts 'that\'s better, like in ' + year.to_s + '.'
  end
end
puts 'bye bye sonny' [/PHP]

The only problem is that year.to_s (year) always gives the same number while running.

If I stop the program and restart it, a new number is picked, but remains the same for the session.

---

### Post by mssever on 2008-08-20
> **billgoldberg said:**
> Got it. *(watched a movie to clear my head)*

I've used this

[php]width = 60
puts "Hello, I'm the granny program".center(width)
puts 'What do you want to ask me?'
down = ' '
year = 1930
while down != 'BYE'
  down = gets.chomp
  if down != down.upcase
    puts 'speak up'
  else
    puts "that's better, like in #{year + rand(21)}."
  end
end
puts 'bye bye sonny' [/php]The only problem is that year.to_s (year) always gives the same number while running.

If I stop the program and restart it, a new number is picked, but remains the same for the session.
You're only calling rand once. If you want the year to change, you need to call rand again.

Also, I've corrected your indentation. Hope the reasons are clear. Additionally, I've changed your quoting in a couple of places to minimize escaping. Also, you don't need to call year.to_s, because string interpolation (using #{}) does that for you.

---

