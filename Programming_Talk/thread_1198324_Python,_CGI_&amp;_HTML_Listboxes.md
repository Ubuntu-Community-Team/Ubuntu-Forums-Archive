---
title: "Python, CGI &amp; HTML Listboxes"
date: 2009-06-27
forum: Programming Talk
---

### Post by matmatmat on 2009-06-27
I want to access a listbox:
```

<form action='delete.py' name='bookmark'>
<select name='bookmark'>
<option value='stuff'>stuff</option>
</select>
<input type=submit value='Delete'></form>

```
& i have this python code:
```

        reshtml = '''Content-Type: text/html\n
        <html><body>
        %s
        </body>
        </html>
        '''
        form = cgi.FieldStorage()
	name = form.getlist("bookmark")
	strin = ""
	for nam in name:
		strin += nam
        print reshtml % (strin)

```
this doesn't print anything, there is no error & I can't find anything on the web

---

### Post by timvoet on 2009-06-29
you'll need to add the <select> and the <option> tags for it to show on the page.  otherwise it will just print the contents in the body of your results page.

---

