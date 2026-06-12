---
title: "beginning python, functions, loops and a structure to my first script"
date: 2014-07-03
forum: Programming Talk
---

### Post by Drone4four on 2014-07-03
I’m working on my first real python script.  Right now it converts miles to kilometers and megabits to megabytes and vice versa.  All 4 functions execute sequentially.  I want to make it more dynamic so when the script is executed in the shell, it prompts the user with the option of which conversion s/he wants.  I also want my script to (after answering the user’s question) ask the user to start from the beginning, giving the user an opportunity to convert a different metric value.  To do this I need to implement a loop.  Understanding the for loop and the while loop have probably been the most challenging concepts for me to wrap my head around so far.  But after watching a number of instructional videos, I think I understand the basic concept of loops.  But I evidently don’t understand loops enough to adapt one of them to the context of what I am trying to do in my script.  

I am asking you guys for a hint without writing the script for me.

Here is my script so far:

```

  1 #!/usr/bin/python
  2 
  3 print "What shall we calculate today?"
  4 
  5 def convMb2MB():
  6         print "I'm gonna convert a value from Megabits to MegaBytes."
  7         user_megabit_value = float(raw_input("Enter the bandwidth tier listed on your carrier's website for the package you subscribe to. >> "))
  8         user_megabyte_value = float(user_megabit_value)/8
  9         print "%s Megabits is equal to %s in MegaBytes" % (float(user_megabit_value), float(user_megabyte_value))
 10 
 11 def convMB2Mb():
 12         print 'I will convert a value from MegaBytes ti Negabits.'
 13         user_megabyte_value = float(raw_input("Enter the maximum download speed shown when using your web browser, >>"))
 14         user_megabit_value = float(user_megabyte_value)*8
 15         print "%s MegaBytes is equal to %s in Megabits" % (float(user_megabyte_value), float(user_megabit_value))
 16 
 17 def convM2KM():
 18         print 'I will convert a value from Miles to Kilometers for you.'
 19         user_mile_value = float(raw_input("Enter the value in miles that you want converted into Kilometers. >>"
 20         user_kilometer_value = float(user_mile_value)/0.62137
 21         print " %s in miles is approximately equivalent to %s in Kilometers" % (float(user_mile_value), float(user_kilometer_value))
 22 
 23 def convKM2M():
 24         print "I will convert a value from Kilometers" 
 25         user_kilometer_value = float(raw_input('Enter the number of kilomete rs you want converteed to miles >>'))
 26         user_mile_value = float(user_kilometer_value)*0.62137
 27         print " %s in Kilometers is approximately equivalent to %s in Miles" % (float(user_kilometers_value), float(user_mile_value))
 28 
 29 if __name__ == '__main__':
 30         convMb2MB()
 31         convMB2Mb()
 32         convM2KM()
 33         convKM2M()

```
It’s crude, I know.  I intend to import this script in a parent which calls the functions at the request of the end user in the shell.  I just have no idea how to structure it and how to use a loop.  Would it be possible for someone to guide me with pseudo code?

By the way: As is, the script chokes in the shell with a syntax error which I don’t understand.  Here is what the interpreter says:
```

$ python initial_conv_script.py 
  File "initial_conv_script.py", line 20
    user_kilometer_value = float(user_mile_value)/0.62137
                       ^
SyntaxError: invalid syntax
$ 

```
(The symbol for exponents is pointing upwards at the ‘e’ in ‘user_kilometer_value’.)  What is the interpreter saying with respect to the reported syntax error?

---

### Post by spjackson on 2014-07-03
> **Drone4four said:**
> 
By the way: As is, the script chokes in the shell with a syntax error which I don’t understand.  Here is what the interpreter says:
```

$ python initial_conv_script.py 
  File "initial_conv_script.py", line 20
    user_kilometer_value = float(user_mile_value)/0.62137
                       ^
SyntaxError: invalid syntax
$ 

```
(The symbol for exponents is pointing upwards at the ‘e’ in ‘user_kilometer_value’.)  What is the interpreter saying with respect to the reported syntax error?
You are missing 2 closing parentheses from the end of the previous line.

---

### Post by michael171 on 2014-07-07
In addition to the missing parens already pointed out, there was an error on line 27 where user_kilometers_value needs to be user_kilometer_value (notice the s)

I would recomend a while loop since it is the easiest to understand.  A while loop simply repeats your code untill a condition becomes false.  If the condition is True, it will loop indefinately.  Inside any loop you may call break at any time to cause python to leave the loop and continue with the rest of the program.  When python runs out of statements or instructions to execute, it will exit. Just realized you asked for hints and not solutions so ill write below my sugestions and attach the solution which I origionaly had pasted here.

solution: [ATTACH]254556[/ATTACH]  [ATTACH]254557[/ATTACH]

using an infinite while loop I would ask the user for a value, then test the value to determine which function to call.  I would recomend something like

print usage

while True:
get input
if input == value0: break # some way to exit the loop
if input == value1: call functiona
if input == value2: call functionb
...

---

### Post by michael171 on 2014-07-07
I wanted to make loops alittle more clear for you as these can trip alot of new comers to python.

A loop simply repeats code untill you tell it not to.  It determines weather it is time to stop looping when the condition becomes false, or you explicitly cause the loop to finish using the break statement.  for loops in python are different than in other languages such as C and C++.  They still loop but the condition that they test is a bit confusing.  For loops simply move from one element to another in a sequence untill it runs out of elements.  If you have a shoping list and you start at the top, you can work your way down the list item by item as you go.  When you get to the bottom of the list you know to stop because there are no more items for you to buy.  In python a list is a type of sequence, simular to our shopping list.  Lets look at how to make a list (syntax):

shoppingList = ['Candy','Pop','Pizza','Cereal']

Here we see what my typical shopping list contains.  If I had to write some code that looped through (loop is not very acurrate here) my shopping list untill it reached the end:
```

for food in shoppingList:
        print food
```

This would simply print to the screen each item in my shopping list, a very bad idea to show someone who is health consious (and knows how to spell)

This is called iteration, which simply means to move from one item in a sequence to another.  for loops stop when the end of the iteration is reached (there is nothing left).  While loops actualy repeat code over and over again untill your condition fails where the for loop runs the code untill there are no more items.

I hope this did not confuse you, if it did please ignore it.

---

### Post by Jonathan_Blasquez on 2014-07-08
Thanks for posting the script. I have been getting the hang of python and this helped me to solve my problem.

---

