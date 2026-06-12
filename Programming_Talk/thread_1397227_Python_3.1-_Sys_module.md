---
title: "Python 3.1- Sys module"
date: 2010-02-03
forum: Programming Talk
---

### Post by eranga1988 on 2010-02-03
I started to self study Python3. I came with a problem, that I cant understand what is the sys module. can u explain me what can we do with sys module. basically I want to know what is argv and what can we do with argv[]???
If u can pls post a very simple code to understand me. Again, I am new to python.
:):):)

---

### Post by nvteighen on 2010-02-03
The sys module is intended to give you access to some of the system's behaivor (system = Python; the os module is which gives you access to the OS). Look at [http://docs.python.org/library/sys.html](http://docs.python.org/library/sys.html) (ok, it's for Python 2.6.4, but the idea is just the same for all versions)

sys.argv is the list of command line arguments passed to the **script**, such that if you call "python myscript.py myfile1 -i 5" or "./myscript.py myfile1 -i 5", sys.argv = ["myscript.py", "myfile1", "-i", "5"]. By convention, sys.argv[0] is the program's name.

FYI, the origin of sys.argv comes from C and thus it has been adopted in almost all mainstream languages.

---

### Post by eranga1988 on 2010-02-03
import sys 
 
 
Zero = ["  ***  ", [INDENT]" *   * ", 
[/INDENT][INDENT]         "*     *", 
[/INDENT][INDENT]         "*     *", 
[/INDENT][INDENT]         "*     *", 
[/INDENT][INDENT]         " *   * ", 
[/INDENT][INDENT]         "  ***  "] 
[/INDENT] One = [" * ", "** ", " * ", " * ", " * ", " * ", "***"] 
Two = [" *** ", "*   *", "*  * ", "  *  ", " *   ", "*    ", "*****"] 
Three = [" *** ", "*   *", "    *", "  ** ", "    *", "*   *", " *** "] 
Four = ["   *  ", "  **  ", " * *  ", "*  *  ", "******", "   *  ", 
[INDENT]         "   *  "] 
[/INDENT] Five = ["*****", "*    ", "*    ", " *** ", "    *", "*   *", " *** "] 
Six = [" *** ", "*    ", "*    ", "**** ", "*   *", "*   *", " *** "] 
Seven = ["*****", "    *", "   * ", "  *  ", " *   ", "*    ", "*    "] 
Eight = [" *** ", "*   *", "*   *", " *** ", "*   *", "*   *", " *** "] 
Nine = [" ****", "*   *", "*   *", " ****", "    *", "    *", "    *"] 
 
Digits = [Zero, One, Two, Three, Four, Five, Six, Seven, Eight, Nine] 
 
try:[INDENT]               digits = sys.argv[1] 
[/INDENT][INDENT]               row = 0 
[/INDENT][INDENT]      while row < 7: 
[/INDENT][INDENT][INDENT]                         line = "" 
[/INDENT][/INDENT][INDENT][INDENT]                         column = 0 
[/INDENT][/INDENT][INDENT][INDENT]                         while column < len(digits): 
[/INDENT][/INDENT][INDENT][INDENT][INDENT]                                                       number = int(digits[column]) 
[/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT]                                                       digit = Digits[number] 
[/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT]                                                       line += digit[row] + "  " 
[/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT]                                            column += 1 
[/INDENT][/INDENT][/INDENT][INDENT][INDENT]                  print(line) 
[/INDENT][/INDENT][INDENT][INDENT]                  row += 1 
[/INDENT][/INDENT]except IndexError:[INDENT]              print("usage: bigdigits.py <number>") 
[/INDENT]except ValueError as err:[INDENT]              print(err, "in", digits)[/INDENT]

---

### Post by eranga1988 on 2010-02-03
sorry I couldnt use indents here

---

### Post by Flimm on 2010-02-03
> **eranga1988 said:**
> sorry I couldnt use indents here
[noparse]Wrap any code with ```
 
``` tags, or even better, [php] [/php] tags. The latter enables syntax colouring for your code, even if it isn't PHP.[/noparse]

Do you have a question about the code you posted?

---

