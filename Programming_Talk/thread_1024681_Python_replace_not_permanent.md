---
title: "Python replace not permanent"
date: 2008-12-29
forum: Programming Talk
---

### Post by openjoel on 2008-12-29
So I'm new to python and this is my first little bigger application,
I'm trying to do some basic templating stuff and then sending it with cherrypy.
```
file = open("templates/index.html", 'r').read()
return file
```
this will print the html code in the browser.
Now the thing I want to do is replace $$title$$ with another value defined in the python file.
But I do not want it to be permanent, if you get what I mean.
I just want the variable file to contain the edited version.

Now how do I do that?

---

### Post by kaivalagi on 2008-12-29
The variable "file" is actually just a string, it is populated from the .read() method

So, if you want to replace something in it then it is a simple case of a string replace:

```
file = file.replace("abc","def")
```

You may want to read up on regular expressions though, as they might handle the replaces better in all cases...[http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)

---

### Post by openjoel on 2008-12-29
> **kaivalagi said:**
> The variable "file" is actually just a string, it is populated from the .read() method

So, if you want to replace something in it then it is a simple case of a string replace:

```
file = file.replace("abc","def")
```

You may want to read up on regular expressions though, as they might handle the replaces better in all cases...[http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)

Thanks man! It worked perfect for my means! Now I just need to make it a bit more intelligent :)

---

