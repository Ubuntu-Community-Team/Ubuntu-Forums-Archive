---
title: "[SOLVED] Take user input and send it to a file"
date: 2007-11-22
forum: Programming Talk
---

### Post by mdpalow on 2007-11-22
Hi Everyone,

I want to try an experiment where I take a user's input (name) and then put it in a text file. Here's my example:

#!/bin/bash

set verbose

echo -n "What is your name?

Please Enter Here:  "
read $name

????? >> /home/my_name/Desktop/testing.txt

fi

unset verbose


The ????? is the part I don't know. 

If the file exists, I want to append it and if not, I want this to create it and then write it.

I've lost some of my reference material and am having problems remembering how to do this.

Thanks for any help you can provide...

---

### Post by vambo on 2007-11-22
?????? = echo
ie echo "$name" > file.txt

---

### Post by mdpalow on 2007-11-22
I did that and it didn't work... let me try again now...

---

### Post by vambo on 2007-11-22
> **mdpalow said:**
> I did that and it didn't work... let me try again now...

Sorry, missed the 2nd line 1st time - added it as an edit

---

### Post by mdpalow on 2007-11-22
for some reason it won't store the $name and then pass it to the file. If I put regular text around $name it puts the text in file, but leave out the $name

#!/bin/bash

set verbose

echo -n "what is your name?

Please Enter Here: "
read $name

echo "$name" >> /home/$USER/Desktop/testing.txt


unset verbose

---

### Post by mdpalow on 2007-11-22
OMG... I found it.... Can't believe I did that...

there's no $ after read.. it's not "read $name" it's just "read name"

Thanks...

---

### Post by vambo on 2007-11-22
np. I didn't see it either :oops:

---

### Post by duuchung on 2007-11-22
I know a little little shell scripting. I have to learn C++ or shell scripting because I have to write a small programme using the above language for a friend . I followed your example. But nothing is written to the testing.txt. The file was opened. Nothing could be read with human eyes when I vi the file.  The last line reads  “testing.txt”4 lines, 4 characters.

Could anyone  tell me what is wrong with my ubuntu set- up in not writing the name to the file properly?

---

