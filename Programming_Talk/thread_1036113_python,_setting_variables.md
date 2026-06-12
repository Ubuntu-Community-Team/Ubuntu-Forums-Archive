---
title: "python, setting variables"
date: 2009-01-10
forum: Programming Talk
---

### Post by nownto on 2009-01-10
I have a script that im running on my home server using apache and mod_python. What im attempting to do is call this script and pass it a post variable, but i cant seem to get the script to want to read this variable. wondering if someone could post some sample code on how to do this? thanks for any direction.

---

### Post by pmasiar on 2009-01-10
How do you run that script? mod_python - seems like web app? As a response to HTTP request?

---

### Post by nownto on 2009-01-10
Yeah mod_python might not mean much. But I do have a python script that I need to call via a http request and somehow setting the variable along the way, any suggestions or code refrences would be great.

---

### Post by pmasiar on 2009-01-10
mod_python might be overkill. Use plain cgi module, it can access variables from GET and POST requests. You don't have to generate HTML page as response (but you can, for debugging: look at cgitb module: CGI traceback).

---

### Post by nownto on 2009-01-10
thanks for the reply, but im still having problems getting python to read the post, something i think i need is  cgi.FieldStorage() , am i right in this assumption. if so how exactly is this used ( sample code :) if you have any ) , thanks.

---

