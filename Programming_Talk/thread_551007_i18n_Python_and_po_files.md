---
title: "i18n Python and po files"
date: 2007-09-14
forum: Programming Talk
---

### Post by StevenHarper on 2007-09-14
Hi, I am currently making a Python GTK program, currently I have all my Translations in a single XML file, however I would like to use po files so that I can use the Translation tools built into Launchpad.

I am aware that each language goes into a single po file, and that each string is linked to a single key.

I am also aware of a getText import that seems to use the local your OS is set to

what I want to know is

[LIST]
[*]Whats the standard and correct place to put my po files
[*]How do I initialize my getText
[*]How do I swap localization in my program at run-time
[*]How do I get a list of current languages that I have po files f
[/LIST]or

can anyone help me, code snippets would be ace

Steve

---

### Post by StevenHarper on 2007-09-15
OK , I'm going to answer my own post : this is so that if anyone else comes looking and finds this they can benefit from my learning.

**PO** files are single language translations for a given application
**POT** files are just a PO file with blank files (a template)
**MO** files are compiled PO files



An Example PO layout may be (**myapp.po**)

```

domain "myapp"

#: NAME
msgid "My App"
msgstr "My App"

#: VERSION
msgid "Version"
msgstr "Version"

```



PO files get compiled to MO files with the command

```
msgfmt myapp.po
```

this will make a file called **myapp.mo**



Next job is putting them in your code structure, MO files live in a structure like this

```

./locale/en/LC_MESSAGES/myapp.mo
./locale/fr/LC_MESSAGES/myapp.mo

```


Ok were close now, now to make a Python Application load them

```

import gettext

class MyApp:

        root="/usr/share/apps/easycrypt"
        transLoc = root +"/locale"
        t = gettext.translation("easycrypt", transLoc)
        _ = t.ugettext
        
        t.install()

```


Now if you wanted to force a given language you could use

```

        t = gettext.translation('easycrypt', transLoc, languages=['fr'])

```

However by default it picks up the language that Ubuntu is set to


Next we have to start using them

```

print _("My App")
print _("Version")

```

is all you need to do.
Whats happening here is that the _ has been linked to the t.ugettext() method
so you just use the _("STRING")  to get the string you want.

Its convention to use the native programmers string as the key.

There are programs to extract all static strings out of an app and make you a PO file, but I hand cranked mine.

on a final note you can put **/n** in po files, but you must also include them in the key, **/n** makes a line break in the string.

There are other more complex thing you can do but I didn't need them, so go off and read if you need more.

great places to start are:

[http://www.gnu.org/software/gettext/manual/gettext.html]("http://www.gnu.org/software/gettext/manual/gettext.html")
[http://docs.python.org/lib/node738.html]("http://docs.python.org/lib/node738.html")

Best wishes

Steve

---

### Post by nanotube on 2007-09-15
cool, thanks for the nice summary. :)
i may be i18n-ing an app in the medium-to-near future, and this will be very handy. :)

---

### Post by padawan555 on 2007-09-19
I can't wait til you are finished: when I run easycrypt I get 

```

Traceback (most recent call last):
  File "./EasyCrypt.py", line 50, in <module>
    class EasyCrypt:
  File "./EasyCrypt.py", line 64, in EasyCrypt
    t = gettext.translation("easycrypt", transLoc)
  File "/usr/lib/python2.5/gettext.py", line 484, in translation
    raise IOError(ENOENT, 'No translation file found for domain', domain)
IOError: [Errno 2] No translation file found for domain: 'easycrypt'

```

I guess it is because of the language settings.
Thanks for helping with a GUI for Truecrypt!

---

### Post by StevenHarper on 2007-09-26
> **padawan555 said:**
> I can't wait til you are finished: when I run easycrypt I get 

```

Traceback (most recent call last):
  File "./EasyCrypt.py", line 50, in <module>
    class EasyCrypt:
  File "./EasyCrypt.py", line 64, in EasyCrypt
    t = gettext.translation("easycrypt", transLoc)
  File "/usr/lib/python2.5/gettext.py", line 484, in translation
    raise IOError(ENOENT, 'No translation file found for domain', domain)
IOError: [Errno 2] No translation file found for domain: 'easycrypt'

```

I guess it is because of the language settings.
Thanks for helping with a GUI for Truecrypt!

What language is your system set to?

Steve

---

### Post by aurka on 2007-10-09
I got the same problem, my system is set to Czech.

---

### Post by maslokm on 2007-12-13
I have 7.10 and my system is set to Polish:

> Traceback (most recent call last):
  File "./EasyCrypt.py", line 50, in <module>
    class EasyCrypt:
  File "./EasyCrypt.py", line 64, in EasyCrypt
    t = gettext.translation("easycrypt", transLoc)
  File "/usr/lib/python2.5/gettext.py", line 484, in translation
    raise IOError(ENOENT, 'No translation file found for domain', domain)
IOError: [Errno 2] No translation file found for domain: 'easycryp

---

