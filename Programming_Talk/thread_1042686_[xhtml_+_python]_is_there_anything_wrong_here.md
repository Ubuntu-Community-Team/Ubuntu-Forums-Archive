---
title: "[xhtml + python] is there anything wrong here?"
date: 2009-01-17
forum: Programming Talk
---

### Post by TreeFinger on 2009-01-17
OK, I am trying to learn python for web development and I am having trouble right away. I am not sure if it is being caused by my xhtml and/or python code, or by my server configuration.

The problems is like this, when I hit 'submit' on my form, the browser asks me to download the script, instead of having it execute and display in the browser what I want...


here are my two files.. 

html file
[php]
<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" lang="EN">

<head>
	<!-- <link rel="stylesheet" type="text/css" href="mystyle.css" /> -->
<title>Admin Page - Enter New Book Into DB</title>
</head>

<body>
	<h1>Add new book to DB</h1>

	<form name="add_book" action="cgi-bin/add_book.py" method="get">
		ISBN: <input type="text" name="isbn" value=""> <br />
		Title: <input type="text" name="title" value=""> <br />
		Author Last: <input type="text" name="last" value=""> <br />
		Publication Year: <input type="text" name="yop" value=""> <br />
		<input type="submit" value="Enter Data" />
	</form>

		<p>Enter Data for one book, and then click the 'Enter Data' button. </p>

	</body>
</html>
[/php]

add_book.py
[php]
# !/usr/bin/python

import cgi

print "Content-Type: text/plain\n\n"

The_Form = cgi.FieldStorage()

for name in The_Form.keys():
	print "Input: " + name + " value: " + The_Form[name].value + "<BR>"

print "All Done."
[/php]

Is this a problem with my code? or my apache configuration?

---

### Post by croto on 2009-01-17
Hi,

Did you check if the python script is executable?

---

### Post by TreeFinger on 2009-01-17
> **croto said:**
> Hi,

Did you check if the python script is executable?

yes, I made my post here first because I want to ensure nothing is wrong with the code. When I verify that I will mark the thread as solved and move to a different section of the forums.

---

### Post by croto on 2009-01-17
sorry, I'm not sure I explained myself correctly... I just meant that in order for the python script to work, it should have "executable" permission (chmod +x add_book.py).

---

### Post by TreeFinger on 2009-01-17
> **croto said:**
> sorry, I'm not sure I explained myself correctly... I just meant that in order for the python script to work, it should have "executable" permission (chmod +x add_book.py).


You did. I answered that question. Yes, it is executable.. just look at the code please :) I don't want to get off topic for the sub-forum.

---

### Post by croto on 2009-01-17
I don't see anything wrong with the code. The fact that the browser wants to download the script instead of executing it suggests that the http server is not even executing the script. I guess then that the problem is with the apache configuration.

EDIT: Actually I see something wrong in the first line. There is a space between "#" and "!" which shouldnt be there:
```

#!/usr/bin/python 

```

---

### Post by TreeFinger on 2009-01-17
> **croto said:**
> I don't see anything wrong with the code. The fact that the browser wants to download the script instead of executing it suggests that the http server is not even executing the script. I guess then that the problem is with the apache configuration.

i changed the file ending to 'cgi' instead of 'py', and I get a little bit better of a result... the contents of the script file is displayed in plain text on the page after clicking 'submit'.

i'll try changing it back and doing the change suggested above... something is wrong with my server right now tho... terminal frozen.. but apache server still working

---

### Post by croto on 2009-01-17
Another comment about the python code. You're telling the browser to interpret the output of your python script as text/plain. The browser will not parse any html tag (it will just print everything as text). If you want to use html tags, you'll have to use "Content-Type: text/html\n\n"

---

### Post by TreeFinger on 2009-01-17
sigh, i can't even get a prompt to restart this server... going to have to hit the power button. someone has been unplugging it from the wall.. i hope i am not running into hardware issues.... sorry for going off topic. i'll make the changes suggested when I can. thank you.

---

### Post by TreeFinger on 2009-01-19
OK, well my server is working just fine right now so I made the changes you guys suggested.

Still asks me to download the .py file after I hit 'submit'

Guess this means it is caused by something in my apache configuration?

form.html
[php]
<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" lang="EN">

<head>
	<!-- <link rel="stylesheet" type="text/css" href="mystyle.css" /> -->
<title>Admin Page - Enter New Book Into DB</title>
</head>

<body>
	<h1>Add new book to DB</h1>

	<form name="add_book" action="cgi-bin/add_book.py" method="post">
		ISBN: <input type="text" name="isbn" value=""> <br />
		Title: <input type="text" name="title" value=""> <br />
		Author Last: <input type="text" name="last" value=""> <br />
		Publication Year: <input type="text" name="yop" value=""> <br />
		<input type="submit" value="Enter Data" />
	</form>

		<p>Enter Data for one book, and then click the 'Enter Data' button. </p>

	</body>
</html>
[/php]

add_book.py
[php]
# !/usr/bin/python

import cgi

print "Content-Type: text/html\n\n"

The_Form = cgi.FieldStorage()

for name in The_Form.keys():
	print "Input: " + name + " value: " + The_Form[name].value + "<BR>"

print "All Done."
[/php]

---

### Post by croto on 2009-01-19
do you still have the space in between # and ! in the shebang line?
```

# !/usr/bin/python 

```


The space should not be there, it will prevent the python code to run normally. You should be able to run the code from the command line like this:
```

./add_book.py

```

It will give the following output:
```

Content-Type: text/html


All Done.

```

If this is not the behavior you're get, then there's something wrong on the python side. If you're getting this, then it may be the appache configuration.

---

### Post by TreeFinger on 2009-01-19
> **croto said:**
> do you still have the space in between # and ! in the shebang line?
```

# !/usr/bin/python 

```


The space should not be there, it will prevent the python code to run normally. You should be able to run the code from the command line like this:
```

./add_book.py

```

It will give the following output:
```

Content-Type: text/html


All Done.

```

If this is not the behavior you're get, then there's something wrong on the python side. If you're getting this, then it may be the appache configuration.


hmm, there just may be something wrong with the script...

```

# ./add_book.py
-bash: ./add_book.py: /usr/bin/python^M: bad interpreter: No such file or directory

```

add_book.py
[php]
#!/usr/bin/python

import cgi

print "Content-Type: text/html\n\n"

The_Form = cgi.FieldStorage()

for name in The_Form.keys():
        print "Input: " + name + " value: " + The_Form[name].value + "<BR>"

print "All Done."
[/php]

this works tho:
```

# python add_book.py
Content-Type: text/html


All Done.

```

---

### Post by croto on 2009-01-19
> **TreeFinger said:**
> hmm, there just may be something wrong with the script...

```

# ./add_book.py
-bash: ./add_book.py: /usr/bin/python^M: bad interpreter: No such file or directory

```


That '^M' is the "linefeed" character. In Unix, the line separator is the "newline" character, while in Windows it is "linefeed"+"newline". Did you copy that file from a windows partition? I guess you would need to convert the file to Unix format. Easiest way: open a text editor and type it in again.

---

### Post by TreeFinger on 2009-01-19
> **croto said:**
> That '^M' is the "linefeed" character. In Unix, the line separator is the "newline" character, while in Windows it is "linefeed"+"newline". Did you copy that file from a windows partition? I guess you would need to convert the file to Unix format. Easiest way: open a text editor and type it in again.


yep, I was editing it in gVim on my windows partition. 

I don't understand how that linefeed character doesn't go away after I delete the lines around it...


OK, thank you. I can now execute the script from CLI.

Yet still, when I view it on the web, the browser asks me to download it...


hmmm... '.py' files in '/usr/lib/cgi-bin' execute...

OK, I can execute the script if i type in the browser [http://192.168.0.2/cgi-bin/add_book.py](http://192.168.0.2/cgi-bin/add_book.py)

but if I first go to form.html and hit submit, it asks me to download...

---

### Post by croto on 2009-01-19
<troubleshooting mode>
hmm, when it asks you to download the file, does it say what file type you're about to download? If you download it, what's the contents of that file?

---

### Post by TreeFinger on 2009-01-19
> **croto said:**
> <troubleshooting mode>
hmm, when it asks you to download the file, does it say what file type you're about to download? If you download it, what's the contents of that file?

well, I do not have python installed on my windows partition, just pops up like a normal download. the content of the file is the same as it is while stored on the server.

this is odd!

---

### Post by croto on 2009-01-19
on my firefox, when I click something to download, there's a popup that tells me on the top of the popup: you have chose to download blah, which is of type blah. What does it say when you submit the form? 
And it downloads the contents of the python script?

---

### Post by TreeFinger on 2009-01-19
> **croto said:**
> on my firefox, when I click something to download, there's a popup that tells me on the top of the popup: you have chose to download blah, which is of type blah. What does it say when you submit the form? 
And it downloads the contents of the python script?


yes, it downloads the entire contents of the python script.

---

### Post by TreeFinger on 2009-01-19
html code again...

[php]

<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" lang="EN">

<head>
        <!-- <link rel="stylesheet" type="text/css" href="mystyle.css" /> -->
<title>Admin Page - Enter New Book Into DB</title>
</head>

<body>
        <h1>Add new book to DB</h1>

        <form name="add_book" method="post" action="cgi-bin/add_book.py">
                ISBN: <input type="text" name="isbn" value=""> <br />
                Title: <input type="text" name="title" value=""> <br />
                Author Last: <input type="text" name="last" value=""> <br />
                Publication Year: <input type="text" name="yop" value=""> <br />
                <input type="submit" value="Enter Data" />
        </form>

                <p>Enter Data for one book, and then click the 'Enter Data' button. </p>

        </body>
</html>
[/php]

---

### Post by croto on 2009-01-19
I uploaded your php and python script to a webhosting account I have to do experiments. On my side, it works fine. The fact that the script runs fine when you point your browser to the script directly makes me think that the python side is ok now. Since the php is fine when I try it here, I wouldn't think the problem is there... I guess things suggest there's a problem with the apache configuration, but I really don't know. Let me know of any result, now I'm curious about this :)

---

### Post by TreeFinger on 2009-01-19
> **croto said:**
> I uploaded your php and python script to a webhosting account I have to do experiments. On my side, it works fine. The fact that the script runs fine when you point your browser to the script directly makes me think that the python side is ok now. Since the php is fine when I try it here, I wouldn't think the problem is there... I guess things suggest there's a problem with the apache configuration, but I really don't know. Let me know of any result, now I'm curious about this :)

could you please show me what file you are using? you said php but it is an html file.

---

### Post by croto on 2009-01-19
I'm using this one:

```

<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" lang="EN">

<head>
        <!-- <link rel="stylesheet" type="text/css" href="mystyle.css" /> -->
<title>Admin Page - Enter New Book Into DB</title>
</head>

<body>
        <h1>Add new book to DB</h1>

        <form name="add_book" method="post" action="cgi-bin/add_book.py">
                ISBN: <input type="text" name="isbn" value=""> <br />
                Title: <input type="text" name="title" value=""> <br />
                Author Last: <input type="text" name="last" value=""> <br />
                Publication Year: <input type="text" name="yop" value=""> <br />
                <input type="submit" value="Enter Data" />
        </form>

                <p>Enter Data for one book, and then click the 'Enter Data' button. </p>

        </body>
</html>  

```

---

