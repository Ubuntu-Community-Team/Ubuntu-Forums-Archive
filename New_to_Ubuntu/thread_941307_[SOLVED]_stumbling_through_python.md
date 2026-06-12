---
title: "[SOLVED] stumbling through python"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by WriteGirl on 2008-10-08
I'm attempting to work my way through a python tutorial and I've gotten stuck at the first one. 

According to what I'm reading, I should put this program
 > #!/usr/bin/python
# Filename : helloworld.py
print 'Hello World'


into a text editor and then use the command python helloworld.py and it will print 'Hello World' 

However, I end up getting 
> SyntaxError: invalid syntax
>>> helloworld.py
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'helloworld' is not defined

Anyone know what I'm doing wrong?

Thanks

---

### Post by iansane on 2008-10-08
well the syntax is right. I just copy/pasted yours and it works for me.

Got similar errors in c++ when I made syntax errors or forgot to include a library.

Maybe make sure you have everything needed for python installed in synaptic. I have no clue what that might be though.

---

### Post by talsemgeest on 2008-10-08
Try just ```
print "Hello World"
``` and then run that.

---

### Post by WriteGirl on 2008-10-08
I know that 'print Hello World' works, but I'm trying to follow this tutorial online, and that is the way they had it. I'm assuming that later I'm going to want to be able to save my programs so I can use them more than once or edit them or something.

Thanks for trying.

---

### Post by OutOfReach on 2008-10-08
Are you trying to launch your script from the Python console? I don't think that will work.

Open a terminal and change to the directory that contains your python file:
```
cd /DIRECTORY/WHERE/FILE/IS/LOCATED
```

Then execute the python script:
```
python my_python_script.py
```

---

### Post by WriteGirl on 2008-10-08
I think I understand what you're saying but I'm not sure how to do it. I think that I want to put change to the directory !/usr/bin/python, but it's telling me that that doesn't exist. Is there a way to create that or is there already a place that I should be using?

---

### Post by OutOfReach on 2008-10-08
Change to the directory where you saved the python file you created. Like, say if I created a Python file, and I saved it to my Desktop, I would do:
```
cd /home/username/Desktop/
```

Then I would execute the python script:
```
python my_python_script.py
```

---

### Post by talsemgeest on 2008-10-08
Where have you saved the file? E.g. if you have saved it at /home/user/desktop/helloworld.py you would open a terminal and type ```
cd /home/user/desktop
python helloworld.py
```

---

### Post by WriteGirl on 2008-10-08
Success! Thank you very much!

---

### Post by skillllllz on 2008-10-08
Your program does have a syntax error.

You wrote this:

```
#!/usr/bin/python
# Filename : helloworld.py
print 'Hello World'
```

When it should look like this:

```
#!/usr/bin/python
# Filename : helloworld.py
print "Hello World"
```

Do you see your mistake?

Also, if you are in the python console, your prompt will look something like this:

```
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

You will need to exit the python console (Ctrl+D) before running your program.

---

### Post by OutOfReach on 2008-10-08
> **skillllllz said:**
> Your program does have a syntax error.

You wrote this:

```
#!/usr/bin/python
# Filename : helloworld.py
print 'Hello World'
```

When it should look like this:

```
#!/usr/bin/python
# Filename : helloworld.py
print "Hello World"
```


Well, you can do both, ' ' quotes and " " quotes make no difference in Python.

@WriteGirl: No problem. Make sure to mark your thread as solved: Thread Tools (above your first post) > Mark As Solved

---

### Post by skillllllz on 2008-10-08
> **OutOfReach said:**
> Well, you can do both, ' ' quotes and " " quotes make no difference in Python.

Just learned me something. Thanks OOR. :)

---

### Post by talsemgeest on 2008-10-08
> **skillllllz said:**
> Just learned me something. Thanks OOR. :)
I guess you are upgrading your "skillllllz" ;) Sorry couldnt resist.

---

### Post by skillllllz on 2008-10-08
> **talsemgeest said:**
> I guess you are upgrading your "skillllllz" ;) Sorry couldnt resist.

Don't you mean upgrading your 'skillllllz'

LOL, sorry couldn't resist either.

---

### Post by talsemgeest on 2008-10-08
I suppose so. :)

---

