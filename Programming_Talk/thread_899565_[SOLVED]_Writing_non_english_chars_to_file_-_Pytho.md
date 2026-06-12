---
title: "[SOLVED] Writing non english chars to file - Python"
date: 2008-08-24
forum: Programming Talk
---

### Post by aktiwers on 2008-08-24
I want to write non English chars to a text file. Letters like ÆØÅæøå

I tried using the info from this link
[http://evanjones.ca/python-utf8.html](http://evanjones.ca/python-utf8.html)

but nothing seams to work..   I keep getting
> TypeError: 'unicode' object is not callable
or
> 
TypeError: an integer is required


How do I use UTF-8 so that I can save non English chars with open.(file, "w") and write?:confused:

---

### Post by jinksys on 2008-08-24
Can't help you without seeing your code.

---

### Post by aktiwers on 2008-08-25
Actually this is the bid:

[php]
    def save_file():
        txt = textField.get(1.0,END)

        if txt:
            out = open("news.txt", "w")
            if out != None:
                out.write(txt)
                out.close()
                tkMessageBox.showinfo("text","Nyheden er nu opdateret!")
[/php]

---

### Post by Bachstelze on 2008-08-25
We also need the whole error message...

---

### Post by aktiwers on 2008-08-25
This is the one I get without using the UTF-8 :
> 
Exception in Tkinter callback
Traceback (most recent call last):
  File "/usr/lib/python2.5/lib-tk/Tkinter.py", line 1406, in __call__
    return self.func(*args)
  File "admin.py", line 35, in save_file
    out.write(txt)
UnicodeEncodeError: 'ascii' codec can't encode characters in position 68-70: ordinal not in range(128)



I removed the UTF-8 stuff from the code because it was not working..  how would I add it to the function correctly?

---

### Post by Bachstelze on 2008-08-25
[PHP]
    import codecs

    def save_file():
        txt = textField.get(1.0,END)

        if txt:
            out = codecs.open("news.txt", "w", "utf-8")
            if out != None:
                out.write(txt)
                out.close()
                tkMessageBox.showinfo("text","Nyheden er nu opdateret!")  [/PHP]

---

### Post by aktiwers on 2008-08-25
Wow I was sure I had already tried that! Thanks a lot it worked!! :)

---

