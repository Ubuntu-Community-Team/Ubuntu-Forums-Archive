---
title: "[Python] What's wrong with this script?"
date: 2008-12-19
forum: Programming Talk
---

### Post by dodle on 2008-12-19
I can't seem to figure out what is wrong with this script.  I bring up an exception by replacing the operator, but my exception handler doesn't work:[PHP]#!/usr/share/env python

def evalit(CMem):
    try:
        if CMem[1] == "+":
            FVal = float(CMem[0]) + float(CMem[2])
        elif CMem[1] == "-":
            FVal = float(CMem[0]) - float(CMem[2])
        elif CMem[1] == "*":
            FVal = float(CMem[0]) * float(CMem[2])
        elif CMem[1] == "/":
            FVal = float(CMem[0]) / float(CMem[2])
    except:
        print "\nNeed a valid operation\n"
        FVal = "Error"
    return FVal

CMem = []

CLoop = True
while CLoop:
    while len(CMem) <= 2:
        CVal = raw_input("NUMBER\n:")
        CMem.append(CVal)
        while len(CMem) == 1:
            OVal = raw_input("OPERATOR\n:")
            CMem.append(OVal)
    print CMem
    FVal = evalit(CMem)
    print "\n%s" % str(FVal)
    CMem = [][/PHP]

---

### Post by mssever on 2008-12-19
> **dodle said:**
> [PHP]def evalit(CMem):
    try:
        if CMem[1] == "+":
            FVal = float(CMem[0]) + float(CMem[2])
        elif CMem[1] == "-":
            FVal = float(CMem[0]) - float(CMem[2])
        elif CMem[1] == "*":
            FVal = float(CMem[0]) * float(CMem[2])
        elif CMem[1] == "/":
            FVal = float(CMem[0]) / float(CMem[2])
    except:
        print "\nNeed a valid operation\n"
        FVal = "Error"
    return FVal[/PHP]
First, catching all exceptions with a bare except is bad practice. You should catch specific exceptions (or specific hierarchies). Doing like you're doing could easily mask a bug.

In your case, though, you're not catching any exceptions because no exceptions are getting raised. No error is occurring. Change your except block to an else block (and get rid of the try) and things will work like you expect.

---

### Post by dodle on 2008-12-19
Thanks, I'll keep trying to improve my coding.

---

