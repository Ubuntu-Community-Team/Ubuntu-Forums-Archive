---
title: "running .py files in terminal ?"
date: 2011-01-04
forum: Programming Talk
---

### Post by kukker32 on 2011-01-04
so well uhm.. i've recently started to learn how to program python. :)
and im making the classic 'helloworld' thing...

this is my code

```
#!/usr/bin/python
#Filename : helloworld.py
print 'Hello World'
```

but when i went to terminal to try and run it.

```

allan@allan-laptop:~$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> python helloworld.py
  File "<stdin>", line 1
    python helloworld.py
                    ^
SyntaxError: invalid syntax
```

i get that error message :( my helloworld.py file is saved on the desktop o.O where should i save it to be able to run it ? or what have i done wrong ?

help is much apprpriciated.

---

### Post by Arndt on 2011-01-04
> **kukker32 said:**
> so well uhm.. i've recently started to learn how to program python. :)
and im making the classic 'helloworld' thing...

this is my code

```
#!/usr/bin/python
#Filename : helloworld.py
print 'Hello World'
```

but when i went to terminal to try and run it.

```

allan@allan-laptop:~$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> python helloworld.py
  File "<stdin>", line 1
    python helloworld.py
                    ^
SyntaxError: invalid syntax
```

i get that error message :( my helloworld.py file is saved on the desktop o.O where should i save it to be able to run it ? or what have i done wrong ?

help is much apprpriciated.

You should not mention "python" twice. You can do it like this:

```
$ python helloworld.py
Hello World
$
```

or like this:

```
$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import helloworld
Hello World
```

And if you have made the script executable, using chmod +x, you can also do this:

```
$ ./helloworld.py
Hello World
$
```

---

### Post by juancarlospaco on 2011-01-04
**#!/usr/bin/env python**

---

### Post by kukker32 on 2011-01-04
> **Arndt said:**
> 

```
$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import helloworld
Hello World
```
$[/CODE]

i tried do this but.. still get the same error message..

---

### Post by Arndt on 2011-01-04
> **kukker32 said:**
> i tried do this but.. still get the same error message..

What do you get? Please show the whole interaction.

---

### Post by kukker32 on 2011-01-04
> **juancarlospaco said:**
> **#!/usr/bin/env python**

is this instead of writing #!/usr/bin/python in the code ?

---

### Post by kukker32 on 2011-01-04
> **Arndt said:**
> What do you get? Please show the whole interaction.


uhm this is quite confusing but i try to hang on.. :)

allan@allan-laptop:~$ python
i entered python to enter python terminal

Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> python helloworld.py
  File "<stdin>", line 1
    python helloworld.py
                    ^
SyntaxError: invalid syntax
>>> $ python helloworld.py
  File "<stdin>", line 1
    $ python helloworld.py
    ^
SyntaxError: invalid syntax
>>> import helloworld
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named helloworld
>>> 


could it be something like the localhost problems i had last month with saving in the wrong places ? because currently it is saved on desktop..

---

### Post by Arndt on 2011-01-04
> **kukker32 said:**
> uhm this is quite confusing but i try to hang on.. :)

allan@allan-laptop:~$ python
i entered python to enter python terminal

Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> python helloworld.py
  File "<stdin>", line 1
    python helloworld.py
                    ^
SyntaxError: invalid syntax
>>> $ python helloworld.py
  File "<stdin>", line 1
    $ python helloworld.py
    ^
SyntaxError: invalid syntax
>>> import helloworld
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named helloworld
>>> 


could it be something like the localhost problems i had last month with saving in the wrong places ? because currently it is saved on desktop..

You misunderstood my examples. When the input lines start with $, it means you are supposed to be in a shell. Those were three different ways of doing the same thing (running your script).

---

### Post by kukker32 on 2011-01-04
> **Arndt said:**
>  $, it means you are supposed to be in a shell. .

? being new to python i don't know what that is or how to 'entern' shell ?

---

### Post by 23dornot23d on 2011-01-04
To create the program

gedit helloworld.py

```

#!/usr/bin/python
#Filename : helloworld.py
print 'Hello World'

```and then save it ....... 

Then

To run the program ..........




  ( just type it all in ..... you are typing python ....... which runs the python editor/console  ...... 

```

but once its running you are asking for it to run itself again ......... you will not see these   >>>  when you run it.
>>>
just type whats in bold below ...... all in one line ...... and it runs the program giving the output
to the screen on the line below of [I]Hello World
[/I] 
```


So yours will just look like this .......

allan@allan-laptop:~$ [B]python helloworld.py

[/B]_*The output will then appear on the line below it .....*_allan@allan-laptop:~$ [B]Hello World

[/B] stick with it .......

---

### Post by nitstorm on 2011-01-04
Open terminal.
Applications->Accessories->Terminal

Then type ```

cd /location/to/where/you/stored/your/python/file

```
In the above command replace /location/to/where/you/stored/your/python/file with the actual location of the folder in which the file is present. For example, if it's in your home directory *cd ~/ *

Then type
```

python helloworld.py

```

That should work :)

---

### Post by kukker32 on 2011-01-04
what i could read from that was you wanted me to run
allan@allan-laptop:~$ python helloworld.py

so i did that.. and

allan@allan-laptop:~$ python helloworld.py
python: can't open file 'helloworld.py': [Errno 2] No such file or directory


:(

---

### Post by kukker32 on 2011-01-04
> **nitstorm said:**
> Open terminal.
Applications->Accessories->Terminal

Then type ```

cd /location/to/where/you/stored/your/python/file

```In the above command replace /location/to/where/you/stored/your/python/file with the actual location of the folder in which the file is present. For example, if it's in your home directory *cd ~/ *

Then type
```

python helloworld.py

```That should work :)


allan@allan-laptop:~$ ~/
bash: /home/allan/: is a directory
allan@allan-laptop:~$ python helloworld.py
Hello World


thanks man !

---

### Post by CaptainMark on 2011-01-04
your opening a python interactive shell and telling that shell you want to run a python program,  imagine walking into shoe shop and telling the assistant you want to go to a shoe shop to buy shoes, 
you can either tell the shell the functions youd like to run interactively
or you can tell a terminal where to find the file in which youve written the functions youd like to run

---

### Post by juancarlospaco on 2011-01-04
> **kukker32 said:**
> is this instead of writing #!/usr/bin/python in the code ?

yes

---

### Post by montypython33 on 2012-11-07
I think the problem might be that you did not save the document as .py file.

---

