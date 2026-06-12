---
title: "[Python] Redirect output to browser"
date: 2011-07-19
forum: Programming Talk
---

### Post by ryuguns on 2011-07-19
How do you put the output from python into the browser instead of a terminal window?

I don't need anything graphical, text will do.

---

### Post by doas777 on 2011-07-19
well, it is my understanding that your execute your script via CGI within the context of the page, and use it to generate your return page.

look into this. shoudl give you the info you need.
[http://docs.python.org/howto/webservers.html](http://docs.python.org/howto/webservers.html)

---

### Post by juancarlospaco on 2011-07-19
In real time? VERY complicated.

if not, just save it into an HTML file, and then open the file.

---

### Post by cgroza on 2011-07-19
Do you want to create a web app? If so, you can use Bottle. It is fairly simple.

---

### Post by juancarlospaco on 2011-07-19
> **cgroza said:**
> Do you want to create a web app? If so, you can use Bottle. It is fairly simple.

**+1**

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
from bottle import route, run
@route('/')
def index():
    return 'Hola Mundo!'
run()
```

---

