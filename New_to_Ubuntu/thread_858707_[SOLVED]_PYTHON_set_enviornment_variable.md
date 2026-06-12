---
title: "[SOLVED] PYTHON set enviornment variable"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-13
hi, I'm such a dork. so I want to learn a programming language.  I decided on python.  so not knowing what I'm doing AT ALL i type in "help" but it seems there is documentation mising.  so I apt-got the recommended documentation, but it still doesn't work leaving me to set the enviornment variable PYTHON DOCS to indicate their location:

"help> OBJECTS

Sorry, topic and keyword documentation is not available because the Python
HTML documentation files could not be found.  If you have installed them,
please set the environment variable PYTHONDOCS to indicate their location.

On Debian GNU/{Linux,Hurd} systems you have to install the corresponding
pythonX.Y-doc package, i.e. python2.5-doc."

I don't know what this means at all.

---

### Post by unutbu on 2008-07-13
Have you done
```

sudo apt-get install python2.5-doc
```
?

---

### Post by adamogardner on 2008-07-13
yes i have. successfully too I might add

---

### Post by unutbu on 2008-07-13
How are you generating the error message that you show  in post #1?

---

### Post by RomeReactor on 2008-07-13
Hi. Since you already have the documentation installed, you can open it with either w3m or Firefox:
```
w3m /usr/share/doc/python2.5-doc/html/index.html
```
or:
```
firefox /usr/share/doc/python2.5-doc/html/index.html
```

You can also install 'Dive Into Python' by Mark Pilgrim:
```
sudo aptitude install diveintopython
```
and to access it:
```
w3m /usr/share/doc/diveintopython/html/toc/index.html
```
or:
```
firefox /usr/share/doc/diveintopython/html/toc/index.html
```

---

### Post by adamogardner on 2008-07-13
HA  I'm sorry, but it works all of a sudden.  what do you mean though that I can open it with firefox?  I don't understand that.  And what is w3m?

---

### Post by RomeReactor on 2008-07-13
> **adamogardner said:**
> HA  I'm sorry, but it works all of a sudden.  what do you mean though that I can open it with firefox?  I don't understand that.  And what is w3m?

python2.5-doc comes in html, so you can use a browser to read it. w3m is a text based web browser that comes pre-installed in Ubuntu.

But it's working now, and that's what counts! :)

---

