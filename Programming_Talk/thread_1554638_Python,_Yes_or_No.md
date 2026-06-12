---
title: "Python, Yes or No?"
date: 2010-08-17
forum: Programming Talk
---

### Post by worksofcraft on 2010-08-17
The computer user has selected French locale and so our gettext translator has generated my output to ask for "Oui ou Non?".

Alas my Python script is still expecting some kind of Y or N response.

How do you cope with translating user input?

---

### Post by dodle on 2010-09-18
Here is an example translating English to Spanish.

loop.py:
[php]possible_answers = ( _("y"), _("yes"), _("n"), _("no") )

loop = True
while loop:
    answer = raw_input( _("Loop again? (Yes or No):  ") )
    answer = answer.lower()
    if answer in possible_answers[:2]:
        continue
    elif answer in possible_answers[2:]:
        loop = False[/php]

Spanish translation:
```
#: loop.py:3
msgid "y"
msgstr "s"

#: loop.py:3
msgid "yes"
msgstr "sí"

#: loop.py:3
msgid "n"
msgstr ""

#: loop.py:3
msgid "no"
msgstr ""

#: loop.py:7
msgid "Loop again? (Yes or No):  "
msgstr "¿Repitir? (Sí ó No): "
```

---

### Post by worksofcraft on 2010-09-18
> **dodle said:**
> Here is an example translating English to Spanish.


Yes thanks dodle :)

I realize I was doing it all wrong now... I was trying to translate the user's input and then compare that with English, but obviously translating the expected replies and doing the comparison in the foreign language makes a lot more sense! :guitar:

---

