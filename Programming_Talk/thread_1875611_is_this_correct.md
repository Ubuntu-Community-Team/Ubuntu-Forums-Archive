---
title: "is this correct ?"
date: 2011-11-05
forum: Programming Talk
---

### Post by Mapkoz on 2011-11-05
Hi.
I would like to create a little program that would ask the user to input some numbers and then calculates the mean and (possibly the median) of them.
How can I do ?
I was thinking about it but I am really n00b and I need some help.
I was thinking about how to input the numbers and save them in a list within the program but cannot really think of how. 
after that the program should sum the numbers in the list --> how ?
then calculate mean and median of then --> is there a function for this ?

thanks everybody

P.s. - I am thinking of writing the program in python.

---

### Post by Mapkoz on 2011-11-05
one concept I came out for the fist part with is :
set a sum S starting at value 0 and adding to S the newly inputed number.
At the same time a value "total input" should start at value 0 and add 1 for each number inputed.
would it be possible to use a if function where if the value is different that 0 or a given symbol it would add 1 to "total input"
is there a better way for this ?

---

### Post by muteXe on 2011-11-05
Add each value to an array (think they might be called lists in python. Can't remember sorry). Then when you need to do your calculations just iterate over all your elements in that array.

---

### Post by squenson on 2011-11-05
Have you thought about using a spreadsheet program like LibreOffice, which already has such functions and can store at the same place the data and the formula?

If you are more interested in the programming challenge, then you need to save your data in a file and reload this file each time you open the program.

---

### Post by gsmanners on 2011-11-05
Instead of thinking about user interaction, think of it as a way to use Python as a calculator. So, for example, you open a terminal and type python to start an interaction session. Then define your list like so:

```
a = [1,2,3]
print a
```

That should return "[1,2,3]". Simple as that. Then, if you want to sum the array, it becomes a simple matter of a for loop.

```
s = 0
for i in a: s = s + i
```

If you then "print s" that should return 6. You can then compute other things in a similar way. Once you have that worked out, you can work on user input, etc.

Press ctrl+D when you're done with the python shell.

---

### Post by NovaAesa on 2011-11-05
There are ways in python to calculate aggregate values on lists easily. For example, the arithmetic mean is simply:
```

sum(my_list) / len(my_list)

```

You can do something similar with the median by taking the middle element of the sorted list (you might have to play around with what to do if the list length is not odd).

---

