---
title: "My little python program... need some help formating"
date: 2007-05-10
forum: Programming Talk
---

### Post by thenetduck on 2007-05-10
Hi, 
   I have been taking all of the programs that I have written in C++ and converting them to python so I will learn the language but am running into some problems with formating the output text in the terminal. Here is my program. It is going to print out a multiplication table 12 X 12

```

# This program will print out a list of multiple table.
# Input: no user input
# Output: The output is in the main for loop

# Print the first line of the table
for fL in range(1, 12):
    print fL
# Print out the rest of the multiplication table
for i in range(1, 12):
    for j in range(1, 12):
        print i * j


```
I would like to know how to make a "cout << endl;" in python and also I need it to print 12 numbers side by side. I don't want it to automatically endl after every print out. Does anyone know how to make it not automatically endl after every print? It's kind of well irritating that it does that . Thanks

 The Net duck

---

### Post by b1g4L on 2007-05-10
I believe this is what you are trying to do. You can use a comma to not endl after a print statement.

```
for i in range(1, 13):
    for j in range(1, 13):
        print i * j,
    print '\n'
```


edit: also remember when using the range function, the second number is exclusive.....so for 12 x 12 you need to end at 13.

---

### Post by n0dl on 2007-05-10
iirc a comma should display information without a newline character at the end. Heres a three liner for you to display the numbers side by side as you requested
```
for i in range(1,13):
    for j in range(1,13):
        print '%d x %d = %d' % (i, j, i*j),
```
The %d is a place holder for the elements (kind of like C) in the tuple which replace it with the integer numbers 1 - 12.
Note: the comma at the end of that tuple on the third line, That will chomp (sorry for the perl lingo) the new line off.

---

### Post by Buffalo Soldier on 2007-05-10
> **n0dl said:**
> iirc a comma should display information without a newline character at the end. Heres a three liner for you to display the numbers side by side as you requested
```
for i in range(1,13):
    for j in range(1,13):
        print '%d x %d = %d' (i, j, i*j),
```The %d is a place holder for the elements (kind of like C) in the tuple which replace it with the integer numbers 1 - 12.
Note: the comma at the end of that tuple on the third line, That will chomp (sorry for the perl lingo) the new line off.

I think you missed one** %** sign.

```

for i in range(1,13):
    for j in range(1,13):
        print '%d x %d = %d' **[COLOR=Blue]%[/COLOR]**(i, j, i*j),

```

---

### Post by jamescox84 on 2007-05-10
How about this for a one line approach.

```

print "\n".join([''.join([str(i * j).ljust(4) for i in range(1, 13)]) for j in range(1, 13)])

```

Python is one ace language!

---

### Post by thenetduck on 2007-05-11
> **jamescox84 said:**
> How about this for a one line approach.

```

print "\n".join([''.join([str(i * j).ljust(4) for i in range(1, 13)]) for j in range(1, 13)])

```

Python is one ace language!

Wow although that is a really cool one liner. I don't follow it so need an explanation. But ya that is what I was trying to do with my other lines of code. Cool stuff I wish I had a good internet connection so I could google more things I just only have about 20 min every day I can get online. Thanks for all the help guys btw.

 The Net Duck

---

### Post by jamescox84 on 2007-05-11
Yeah, the one liner is cool, but I don't think you want to use it, because it's a very long unreadable line. I just wondered if I could do it in one line.

It uses list comprehension, which is to say it use the contents of one list (range(1, 13) generates a list) to generate another.

Example:
```

# Generates a list containing the two times tables up to 10.
two_times = [i * 2 for i in range(1, 11)]
# The first part is the expression that gets executed for every iteration
# of the nested for loop, what this evaluates to gets inserted into
# the new list.

```

Then it uses a strings built in method to join lists of strings together.
```

print ', '.join(['Some', 'Items', 'in', 'a', 'List'])
# Yields 'Some, Items, in, a, List'

```

Here I've spreader the one liner onto multiple lines and added some comments, hope this
helps.
```

print "\n".join(               # Join all lines with new line 
                               # character
       [''.join(               # Join each answer into one long line 
                               # using an empty string
       [str(i * j).ljust(4)    # Perform the multiplication, convert to a
                               # string with str, and then place it in an
                               # other string of length 4 on the left hand
                               # side with .ljust(4) this keeps the table tidy
       for i in range(1, 13)]) # Generates list of answers
       for j in range(1, 13)]) # Generates list of lines of answers

```

And here is a tidier solution that I actually recommend.
```

for j in range(1, 13):
    print ''.join([str(i * j).ljust(4) for i in range(1, 13)])

```

Hope that helped.

---

