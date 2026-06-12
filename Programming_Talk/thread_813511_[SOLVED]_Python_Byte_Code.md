---
title: "[SOLVED] Python Byte Code?"
date: 2008-05-30
forum: Programming Talk
---

### Post by -grubby on 2008-05-30
I edited a string for my supybot IRC bot,the factoids plugin, names config.py. The change didn't work after I restarted my bot, and I noticed a file named config.pyc. Apparently this is a "python byte code" and it some kind of compiled Python script. It's a binary file, so I can't edit it. How would I reproduce this file after the change I made?

---

### Post by Can+~ on 2008-05-30
[http://bytes.com/forum/post1687531-3.html](http://bytes.com/forum/post1687531-3.html)

In other words: It's made automatically, unless you're executing the python script with "./something.py"

---

### Post by -grubby on 2008-05-30
Oh, well it hasn't been updated yet. Should I just delete it and have it auto generate?

---

### Post by Can+~ on 2008-05-30
I think it's safer to just do "python myscript.py" directly to the edited file. If it doesn't work, then the change you made didn't have an effect.

---

### Post by -grubby on 2008-05-30
It didnt' work. Strange, because it should have...

---

### Post by geirha on 2008-05-30
It's safe to delete the pyc-files. In fact it's a good idea to delete all pyc-files when you make changes to the code, so you can be sure only the new code is run.

---

### Post by days_of_ruin on 2008-05-30
> **geirha said:**
> It's safe to delete the pyc-files. In fact it's a good idea to delete all pyc-files when you make changes to the code, so you can be sure only the new code is run.

That is a waste of time.Just dont do "python program.pyc".
As long as you execute the .py file it will always run you current code.

---

### Post by -grubby on 2008-05-30
Listen, I don't even know Python. I was just editing a string that's to be used by the factoids plugin in supybot, an irc bot (like eggdrop bot or similar)

---

### Post by geirha on 2008-05-30
If you split a module into multiple files or vice versa, you'll have two sets of pyc-files for the same code. Python won't give you any warnings for that. Better safe than sorry.

---

### Post by -grubby on 2008-05-30
Huh? I was just editing one file, I didn't create, split, or do anything else with it...

---

### Post by geirha on 2008-05-30
> **nathangrubb said:**
> Huh? I was just editing one file, I didn't create, split, or do anything else with it...

Sorry, that was a response to days_of_ruin.

Anyway, if you delete the .pyc-file, restart the bot and a new .pyc-file does not show up, then that .py-file simply isn't used. If a new .pyc-file does show up, then perhaps you've changed the wrong part of the code?

---

### Post by Can+~ on 2008-05-30
> **nathangrubb said:**
> Listen, I don't even know Python. I was just editing a string that's to be used by the factoids plugin in supybot, an irc bot (like eggdrop bot or similar)

Maybe you should post the piece of code in question, and what exactly you want to do.

---

### Post by -grubby on 2008-05-31
@geirha : I have restarted the bot and it still hasn't appeared, the the code I edited is below. I have highlighted the parts I edited

old version: 
```

conf.registerChannelValue(Factoids, 'factoidPrefix',
    registry.StringWithSpaceOnRight('[color=red]could be[/color]', """Determines the string that
    factoids will be introduced by."""))

```
New Version:
```

conf.registerChannelValue(Factoids, 'factoidPrefix',
    registry.StringWithSpaceOnRight('[color=red]: [/color]', """Determines the string that
    factoids will be introduced by."""))

```

---

### Post by -grubby on 2008-05-31
I've solved this, I found what I was looking for in The main config file (~/botname.conf) under supybot.plugins.Factoids.factoidPrefix: on line 932. 

Thread marked as solved

---

### Post by pmasiar on 2008-05-31
> **geirha said:**
> If you split a module into multiple files or vice versa, you'll have two sets of pyc-files for the same code. Python won't give you any warnings for that. Better safe than sorry.

but better to have clue than pretend and not have it at all. OP might feel like you know what you are talking about, and OP knows even less Python than you do, but rather obviously you don't.

.pyc is used by python **only** if relevant  .py was not changed. Deleting .pyc you are not making safe, you just get them all recompiled again.

Not sure how you can ever manage to gave two sets on .pyc files from different sources? They would obviously be in different directories, right? And then, PATH takes precedence. Thats CompSci 101.

---

