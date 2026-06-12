---
title: "Python - text editor, need some help"
date: 2010-04-21
forum: Programming Talk
---

### Post by mo.reina on 2010-04-21
i've written a very rudimentary text editor, just to see if i understood the concepts.  one thing i'm unclear about is how to edit the text from an existing file, not pattern matching, but the same way text is edited when you start up nano or vim, by moving the cursor to the location and manually editing.

this is the code i came up with (very very basic).  almost no comments as the code is extremely simple
```
!/usr/bin/python

import sys

import re

def main_menu():
    print '-----Main Menu-----'
    print ' 1) write to a file'
    print ' 2) read a file'
    print ' 3) quit'

def write_file():
    print 'enter file name: '
    f_name = raw_input() + '.txt'  # adds the .txt extension to the desired file name
    f = open(f_name, 'a')
    while 1:
        text = raw_input('enter text: ')
        if text == ':q':
            f.close()
            return
        text = re.sub('-P-', '    ', text)   # I'm using -P- to define paragraphs, just something i put it in to see if i understood pattern matching
        text = text + '\n'
        f.write(text)

def read_file():
    print 'enter file name (include extension): '
    f_name = raw_input()
    f = open(f_name, 'r')
    print f.read()
    f.close()

main_menu()

choice = raw_input(': ')

if choice == '1':
    write_file()

elif choice == '2':
    read_file()

elif choice == '3':
    sys.exit()

else:
    print 'invalid choice'
    sys.exit()
```

---

### Post by diesch on 2010-04-22
Have a look at the *curses* module.

---

### Post by mo.reina on 2010-04-22
great thanks

---

