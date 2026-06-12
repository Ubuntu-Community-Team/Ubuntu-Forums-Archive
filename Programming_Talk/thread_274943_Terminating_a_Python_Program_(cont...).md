---
title: "Terminating a Python Program (cont...)"
date: 2006-10-10
forum: Programming Talk
---

### Post by thomasaaron on 2006-10-10
Sorry I started a new thread. I can't figure out how to get this thing to show indentations once it is posted.

Essentially, the whole bloody thing is function cat_text_menu() EXCEPT for the last line, which starts the function.

My question is:
Why will option 4 not terminate the program?
And what is a good way to kill the entire program carte blanche when "4" is selected.

Thanks,
Tom


[PHP]#File Name: categorymanager.py

# To Do: Main Menu Items--Add Category, View Category, Delete Category, End
#        Request Menu--



# Import Necessary Modules and Assign Working Variables

import os
import sys

cls = 'os.system("clear")'
delay = 'os.system("sleep 2s")'
endprog = 'sys.exit(0)'
        
# Category Menu Function

def cat_text_menu():    

        # Globalize necessary variables
        global cls
        global delay
        global endprog

        # Display categories and menu options
    
        while True:
            exec cls
            print "Category Manager 1.0"
            print
            print "Available Categories:"
            print
            #Call category-reading function here
            print
            print "Menu:"
            print
            print "1. Add category"
            print "2. View category"
            print "3. Delete category"
            print "4. End"
            print
            print
            try:
                choice = raw_input('What would you like to do? ')
                if choice == "1":
                    print "You have chosen #1" #place holder
                    exec delay
                    cat_text_menu()
                elif choice == "2":
                    print "You have chosen #2" #place holder
                    exec delay
                    cat_text_menu()
                elif choice == "3":
                    print "You have chosen #3" #place holder
                    exec delay
                    cat_text_menu()
                elif choice == "4":
                    print "You have cosen #4" # CHOICE 4 IS NOT WORKING
                    exec delay
                    exec endprog
                else:
                    exec cls
                    print "That is not a valid choice."
                    exec delay
                    cat_text_menu()
            except:
                exec cls
                print "That is not a valid choice."
                exec delay
                cat_text_menu()


cat_text_menu()[/PHP]

---

### Post by po0f on 2006-10-10
thomasaaron,

Why can't you call sys.exit() normally?
```
import time
import sys

(snip...)

    elif choice == "4":
        print "You have chosen #4" # CHOICE 4 IS NOT WORKING
        time.sleep(2)
        sys.exit("Not a valid choice.")
```

(Added time.sleep() in there instead of what you had.  Calling a function via os.system() spawns a child process.  I'm sure it doesn't matter much in this situation, but when you start coding bigger programs, every little bit of performance counts.)

---

