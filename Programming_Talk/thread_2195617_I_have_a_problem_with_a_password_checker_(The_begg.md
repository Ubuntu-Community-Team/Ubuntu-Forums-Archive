---
title: "I have a problem with a password checker (The beggining of one)"
date: 2013-12-25
forum: Programming Talk
---

### Post by turtureagabriel on 2013-12-25
I debug the program and it says unexpected end of file i tryied with evrything , with "fi" i also tryied with exit and everything that i could find i just want a quick and easy solution for it.Sorry if i have lots of problems im just a begginer with bash.:-$
BTW the terminal starts but it disappears.Help me i am really confused :(:lolflag:
Code:
```

#! /bin/bash/
function pause {
    read -p "Paused" nothing
    }

pass=0

echo "Welcome to the interactive password script!"
$Pause
if [ $pass=0 ]; then echo "Your password isn't set!" echo "Type your new password in the terminal" read $pass_set set [ $pass=$pass_set ]
$Pause
else echo "Type in your password to unlock options"
read $pass_conf
if [ $pass_conf = $pass ] then echo "Password Correct!" else echo "Password incorrect!"
$Pause
exit



```

---

### Post by Iowan on 2013-12-25
I'm not familiar with BASH either - I can't tell you when/why an **if/then/else** needs a semicolon following the conditional, but from the (few) examples I checked, it looks like each **if** statement should end with a **fi**

Edit: Found this to answer my own question:
> Always terminate the line before putting a new keyword like &#8220;then&#8221;. The words if, then, else, elif and fi are shell keywords, meaning that they cannot share the same line. Put a &#8220;;&#8221; between the previous statement and the keyword or place the keyword on the start of a new line. Bash will throw errors like &#8220;syntax error near unexpected token `fi&#8217;&#8221; if you don&#8217;t.

---

### Post by ofnuts on 2013-12-26
Plenty of wrongness in this line
```

if [ $pass=0 ]; then echo "Your password isn't set!" echo "Type your new password in the terminal" read $pass_set set [ $pass=$pass_set ]

```

Some of it may be due to missing line feeds when you pasted, but the equal sign in the test should be detached ("$pass = 0") and I don't see what you are trying to do with "read $pass_set set [ $pass=$pass_set ]" 

Also, I don't see any "fi" to close the "if".

The "terminal starts" but your "exit" statement at the end makes the bash process terminate (assuming it's not terminated early due to other errors). Putting an exit statement at the end of a script is normal, a good script with exit with an error status (0 if OK). While you are debugging it, start it from a terminal, not by clicking on it in some file manager... then "exit" will exit the script only, and bring you back to the shell, without closing the terminal window. You can set fix errors and relaunch the script from the shell.

---

### Post by turtureagabriel on 2014-01-24
Nevermind, i was just a noob at that time in bash i fixed it.Thanks for your help

---

