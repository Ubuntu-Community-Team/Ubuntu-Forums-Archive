---
title: "&quot;%s %d %f&quot;, what are they called?"
date: 2008-10-13
forum: Programming Talk
---

### Post by Moezzie on 2008-10-13
Hello there.
Im looking for a way to shape the output from one of my applications. A long time ago i used something that looked like: %s or %d for this kind of thing. I think i could put it to good use here, but sadly enough i cant remember how to use it. And i don't remember what this procedure is called , so im having huge trouble finding something useful though google.
I know lots of languages use it, and it looks similar in most of them.

Could you maybe give me a name or point me to a good site?

---

### Post by leg on 2008-10-13
They are called format strings and are used as an argument in a function. The function would be a printf type functions that requires a number of strings each of which can have an accompanying format String.

```
printf(pi, '%d');
```or something similar.

[cpp reference for it.]("http://www.cplusplus.com/reference/clibrary/cstdio/printf.html")

Hope this helps.

---

### Post by dwhitney67 on 2008-10-13
Those look like formatting flags for the C language's printf() statement.

%s is for a string (char array).
%d is for an integer (int).
%f is for a float/double.

What language are you programming in?  C?

---

### Post by dwhitney67 on 2008-10-13
> **leg said:**
> They are called format strings and are used as an argument in a function. The function would be a printf type functions that requires a number of strings each of which can have an accompanying format String.

```
printf(pi, '%d');
```or something similar.

[cpp reference for it.]("http://www.cplusplus.com/reference/clibrary/cstdio/printf.html")

Hope this helps.
Aarrgg... why do you include code that is incorrect??  The rest of your post is correct though.

---

### Post by Canis familiaris on 2008-10-13
The "%s %d %f" are format specifiers
Which language are you using? C? Python? Something else.

Anyway for C the usage is eg.:

```
char strng[]="Linux"
printf("The OS is %s", strng);
```

and Python Usage is:
```
strng = "Linux"
print "The OS is %s" %strng
```

Now the %s in this example is the format specifier for a string. In both these cases the %s would be replace by the value of corresponding variable.

Similarly %d is for integers, %f is for float.

Look here for more details:
Python: 
[http://www.python.org/doc/2.5.2/lib/typesseq-strings.html](http://www.python.org/doc/2.5.2/lib/typesseq-strings.html)
C: 
[http://www.cplusplus.com/reference/clibrary/cstdio/printf.html](http://www.cplusplus.com/reference/clibrary/cstdio/printf.html)
[http://www.cplusplus.com/reference/clibrary/cstdio/scanf.html](http://www.cplusplus.com/reference/clibrary/cstdio/scanf.html)

---

### Post by Moezzie on 2008-10-13
Oh, so its just C? I thought i hade seen these "formating strings" in python too, but i guess im mistaken then.
Im actually programming in Python right now. Maybe you could help me out with my actual problem instead.

Im trying to send a query to a MySQL server, but Python always throws a TypeError at me. Im getting the size of a file through os.path.getsize(pathToFile).
In the mysql table size is an int value and file_name is a varchar.
```
self.cursor.execute("INSERT INTO file_info (size) VALUES("+int(size)+") WHERE file_name = '"+str(name)+"'")
```
```
self.cursor.execute("INSERT INTO file_info (size) VALUES("+int(size)+") WHERE file_name = '"+str(name)+"'")
TypeError: cannot concatenate 'str' and 'int' objects
```

Feels like I've written this query in a hundred different ways, but it never seems to work.

---

### Post by mssever on 2008-10-13
> **Moezzie said:**
> Oh, so its just C?
See Anurag_panda's post above. They work in Python, too. Format strings are the only reasonable way to include variables in Python strings, IMO. String concatenation is slow and tedious, and Python has no string interpolation.

EDIT: Here's one of your examples rewritten:
```
self.cursor.execute("INSERT INTO file_info (size) VALUES('%d') WHERE file_name = '%s'" % (size, name))
```

---

### Post by leg on 2008-10-13
> **dwhitney67 said:**
> Aarrgg... why do you include code that is incorrect??  The rest of your post is correct though.yea apologies but I wrote it from memory and wasn't sure of the correct format. They are used in more than the C language though and used differently in some of those. I don't actually do much C programming and my memory was probably corrupted from sql syntax which I believe is closer to what I wrote.

---

