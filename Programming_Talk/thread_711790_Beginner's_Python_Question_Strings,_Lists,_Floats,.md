---
title: "Beginner's Python Question: Strings, Lists, Floats, Tuples..."
date: 2008-03-01
forum: Programming Talk
---

### Post by JaggedOne on 2008-03-01
I am teaching myself python as my firs programming language. There is one thing I don't get. There are all these types of data. The only ones that come to mind right now are lists, tuples, strings and floats. I think there is one more type of number data though. 

I can't quite grasp how they are all different. Could anyone explain it to me?

---

### Post by Wybiral on 2008-03-01
> **JaggedOne said:**
> I am teaching myself python as my firs programming language. There is one thing I don't get. There are all these types of data. The only ones that come to mind right now are lists, tuples, strings and floats. I think there is one more type of number data though. 

I can't quite grasp how they are all different. Could anyone explain it to me?

They all represent different ...Types of data :) You'll get the hang of it. Think about this...

You can add two strings (text) together such as: "Hello" + "world" to get "Helloworld" But what happens when you use: "10" + "2"? You get "102" because they're strings, however: 10 + 2 would yield 12 because those are integers. And since Python is strongly typed, you can't use "10" + 2 at all (it throws an error).

You'll REALLY get the hang of it when you get to make your own types (Python is object oriented and lets you create your own object types (classes)).

---

### Post by LaRoza on 2008-03-01
**integer** - Positive or negative whole numbers. They have no decimal point. You can perform mathematical operations on them, but when you do integer math your answer will be an integer.

Example: 
>>>2 + 4
>>>6

>>>1/2
>>>0

**float** - Positive or negative number, with a decimal point. You can use these like integers as well. To declare an variable of type float, use a decimal point. Math operations are more precise.

Example:
>>>2. + 4
>>>6.0

>>>1./2
>>>0.5

**string** - Character strings, you cannot use these in math as they are. Anything in quotes is a string, even if the characters are numbers.

**list + tuple + dictionary** - More complex data types, they are collections of variables in one name, and indexed by number (list + tuple) or key (dictionary). Tuples cannot be changed, lists can. Many functions return a tuple.

Example (list):
>>>grades = [100,90,95,30]

>>>print grades
>>>for grade in grades:
...    print grade
>>>grade.append(105)
>>>print grades
>>>print grades[0]
>>>print grades[1]

The above examples should make things a little clear. The use of variable types becomes more clear when you use them more often.

---

### Post by pmasiar on 2008-03-01
Tuples, list and dictionaries are to handle collections of objects (like multiple numbers, strings, or objects). Ie you can have list of lists (list, where each item is another list), etc.

You use list or dictionary if you need to handle variable number of items. List is ordered (access items sequentially by index), dictionary is not ordered (access items directly by key). All items in list or dictionary  are in some sense similar (the same "type"), you just don't know how many you have.

Tuple is for fixed number ordered data structure, where underlying type of each item might be different. Like if function get_person(id) returns tuple (first_name, last_name, age). Most obvious example of a tuple is  parameters of a function: you need to have proper number, each of proper type, for function to "work".

With some experience it will be obvious which kind of collection to use.

---

### Post by popch on 2008-03-01
> **JaggedOne said:**
> I am teaching myself python as my firs programming language. There is one thing I don't get. There are all these types of data. (...)I can't quite grasp how they are all different. Could anyone explain it to me?

The idea of a 'data type' is one of the first concepts one encounters when learning how to program. It is, at first, for many hard to grasp because there is no true equivalent in the real world.

There are two ways in which data types differ.

Once: In a computer all data is stored in 'binary format' in small pieces called bits and bytes. Since you as a user or programmer do not usually want to see all your data broken up into bits and bytes, the computer applies some rules to change 'your' data into 'its' data and back to 'your'. There are several ways in which this can be done, and the results are different 'data types'.

Two: Once the data has been put into the computer in the required sequence of bits and bytes, there are different things the computer can do with it. What can be done with a particular item of data depends wholly on how it stored (see above), i.e. its 'type'.

---

### Post by pmasiar on 2008-03-01
> **JaggedOne said:**
> I am teaching myself python as my firs programming language. 

Which book do you use?

---

