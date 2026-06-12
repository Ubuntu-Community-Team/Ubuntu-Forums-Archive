---
title: "If statement with empty string"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by thedawg on 2013-02-20
Hi there, 

I got a problem with a little If statement and Empty sting here. 

The Idea is to check for the Graphic Card so I can select an Installation-package for the right Video Drivers (Intel, ATI, NVIDIA,...) 

My If statement shall determine if the string I am looking for exists or not

This is my Trial and Error Code:
```

#! /bin/sh
if [ `lspci | grep -i vga | grep -i nvidia` = "" ]; then
    echo "off"
else   
    echo "on"
fi
```

And i get always the same result no matter what I'm looking for, or on which Computer I'm testing it:
```
-su: [: =: unary operator expected
on
```

Hope some of you can help me
THX in advance :)

---

### Post by schragge on 2013-02-20
Quote it
```

if [ -z "`lspci | grep -i vga | grep -i nvidia`" ]; then

```
or, better yet, avoid the *test* command althogether
```

if lspci | grep -qi 'vga .* nvidia'; then
  echo on
else
  echo off
fi

```

---

### Post by thedawg on 2013-02-20
Still getting 
-su: [: too many arguments
on


on the wrong system 
:(

---

### Post by schragge on 2013-02-20
Can you please post the command you're trying now? And what about getting rid of *test*? I've updated my previous post.

---

### Post by sudodus on 2013-02-20
+1 "quote it"

I think it is easier to see what is happening when you write the script like this:

```
#!/bin/bash
if [ "$(lspci | grep -i vga | grep -i nvidia)" == "" ]
then
 echo "off"
else 
 echo "on"
fi

```

*Edit*: The if [ ] syntax is for bash and will not work in sh

---

### Post by thedawg on 2013-02-20
Thx I'll try that

what did you mean with the test command ? :) 

I'm really new to this stuff ^^

---

### Post by thedawg on 2013-02-20
Hahaa! It seems to work, with the last one, thank you very much for your help, kind Sirs.

---

### Post by SeijiSensei on 2013-02-20
If you're testing the result of a command with $(), you need to wrap that in quotes as you just did:

```
if [ "$(some command)" = "" ]
```

---

