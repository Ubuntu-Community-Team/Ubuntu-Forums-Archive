---
title: "C# {n} like , in python"
date: 2009-11-27
forum: Programming Talk
---

### Post by McWeirdo on 2009-11-27
Hi , I've encountered a problem in python, as I've learned more advanced stuff and skipped the basics I'm missing a simple thing:
I have  2 variables say x and y and I want to print:
" x:value_of_x y:value_of_y" 
where the values are the real values of x and y
in C# I would write:
"x:{0} y:{1}",x,y
can't find in py doc the appropriate syntax,
but I think I once saw it's something like that "x:%d y:%d" %x %y
but it doesn't work,it mumbles about&#1488;&#1496;&#1508;&#1511;&#1491;:P
print '+%d*x^%d' %self.data[self.sed-i] %self.sed-i

where sed is integer and the data[index] is integer THE ERROR:
TypeError: not enough arguments for format string

so if anybody could help me ,I would appreciate it.
Thx in advance!!

MCW

---

### Post by 0cton on 2009-11-27
you could just use string concatenation
"X:"+str(x)+"Y:"+str(y)
or that is called print formating 
%d stands for decimal %s for string there is also %h for hex and other stuff as well
the way it works in python  is
"this is %s and you have %d lives" % ("sparta",98)
you present it with a bunch of % and give it a tuple argument of all required replacements
I think you must have printf in C# were you do
printf("This is %s and you have %d lives %s","sparta",45,"man")

---

### Post by McWeirdo on 2009-11-27
> **0cton said:**
> you could just use string concatenation
&quot;X:&quot;+str(x)+&quot;Y:&quot;+str(y)
or that is called print formating 
%d stands for decimal %s for string there is also %h for hex and other stuff as well
the way it works in python  is
&quot;this is %s and you have %d lives&quot; % (&quot;sparta&quot;,98)
you present it with a bunch of % and give it a tuple argument of all required replacements
I think you must have printf in C# were you do
printf(&quot;This is %s and you have %d lives %s&quot;,&quot;sparta&quot;,45,&quot;man&quot;)

 Thank you :D

---

### Post by LKjell on 2009-11-27
The % is deprecated in version 3. If you use v2.6 it is recommended to use the new syntax. [http://docs.python.org/library/string.html#formatstrings](http://docs.python.org/library/string.html#formatstrings)

---

### Post by wmcbrine on 2009-11-27
Simplest, in this case (for Python 2.x):
```
print 'x:', x, 'y:', y
```
or -- one string with formatting codes and a tuple of values:
```
print 'x: %d y: %d' % (x, y)
```
2.6 and later add a new style that might seem familiar to you:
```
print 'x: {0} y: {1}'.format(x, y)
```

---

