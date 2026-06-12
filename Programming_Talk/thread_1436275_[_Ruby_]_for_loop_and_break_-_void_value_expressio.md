---
title: "[ Ruby ] for loop and break - void value expression ( error )."
date: 2010-03-22
forum: Programming Talk
---

### Post by HellBoz on 2010-03-22
[PHP]#!/usr/bin/env ruby

def revnum(num)
    return num.to_s().reverse.to_i()
end

for num in (11..10000)
    sum = num + revnum(num)
    if (sum == revnum(sum))
        puts "#{num} is a palindrome ( 1 iteration, result: #{sum} )."
    elsif
        for iteration in (2..30)
            sum = sum + revnum(sum)
            if (sum == revnum(sum))
                puts "#{num} is a palindrome ( #{iteration} iterations, result: #{sum} )."
                break
            elsif
                if (iteration == 30)
                    puts "#{num} is a Lychrel number ( #{iteration} iterations, No palindrome could be found )."
                    break
                end
            end
        end
    end
end[/PHP]Basically, once I add the second break statement ( elsif if statement ), the whole application crashes with the following error.

```
[COLOR=Red]main.rb:23: void value expression
main.rb:24: void value expression[/COLOR]
```What I'm missing here ?

---

### Post by stylishpants on 2010-03-22
The problem is you're starting an if statement and not finishing it.

> **HellBoz said:**
> [PHP]
            elsif
                if (iteration == 30)
                    puts "#{num} is a Lychrel number ( #{iteration} iterations, No palindrome could be found )."
                    break
                end
            end
[/PHP]
```
[COLOR=Red]main.rb:23: void value expression
main.rb:24: void value expression[/COLOR]
```What I'm missing here ?

You are using an elsif like it is an else.  It needs a condition.


Change the "elsif" to an "else" and it will work.
Or, more readably, move this condition: (iteration == 30) to be after the elsif, and then get rid of the unnecessary if/end.

---

### Post by HellBoz on 2010-03-22
Thank you - works like a charm now. Just one thing - if I remove [COLOR=Blue]break[/COLOR], those errors doesn't come up at all and everything works as expected, even without the [COLOR=Blue]elsif[/COLOR] conditional statement :-s

---

