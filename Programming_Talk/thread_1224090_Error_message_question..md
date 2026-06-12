---
title: "Error message question."
date: 2009-07-27
forum: Programming Talk
---

### Post by swoll1980 on 2009-07-27
[python]

Is there a better way to do an error check/message than how I did it?

```
[COLOR="Sienna"]def[/COLOR] octal():
    x = [COLOR="MediumTurquoise"]input[/COLOR] ([COLOR="Magenta"]"Enter a whole number that is less than 64   "[/COLOR])
    [COLOR="DarkRed"]if[/COLOR] x >= [COLOR="Magenta"]64[/COLOR]:
        [COLOR="DarkRed"]print[/COLOR] [COLOR="Magenta"]"Please use only numbers that are less than 64"[/COLOR]
        [COLOR="DarkRed"]print[/COLOR]
        error()
   [COLOR="DarkRed"] else[/COLOR]:
        s1 = [COLOR="DeepSkyBlue"]str[/COLOR](x/8)
        a = x/[COLOR="Magenta"]8[/COLOR]
        b = a*[COLOR="Magenta"]8[/COLOR]
        s2 = [COLOR="DeepSkyBlue"]str[/COLOR](x-b)
        octal = s2 + s1
      [COLOR="DarkRed"]  print[/COLOR] x,[COLOR="Magenta"]"In octal is"[/COLOR], octal
        [COLOR="DarkRed"]print[/COLOR]
        main()

[COLOR="DarkRed"]def[/COLOR] error():
    octal()
```

---

### Post by monraaf on 2009-07-27
I think it's preferable to put the relevant code between php or code tags. like so:

[PHP]
print 'hello world'
[/PHP]

People aren't generally inclined to download attachments.

---

### Post by swoll1980 on 2009-07-27
OK. fixed it.

---

### Post by swoll1980 on 2009-07-27
> **monraaf said:**
> I think it's preferable to put the relevant code between php or code tags. like so:

[PHP]
print 'hello world'
[/PHP]

People aren't generally inclined to download attachments.

I fixed how I posted the source. I still want to know if this is the best way to do an error message. Looking at what I wrote that might not have been clear.

---

### Post by swoll1980 on 2009-07-27
bump

---

### Post by Can+~ on 2009-07-27
If you're building a module for other programmers to use, the proper way is to raise an exception, for example:

[PHP]def octal(decvalue):
	
	if decvalue > 64:
		raise ValueError("Number cannot exceed 64")
	
	# return string formatted as Octal
	return "%o" % decvalue[/PHP]

So when you call it with a number it will stop de execution

[PHP]Traceback (most recent call last):
  File "asdf.py", line 12, in <module>
    print octal(65)
  File "asdf.py", line 6, in octal
    raise ValueError("Number cannot exceed 64")
ValueError: Number cannot exceed 64[/PHP]

It causes an exception. And then, when you want to use it:

[PHP]try:
	x = int(raw_input("Number to convert:"))
	print octal(x)
except ValueError, errormsg:
	print errormsg[/PHP]

Now, all this is for the purpose of having an application that is as modular as possible, so later I could use your function and it will raise the proper exception in my code so I can catch it.

If you're dealing with user input in short snippets, there's no point on using all this, therefore, you can just use a while() to do the error checking.

And btw, the other day you asked about how to fromat output, in the link I gave you that day, there was one particular output that you should've noticed

[PHP]print "%o" % number[/PHP]

Prints as Octal.

---

### Post by swoll1980 on 2009-07-27
> **Can+~ said:**
> 

[PHP]print "%o" % number[/PHP]

Prints as Octal.

Thanks for your time. I wish I would have noticed that yesterday. I didn't need it at the time, so it didn't catch my eye. As far as the program goes, I'm just learning how to create functions. I'm just chaining together a bunch of random crap, to learn how this stuff works. This module, interacts with another menu module, that calls other various functions.

---

