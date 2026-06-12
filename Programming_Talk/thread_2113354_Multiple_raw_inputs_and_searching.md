---
title: "Multiple raw_inputs and searching"
date: 2013-02-07
forum: Programming Talk
---

### Post by fxStar on 2013-02-07
Hello. Because programming is one of my favorite hobbies I started a small project in python.

I'm trying to make a nutritional calculator for daily routine, see the code below:

```
# Name: nutri.py 
# Author: pyn

my_dict = {'chicken':(40, 50, 10),
        'pork':(50, 30, 20)
         }

foods = raw_input("Enter your food: ")

#explode / split the user input

foods_list = foods.split(',')

#returns a list separated by comma

print foods_list
```

What I want to do:

1. Get user input and store it in a variable
2. Search the dictionary based on user input and return the asociated values if the keys / foods exists
3. Sum these values in different nutritional chunks and return them, something like: You ate **x** protein, **y** carbs and **z** fat etc.

Any ideas are welcome and sorry for my bad english.

---

