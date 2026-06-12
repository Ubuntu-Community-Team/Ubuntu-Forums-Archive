---
title: "Using AJAX with Flask"
date: 2012-06-30
forum: Programming Talk
---

### Post by Datweakfreak on 2012-06-30
I'm trying to use AJAX with Python Flask. I have a HTML page with an input form, and a div. When I type into the form and press enter, I want a POST request to be sent to the flask server, and when the server responds with some text, I want the response text to fill the div's contents.

[Here's the code.]("https://pastee.org/f4yc6") 

Sorry about the unclean code, and also, the paste contains two files templates/index.html and flask.py.

It works fine, except that when I type into the form and press enter, it shows a new HTML page with the response text. It doesn't put the response text into the div. Any help would be much appreciated.

Thanks!

---

### Post by Dimarchi on 2012-07-03
At the very least, I would add
```

onsubmit="return false;"
```to the form tag.

---

