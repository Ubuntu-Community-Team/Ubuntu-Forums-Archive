---
title: "need a help to write a script with parallel processing.."
date: 2011-09-21
forum: Programming Talk
---

### Post by jpjohnj on 2011-09-21
hi..

i need a help to create a shell script ...

i will explain concept i need...


i need to know how to run a parallel process at a same time with the script..

i.e consider two terminal, in one terminal i will run ls command and other terminal i will run who command..

i dont want a output to be redirected to other process like pipe program...

-------------------

help me to create a script


------------

---

### Post by nothingspecial on 2011-09-21
Moved to Programming Talk.

---

### Post by dethorpe on 2011-09-21
You could try a couple of things (there are no doubt other ways):
 
1) Start your scripts in the background using the & operator. Either both from a third start script, or just one from the other which stays in foreground after starting the background one.
2) Use the bash coprocess to start one process in the background from the other and then capture and process its output as required
 
Which way depends on exactly what you are trying to do with the two processes/scripts?
 
You can search for bash coprocess and & operator to get details of how to use them.

---

### Post by ofnuts on 2011-09-21
Use a named pipe between the two:

[http://www.linuxjournal.com/article/2156](http://www.linuxjournal.com/article/2156)

---

### Post by karlson on 2011-09-21
> **jpjohnj said:**
> hi..

i need a help to create a shell script ...

i will explain concept i need...


i need to know how to run a parallel process at a same time with the script..

i.e consider two terminal, in one terminal i will run ls command and other terminal i will run who command..

i dont want a output to be redirected to other process like pipe program...

-------------------

help me to create a script


------------

You either doing something way to complicated with Shell or not explaining exactly what you need.  You could do something like this:

```

#!/bin/bash

xterm -e "command 1" &
xterm -e "command 2" &

```

I would try and rethink your design a little bit.

---

