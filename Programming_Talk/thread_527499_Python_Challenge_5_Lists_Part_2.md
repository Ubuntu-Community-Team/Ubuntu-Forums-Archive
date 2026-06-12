---
title: "Python Challenge 5: Lists Part 2"
date: 2007-08-16
forum: Programming Talk
---

### Post by yuvlevental on 2007-08-16
First, the program I will refer to: 

print &#8220;List of First Five Greek Letters&#8221;
greek_letters = [&#8217;Beta&#8217;, &#8216;Alpha&#8217;, &#8216;Gamma&#8217;, &#8216;Delta&#8217;, &#8216;Epsilon&#8217;]
print &#8220;Third value in list is: &#8220;, greek_letters[2]
greek_letters[2] = 3
print &#8220;Value has been changed. It is now: &#8220;, greek_letters[2]
print &#8220;Length of list is: &#8220;, len(greek_letters)
del greek_letters[2]
print &#8220;Third letter has been deleted. Length is now: &#8220;, len(greek_letters)
if &#8220;Alpha&#8221; in greek_letters:
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; print &#8220;Alpha is in the list at the moment.&#8221;
else:
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; print &#8220;Alpha is not in the list at the moment.&#8221;
print &#8220;The current list: &#8220;, greek_letters
print &#8216;Alpha is in position&#8217;, greek_letters.index(&#8217;Alpha&#8217;) + 1
greek_letters.sort()
&#8220;List has been sorted alphabetically.&#8221;
print &#8220;New list: &#8220;, greek_letters
print &#8216;Alpha is in position&#8217;, greek_letters.index(&#8217;Alpha&#8217;) + 1
greek_letters.remove(&#8221;Beta&#8221;)
print&#8221;Beta has been removed.&#8221;, greek_letters

The challenge: In the program, the list, variables, ect. is determined. The challenge is to make a program where there a list, which is initially blank, and you can add, remove, print, sort, ect. items to the list. Taken from my lesson [here]("http://my-python-blog.freehostia.com/?p=19"). Email the answer to yuval [dot] imperius [at] gmail [dot] com. You will be credited on the [forums]("http://my-python-blog.freehostia.com/forum/") and get 40 credits.

---

### Post by Jessehk on 2007-08-16
> **yuvlevental said:**
> 
The challenge: In the program, the list, variables, ect. is determined. The challenge is to make a program where there a list, which is initially blank, and you can add, remove, print, sort, ect. items to the list. Taken from my lesson [here]("http://my-python-blog.freehostia.com/?p=19"). Email the answer to yuval [dot] imperius [at] gmail [dot] com. You will be credited on the [forums]("http://my-python-blog.freehostia.com/forum/") and get 40 credits.

So the challenge is to use the list class in a program? Your posts continue to confuse me. :confused:

---

### Post by yuvlevental on 2007-08-16
Pretty much. In the program I'm looking for, there are several options what you can do with a pre-created list that is initially blank. The user can add and remove items, print out the list, order the list alphabetically, ect.

---

### Post by smartbei on 2007-08-17
So nearly the whole challenge lies in interpreting user input. Do you plan on increasing the difficulty for your challenges?

On a side note, please use [ code][ /code] tags for code.

---

### Post by gnuman on 2007-08-17
I think the point is to have the challenges build up in complexity, which is a good idea.  For instance, if students are learning, say, dictionaries, you could start with simple challenges like this:

1.  Create a small program in which the user can give a key and have the value printed.

2.  Create a small program in which the user can print a table of key/value pairs sorted by keys.

3.....etc

Now after a few of these you can then hit them with something like this:

8.  Now, create an employee/salary database program that will allow the user to:
--Enter new employees and salaries
--Edit an employees salary 
--Delete an employee
--Print a table sorted alphabetically
--Print a formatted table sorted by salary
--save/load the database to a file
--interact with the program in a simple menu system

---

