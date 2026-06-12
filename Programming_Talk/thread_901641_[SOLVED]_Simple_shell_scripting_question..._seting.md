---
title: "[SOLVED] Simple shell scripting question... seting and testing variables"
date: 2008-08-26
forum: Programming Talk
---

### Post by Iceman99one on 2008-08-26
Ok--

I have been teaching myself how to write simple scripts to do very basic things.

I was wondering if it was possible to set a variable to a string of text with embedded spaces and then test that variable in your script. It's hard to explain. 

Here is an example that might help clarify my question:

```

#!/bin/bash

text=0

echo -n "Enter \"the secret code\"----->"
read text
echo "You entered---> $text"

if [ $text= "the secret code" ];then
     echo "Wow you sure are smart!"
else
     echo "Please play again!"
fi

```

I want to test if the user entered the secret code...

Any help would be appreciated!
Thanks!

---

### Post by mike_g on 2008-08-26
I havent done much bash scripting, but I think that to test for equality you would do:
```
if [ "$text" -eq "the secret code" ];then
```

---

### Post by cyberslayer on 2008-08-26
No, -eq is only for integers.  See the manpage for test for details.  The problem is that there is no space between $text and the equals sign.  You need to change the line with the if to this:

```
if [ $text = "the secret code" ]; then
```

---

### Post by cyberslayer on 2008-08-26
Double posted by accident, sorry

---

### Post by dtmilano on 2008-08-26
Don't forget to quote "$text".

---

### Post by Iceman99one on 2008-08-26
I put quotes around $text and it fixed my problem!

Thanks for all your help!

---

