---
title: "[Python] what am I doing wrong?"
date: 2011-03-05
forum: Programming Talk
---

### Post by Red Kelly on 2011-03-05
hi I'm trying to learn python and after typing this up the same as what is in the book I still get an error could you tell me what is wrong with it?
```

"""
chargen.py
Problem: Generate a description for a fantasy role-playing character.
Target Users: Me and my friends
Target System: GNU/Linux
Interface: Command-line
Functional Requirements: Print out the character sheet
User must be able to input the character's
name, description, gender and race
Testing: Simple run test
Maintainer: maintainer@website.com
"""
__version__ = 0.1


Name = ""
Desc = ""
Gender = ""
Race = ""

# Prompt user for user-defined information
Name = input("What is your Name? ")
Desc = input('Describe yourself: ')
Gender = input('What Gender are you? (male / female): ')
Race = input('What fantasy Race are you? - (pixie / Vulcan / Gelfling / Troll): ')

# Output the character sheet
fancy = "-----------------------------------"
print("\n", fancy)
print("\t", Name)
print("\t", Race, Gender)
print("\t", Desc)
Print(fancy, "\n")

```
and this is the error I get after entering my name
```

What is your Name? Red
Traceback (most recent call last):
  File "fantacy_game.py", line 22, in <module>
    Name = input("What is your Name? ")
  File "<string>", line 1, in <module>
NameError: name 'Red' is not defined

```

---

### Post by talonmies on 2011-03-06
Read [this]("http://docs.python.org/library/functions.html#input"). input() is not the correct function to be using for this - try raw_input() instead.

---

### Post by Red Kelly on 2011-03-06
Thanks that helped. I realised I was writing a python 3 and running it in python 2.x
changing to raw_input did fix to run in python 2.x, did print a bit funny tho.
Works as is when I use python 3.

---

