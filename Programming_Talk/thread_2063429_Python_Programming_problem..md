---
title: "Python Programming problem."
date: 2012-09-27
forum: Programming Talk
---

### Post by jnLink on 2012-09-27
```
#!/usr/bin/env python
print "=======jnLink v.1.0======="
x=raw_input('User name: ')
y=raw_input('Password: ')
if x=='Jon' and y=='turtles21':
    print "Logged On, Welcome Jonathan Nunamaker."
else:
    print "logon failed"
    c=1
    while c <10:
        print "Logon Failed"

```   

"actual coding"

```
start=raw_input("EF to edit file: ")
if start=='EF':
    filedestination=raw_input('File name please? ')
    editorwrite=raw_input('Edit or Read this file? (r to read and w to write. )')
    fob=open('/home/jon/My Cheat Tables/computer/' + filedestination, editorwrite)
    if editorwrite== 'q':
        print "Main Menu: "
    if editorwrite== 'w':
        fob.write(raw_input('Your file is open: '))
        fob.close()
    if editorwrite== 'r':
         print "=======file======="
         print fob.read()
         print "=======file======="
         closeorjump=raw_input('type c to exit to main menu: ')
         if closeorjump== 'c':
             fob.close()
```
  ==========================================
I have this; I need to have it go back to main menu after the end of each if statement. Any ideas? Please?

---

### Post by lisati on 2012-09-27
*Thread moved to **Programming Talk**.*

I've addded "code" tags [noparse](```
 and 
```)[/noparse] which can help with readability

---

### Post by satsujinka on 2012-09-27
What you want is a loop. A while loop would probably be a good choice.
[http://wiki.python.org/moin/WhileLoop](http://wiki.python.org/moin/WhileLoop)

---

### Post by Tony Flury on 2012-09-28
And use functions to help you divide your code into logical sections.

---

### Post by greenpeace on 2012-10-05
For capturing the password on the command line you might want to consider using the python [getpass]("http://docs.python.org/library/getpass.html") library as well:

```
from getpass import getpass

name = raw_input("Username: ")
pswd = getpass("Password: ")

print "\nResults:"
print "name: %s \npass: %s" % (name, pswd)

```

---

