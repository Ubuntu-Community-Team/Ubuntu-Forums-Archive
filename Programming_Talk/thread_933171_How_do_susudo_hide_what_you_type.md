---
title: "How do su/sudo hide what you type?"
date: 2008-09-29
forum: Programming Talk
---

### Post by Amaroq on 2008-09-29
I'm curious, how exactly do su/sudo hide your text when you type in your password? So far, the only conclusion I could come to was that it uses ncurses somehow. So I checked into ncurses, however that blanks the whole terminal when it initializes. I want to leave the terminal untouched, give the user a blank line, collect what they type, and hide it as they type it, just like sudo and su do.

I'd prefer to use c++ if possible, though any explanation would be welcome.

---

### Post by kpatz on 2008-09-29
Download the sudo source and look for yourself... it's in tgetpass.c.

Long story short, it uses ioctl calls to the tty to turn local echo off during the password prompt, and back on again afterward.  You'll have to make sure to catch signals so that the echo gets turned back on if the user interrupts the program.

You can even turn echo off from the shell with "stty -echo" and back on with "stty echo".

---

### Post by John164918a on 2008-09-29
I see! The whole bash login thingy is soooo cool! And so secure!

---

### Post by Amaroq on 2008-09-30
*chuckles* That stty -echo/echo thing might be all I need actually. Though I have also downloaded the sudo source code. Thanks for the tips!

---

### Post by Amaroq on 2008-10-02
Turns out there's an even easier way to do it if you're looking to do it from a shell script.

```
read -s
```

Whatever you type after read is invoked is stored in a variable called REPLY.

```
echo $REPLY
```

You can add the -p flag for a prompt. Unfortunately, the user@computer prompt will append onto your read prompt if you use the -p flag.

Though you could easily fix that by adding something that will newline for you.

```
read -s -p Password:\  && echo ''
```

Voila, you've got a su-like password prompt retrievable from the $REPLY variable.

---

