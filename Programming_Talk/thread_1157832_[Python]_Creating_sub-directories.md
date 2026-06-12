---
title: "[Python] Creating sub-directories?"
date: 2009-05-13
forum: Programming Talk
---

### Post by dodle on 2009-05-13
I am trying to build a program that creates a series of sub-directories depending upon the input of the user.  For some reason, I can't keep it going.  It makes half of the direcories then quits.  Here is my code:
[php]#! /usr/bin/env python

import os
from os.path import exists

home_dir = os.getenv("HOME")
target_dir = "%s/Desktop/Testing" % home_dir
if not exists(target_dir):
    os.system("mkdir %s" % target_dir)

dir_tree = raw_input("Create a directory tree: ")  # type a sentence using "/" to separate directories
tree_group = dir_tree.split("/")

for item in tree_group:  # Removes any empty strings from the list
    if item == "":
        tree_group.remove(item)

tree_count = len(tree_group)  # Retrieves the amount of directories that need to be made
print "\nWill make %s directories.\n" % tree_count

for item in tree_group:
    new_group = tree_group
    if tree_count > 0:
        temp = target_dir.split()
        print "New Directory \"%s\"" % new_group[0]
        temp.append(new_group[0])
        target_dir = "/".join(temp)
        print "Going to make %s" % target_dir
        os.system("mkdir %s" % target_dir)
        tree_count -= 1
        print "%s directories left to make" % tree_count
        new_group.remove(new_group[0])
        print "New Group = %s\n" % tree_group
[/php]

If someone could point out my error, I would be most appreciative.  Also, is there a better way to do this, or is my sample code acceptable?

---

### Post by ghostdog74 on 2009-05-13
why are making calls to system commands when its not necessary? 
check out the documentation for the makedirs() , or mkdir() method from the os module. use os.path.join() to create paths to use as variables. use try/except to catch errors so that you can easily debug your code.

---

### Post by dodle on 2009-05-13
Thanks ghostdog, that os.makedirs() is so simple.  I appreciate your help.

[php]#! /usr/bin/env python

import os
from os.path import exists

home_dir = os.getenv("HOME")
target_dir = "%s/Desktop/Testing" % home_dir
if not exists(target_dir):
    os.mkdir("%s" % target_dir)

dir_tree = raw_input("Create a directory tree: ")  # type a sentence using "/" to separate directories
tree_group = dir_tree.split("/")

for item in tree_group:  # Removes any empty strings from the list
    if item == "":
        tree_group.remove(item)

tree_count = len(tree_group)  # Retrieves the amount of directories that need to be made
print "\nWill make %s directories.\n" % tree_count

os.makedirs("%s/%s" % (target_dir,dir_tree))[/php]

---

