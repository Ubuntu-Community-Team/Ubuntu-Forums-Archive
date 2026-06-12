---
title: "adding link in jsp file"
date: 2008-05-22
forum: Programming Talk
---

### Post by hechizera on 2008-05-22
hi there!!

could anyone please tell me how to add link to some other .htm file in jsp? for example, when I write 

```
<a href="logged.htm">Login here</a>
```
 in the middle of if statement, like if this then go to this page,  else go to some other page, I get errors, which don't say much about how to improve this part of code :(

please help me with the correct way of adding links :(

---

### Post by NormR2 on 2008-05-22
> I get errors
Please copy and paste the error message you get and the related lines of code. 

The jsp code generates text that is valid HTML. Perhaps you need to escape some of the HTML special characters so jsp doesn't get confused.  It needs to process the HTML as strings and not try to execute them.

---

### Post by xlinuks on 2008-05-22
There are several ways, here's one of them:
```


<% if( true ) {%>
	<a href="page1.htm">page 1</a>
<%} else if( false ) {%>
	<a href="page2.htm">page 2</a>
<%}%>

```

---

