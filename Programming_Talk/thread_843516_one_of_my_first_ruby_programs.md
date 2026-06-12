---
title: "one of my first ruby programs"
date: 2008-06-28
forum: Programming Talk
---

### Post by andrewoftheelves on 2008-06-28
Hello all. I'm a new programmer and this is one of my first codes. It's a simple calculator, and I still want to add things like a loop so that after each answer you get, you can continue adding and subtracting to that answer, but I want to keep it elegant and simple. So if anyone has any suggestions that would be great(and please comment on if you think my code sucks or not).Also I want to make this executable (like start just by clicking on an icon) I thought #! /usr/bin/ruby did that but it dosn't work, does anyone know how to make that work? Thanks.
```
#!/usr/bin/ruby


#calc accepts the first number, second number, 
#the sign to do calculations with, and returns the answer
def calc(aNum,aNum2,aSign)
 if aSign==1
   ans=aNum+aNum2
elsif aSign==2
  ans=aNum-aNum2
elsif aSign==3
   ans=aNum*aNum2
elsif aSign==4
   ans=aNum/aNum2
else
end
return ans
end

#accepts a string, prints it to the screen,gets a number, and returns it. 
def get_f(aString)
  puts aString
  v1 = gets.to_f
  return v1
end

#accepts a sign, gets 2 numbers from get_f
# sends all three variables to the calc, and prints the answer.
def print(aSin)
n1 =  get_f("what is your first num?")
n2 = get_f("what is you second num")
a1 = calc(n1, n2, aSin)
  puts "The ans is: #{a1.to_s}"
end

#prints a menu, gets the number and uses it for the "switch" statement
puts "Welcome to your calculator menu:\n"+\
  "1.Add\n"+\
  "2.Subtract\n"+\
  "3.Multiply\n"+\
  "4.Divide\n"+\
  "Pick a number:"
  foo=gets.to_i
  case foo
    when 1 ;print(1)
    when 2 ;print(2)
    when 3 ;print(3)
    when 4 ;print(4)
    end
```

---

### Post by Phenax on 2008-06-28
That's alright.

You should look into Classes, and being more object-orientated in ruby. As for the 'shebang' at the top, try ```
#!/usr/bin/env ruby
```

---

### Post by andrewoftheelves on 2008-06-28
yeah I tried to make the methods classes at first, but it just seemed a little too complex for what a simple program I was making. The program was a lot longer and messier, so i decided on methods. But if you have an example you could show me of an easy way to do it, I would definitely take it to heart.

---

### Post by Phenax on 2008-06-28
OK, I changed your script around a tad bit. This isn't `optimal' but I don't want to introduce too many confusing concepts.


[LIST]
[*]Fixed poor indentation (personal preference)
[*]Changed the way the welcome string was made (personal preference)
[*]"print" method is already a method provided by Ruby, renamed it to print_message.
[*]Don't need those redundant return statements. See [1].
[*]Made it inside of a class.
[*]Added a better handler for if they enter a number not 1-4
[*]Made aSign if a case
[/LIST]

[1] Ruby returns the last statement's result by default.

This would return 4:
```
def wat
  2+2
end

```


Other than that, I'd probably choose more descriptive variable names. And read up a little more on the object orientated side of Ruby (my class'd version doesn't utilize much.)

[php]
#!/usr/bin/env ruby

class Calculator
  def initialize
  end
  
  def menu
    welcome_string = "Welcome to your calculator menu:\n"
    welcome_string << "1. Add\n"
    welcome_string << "2. Subtract\n"
    welcome_string << "3. Multiply\n"
    welcome_string << "4. Divide\n"
    welcome_string << "Pick a number: "
    print welcome_string
    
    foo=gets.to_i
    case foo
      when 1; print_message(1)
      when 2; print_message(2)
      when 3; print_message(3)
      when 4; print_message(4)
      else
        puts "\nPlease pick a number 1-4!"
        menu
    end
  end

  def calc(aNum,aNum2,aSign)
    case aSign
      when 1; ans=aNum+aNum2
      when 2; ans=aNum-aNum2
      when 3; ans=aNum*aNum2
      when 4; ans=aNum/aNum2
    end
  end

  def get_f(aString)
    puts aString
    v1 = gets.to_f
  end

  def print_message(aSin)
    n1 =  get_f("What is your first number?")
    n2 = get_f("What is you second number?")
    a1 = calc(n1, n2, aSin)
    puts "The answer is: #{a1.to_s}"
  end
end

calc = Calculator.new
calc.menu
[/php]

---

### Post by NathanB on 2008-06-29
Interesting..  I also chose to do a calculator as my first Ruby program.  I had not yet discovered Ruby's syntax for a Select-Case construct (it is 'case...when...end') so this example contains the less readable if..elsif..end awkwardness.

[php]
class Stack

    def initialize

        @items = Array.new

        @count = 0

    end

    def push( item )

        @items[@count] = item

        @count = @count + 1

    end

    def pop

        @count = @count - 1

        temp = @items[@count]

        @items[@count] = nil

        temp

    end

    def top

        @items[@count - 1]

    end

end



RIGHTPARENTH = 41; LEFTPARENTH = 40; PLUS = 43; MINUS = 45

value = Stack.new

operator = Stack.new

scan = Stack.new

temp = Stack.new

#expression = "55 + ( 27 - ( 6 + 9 ) ) - 4"
print "\n  Enter an arithmetic expression of the form:"
print "\n  55 + ( 27 - ( 6 + 9 ) ) - 4"
print "\n  Use Ctrl-C to exit.\n"

while 5 == 5
	print "> "
	expression = gets
	expression.reverse!

	expression.each_byte { |x| scan.push( x ) }



	while scan.top != nil

		item = scan.pop

		if item > 47 and item < 58

			item -= 48

			temp.push( item )

			quit = 0

			while scan.top != nil and quit != 1

				item = scan.top

				if item > 47 and item < 58

					item -= 48

					temp.push( item )

					scan.pop

				else

					quit = 1

				end

			end

			order = 1

			number = 0

			while temp.top != nil

				digit = temp.pop * order

				number = number + digit

				order = order * 10

			end

			if value.top != nil and operator.top != nil and operator.top != LEFTPARENTH

				value.push( number )

				scan.push( RIGHTPARENTH )

			else

				value.push( number )

			end

		elsif item == LEFTPARENTH

			operator.push( item )

		elsif item == RIGHTPARENTH

			calc = operator.top

			if calc == PLUS

				right = value.pop

				left = value.pop

				result = left + right

				operator.pop

				value.push result

				if operator.top == LEFTPARENTH

					operator.pop

				end

			elsif calc == MINUS

				right = value.pop

				left = value.pop

				result = left - right

				operator.pop

				value.push result

				if operator.top == LEFTPARENTH

					operator.pop

				end

			end

			if value.top != nil and item == 46

				scan.push( RIGHTPARENTH )

			end

		elsif item == PLUS

			operator.push( item )

		elsif item == MINUS

			operator.push( item )

		end

	end



	print "= "
	puts value.pop

end
[/php]

Nathan.

---

### Post by rlameiro on 2008-06-29
> **andrewoftheelves said:**
> Also I want to make this executable (like start just by clicking on an icon) I thought #! /usr/bin/ruby did that but it dosn't work, does anyone know how to make that work? Thanks.


I think to run it you just need to mark the program as executable. in the permissions. I don't remember how to do that in command line, but in gnome is just right click, permissions. and chose the box that says executable.

Edit:
```
chmod +x yourscript

```
just tipe that in your command line

---

