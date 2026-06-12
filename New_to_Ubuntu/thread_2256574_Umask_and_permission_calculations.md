---
title: "Umask and permission calculations"
date: 2014-12-13
forum: New to Ubuntu
---

### Post by wannbenixdude on 2014-12-13
I understand that a umask is a feature that determines default permissions for newly created files and directories. 
I understand that the default file permission cant exceed 666.
I understand that the defaule directory permission is 777. 
I understand that the umask is subtracted from the default (file or directory respectively) permissions to determine the new file or directory creation permission. 

if umask is 022, file permission will be 644 and directory permissions will be 755. (ofcourse assuming 0 setuid/setgid/sticky).

What Im having problems not understanding .. "seeing" is : 

If umask is 027 file permission is 640... Im guessing dir permissions would be 750 ?

Just cant see the math here ... the only thing I can think of is because its octal .. there isnt any 8 or 9, the 7 in the umask causes a roll to zero.

---

### Post by Morbius1 on 2014-12-13
Starting point for files ( 666 ) is 110 110 110 
Logical not of umask ( 027 ) is 111 101 000 ( or 750 )

The two series of numbers is then AND'ed logically ( represented by a "+" below ):
110 + 111 = 110 ( or 6 )
110 + 101 = 100 ( or 4 )
110 + 000 = 000 ( or 0 )

A logical AND returns a "1" when both numbers are "1"  ( 1+1=1 )
A "0" when only one number is "1" ( 0+1=0 )
A "0" when both numbers are "0" ( 0+0=0 )

Same with directories which start off at 777 ( 111 111 111 ):
111 + 111 = 111 ( or 7 )
111 + 101 = 101 ( or 5 )
111 + 000 = 000 ( or 0 )

[COLOR=#0000cd]**EDIT**[/COLOR]: [COLOR=#0000cd]Here's another way to look at the same thing:
[/COLOR]
For a directory:

777 = rwx rwx rwx
027 = - - -   -w- rwx
===========
750 = rwx r-x - - -

---

