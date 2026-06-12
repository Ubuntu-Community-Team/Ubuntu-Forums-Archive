---
title: "Python web developing - inline suggestion"
date: 2011-03-02
forum: Programming Talk
---

### Post by qrwe on 2011-03-02
Hello,

Sometimes when I make some code snippets in PHP, I really wished that the PHP-simplicity of web development would be available for python. I'm well informed about django (among other frameworks), but thinks that python CGI development could be more intuitive than that. Example given:

```

<html>
.
.
.
<?python
def myFunction(arg1, ..., argn):
  variables
  statements
  return value

...more python code...
?>
.
.
.
</html>

```

I just wonder if anyone has seen something like this to keep my eyes on. Maybe I'm just dreaming about the pink cloud, but still: it would be truly cool if there's any project out there, supporting this kind of web development.

---

### Post by DaithiF on 2011-03-02
As you probably know, the mixing of code and html like this is usually seen as a very bad thing ... django and other web-frameworks were created to solve this problem, ie. to avoid the need to mix programming logic & html like this.

with that said, Karrigell seems to offer what you want, in particular its python-inside-html feature: [http://www.karrigell.fr/doc/en/pythoninsidehtml.html](http://www.karrigell.fr/doc/en/pythoninsidehtml.html)

also of interest may be this list: [http://wiki.python.org/moin/Templating](http://wiki.python.org/moin/Templating)

but really, I would recommend you stick with django, its a much much better way to do web development :)

---

### Post by qrwe on 2011-03-02
> **DaithiF said:**
> As you probably know, the mixing of code and html like this is usually seen as a very bad thing ... django and other web-frameworks were created to solve this problem, ie. to avoid the need to mix programming logic & html like this.

with that said, Karrigell seems to offer what you want, in particular its python-inside-html feature: [http://www.karrigell.fr/doc/en/pythoninsidehtml.html](http://www.karrigell.fr/doc/en/pythoninsidehtml.html)

also of interest may be this list: [http://wiki.python.org/moin/Templating](http://wiki.python.org/moin/Templating)

but really, I would recommend you stick with django, its a much much better way to do web development :)

Thank you for both info and advice! I'll consider them both.

---

