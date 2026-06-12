---
title: "python function that takes filename as argument"
date: 2008-09-27
forum: Programming Talk
---

### Post by slentzen on 2008-09-27
Hi, I have just recently started learning python, and my question will probably seem very simple to anyone with a little more programming experience. I hope someone can help me.

i am trying to make a small module in which I define a function that takes a filename as an argument e.g "filename.txt". The function uses regular expressions to locate all double occurences of words in the text file.
The problem is that when I call the function giving the filename as an argument like "findDouble(notes.txt)" I get a Name Error saying that anything before the ".txt" is not defined.
What am i doing wrong in my function?
Thanks

```

#!/usr/bin/python
def findDouble(inputfilename):
	''' a function that finds all double occurences of a word'''
	input = open('inputfilename','r')
	filelist = input.readlines() # this will import all lines as elements in a list
	input.close()
	import re
	double = re.compile(r'(\b\w+) \1\b') # regular expression for matching all double words
	strfilename = "" # placeholder for str converted filelist, should it be outside loop?
	findnewline = re.compile(r'\n')
	for elements in range(len(filelist)): #remove all "\n" and make list to single str
		strfilename += str(filelist[elements])
		findnewline.sub(' ', strfilename)
		
	result = double.findall(strfilename)
	return result


```

---

### Post by Greyed on 2008-09-27
> **slentzen said:**
> 
The problem is that when I call the function giving the filename as an argument like "findDouble(notes.txt)" I get a Name Error saying that anything before the ".txt" is not defined.
What am i doing wrong in my function?


Uhm, calling it wrong.

notes.txt is a class.method, class.variable reference.

"notes.txt" is a string that contains notes.txt.  Note the quotes.

findDouble("notes.txt")

---

### Post by slentzen on 2008-09-27
thank you very much for your answer.
If I would like to make the function-call more user friendly, such that the user would not have to include the quotes, how should i do that? 
e.g user writes: findDouble(notes.txt)
Should I write "def findDouble(str(inputfilename9):"?

---

### Post by Greyed on 2008-09-27
You would want to assign it to a variable.  eg:

[PHP]
filename = raw_input('Filename: ')
findDouble(filename)
[/PHP]

Also you have a mistake later on the the code.  You are passing the filename into a variable named filename.  However in your open call you're encasing it in quotes this making it a string.  So if the filename is notes.txt your open call is trying to open filename.

---

### Post by Greyed on 2008-09-27
Also, just had another thought.

If you're just learning Python take advantage of the interactive nature of the interpretor.  If you're writing code in one window have another open with the interpretor.  Then if you run across something that you're not sure of or does something unexpected, twiddle with it in the interpretor window until you get it to do what you want and move that into your code.  This is how I got used to the concept of slices.  Every time I needed to slice a string I had an interpretor open and I literally did this....

```

{grey@igbuntu:~} python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52)
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> string = 'I want the 2nd through 5th words.'
>>> string[2:20]
'want the 2nd throu'
>>> string[2:21]
'want the 2nd throug'
>>> string[2:23]
'want the 2nd through '
>>> string[2:22]
'want the 2nd through'

```

This is a contrived example so noone needs to point out split to me, thanks.  Point is I had to literally create a sample string and if I wanted columns 2 through 21 I'd mess with the string in the interpretor until I got what I wanted and then moved that back into my code.

I think that will help you catch a lot of the mistakes you're making like this...

```

>>> filename = 'notes.txt'
>>> open('filename')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IOError: [Errno 2] No such file or directory: 'filename'

```

---

### Post by slentzen on 2008-09-27
Thank you very much for your help. As soon as i got back and did as you recommended, I also realised that there was the mistake with converting the filename to a string. It has been corrected now.

I am already doing as you recommend with running the interactive interpreter while writing the scripts, and it really does help alot. But it can't find all of my mistakes. That's when you people here can supply me with more understandable information on my mistakes :) Thanks

---

