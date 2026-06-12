---
title: "Python trouble with textfiles in windows and linux"
date: 2007-02-20
forum: Programming Talk
---

### Post by [h2o] on 2007-02-20
Hi!

Currently working on a project which uses python (2.4), pygtk and glade.
The program is supposed to run under both Linux and Windows (using py2exe).

I want the program to be configurable through the use of simple textfiles, which causes trouble since Windows uses '\r\n' as newline character and Linux uses '\n'. I found something about opening the files with open(filepath,'U') but it doesn't seem to work.
Ok, that was problem number one.

Problem number two is that I read (key, name) pairs from a textfile and store them as possible values to put into a database (MySQL, the field is a textfield storing the key).
Problem is that the values I read from the database and the values from the textfield is not being compared appropriately on Windows. It works like a charm on Linux though.
My guess is this having to do with my Ubuntu environment utilizing UTF-8 while Windows doesn't. Current code just uses the == operator, is there another way?

Any ideas on how to solve my problems?

---

### Post by dwblas on 2007-02-20
I think the easiest way to solve the text file problem is to not use returns.  You can then use any word processor to put them in on each machine, or use something like "***" as a line deliminator and data.split( "***" ).  You could also use MToolsFM to copy from Linux to a DOS diskette and it will add the proper termination characters.> Problem is that the values I read from the database and the values from the textfield is not being compared appropriately on Windows.Doesn't make any sense (does it ever) unless you are changing the textfield before you add it to the database.  Do an ord(chr) one by one for both fields as that will give you the actual decimal values and see where the difference is.  Another thought is to use string.strip().  One of them may have a space or two appended somewhere.

---

### Post by [h2o] on 2007-02-20
Well, using a line delimiter has come to mind, but I'd prefer not to since it makes the file harder to read.
Using floppies are not in question since A) it is 40 MB in size when packed together with GTK, and B) I don't have one ;)

I am having some difficulties debugging exactly what goes wrong since the .exe I get from py2exe doesn't write to the terminal (anyone knows how to fix this??) so I am more or less guessing exactly what goes wrong.
I'll try to explain in more detail what the program does and where it goes wrong:
I have a field in the database that contains a string with a certain keyword. I also have a .txt-file that holds all available keys and their respective name.
The program loads the list of available keys and names from the textfile into a list. This list is used to create a dropdown menu (GtkComboBoxEntry).
Then it gets the data from the database and should select the correct row in the dropdown menu by iterating through the list while counting up an index variable until it founds the correct one and breaks out of the loop, and then selects the row with that specific index number.

I should perhaps point out that the possible keys could contain non-english characters, or more specifically the extra swedish chars 'å, ä and ö' which I guess might have some impact on things.

And note also that everything works fantastically well in Ubuntu, but the same code in Windows doesn't.

---

### Post by gh0st on 2007-02-20
This is just a suggestion as I don't have a lot of experience of Python development on Windows ;) 

Can't you copy the source code to the Windows machine and then just run the code from the Python interpreter in a command window? The usual "python myprogram.py" should work if Python is installed on the Windows box. It might help you debug the program.

If for some reason you don't want users to have access to the source in the finished product you could package it with py2exe when the problems are ironed out.

Like I say just a suggestion and it may not be be much help. Thought it was worth mentioning though. Good luck :)

---

### Post by Tomosaur on 2007-02-20
You should use the open and read methods rather than parsing the file yourself, specifically for this reason.

Read up on this [Here](http://docs.python.org/lib/built-in-funcs.html#built-in-funcs)
and [here](http://docs.python.org/lib/bltin-file-objects.html). It can be a little confusing at first, but practice makes perfect :)

---

### Post by dwblas on 2007-02-20
The Swedish characters should not create a problem as I am pretty sure that they are 8 bit.  Somewhere in the decimal 240 range.  Again, you may want to convert everything to decimal, and write each of the compare letters and the result to an error file.  Also, are both the db field and the textfile field unicode?  That can make a difference if one is and one isn't.  Who knows what happens in Windows.  It's closed source.

---

### Post by [h2o] on 2007-02-21
> **Tomosaur said:**
> You should use the open and read methods rather than parsing the file yourself, specifically for this reason.
That is what i am doing. It looks sort of like this when I parse the file.
```

f = open(textfile)
my_list = []
rows = f.readlines()
for row in rows:
  if row[0] == '#': continue # Commented rows
  name, id = row.strip().split()
  my_list.append([id,name])

```

---

### Post by cwaldbieser on 2007-02-21
> **'[h2o] said:**
> That is what i am doing. It looks sort of like this when I parse the file.
```

f = open(textfile)
my_list = []
rows = f.readlines()
for row in rows:
  if row[0] == '#': continue # Commented rows
  name, id = row.strip().split()
  my_list.append([id,name])

```

You could always write your debugging code out to another file:
```

f = open(textfile)
fout = open("debug.txt", "w")
my_list = []
rows = f.readlines()
for row in rows:
  if row[0] == '#': continue # Commented rows
  name, id = row.strip().split()
  my_list.append([id,name])
  fout.write("[%s], [%s]" % (id, name))

```

Then just open the debug file in an editor like notepad++ or something that allows you to see the line ends and whitespace.

---

### Post by [h2o] on 2007-02-21
I realized that there was no problem running my application through the console if I just skipped the py2exe part. Thanks!

I also found a good-enough solution. That which caused the problem seems to have been the model = gtk.ListStore(str,str) I used to store everything in. It did 'something' to the character encoding.

What I do now is reading the data from file, then decoding it from either utf8 or iso-8859-1 (configurable in a configfile, ofcourse) and save it to a list.
Then I make a model, but when iterating I skip using the model and iterate through my list instead, since the list holds the correct values.
Not the prettiest solution perhaps, but now it works.

---

