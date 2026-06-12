---
title: "mod_python just displays raw html"
date: 2008-06-13
forum: Programming Talk
---

### Post by molotov00 on 2008-06-13
Hey Guys,

I have a basic python script that just displays some html pulled from a database.

See the page here:
[http://jubuntu.dyndns.org/read.py](http://jubuntu.dyndns.org/read.py)

You see... I have html tags but the browser displays it instead of parsing it. I see:```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
``` in my browser.

I don't think it's Apache because regular html and even php pages render correctly. I think it's mod_python.

My script:
```

from mod_python import apache

#def index(req):
def index(req):
	req.content_type = 'text/plain'
	import sqlite3
	conn = sqlite3.connect("/var/www/articles.db")
	c = conn.cursor()
	op = """<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta content="text/html; charset=utf-8" http-equiv="Content-Type" py:replace="''"/>
<title>iShares: Premium/Discount Chart</title>"""
	c.execute('select title,id from articles where site="wsj" order by time')
	op += "WSJ Articles<br />"
	for row in c:
		op += row[1] + " " + row[0] + "<br />"
	req.write(op)
	return apache.OK

```

If I use "return op" instead of req.write and ommit req.content_type the results are the same.

Any ideas?

---

### Post by Fibonacci on 2008-06-13
Your server is returning a Content-Type of "text/plain", but it should return "text/html" if you want it to display HTML instead of plain text.
Unfortunately I don't know how to fix that, since I've never used mod-python - or even Python, for that matter.

---

### Post by Wybiral on 2008-06-13
> **Fibonacci said:**
> Your server is returning a Content-Type of "text/plain", but it should return "text/html" if you want it to display HTML instead of plain text.
Unfortunately I don't know how to fix that, since I've never used mod-python - or even Python, for that matter.

Actually, for this one it's right there in the code:

```

	req.content_type = 'text/plain'

```

---

### Post by molotov00 on 2008-06-13
Well that was easy, but I still wonder:

On the official mod_python site doesn't even have any mention of req.content_type ([http://www.modpython.org/live/current/doc-html/tut-pub.html](http://www.modpython.org/live/current/doc-html/tut-pub.html)). The code on that example wouldn't work, would it?

This makes me think there's still something on my end as far as configuration. Or is it normal to have to specify the content_type in the script? If I comment out the "plain/text" line it defaults to text.

---

