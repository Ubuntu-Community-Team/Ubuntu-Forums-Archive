---
title: "Newb python help."
date: 2008-03-30
forum: Programming Talk
---

### Post by rob1101 on 2008-03-30
ok well im doing a python project that is supposed to help you edit files this is my first python project and my first "real" programming project in general. The problem i am having now is a function retuning 2 variables. How do i assign each of those variables in the main program. 

here is the source to the program it is in the get_option() function. 

PS. I know im a noob and this is probably the most inefficient/dumbest way to do this but like i said im a noob. Any help will be appreciated. 

```

from safe_edit_functions import *
import os

list_options()

get_option()


backup(filepath)

os.system("sudo gedit " + str(filepath)) 

``````

import os

# List options
def list_options():
    options = ['grub.lst', 'Other']
    
    for while_counter in range(0,2):
        print str(while_counter) + " " + options[while_counter]


# Get option
def get_option():
    option = input("Enter an option: ")
    
    if option == 0:
        filepath = "/boot/grub/menu.lst"
        filevar = "menu.lst"
        return(filepath, filevar)    
        
    elif option == 1:
        get_filepath()

            
# Get filepath
def get_filepath():
    filepath = raw_input("Enter file path: ")
    return(filepath)
    

# Backup file
def backup(filepath):
    os.system("cat " + str(filepath) + " > ~/.backup/" + filevar)
    return 0
    
# Pikcle index
def picle_index():
    file = open('~/.backup/index', 'w')

```

---

### Post by WW on 2008-03-30
> **rob1101 said:**
> The problem i am having now is a function retuning 2 variables. How do i assign each of those variables in the main program. 

A function can return more than one value.  For example:
```

>>> def myfunc():
...     return 10, "Something very important."
... 
>>> n, str = myfunc()
>>> n
10
>>> str
'Something very important.'
>>> 

```
Is **get_option** the function that you want to return more than one value?  It looks like that's what you are doing if option == 0, but if option == 1, you don't return anything.

---

### Post by rob1101 on 2008-03-30
thx for the reply. yes if it is 1 its not supposed to return anything. You fixed my problem thank you

---

### Post by nvteighen on 2008-03-30
Not a Python programmer, but... are you sure that os.system("sudo gedit " + str(filepath)) is useful?

I'd really wouldn't do any distinction whether the file is or not grub.lst and let the system decide if sudo is needed or not. Then, I'd run "sudo python <whatever>" for that exact file owned by root or another user.

Or are you trying to do something special with grub.lst?

---

### Post by Majorix on 2008-03-30
Just something I noticed... I wouldn't use the "from x import *" syntax. Import things one by one, so that your code is readable. Imagine how messed up the code would look if there were imports from multiple files and lots of functions around.

I should actually suggest the removal of that usage by the Python devs :)

---

