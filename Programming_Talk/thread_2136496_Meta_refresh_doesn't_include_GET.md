---
title: "Meta refresh doesn't include GET"
date: 2013-04-17
forum: Programming Talk
---

### Post by ki4jgt on 2013-04-17
I have a CGI server running with python as my language of choice. In it I have the following code:

```

if cgi.FieldStorage().getvalue("p") == "None":
	print """<meta http-equiv="refresh" content="0; url=index.py?p=1">"""

```

However, I do not get redirected to index.py?p=1

---

### Post by ofnuts on 2013-04-18
I don't know this API, but  ***=="None***" shouldn't be ***==None ***?

---

### Post by epicoder on 2013-04-19
ofnuts is right. cgi.FieldStorage.getvalue returns the object None, not the string "None", if the value isn't found. You are effectively checking for index.py?p=None
Technically it should be ***== None*** (note the space) if you want to follow Python conventions. :P

---

