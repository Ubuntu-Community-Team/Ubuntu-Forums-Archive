---
title: "Python noob needs input."
date: 2008-07-21
forum: Programming Talk
---

### Post by medicineman24 on 2008-07-21
Ok, so I have written this simple python script which basically starts hamachi and a game with the proper ip address selected.


[PHP]#needs multiplatform support... 

import socket
import os

running = True
addrs = socket.getaddrinfo(socket.gethostname(), None)

while running:
    
    selection = raw_input("Enter 1 For Local Ip\nEnter 2 For Hamachi Ip\n")
    
    if selection == '1':
        
        aoeconfig = open(r"C:\Users\Matt\Documents\My Games\Age of Empires 3\Startup\user.cfg", "w")
        aoeconfig.write(r'overrideaddress="')
        aoeconfig.write(addrs[3][4][0])
        aoeconfig.write(r'"')
        aoeconfig.close()
        running = False
        
    elif selection == '2':
        
        aoeconfig = open(r"C:\Users\Matt\Documents\My Games\Age of Empires 3\Startup\user.cfg", "w")
        aoeconfig.write(r'overrideaddress="')
        aoeconfig.write(addrs[4][4][0])
        aoeconfig.write(r'"')
        aoeconfig.close()
        running = False
        
    else:
        
        print "Incorrect Input\nPlease Try Again\n"

os.system(r'vcdmount "C:/Program Files/Age of Empires 3/asians.iso"')#needs multiplatform support

print "\nMounting Disk"

os.startfile('"C:/Program Files/Age of Empires 3/age3y.exe"')#needs multiplatform support

print "\nBooting AOE3."

if selection == '2':

    os.startfile(r'"C:\Program Files\Hamachi\Hamachi.exe"')#needs multiplatform support

    print "\nBooting Hamachi"

print "\nEnjoy Your Gaming!" [/PHP]

Currently it only runs on my machine (under windows D; ) due to specific paths in the script, the assumption that they have certain paths in their PATHEXT, and the fact that they might not have the same iso-mount program.  Any help/suggestions on how to make this script automatically run on my friends machines would be greatly appreciated.  BTW thanks much in advance and I hope this non-ubuntu question is a-ok.

EDIT: Suggestions simply regarding what I already have are also greatly appreciated.

---

### Post by Can+~ on 2008-07-21
Ok, since you request everything inside C:\Users...\Age of Empires 3\... you could store it into a variable, AND, using os.sep

[PHP]import os

a_path = r"this%(p)sis a%(p)spath" % {"p":os.sep}

print a_path[/PHP]

In Ubuntu this prints:
```
this/is a/path
```

os.sep is "/" with *nix and "\" with Windows.

Everything inside the "os" and "os.path" helps to make a portable application. "os.path.join" for safe adding of folders with the corresponding separator. Also, in my above example I use a dictionary to fill the spaces:

[PHP]astring = "%s" % "value" # %s is a string filled with "value"
astring2 = "%(key)s" % {"key":"value"} # is the same above with a dictionary.[/PHP]

You could also load the path from another file, so it's a bit more "user friendly" to edit.

---

### Post by medicineman24 on 2008-07-21
Ok so in order to get the paths correct for any computer:

I could create a dictionary of a few default paths, then test them during the script and finally perform the operations on the files.

I could of course take user input...

Is there some kind of search function that could locate filenames and store their paths in a tuple or something?

btw thanks for os.path hint, im going to read up on the documentation.

---

### Post by Can+~ on 2008-07-21
os.walk navigates file and folders, then you could add a search condition using the string methods.

Other safety methods would include to use "try/except" to avoid errors when loading or writing files. Consider using functions to avoid repeating blocks. And if you find the folder, you could store it using one of those modules to store python binary data, like shelf, marshal or pickle... Or even a simple text file can do.

---

### Post by medicineman24 on 2008-07-21
Alright thank you, I'll see what I can do.

---

### Post by medicineman24 on 2008-07-22
Thanks much. I've successfully got a search function that finds corresponding files and opens them.  Also, when the paths are found they are stored in a dictionary txt file using pickle.dump, so that the program only searches the first time it's run.  I also cut the time it takes for the program to complete by about 50%. The code is still really messy tho. :lolflag: at least i learned something in the process.

---

### Post by LinuX-M@n1@k on 2008-07-22
> **medicineman24 said:**
> Ok, so I have written this simple python script which basically starts hamachi and a game with the proper ip address selected.


[PHP]#needs multiplatform support... 

import socket
import os

running = True
addrs = socket.getaddrinfo(socket.gethostname(), None)

while running:
    
    selection = raw_input("Enter 1 For Local Ip\nEnter 2 For Hamachi Ip\n")
    
    if selection == '1':
        
        aoeconfig = open(r"C:\Users\Matt\Documents\My Games\Age of Empires 3\Startup\user.cfg", "w")
        aoeconfig.write(r'overrideaddress="')
        aoeconfig.write(addrs[3][4][0])
        aoeconfig.write(r'"')
        aoeconfig.close()
        running = False
        
    elif selection == '2':
        
        aoeconfig = open(r"C:\Users\Matt\Documents\My Games\Age of Empires 3\Startup\user.cfg", "w")
        aoeconfig.write(r'overrideaddress="')
        aoeconfig.write(addrs[4][4][0])
        aoeconfig.write(r'"')
        aoeconfig.close()
        running = False
        
    else:
        
        print "Incorrect Input\nPlease Try Again\n"

os.system(r'vcdmount "C:/Program Files/Age of Empires 3/asians.iso"')#needs multiplatform support

print "\nMounting Disk"

os.startfile('"C:/Program Files/Age of Empires 3/age3y.exe"')#needs multiplatform support

print "\nBooting AOE3."

if selection == '2':

    os.startfile(r'"C:\Program Files\Hamachi\Hamachi.exe"')#needs multiplatform support

    print "\nBooting Hamachi"

print "\nEnjoy Your Gaming!" [/PHP]

Currently it only runs on my machine (under windows D; ) due to specific paths in the script, the assumption that they have certain paths in their PATHEXT, and the fact that they might not have the same iso-mount program.  Any help/suggestions on how to make this script automatically run on my friends machines would be greatly appreciated.  BTW thanks much in advance and I hope this non-ubuntu question is a-ok.

EDIT: Suggestions simply regarding what I already have are also greatly appreciated.

I have a question - what's the "r" for in
[php]os.startfile(r'"C:\Program Files\Hamachi\Hamachi.exe"')
             ^[/php]
You don't have it here:
[php]os.startfile('"C:/Program Files/Age of Empires 3/age3y.exe"')
             ^[/php]
I'm a newbie in Python :). Thank you.

---

### Post by imdano on 2008-07-22
The 'r' marks the following string as a raw string, meaning Python won't recognize escape sequences.
```
>>> print r"hey\n there"
hey\n there
>>> print "hey\n there"
hey
 there
>>> 


```Read more [here](http://docs.python.org/ref/strings.html)

---

