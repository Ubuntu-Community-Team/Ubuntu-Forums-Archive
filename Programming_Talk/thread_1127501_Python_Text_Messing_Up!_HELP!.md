---
title: "Python Text Messing Up! HELP!"
date: 2009-04-16
forum: Programming Talk
---

### Post by Swenghk on 2009-04-16
Okay, so I made a menu for this text-based game, but when I run it in the terminal or in IDLE, it gets skewed. Here's the code:

```
def mainmenu():
    print \
          """
       +===============================+
       |ADVENTURE I: THE JOURNEY BEGINS|
       +===============================+

    1 - New Game

    2 - Load Game   
                                  
    3 - Credits                   
                                    
    4 - About                    
                                
    5 - Quit Game

                   
              (@|
 ,,           ,)|_____________________________________
//\\8@8@8@8@8@8 / _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ \
\\//8@8@8@8@8@8 \_____________________________________/
 ``           `)|
              (@|
              
Version: 1.0

"""
```

But when it runs in the terminal, this happens

```
Adventure I: The Journey Begins
Version: 1.0

       +===============================+
       |ADVENTURE I: THE JOURNEY BEGINS|
       +===============================+

    1 - New Game

    2 - Load Game (not available)   
                                  
    3 - Credits                   
                                    
    4 - About                    
                                
    5 - Quit Game

                   
              (@|
 ,,           ,)|_____________________________________
//\8@8@8@8@8@8 / _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ \//8@8@8@8@8@8 \_____________________________________/
 ``           `)|
              (@|
              
Version: 1.0


```

Can you tell me whats going on?!

---

### Post by imdano on 2009-04-16
You have to make it a raw string, otherwise python will try to escape the '\' characters.  Just do
```
print r"""this is a raw string \n"""
```

---

### Post by Swenghk on 2009-04-16
What's a raw string? (I'm still new to python)

Yes! That worked! Thanks so much!!!!!!

---

### Post by imdano on 2009-04-16
From the Python documentation > When an 'r' or 'R' prefix is present, a character following a backslash is included in the string without change, and all backslashes are left in the string. For example, the string literal r"\n" consists of two characters: a backslash and a lowercase 'n'. String quotes can be escaped with a backslash, but the backslash remains in the string; for example, r"\"" is a valid string literal consisting of two characters: a backslash and a double quote; r"\" is not a valid string literal (even a raw string cannot end in an odd number of backslashes). Specifically, a raw string cannot end in a single backslash (since the backslash would escape the following quote character). Note also that a single backslash followed by a newline is interpreted as those two characters as part of the string, not as a line continuation.

See here for more info: [http://docs.python.org/reference/lexical_analysis.html#string-literals](http://docs.python.org/reference/lexical_analysis.html#string-literals)

---

### Post by nvteighen on 2009-04-16
> **Swenghk said:**
> What's a raw string? (I'm still new to python)

Yes! That worked! Thanks so much!!!!!!
A "raw string" is a string that is taken literally, without taking the escape sequences in account. So, '\n' is treated as '\' + 'n' instead of a newline, e.g.

Actually, the difference between cooked strings and raw strings is not that critical in Python... except for your case :)

---

