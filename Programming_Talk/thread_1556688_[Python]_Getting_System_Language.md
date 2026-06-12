---
title: "[Python] Getting System Language"
date: 2010-08-19
forum: Programming Talk
---

### Post by dodle on 2010-08-19
I have used the following script to get the system language and encoding, but it depends on the system command "locale":

[php]import commands

# Set dummy language and encoding to make sure locale is found
language = "English"
encoding = "enc"

data = commands.getoutput("locale")
data = data.split("\n")
for locale in data:
    # Find the language locale
    if locale.split("=")[0] == "LANG":
        language = locale.split("=")[1].split(".")[0]
        encoding = locale.split("=")[1].split(".")[1]

print "Language = %s" % language
print "Encoding = %s" % encoding[/php]

On my system this ouputs:
```
Language = en_US
Encoding = utf8
```

But, is there a better way to get this information, or is what I have done fine?  I have tried using python's built-in module "locale" but always receive a tuple of (None, None):

```
:~$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import locale
>>> locale.getlocale()
(None, None)
>>> locale.getdefaultlocale("LANG")
(None, None)
>>> 
```

Am I doing something wrong?

---

### Post by StephenF on 2010-08-19
```

>>> locale.getdefaultlocale()
('en_GB', 'UTF8')

```

---

### Post by dodle on 2010-08-19
Thanks, I guess I thought an argument was required.

---

### Post by worksofcraft on 2010-08-19
Just out of curiosity... well no, more out of concern for the implications of writing programs that hard code locale dependencies...

Why would you want to get the locale information?

Is not the whole purpose of *internationalization* to make *localization* transparent to the application?

---

### Post by Some Penguin on 2010-08-19
> **worksofcraft said:**
> Just out of curiosity... well no, more out of concern for the implications of writing programs that hard code locale dependencies...

Why would you want to get the locale information?

Is not the whole purpose of *internationalization* to make *localization* transparent to the application?

Python must be totally awesome if it can automatically translate everything in UI components to Urdu without also mangling data.

---

### Post by worksofcraft on 2010-08-19
lol, no....

gettext() package does that. The programmer doesn't have to know anything about Urdu and the Urdu-ians (or whatever they are called) don't have to know anything about programming... as long as one of them somewhere did a .mo file to include in the distribution.

---

### Post by dodle on 2010-08-20
I don't know anything about *localization* or *Urdu*.  Here is what I am doing, I don't really know if it is the best way, but it is the only way I know how:

My program first checks which language the system is using and compares it to a directory of xml files.  The xml files contain the text for the program.  Here is an example of one of the files:

[html]<langversion=1.0/>
<language=en_US/>
<encoding=utf8/>

<main>
  <title>Debreate - Debian Package Builder</title>
  <menubar>
    <file=File>
      <0>New</0>
      <1>Open...</1>
      <2>Save</2>
      <3>Save as...</3>
    </file>
  </menubar>
  <quit>
    <title>Confirm Quit</title>
    <message>There is unsaved information.
Really quit?</message>
  </quit>
</main>[/html]

So if the system locale is set to United States English encoded in utf8 the program will get all its text from this xml file.

---

### Post by worksofcraft on 2010-08-20
> **dodle said:**
> 
My program first checks which language the system is using and compares it to a directory of xml files.  The xml files contain the text for the program.  Here is an example of one of the files:


I like your use of XML, but I think you might save yourself a lot of work as well as benefit from more advanced techniques if you adopt the GNU gettext package [http://www.gnu.org/software/gettext/](http://www.gnu.org/software/gettext/). It works with many programming languages, including C++ and Python.

A link for simple hands on tutorial I found useful:
[http://oriya.sarovar.org/docs/gettext_single.html](http://oriya.sarovar.org/docs/gettext_single.html)

---

### Post by dodle on 2010-08-20
Thanks, I will look into that.

---

### Post by dodle on 2010-08-30
> **worksofcraft said:**
> I like your use of XML, but I think you might save yourself a lot of work as well as benefit from more advanced techniques if you adopt the GNU gettext package [http://www.gnu.org/software/gettext/](http://www.gnu.org/software/gettext/). It works with many programming languages, including C++ and Python.

Thanks again, using gettext is much easier.

---

### Post by worksofcraft on 2010-08-30
> **dodle said:**
> Thanks again, using gettext is much easier.

The web really has brought the whole world together in cyberspace and writing globalization aware software is the future.

When I first learnt of gettext I thought it was a bit of strange way to go about it, but after I had experimented I was convinced it is a very good design. The separating of programming implementation from translation issues is the key :)

---

