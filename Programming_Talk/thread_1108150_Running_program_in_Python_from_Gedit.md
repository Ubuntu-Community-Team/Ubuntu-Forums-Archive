---
title: "Running program in Python from Gedit?"
date: 2009-03-27
forum: Programming Talk
---

### Post by rodney757 on 2009-03-27
I am learning python and am trying to run a simple program that I typed in gedit. I set the file as exe. When I select run in terminal, the terminal opens and the closes. When I select run in Python, nothing happens. Heres the program I typed:

```
#! /usr/bin/env python


# Area calculation program

print “Welcome to the Area calculation program”
print “–––––––––––––”
print

# Print out the menu:
print “Please select a shape:”
print “1  Rectangle”
print “2  Circle”
print "3  Square"

# Get the user’s choice:
shape = input(“> “)

# Calculate the area
if shape == 1:
    height = input('Please enter the height: ')
    width = input('Please enter the width: ')
    area = height*width
    print 'The area is', area
elif shape == 2:
    radius = input('Please enter the radius: ') 
    area = 3.14*(radius**2)
    print 'The area is', area
else:
    height = input('Please enter the height: ')
    width = input('Please enter the width: ')
    area = height*width
    print 'The area is', area
```

---

### Post by maddog39 on 2009-03-27
All you need to do is open a new terminal windows via Applications > Accessories > Terminal and type change to the directory your program is in. You can do this by doing:
```

cd name_of_the_directory_here

```
and then simply type:
```

python filename_of_your_program.py

```
This is the easiest and probably best way to run your python applications that I know of. Gedit isn't intended to be used as an IDE and I haven't ever used the functionality that youre referring to but using the command line directly is probably best.

---

### Post by Can+~ on 2009-03-27
Also, you can make things clearer using the """string"""

Instead of:
[PHP]print "Please select a shape:"
print "1  Rectangle"
print "2  Circle"
print "3  Square"[/PHP]

Use:
[PHP]print """Please select a shape:
  1. Rectangle
  2. Circle
  3. Square"""[/PHP]

(besides: '' or "" for strings, &#8220;&#8221; is not valid)

Also:
```
#! /usr/bin/env python
#!/usr/bin/env python
```

Remove that space.

---

### Post by rodney757 on 2009-03-27
When I do that I get this error:
```
File "Area Calculation Program.py", line 4
SyntaxError: Non-ASCII character '\xe2' in file Area Calculation Program.py on line 4, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```

---

### Post by Can+~ on 2009-03-27
> **rodney757 said:**
> When I do that I get this error:
```
File "Area Calculation Program.py", line 4
SyntaxError: Non-ASCII character '\xe2' in file Area Calculation Program.py on line 4, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```

Use either single quotes 'something' or double quotes "something":

“–––––––––––––” Wrong
"–––––––––––––" Good
'–––––––––––––' Good

---

### Post by rodney757 on 2009-03-27
> **Can+~ said:**
> Also, you can make things clearer using the """string"""

Instead of:
[PHP]print "Please select a shape:"
print "1  Rectangle"
print "2  Circle"
print "3  Square"[/PHP]

Use:
[PHP]print """Please select a shape:
  1. Rectangle
  2. Circle
  3. Square"""[/PHP]

(besides: '' or "" for strings, “” is not valid)

Also:
```
#! /usr/bin/env python
#!/usr/bin/env python
```

Remove that space.

Thanks for the suggestions. I was just following a tutorial and thats how it showed to type it, but your way is easier to read. I will keep that in mind from now on.

---

### Post by rodney757 on 2009-03-27
> **Can+~ said:**
> Use either single quotes 'something' or double quotes "something":

“–––––––––––––” Wrong
"–––––––––––––" Good
'–––––––––––––' Good

Does this look right?
```
#!/usr/bin/env python

# Area calculation program

print "Welcome to the Area calculation program"
print "–––––––––––––"
print

# Print out the menu:

print """Please select a shape:
  1.  Rectangle
  2.  Circle
  3.  Square"""

# Get the user’s choice:

shape = input(“> “)

# Calculate the area

if shape == 1:
    height = input("Please enter the height: ")
    width = input("Please enter the width: ")
    area = height*width
    print "The area is", area
elif shape == 2:
    radius = input("Please enter the radius: ") 
    area = 3.14*(radius**2)
    print "The area is", area
else:
    height = input("Please enter the height: ")
    width = input("Please enter the width: ")
    area = height*width
    print "The area is", area
```

If so, I still get this error:
```
 File "Area Calculation Program.py", line 6
SyntaxError: Non-ASCII character '\xe2' in file Area Calculation Program.py on line 6, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```

If not, can you elaborate a little more on what I'm doing wrong. I just started learning python last night:):)Thanks

---

### Post by nvteighen on 2009-03-27
Look at line 6 :)

Your error is just that you're using a non-ASCII character. Therefore, Python doesn't understand your code...

---

### Post by rodney757 on 2009-03-27
> **nvteighen said:**
> Look at line 6 :)

Your error is just that you're using a non-ASCII character. Therefore, Python doesn't understand your code...

Yeah I got that part, but I'm not sure what the non-ASCII character is? I'm not seeing the problem.

---

### Post by WW on 2009-03-27
The first double quote is not actually a double quote, it is '\xe2'.  Go to line 6 and manually retype the line.  You'll probably have to do this for some of the other quote-like characters.

By any chance did you cut-and-paste this code from a PDF file?  That often leads to problems like this.

---

### Post by Can+~ on 2009-03-27
[PHP]#!/usr/bin/env python

# Area calculation program

print "Welcome to the Area calculation program"
print "---------------"
print

# Print out the menu:

print """Please select a shape:
  1.  Rectangle
  2.  Circle
  3.  Square"""

# Get the user’s choice:

shape = input("> ")

# Calculate the area

if shape == 1:
    height = input("Please enter the height: ")
    width = input("Please enter the width: ")
    area = height*width
elif shape == 2:
    radius = input("Please enter the radius: ") 
    area = 3.14*(radius**2)
else:
    height = input("Please enter the height: ")
    width = input("Please enter the width: ")
    area = height*width

print "The area is", area[/PHP]

Fixed.

Also, why ask the height and width of a square? With one side you could do it.

---

### Post by rodney757 on 2009-03-28
^Thanks. I tried your copy and it said there was a error on line 16, so I just retyped it and it worked. I guess I do only need one side of a square. I need to learn to think a little differently. I didn't copy this off a pdf and I typed it out. I'm wondering why the quotes were messed up like that? Any idea?

---

### Post by Chokkan on 2009-03-28
Yeah sometimes if you copy and paste from a web page the quotes come out funky.

---

### Post by Can+~ on 2009-03-28
> **rodney757 said:**
> ^Thanks. I tried your copy and it said there was a error on line 16, so I just retyped it and it worked. I guess I do only need one side of a square. I need to learn to think a little differently. I didn't copy this off a pdf and I typed it out. I'm wondering why the quotes were messed up like that? Any idea?

Just take a peek at LaTeX documents:

```
``I'm wondering, why the quotes were messed up \emph{like that}?''---rodney757 exclaimed.
```

The LaTeX quotation marks are the same that are used in literature, start and ending quotes. Python uses the C-style quotes " " and ' '. I don't know any language that uses the literal quotation marks.

---

