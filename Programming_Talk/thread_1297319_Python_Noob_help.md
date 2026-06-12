---
title: "Python Noob help"
date: 2009-10-21
forum: Programming Talk
---

### Post by Hume's doona on 2009-10-21
I'm having trouble returning a variable to the calling function in a program I am writing for uni.

I've stripped it back to post here so I can show only the problematic part.

```
def main():
#simplified main function stripped to show the element I am having trouble with.
	four_categories()
	print categories

#define 4_categories
def four_categories():
	a="Objects"
	b="Algorithms"
	c="Recursion"
	d="Top_Down_Design"
	e="Loops"	
	f="Functions"
	g="Built_in_functions"
	h="decisions"
	i="Data_types"
	print "There are nine possible categories of questions to choose from."
	print "You will be prompted to choose four"
	print
	print "The categories are as follows:"
	print "____________________________"
	print "a- Objects"
	print "b- Algorithms"
	print "c- Recursion"
	print "d- Top-Down-Design"
	print "e- Loops"
	print "f- Functions"
	print "g- Built-in-functions"
	print "h- Decisions"
	print "i- Data_types"
	print "_____________________________"
	print "Enter the letter associated with your four choices."
#user input
	categories=input("Enter choices as lower case letters, separated by commas. > ")
	return categories
main()


```

The error I'm getting is this:

> Traceback (most recent call last):
  File "G:\programming1\assignment2\test_return.py", line 36, in <module>
    main()
  File "G:\programming1\assignment2\test_return.py", line 4, in main
    print categories
NameError: global name 'categories' is not defined
I can't for the life of me figure out the problem. Is there more to the return statement? 

I really am lost :confused::(

any help or feedback much appreciated
cheers

Dan

---

### Post by snova on 2009-10-21
> **Hume's doona said:**
> I'm having trouble returning a variable to the calling function in a program I am writing for uni.

I've stripped it back to post here so I can show only the problematic part.

```
def main():
#simplified main function stripped to show the element I am having trouble with.
	four_categories()
	print categories
```

I can't for the life of me figure out the problem. Is there more to the return statement?

A bit. Everything is fine except you're discarding the object that four_categories() returns, by not explicitly keeping it. Try this instead:

[PHP]
def main():
    categories = four_categories()
    print categories
[/PHP]

---

### Post by Hume's doona on 2009-10-21
Thank you! That worked.

---

### Post by Can+~ on 2009-10-21
You should also consider changing the massive amount of print statements, to one (triple quotation mark):

[PHP]print """Hello
multiple-line
world!"""[/PHP]

---

### Post by Hume's doona on 2009-10-21
> **Can+~ said:**
> You should also consider changing the massive amount of print statements, to one (triple quotation mark):

[PHP]print """Hello
multiple-line
world!"""[/PHP]

Thanks, I didn't know about that with the triple quotes

gotta love the ubuntu community :)

---

