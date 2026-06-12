---
title: "How to access python documentation from shell"
date: 2009-12-25
forum: Programming Talk
---

### Post by thebrotherofasis on 2009-12-25
Hello,

I recently installed python3.1 python3.1-minimal and **python3.1-doc**

The package python3.1-doc is supposed to contain python documentation, right?

Ok, but I don't know how I can access it??

Ok, I know that If I do 

```
man python
```

... it shows some stuff, but nothing compared to this (which is the description from synaptic of python3.1-doc).

>   * What's New in Python3.1
  * Tutorial
  * Python Library Reference
  * Macintosh Module Reference
  * Python Language Reference
  * Extending and Embedding Python
  * Python/C API Reference
  * Installing Python Modules
  * Documenting Python
  * Distributing Python Modules

So, how can I access this documentation from my local machine? (Yes, I know it is available online... but I want to be able to access it while being offline)

On the other hand, but related to this question, is, I am learning Emacs, including its *info* commands. However, If I go to the main info directory (by typing "d"), I can't see a python manual in the menu list (there are no manual nodes for python in the main *info* node)

Is there a way to access python documentation from the python3.1-doc package, from inside emacs, using its *info* console?

Thank you for your help.

---

### Post by Barriehie on 2009-12-25
Can't help with the emacs ? although I'm a fan myself :)  If you go back into synaptic and look at the installed files for the python3.1-doc package you MIGHT find where it's installed html versions.  That's what I do on my end and then point your browser at the local file.  I'm using python 2.5 so I point my browser:
```

file:///usr/share/doc/python2.5/html/index.html
``` here.

HTH
Barrie

Edit: I just remember seeing the other day where you can tell emacs to open your browser and view a url/file.  M-x browse-url-firefox and then you're prompted for the url.

---

### Post by Can+~ on 2009-12-25
Install gnomes' [devhelp]("apt:devhelp"), and you can read all the html documentation available.

---

### Post by tom66 on 2009-12-25
[font=monospace]pydoc <name of type or function or syntax element to look up>[/font]

for example, try these:
[font=monospace]
pydoc print -> to show information on the "print" statement.
pydoc TypeError -> to show information on built-in class "TypeError".
pydoc gtk -> to show information on module gtk.
pydoc gtk.Window -> to show information on class Window in module gtk.
pydoc gtk.Window.__init__ -> to show information on method __init__() in class Window in module gtk.
[/font]
You might need to have the pydoc package installed.

Alternatively, for types ONLY, you can use the help() function in the interpreter. However, help() works with instances also, because you can't create objects on the pydoc command-line.

```
Python 2.6.4 (r264:75706, Dec  7 2009, 18:43:55) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> x = 8.4
>>> help(x)
Help on float object:

class float(object)
 |  float(x) -> floating point number
 |  
 |  Convert a string or number to a floating point number, if possible.
 |  
 |  Methods defined here:
 |  
 |  __abs__(...)
 |      x.__abs__() <==> abs(x)
 |  
 |  __add__(...)
 |      x.__add__(y) <==> x+y
 |  
 |  __coerce__(...)
 |      x.__coerce__(y) <==> coerce(x, y)
 |  
 |  __div__(...)
 |      x.__div__(y) <==> x/y
 |  
 |  __divmod__(...)
 |      x.__divmod__(y) <==> divmod(x, y)
:
>>> help(print) # Note that you can't use statements, only types!
  File "<stdin>", line 1
    help(print)
             ^
SyntaxError: invalid syntax

```

Press 'Q' to exit from the listing on either the pydoc program or the help() builtin.

---

### Post by nvteighen on 2009-12-26
> **tom66 said:**
> 
Alternatively, for types ONLY, you can use the help() function in the interpreter. However, help() works with instances also, because you can't create objects on the pydoc command-line.


help() reads the docstrings in whatever it encounters. It can be a function, classes or even a module. It isn't just for types (I suppose you refer to classes).

---

### Post by dhillonv10 on 2009-12-26
Gnome's Devhelp would make things really easy for you, not only python but you would be able to do a lot more with that :KS

---

### Post by jpkotta on 2009-12-28
[http://stackoverflow.com/questions/1054903/how-do-you-get-python-documentation-in-texinfo-info-format](http://stackoverflow.com/questions/1054903/how-do-you-get-python-documentation-in-texinfo-info-format)

Seems like Python docs are no longer in texinfo format.  You can do pretty well in Emacs with this:

```

;; modified from http://www.emacswiki.org/emacs/PythonMode
(defun pydoc (w)
  "Launch PyDOC on the Word at Point"
  (interactive
   (list (let* ((word (thing-at-point 'word))
                (input (read-string 
                        (format "pydoc entry%s: " 
                                (if (not word) 
                                    "" 
                                  (format " (default %s)" word))))))
           (if (string= input "") 
               (if (not word) (error "No pydoc args given")
                 word) ;sinon word
             input)))) ;sinon input
  (save-window-excursion
    (shell-command (concat "pydoc " w) "*PYDOCS*"))
    ;;(view-buffer-other-window "*PYDOCS*" nil 'bury-buffer))
    (view-buffer "*PYDOCS*" 'bury-buffer))

```

---

### Post by thebrotherofasis on 2009-12-30
> **jpkotta said:**
> [http://stackoverflow.com/questions/1054903/how-do-you-get-python-documentation-in-texinfo-info-format](http://stackoverflow.com/questions/1054903/how-do-you-get-python-documentation-in-texinfo-info-format)

Seems like Python docs are no longer in texinfo format.  You can do pretty well in Emacs with this:

```

;; modified from http://www.emacswiki.org/emacs/PythonMode
(defun pydoc (w)
  "Launch PyDOC on the Word at Point"
  (interactive
   (list (let* ((word (thing-at-point 'word))
                (input (read-string 
                        (format "pydoc entry%s: " 
                                (if (not word) 
                                    "" 
                                  (format " (default %s)" word))))))
           (if (string= input "") 
               (if (not word) (error "No pydoc args given")
                 word) ;sinon word
             input)))) ;sinon input
  (save-window-excursion
    (shell-command (concat "pydoc " w) "*PYDOCS*"))
    ;;(view-buffer-other-window "*PYDOCS*" nil 'bury-buffer))
    (view-buffer "*PYDOCS*" 'bury-buffer))

```

Thank you all for lighting up my mind here.

If I were to include this text (above), where should I include it? Is there an emacs conf file where I can put this?

---

### Post by thebrotherofasis on 2009-12-30
I did all of the above, and everything seems just great.

After playing a little with devhelp, it seems that it's just what I was looking for.

By the way. the html docs are also accessible from here (didn't know that)!

file:///usr/share/doc/python3.1/html/index.html

Thank you all .:P

Now, since I am getting more and more comfortable with emacs, I'd really like to know (maybe just for the sake of curiousity) how to tweak emacs to see the python docs into the *info* mode. That is what jpkotta suggested, right?

---

### Post by jpkotta on 2009-12-30
> **thebrotherofasis said:**
> 
Now, since I am getting more and more comfortable with emacs, I'd really like to know (maybe just for the sake of curiousity) how to tweak emacs to see the python docs into the *info* mode. That is what jpkotta suggested, right?

No, what I posted was a function that takes the word the cursor is on, looks it up with pydoc, and puts the pydoc output in a buffer.  The pydoc buffer is in view mode, and is not part of the info system in any way.  I completely agree that it would be great if the python docs were in info format, but it seems like they're not and I couldn't find a way to convert them.  

You can put the code in ~/.emacs, or if you prefer (and I do) ~/.emacs.d/init.el which is used if ~/.emacs doesn't exist.

---

### Post by thebrotherofasis on 2009-12-30
> **jpkotta said:**
> No, what I posted was a function that takes the word the cursor is on, looks it up with pydoc, and puts the pydoc output in a buffer.  The pydoc buffer is in view mode, and is not part of the info system in any way.  I completely agree that it would be great if the python docs were in info format, but it seems like they're not and I couldn't find a way to convert them.  

You can put the code in ~/.emacs, or if you prefer (and I do) ~/.emacs.d/init.el which is used if ~/.emacs doesn't exist.

Great, it worked on my end! Now when the cursor is standing on a word and I type "Alt+X pydoc", it takes me to the documentation of that word I am standing on.

It is a really handy function. Emacs is so customizable!

On the other hand, the help() command inside the python the interpreter seems really powerful too.

---

