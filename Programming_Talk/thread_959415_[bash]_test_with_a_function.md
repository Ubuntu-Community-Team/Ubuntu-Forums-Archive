---
title: "[bash] test with a function"
date: 2008-10-26
forum: Programming Talk
---

### Post by DLGandalf on 2008-10-26
some pseudo code for a probably noob question, but in every tutorial they never test on functions

```

function x
{
return 0
}

if [x]; then
  echo nice
else
  echo bla

```

why does this give an  command unknown error, as in it's trying to find a binary in my path instead of using the defined function.

---

### Post by wd5gnr on 2008-10-26
Without thinking too hard... why not:

x
if [ $? ]
then ....

---

### Post by forger on 2008-10-26
*spaces* *fi missing* *use $()* :)
$ function x { return 0; }
$ if **[ $(x) ]**; then echo nice; else echo bla; fi
nice

---

### Post by wd5gnr on 2008-10-26
Actually I had thought of $() also and edited my post to add it (I thought I had tried it). But then I tried a little harder and removed it. Try this:

function x { return 1; }
function y { return 0; }
if [ $(x) ] ; then echo A ; else echo B ; fi
if [ $(y) ] ; then echo C ; else echo D ; fi

You get B and D!

---

### Post by skotos on 2008-10-26
A full sample to try ```
#!/bin/bash

# GLOBAL CONSTANTS
declare -ir FALSE=1
declare -ir TRUE=0

# Functions
amIroot() {
    local ROOT_UID=0;
    if [ ${UID} -eq ${ROOT_UID} ]
    then
    return ${TRUE}
    else
    return ${FALSE}
    fi
}

# Main

amIroot
nRC=$?

if [ ${nRC} -eq ${TRUE} ]; then
    echo "`basename $0 .sh` is running with root privileges"
else
    echo "root privileges required to run `basename $0 .sh`"
fi
```Save the code as test.sh and remember:```
chmod +x test.sh
./test.sh
```Pay attention to equality: -eq is valid for numbers, = (just one) for strings.
The better way to compare strings is```
if [ "X${CONST}" = "X${sVar}" ]; then
```The X's are wanted to avoid other errors.

---

### Post by DLGandalf on 2008-10-26
why don't they add these helpful things in the dozen tutorials I've found

thanks for the replies!

---

### Post by agrings on 2012-01-31
Maybe I'm a little late, but...
The problem here is the test function.
Remove it.

function x { return 1; }                                                                                                                                       
function y { return 0; }                                                                                                                                       
if $(x) ; then echo A ; else echo B; fi                                                                                                                        
if $(y) ; then echo C ; else echo D ; fi

---

### Post by sisco311 on 2012-01-31
Necromancy. 

[[img]http://ompldr.org/tYzBtcQ[/img]](http://ompldr.org/vYzBtcQ)

Thread Closed.

---

