---
title: "scripting"
date: 2013-07-17
forum: Programming Talk
---

### Post by kiminaiseah on 2013-07-17
hi i need some help from experienced or expert here, 

im struggling with this one, 

i have sensor device on /dev/ttyUSB0 

on its power cycle it send message CHECKING

then i have to echo OKAY > /dev/ttyUSB0 

i that way the sensors does not restart

and aside that it randomly send mesage CHECKING ,

i want this thing be automatically something like in this sequence

1. cat /dev/ttyUSB0 > logging.log
2. read logging.log in infinite loop
3. if message CHECKING spawn 
4. echo OKAY > /dev/ttyUSB0
5. then have to echo "" > logging.log 

and sometime it send other words like RED, YELLOW, GREEN

if the sensors send message RED i have to echo PUSH > /dev/ttyUSB0
if the sensors send message YELLOW i have to echo PULL > /dev/ttyUSB0
if the sensors send message GREEN i have to echo BEEP > /dev/ttyUSB0

can do someone help me solve automating this in a script?

thanks

---

### Post by Lars Noodén on 2013-07-18
Can you provide some sample output from 'cat /dev/ttyUSB0' ?

---

### Post by kiminaiseah on 2013-07-18
hi sir please see attach screenshot 

thats the exact reading from /dev/ttyUSB0

it does not seperate by line but rather continues the log no spacing , it is because also want to send empty echo to /dev/ttyUBS0 to clear those log

[ATTACH=CONFIG]244853[/ATTACH]

---

