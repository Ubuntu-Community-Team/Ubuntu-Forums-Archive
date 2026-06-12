---
title: "mod_python and apache2"
date: 2007-04-02
forum: Programming Talk
---

### Post by MadeR on 2007-04-02
Desiring to learn python for my degree thesis (web based application), I installed mod_python.
I wish python had a documentation like the one on php site. I'm getting mad try to figure out how to get something like $_GET and $_POST.
To learn the basics of mod_python and PSP pages I created two files:

---------------index.html---------------
<html>
	<head>
		<title>X</title>
	</head>
	<body>
		<form id='x' name='x' method='get' action='prova.psp'>
			<input type='text' name='t' id='t'/><br/>
			<input type='text' name='u' id='u'/><br/>
			<input type='submit' value='ok'/><br/>
		</form>
	</body>
</html>

---------------prova.psp---------------
<html>
<%= dir(form) %>
<%= form.list %>
</html>

whose output is:
['__contains__', '__doc__', '__getitem__', '__init__', '__len__', '__module__', 'get', 'getfirst', 'getlist', 'has_key', 'keys', 'list', 'make_field', 'make_file', 'read_to_boundary']
[Field('t', 'xyz'), Field('u', '123')]

Shouldn't form have 'values' and 'items' properties? [http://www.modpython.org/live/mod_python-3.3.1/doc-html/pyapi-util-fstor.html](http://www.modpython.org/live/mod_python-3.3.1/doc-html/pyapi-util-fstor.html)

maybe I missed a step during installation?

---

### Post by MadeR on 2007-04-02
another problem: same .html file but different .psp file:

<html>

<%= [ dir(x) for x in form.list ] %>
<%= [ x.value for x in form.list ] %>
<%

def f( x ):
	x.value

%>

<%= map( f, form.list ) %>

</html>

output:
[['__del__', '__doc__', '__getattr__', '__init__', '__module__', '__repr__', 'disposition', 'disposition_options', 'file', 'filename', 'headers', 'name', 'type', 'type_options'], ['__del__', '__doc__', '__getattr__', '__init__', '__module__', '__repr__', 'disposition', 'disposition_options', 'file', 'filename', 'headers', 'name', 'type', 'type_options']]
['xyz', '123']
[None, None]

This is strange:
 the first line tells us that a Field object has no value attibute (the very opposite of what is written in mod_python documentation), but the second python line show us that it exists.
So why the 3rd line returns [None,None] ? :confused:




Finally: is there a smarter way to get the same variable as PHP $_POST other the following code?
<html>

<% 
k=[ x.name  for x in form.list ]
v=[ x.value for x in form.list ] 
%>
<%= zip( k, v ) %>

</html>

---

### Post by pmasiar on 2007-04-03
> **MadeR said:**
> Desiring to learn python for my degree thesis (web based application), I installed mod_python.

mod_python is not the simplest choice for a beginner, and stay away from PSP. It looks like PHP, you have fuzzy feeling, but if you want to mix code and presentation, don't bother and do it in PHP.

Check [http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication) - simple CGI server in 7 lines of Python, and 2 simple CGI apps. For real big web application, you need to use model-view-controller pattern, check MVC web frameworks: TurboGears and Django are most popular. (all links at wiki)

---

### Post by Mirrorball on 2007-04-03
I recommend Django as well. Mixing logic and presentation is simple but you will regret it later. I do.

---

