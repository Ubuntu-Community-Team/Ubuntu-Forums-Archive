---
title: "My First Terminal Game"
date: 2011-08-17
forum: Programming Talk
---

### Post by Pyprokid on 2011-08-17
Hello! :D

I made a small Terminal version of Rock-Paper-Scissors, I am still fairly new to programming and was wondering if it is good or not? The link to the code is: 

[http://pastebin.com/tn7Tudja]("http://pastebin.com/tn7Tudja")

Please reply with your thoughts. :) 

- Matt

---

### Post by Smart Viking on 2011-08-17
I think it was fun. ;)

It would be nice though, if you could continue playing without having to restart the program, you could add a loop to do that.

Keep doing what you're doing! :)

---

### Post by Pyprokid on 2011-08-17
> **Smart Viking said:**
> I think it was fun. ;)

It would be nice though, if you could continue playing without having to restart the program, you could add a loop to do that.

Keep doing what you're doing! :)

Thanks alot! :) 
I'll add the loop and probably a score system soon. :)

---

### Post by Queue29 on 2011-08-17
If you're gonna use python, you may as well go all the way and make it platform independent. The way you're clearing the screen will only work on posix systems. Here's what I do:

```

import os

def clear():
    cmd = 'cls' if 'nt' in os.name else 'clear'
    os.system(cmd)

```

Also, using camelCaseStyle is a Java/C# thing. Real pythoners encourage underscore_names_like_this instead. I recommending giving [PEP8]("http://www.python.org/dev/peps/pep-0008/") a looking over.

---

### Post by Pyprokid on 2011-08-17
> **Queue29 said:**
> If you're gonna use python, you may as well go all the way and make it platform independent. The way you're clearing the screen will only work on posix systems. Here's what I do:

```

import os

def clear():
    cmd = 'cls' if 'nt' in os.name else 'clear'
    os.system(cmd)

```

Also, using camelCaseStyle is a Java/C# thing. Real pythoners encourage underscore_names_like_this instead. I recommending giving [PEP8]("http://www.python.org/dev/peps/pep-0008/") a looking over.

Ah, I hadn't thought about that, thanks alot for the advice. :D I'll implement that into the code as well. :)

---

### Post by ilovelinux33467 on 2011-08-17
This is really good :).

---

### Post by ofnuts on 2011-08-17
> **Pyprokid said:**
> Hello! :D

I made a small Terminal version of Rock-Paper-Scissors, I am still fairly new to programming and was wondering if it is good or not? The link to the code is: 

[http://pastebin.com/tn7Tudja](http://pastebin.com/tn7Tudja)

Please reply with your thoughts. :) 

- MattNot a bad effort, but several remarks nevertheless:

The first thing that strikes me is the amount of code duplication. Playing between two people and playing against the 'puter is fundamentally the same. You should put that in a function. There is no good reason to have the player's choice expressed **internally** as {1,2,3} and the internal draw as {0,1,2}. You can/should transform your user input to put it in the {0,1,2} range. Then you discover that your stack of if's can be replaced by a 3x3 static decision table, indexed by the choices, and another 3x3 array of messages (you can also use, Python style,  a 3x3 array of tuples with the result and the messages).

Likewise the display of the results should be all in a function to which you pass the relevant parameters (ie, win/lose/tie plus message) (or the tuple from above...) and that adds the "formatting" around it.

Then make functions for all the different functional  bits (for instance getting user input)

So finally your "main" code would become something like:
```

playerChoice=getPlayerChoice()
computerChoice=random.randrange(3)

displayResult(table[playerChoice][computerChoice])

```

In short, be lazy. Think of ways to reduce your typing and the brainpower to understand the code (chop it in independent bits, aka "functions", easy to design/code/understand).

---

### Post by Pyprokid on 2011-08-17
> **ofnuts said:**
> Not a bad effort, but several remarks nevertheless:

The first thing that strikes me is the amount of code duplication. Playing between two people and playing against the 'puter is fundamentally the same. You should put that in a function. There is no good reason to have the player's choice expressed **internally** as {1,2,3} and the internal draw as {0,1,2}. You can/should transform your user input to put it in the {0,1,2} range. Then you discover that your stack of if's can be replaced by a 3x3 static decision table, indexed by the choices, and another 3x3 array of messages (you can also use, Python style,  a 3x3 array of tuples with the result and the messages).

Likewise the display of the results should be all in a function to which you pass the relevant parameters (ie, win/lose/tie plus message) (or the tuple from above...) and that adds the "formatting" around it.

Then make functions for all the different functional  bits (for instance getting user input)

So finally your "main" code would become something like:
```

playerChoice=getPlayerChoice()
computerChoice=random.randrange(3)

displayResult(table[playerChoice][computerChoice])

```

In short, be lazy. Think of ways to reduce your typing and the brainpower to understand the code (chop it in independent bits, aka "functions", easy to design/code/understand).

Ah, that makes sense. Thanks, I'll work on incorporating that now for fun. :D

---

