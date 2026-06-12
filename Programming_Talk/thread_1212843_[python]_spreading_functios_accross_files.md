---
title: "[python] spreading functios accross files"
date: 2009-07-14
forum: Programming Talk
---

### Post by Pyro.699 on 2009-07-14
So, i have these 2 files

file1.py
[php]
import file2

def my_func():
    print "Hey"

global my_var
    my_var = "var"

my_sec_func()
[/php]file2.py
[php]
def my_sec_func():
 my_func()
 print my_var
[/php]Obviously, **my_func()** and **my_var** are not going to carry over to file2, but any way that i can call **my_sec_func()** while still using variables and functions (and classes in my real program) from the second file...

For more understanding i have a bunch of modules that are very lengthy and if they were to be put in the main program it would cause a lot of clutter for me. I need a way to organize functions by file name, and when i import the functions, they gain all the function useage from the main file.

Here is an excerpt from my script that im using.

main.py
[php]
import functions

class P:
    def __init__(self):    
        self.tab_index = 0
        self.backup = 0
    def up(self):
        self.tab_index += 1
    def down(self):
        self.tab_index -= 1
    def set(self, x):
        self.tab_index = x
    def get(self):
        return self.tab_index
    def save(self):
        self.backup = self.get()
    def rest(self):
        self.set(self.backup)
    def rint(self, string="", nl=True, tb=True, st=True):
        out = ""
        for i in range(0, self.tab_index):
            out += "\t"
        if(tb): sys.stdout.write(out)
        if(st): sys.stdout.write(string)
        if(nl):    print

global p        
p = P()

/* A bunch of code here */

functions._do()
[/php]functions.py
[php]
def _do():
    p.save()
    /*I need to be able to use p.save which was decalred in the first file*/
[/php]
Thanks again
~Cody Woolaver

---

