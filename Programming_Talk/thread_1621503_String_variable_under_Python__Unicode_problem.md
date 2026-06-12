---
title: "String variable under Python : Unicode problem"
date: 2010-11-14
forum: Programming Talk
---

### Post by yanes on 2010-11-14
Hi all ,
I have coded an application that manipulate some file paths ,  it works perfectly with some paths ,
But it fails with some files or dirs with french accented chars or arabic file names , 
please how to make python accept and opens files with unicode encoded paths ?

Thanks in advance :)

---

### Post by Arndt on 2010-11-14
> **yanes said:**
> Hi all ,
I have coded an application that manipulate some file paths ,  it works perfectly with some paths ,
But it fails with some files or dirs with french accented chars or arabic file names , 
please how to make python accept and opens files with unicode encoded paths ?

Thanks in advance :)

I don't know what exactly is needed for this to work, but I tried this experiment, which worked nicely:

```
$ python
Python 2.6.4 (r264:75706, Dec  7 2009, 18:45:15) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> open("pélé à gagné","w")
<open file 'pélé à gagné', mode 'w' at 0xb77774d0>
>>> 
$ ls 'pélé à gagné'
pélé à gagné
$ echo LANG
en_US.UTF-8
```

Does the same thing work for you? Does your LANG environment variable perhaps not contain a reference to UTF-8?

---

### Post by mo.reina on 2010-11-14
```
>>> s = 'hello byte string'
>>> u = unicode(s)
>>> u
u'hello byte string'
>>> u.encode()
'hello byte string'
>>> 

```

---

### Post by worksofcraft on 2010-11-14
Python source code defaults to ASCII.
To define a different source code encoding, you need a "magic comment" placed into the source files either as first or second line in the file:
```

          #!/usr/bin/python
          # -*- coding: utf-8 -*-

```

I think you also have to make sure that your locale is using utf-8 and not one of the other iso codes.

---

### Post by nvteighen on 2010-11-14
> **yanes said:**
> Hi all ,
I have coded an application that manipulate some file paths ,  it works perfectly with some paths ,
But it fails with some files or dirs with french accented chars or arabic file names , 
please how to make python accept and opens files with unicode encoded paths ?

Thanks in advance :)

Please show us code that reflects this behaivor.

---

### Post by cgroza on 2010-11-14
> **worksofcraft said:**
> Python source code defaults to ASCII.
To define a different source code encoding, you need a "magic comment" placed into the source files either as first or second line in the file:
```

          #!/usr/bin/python
          # -*- coding: utf-8 -*-

```I think you also have to make sure that your locale is using utf-8 and not one of the other iso codes.
^^This is the solution.

---

### Post by wmcbrine on 2010-11-14
> **nvteighen said:**
> please show us code that reflects this behaivor.+1

---

### Post by nvteighen on 2010-11-15
Yup it works:

```

#!/usr/bin/python
#-*- coding: utf-8 -*-

def main():
    filename = "&#917;&#8016;&#961;&#953;&#960;&#943;&#948;&#959;&#965; &#914;&#940;&#954;&#967;&#945;&#953;"
    message = " &#7981;&#954;&#969; &#916;&#953;&#8056;&#962; &#960;&#945;&#8150;&#962; &#964;&#942;&#957;&#948;&#949; &#920;&#951;&#946;&#945;&#943;&#969;&#957; &#967;&#952;&#972;&#957;&#945;..."
    myfile = open(filename, "w")
    myfile.write(message)
    myfile.close()

if __name__ == "__main__":
    main()

```

Call me stupid, but I though **-*- coding: utf-8 -*-** was an Emacs or vim thing, not a Python issue... :P

---

### Post by worksofcraft on 2010-11-15
> **nvteighen said:**
> 
Call me stupid, but I though **-*- coding: utf-8 -*-** was an Emacs or vim thing, not a Python issue... :P

No, you are correct :) The designers of Python decided to make it compatible with a number of existing practices instead of making a new one of their own. I think all that it actually needs is the word "coding" and a legitimate code in a comment on the 1st or second line

---

### Post by yanes on 2010-11-17
> **nvteighen said:**
> Please show us code that reflects this behaivor.

This is the code (the exact function that raises the err :
[PHP]
--My Plain code :
def askUserForFilename(self, **dialogOptions):
        dialog = wx.FileDialog(self, **dialogOptions)
        if dialog.ShowModal() == wx.ID_OK:
            userProvidedFilename = True
            self.filename = dialog.GetFilename()
            self.dirname = dialog.GetDirectory()
            print type(self.dirname)
            print "fileName : " ,self.filename
            print "DirName : " , self.dirname
        else:
            userProvidedFilename = False
        dialog.Destroy()
        return userProvidedFilename

--Python Output : 
Event handler `On_Open' invoked!
<type 'unicode'>
fileName :  dsc_1576.jpg
DirName :  /home/yanes/Téléchargements
/home/yanes/Téléchargements/dsc_1576.jpg
Traceback (most recent call last):
  File "img_r_2.py", line 207, in On_Open
    print str(self.dirname+"/"+ self.filename)
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe9' in position 13: ordinal not in range(128)
[/PHP]

As you look , the problem is in the variable "self.dirname" it's the result of a wx.FileDialog .
The second line of the Output is the type() of this variable , python knows that it's a unicode string    ?? That's Strange ?? 
If it recognize it as unicode , why it raises this error ? 

another thing that I think it's important : 
From the module os.path I tried this :
[PHP]
Python 2.6.6 (r266:84292, Sep 15 2010, 15:52:39) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os.path
>>> os.path.supports_unicode_filenames
False
>>> 

[/PHP]:confused::confused:

So what do you think ?

---

### Post by Arndt on 2010-11-18
> **yanes said:**
> This is the code (the exact function that raises the err :
[PHP]
--My Plain code :
def askUserForFilename(self, **dialogOptions):
        dialog = wx.FileDialog(self, **dialogOptions)
        if dialog.ShowModal() == wx.ID_OK:
            userProvidedFilename = True
            self.filename = dialog.GetFilename()
            self.dirname = dialog.GetDirectory()
            print type(self.dirname)
            print "fileName : " ,self.filename
            print "DirName : " , self.dirname
        else:
            userProvidedFilename = False
        dialog.Destroy()
        return userProvidedFilename

--Python Output : 
Event handler `On_Open' invoked!
<type 'unicode'>
fileName :  dsc_1576.jpg
DirName :  /home/yanes/Téléchargements
/home/yanes/Téléchargements/dsc_1576.jpg
Traceback (most recent call last):
  File "img_r_2.py", line 207, in On_Open
    print str(self.dirname+"/"+ self.filename)
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe9' in position 13: ordinal not in range(128)
[/PHP]

As you look , the problem is in the variable "self.dirname" it's the result of a wx.FileDialog .
The second line of the Output is the type() of this variable , python knows that it's a unicode string    ?? That's Strange ?? 
If it recognize it as unicode , why it raises this error ? 

another thing that I think it's important : 
From the module os.path I tried this :
[PHP]
Python 2.6.6 (r266:84292, Sep 15 2010, 15:52:39) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os.path
>>> os.path.supports_unicode_filenames
False
>>> 

[/PHP]:confused::confused:

So what do you think ?

I can duplicate the problem, without any actual file handling. The simplest way is to do

```
$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os.path
>>> os.path.supports_unicode_filenames
False
>>> s = u"/home/yanes/Téléchargements"
>>> s
u'/home/yanes/T\xe9l\xe9chargements'
>>> print s
/home/yanes/Téléchargements
>>> type(s)
<type 'unicode'>
>>> str(s)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe9' in position 13: ordinal not in range(128)
>>> 

```

In the documentation, however, I see this: "...the slightly different str() function). The latter function is implicitly used when an object is written by the print() function." which is obviously not the case (documentation for 2.6 and 2.7 is the same here, and I'm using 2.6).

Can you just lose the 'str' call? Or is it inside some library code?

You can apparently transform the string so it becomes palatable to 'str':

```
>>> s = u"/home/yanes/Téléchargements"
>>> s2 = s.encode('utf-8')
>>> s2
'/home/yanes/T\xc3\xa9l\xc3\xa9chargements'
>>> type(s2)
<type 'str'>
>>> str(s2)
'/home/yanes/T\xc3\xa9l\xc3\xa9chargements'
>>> print(s2)
/home/yanes/Téléchargements
>>> print str(s2)
/home/yanes/Téléchargements
>>> 
```

---

### Post by yanes on 2010-11-18
Ok , I'll try the unicode() function 
To be exact the problem was caused by the str() function , by removing it , the scipts executed sucseefully under the console 
> 
Python myscript.py

but raises an error under SPE python IDE 
I don't understand the cause ;)

I'll try it now in the hope it will not raises the error :'No such file or directory'  :) ;)
thanks for all of you

---

### Post by yanes on 2010-11-20
Very well, your hint works fine Mr [Arndt]("http://ubuntuforums.org/member.php?u=106064"),

thank you my program can now opens french, arabic , and some other arbitrary chars that i tested

---

