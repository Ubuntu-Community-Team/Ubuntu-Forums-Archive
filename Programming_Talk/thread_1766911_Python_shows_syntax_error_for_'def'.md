---
title: "Python shows syntax error for 'def'"
date: 2011-05-25
forum: Programming Talk
---

### Post by debd on 2011-05-25
Hi, 
I've been self-teaching python for some time.
I wanted to modify and test a program example.
the purpose is to create the final output look something like:
[LEFT]*------------------*
        |  Item1     36.00    |
        |  Item2     39.00    |
        ....................
       | Total       75.00     |
        --------------------[/LEFT]
My problem is, when the compiler (2.7.1 , win32) encounters the second '[COLOR="Purple"]**def**[/COLOR]' , it gives a 'syntax error'.
What am I missing?
the codes are below:
```
#to create the top and bottom formatting.
#width is the line width, char is the string to be used 
#to draw the line
def top_bottom(char,width):
	return '%s%s%s' % ('*', char*(width - 2), '*')
	
#the function for formatting the line containing the item names and values
[COLOR="Purple"]**def**[/COLOR] base_program(val1,left,val2,right):
	part2='%.2f' % val2
	return '%s%s%s%s' % ('|', val1.ljust(left-2, ' '), part2.rjust(right-2,' '), '|')

#data input
s1=raw_input('Enter the first item name :')
s2=raw_input('Enter the second item name :')
pr1=raw_input('Enter the first item price :')
pr2=raw_input('Enter the second item price :')

#calling the func.s
print top_bottom ('-',40)
print base_program (s1,30,pr1,10)
print base_program (s2,30,pr2,10)
print top_bottom ('..',40)
print base_program ('Total',30,pr1+pr2,10)
print top_bottom ('-',40)
```

---

### Post by simeon87 on 2011-05-25
I just copied your source and it loads fine here. Could it be a problem with tabs and spaces? Indentation is part of Python's syntax so using the wrong spacing can cause a syntax error.

---

### Post by debd on 2011-05-25
> **simeon87 said:**
> I just copied your source and it loads fine here. Could it be a problem with tabs and spaces? Indentation is part of Python's syntax so using the wrong spacing can cause a syntax error.

no..am sure about the indentations. I used tab.
may this be a problem with the compiler for windows?

---

### Post by simeon87 on 2011-05-25
> **debd said:**
> no..am sure about the indentations. I used tab.
may this be a problem with the compiler for windows?

That sounds unlikely, there's nothing peculiar about your code that would make the compiler for Windows give a syntax error. Can you post the actual error message? I just want to see if it's really a syntax problem with that second 'def'; I just don't see an error otherwise because it runs fine here (Python 2.6.5, Ubuntu).

---

### Post by raydeen on 2011-05-25
I tried running it and got the following error:

```

Traceback (most recent call last):
  File "/Users/shingle/formatting.py", line 20, in <module>
    print base_program (s1,30,pr1,10)
  File "/Users/shingle/formatting.py", line 9, in base_program
    part2='%.2f' % val2
TypeError: float argument required

```

I was able to get it working correctly by changing the the assignments for pr1 and pr2 from raw_input to input.

```


#data input
s1=raw_input('Enter the first item name :')
s2=raw_input('Enter the second item name :')
pr1=input('Enter the first item price :')
pr2=input('Enter the second item price :')


```

Edit: I'm running Python 2.5.1 on OSX. Haven't tried the code in Windows or Linux yet.

---

### Post by debd on 2011-05-26
thank you all for the responses.

Reydeen, the same happened for me, substituting with 'input' was need. though I dont know why yet.  I know little about python. It ran smooth in Ubuntu.  

Simon, when I'll log back to windows, I'll post the output.

btw, python feels a bit odd to me...
 I mean, you dont have to define datatypes, little use of punctuations and some other dissimilarities ( with C), that of course accounts for less effort in terms of typing , but sometimes it really confuses me. . :/

---

### Post by DangerOnTheRanger on 2011-05-26
> 
btw, python feels a bit odd to me...
 I mean, you dont have to define datatypes, little use of punctuations  and some other dissimilarities ( with C), that of course accounts for  less effort in terms of typing , but sometimes it really confuses me. .  :/     
Trust me, once you get used to it, you feel like a bird freed from a cage. :)

Also, DO NOT use **input**. It's dangerous, as arbitrary code can be easily executed.
Instead, do:
s1=raw_input('Enter the first item name :')
s2=raw_input('Enter the second item name :')
pr1=float(raw_input('Enter the first item price :'))
pr2=float(raw_input('Enter the second item price :'))

This is the most "Pythonic" way to solve this problem.

---

### Post by TwoEars on 2011-05-26
> **debd said:**
> Hi, 
I've been self-teaching python for some time.
I wanted to modify and test a program example.
the purpose is to create the final output look something like:
[LEFT]*------------------*
        |  Item1     36.00    |
        |  Item2     39.00    |
        ....................
       | Total       75.00     |
        --------------------[/LEFT]
My problem is, when the compiler (2.7.1 , win32) encounters the second '[COLOR="Purple"]**def**[/COLOR]' , it gives a 'syntax error'.
What am I missing?
the codes are below:

Firstly, the Python you're using is not a compiler. It's an interpretor. The difference is quite important, but not relevant to your problem, so I'll let you work that one out yourself :)
> ```
#to create the top and bottom formatting.
#width is the line width, char is the string to be used 
#to draw the line
def top_bottom(char,width):
	return '%s%s%s' % ('*', char*(width - 2), '*')

```
There's no need to have either of the '*' there in the formatting - use ```
 '*%s*' % (char*(width-2)) 
``` instead.
> 
```

#the function for formatting the line containing the item names and values
[COLOR="Purple"]**def**[/COLOR] base_program(val1,left,val2,right):
	part2='%.2f' % val2
	return '%s%s%s%s' % ('|', val1.ljust(left-2, ' '), part2.rjust(right-2,' '), '|')

```

Same here again - there's no need for the '|'. Also, try to use descriptive instead of generic naming.
> 
```

#data input
s1=raw_input('Enter the first item name :')
s2=raw_input('Enter the second item name :')

```

What is the main benefit of Python? Readability. In order to make assignments more readable, leave a gap between the equals sign - 
```
s1 = raw_input('Enter the first item name :'))
```
Same here again - 
> 
```

pr1=raw_input('Enter the first item price :')
pr2=raw_input('Enter the second item price :')

```

You also have no form of validation. Someone could enter 'cat' as their first item price, and it wouldn't be caught, meaning that when the program expects a numerical value, it'll crash. There's also no form of conversion here - use float() as someone suggests.
```

>>> pr1=raw_input('Enter the first item price :')
Enter the first item price :cat
>>> pr1
'cat'

```
See? :)
> 
```

#calling the func.s
print top_bottom ('-',40)
print base_program (s1,30,pr1,10)
print base_program (s2,30,pr2,10)
print top_bottom ('..',40)
print base_program ('Total',30,pr1+pr2,10)
print top_bottom ('-',40)
```
[/code]
[/quote]

It's standard to include this in the following form -

```

def main():
    call_functions()

if __name__ == '__main__':
    main()

```

The reason for this is future use as a module. When you import something in Python, all the code is run. To ensure that none of the function calls run unless you want them to, you do the above. This checks the name of the script - if the script is run by calling the script directly (i.e, not through importing) then the name is __main__, otherwise it's whatever the file is called. (You can check this by creating a file with "print __name__" in, save it, then run python file_name.py, then after run python and run "import file_name" in python)


Also, in Python 2.x, never, ever use input(). In Python 3.x, input() is basically raw_input(), but in Python 2.x it's dangerous. Why? Because it runs eval() on whatever the input is.  Let me give you an example - 
```

>>> important_list = [5, 12, 13]
>>> danger = input('Something?')
Something?important_list.append(345)
>>> important_list
[5, 12, 13, 345]
>>> danger_again = input('Huh?')
Huh?locals()
>>> print danger_again
{'important_figure': 42, 'e': <module 'e' from 'e.py'>, 'danger': {...}, '__builtins__': <module '__builtin__' (built-in
)>, '__package__': None, 'pr1': 'cat', 'important_list': [5, 12, 13, 345], '__name__': '__main__', '__doc__': None}

```

As you can see, input would allow someone to do things they shouldn't be allowed to - ever. Of course, there are more dangerous examples.

HTH.

---

### Post by raydeen on 2011-05-27
> **DangerOnTheRanger said:**
> Trust me, once you get used to it, you feel like a bird freed from a cage. :)

Also, DO NOT use **input**. It's dangerous, as arbitrary code can be easily executed.
Instead, do:
s1=raw_input('Enter the first item name :')
s2=raw_input('Enter the second item name :')
pr1=float(raw_input('Enter the first item price :'))
pr2=float(raw_input('Enter the second item price :'))

This is the most "Pythonic" way to solve this problem.

Good to know. I'm a bit of a newb and since I'm the only one ever running my programs I usually don't worry about things like that. I'll have to start implementing my inputs like that on the off chance that someone else might actually want to run my scripts. :D

---

### Post by debd on 2011-05-27
TwoEars, thanks man.. nice explanations. 
Thanks everyone!
The codes now work on windows as well after rectifying the input syntaxes for 'pr1'.

well..py feels a lot easier than what it felt at the first experiences of C. am enjoying it.
but somethings still confuse me.. one big thing is understanding scopes in python which I think I haven't got the grip of yet.

---

### Post by skytreader on 2011-05-27
> **DangerOnTheRanger said:**
> Trust me, once you get used to it, you feel like a bird freed from a cage. :)

Also, DO NOT use **input**. It's dangerous, as arbitrary code can be easily executed.
Instead, do:
s1=raw_input('Enter the first item name :')
s2=raw_input('Enter the second item name :')
pr1=float(raw_input('Enter the first item price :'))
pr2=float(raw_input('Enter the second item price :'))

This is the most "Pythonic" way to solve this problem.

So...I'm aware that the discussion is for Python 2.x but I might as well ask...

Unless I'm misinformed, or my interpreter just went bonkers, *raw_input* does not exist in Python3. So...any alternatives to *input* when using Python3? Or is *input* safe at Python3 now?

---

### Post by TwoEars on 2011-05-27
> **skytreader said:**
> So...I'm aware that the discussion is for Python 2.x but I might as well ask...

Unless I'm misinformed, or my interpreter just went bonkers, *raw_input* does not exist in Python3. So...any alternatives to *input* when using Python3? Or is *input* safe at Python3 now?


See my post. input in Python 3.x is raw_input in Python 2.x.

---

