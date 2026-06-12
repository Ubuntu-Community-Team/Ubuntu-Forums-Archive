---
title: "Python: Variables in Variables"
date: 2010-04-04
forum: Programming Talk
---

### Post by Psycho.mario on 2010-04-04
Hi,
   I am new to python, and have just started writing my first real program in it. It is going to be an NTLM password brute forcer (it's only a test of my programming skill). For the character set for brute forcing, the user is asked to give a list of wanted character sets, which are already variables in the program, for example
```
upper = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
```and the user would give the word "upper" for sys.argv[1] (the first argument). However, this makes the given variable the word "upper". How could i make python change the word "upper" to the contents of the "upper" variable. I don't think i've explained this very well. Here's the program so far:
```
# -*- coding: cp1252 -*-
import ntlm
import binascii
import sys
def hasher(password):
    LM = binascii.b2a_hex(ntlm.create_LM_hashed_password_v1(password))
    NT = binascii.b2a_hex(ntlm.create_NT_hashed_password_v1(password))
    return LM.upper()+":"+NT.upper()
upper = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
lower = "abcdefghijklmnopqrstuvwxyz"
numeric = "0123456789"
space = " "
symbols = """!$%^&*()_+-={}[]:@~;'#<>?,."""
if len(sys.argv) == 1:
    print "ERROR: Not Enough Arguments"
elif sys.argv[1] == "-h":
    print """NTLM Brute Forcer by PsychoMario
    NTLM_Forcer.py <charset> <hash>

    charset can be any of the following:
    upper
    lower
    numeric
    symbols
    space
    If you want more than one you MUST put a '+' between your choices

    hash must be in the LMNT format:
    e.g
    LM:NT
    e52cac67419a9a224a3b108f3fa6cb6d:8846f7eaee8fb117ad06bdd830b7586c
    These hashes can be aquired from running programs such as Cain & Abel, \n\x20\x20\x20\x20fgdump or ophcrack
    """

```PLEASE do not criticise my code, i have been learning python for about a week. Although contructive criticism with a fix is welcome.

Thanks in advance

---

### Post by km0r3 on 2010-04-04
> **Psycho.mario said:**
> Hi,
How could i make python change the word "upper" to the contents of the "upper" variable.

You could simply use a "temporary" variable referencing it to the `upper` variable.

```
var = upper
```In your case:
```

if sys.argv[1] == "upper":
    var = upper
```Now, that's ugly. There are several other ways to do that better.

Have I interpreted your question correctly?

---

### Post by Psycho.mario on 2010-04-04
That was is a way to do it, but then i would have to do a massive elif statement for every combination, say the user asked for upper AND lower, they could just put upper+lower which i want to be interpreted as ABC.....XYZabc...xyz

Thanks

EDIT: 
after re-reading your post, would it be possible to say, if "upper" is in sys.argv[1], then make var = upper, then if "lower" is in sys.argv[1] as well, make var = var+lower?

EDIT2:
it is possible to say var = upper and then var = var+lower which makes it work correctly. How can i search in sys.argv[1] for upper, if (e.g) sys.argv[1] = upper+lower+space

EDIT3:
i can search inside a string with var.index("upper"), but if the search criteria is not there it returns a dirty great error, is there any way to search without a big error? so it just gives True or False if found or not found respectively

---

### Post by Bachstelze on 2010-04-04
Things like this are generally done by using a [font=monospace]dict[/font]:

```

character_sets = {'upper': 'ABCDEFGHIJKLMNOPQRSTUVWXYZ',
                  'lower': 'abcdefghijklmnopqrstuvwxyz',
                  'numeric': '0123456789',
                  'space': ' ',
                  'symbols': '!$%^&*()_+-={}[]:@~;\'#<>?,.'}

character_sets_on_input = sys.argv[1].split('+')
characters = []
for i in character_sets_on_input:
    characters += character_sets[i]
```

And the [font=monospace]characters[/font] variable contains all your characters. A one-liner to do the same thing would be:

```
characters = ''.join([character_sets[i] for i in sys.argv[1].split('+')])
```

---

### Post by km0r3 on 2010-04-04
> EDIT: 
after re-reading your post, would it be possible to say, if "upper" is in sys.argv[1], then make var = upper, then if "lower" is in sys.argv[1] as well, make var = var+lower?Yes, that's very possible. You get the idea :) .

**Beware. **If you pass "upper" and "lower" then you have sys.argv[1] and sys.argv[2].

> 
EDIT3:
i can search inside a string with var.index("upper"), but if the search criteria is not there it returns a dirty great error, is there any way to search without a big error? so it just gives True or False if found or not found respectively

```
var.find("upper")
```I think there's no way around elif blocks if you're doing it that way, which is not necessarily bad!

EDIT:
@Bachstelze: I like your workaround!

---

### Post by Psycho.mario on 2010-04-04
Thank you all, i got it working with this:
```

charsets = {'upper' : "ABCDEFGHIJKLMNOPQRSTUVWXYZ",
            'lower' : "abcdefghijklmnopqrstuvwxyz",
            'numeric' : "0123456789",
            'space' : " ",
            'symbols' : """!\"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~";"""}
charset = ''.join([charsets[i] for i in sys.argv[1].split('+')])
```

Thanks for all your help

---

### Post by wmcbrine on 2010-04-04
I agree that a dict is the best way to go here. But your original idea can be made to work, too, by using globals() or locals(), which will return a dict of the appropriate variables.

```
>>> a = 'foo'
>>> globals()['a']
'foo'
```

---

