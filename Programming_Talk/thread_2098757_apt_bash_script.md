---
title: "apt bash script"
date: 2012-12-27
forum: Programming Talk
---

### Post by DarkSnake-Kobra on 2012-12-27
I have a friend that wanted me to look at a bash script for him that he's having trouble with. I don't really know much about bash scripts and took me a couple hours to make a working one, but it wasn't to his liking as he wanted it to return 0. This is what he has, but the quit option is not working and it also runs both options and not one or the other which it should be doing.

```
#!/bin/bash 
# 
# 
# 
# 
# 
# 
quit= { return 0 }   
echo "Please enter a number between 1-2 then press enter" 
read number  
if [ $number = 1 ] 
then sudo apt-get update; sudo apt-get dist-upgrade -y 
else $quit 
fi 
if [ $number = 2 ] 
then sudo apt-get autoremove; sudo apt-get autoclean 
else $quit 
fi
```

---

### Post by Lars Noodén on 2012-12-27
You'll probably want to use 'quit' as a function.

```

#!/bin/sh
quit() {
  return 0
}

echo "Please enter a number between 1-2 then press enter"
read number

if [ 1 -eq $number ]; then
  sudo apt-get update;
  sudo apt-get dist-upgrade -y
elif [ $number -eq 2 ]; then
  sudo apt-get autoremove;
  sudo apt-get autoclean
else
  quit
fi

```

Depending on what you are doing, a case statement might be better than if-then.

---

### Post by DarkSnake-Kobra on 2012-12-27
Thanks! I'll give that to him and hope that's what he wants. :)

---

### Post by r-senior on 2012-12-27
Although your quit() function works, the more conventional way to return a value is using exit with a parameter of the value you would like to return, e.g.:

```
exit 0
```

[http://tldp.org/LDP/abs/html/exit-status.html](http://tldp.org/LDP/abs/html/exit-status.html)

When a script "returns" a value, i.e. has an exit status, it is usually to indicate success or failure. By convention, returning zero means success. Is not entering a valid choice considered success in this case?

A couple more questions:

1. Have you considered what happens if the first command of each pair fails? For example, "apt-get update" fails because there is no network? Should "apt-get dist-upgrade" run in that case?

2. In six months' time, when your friend runs the script and it says "Please enter a number between 1-2 then press enter", will he remember what 1 and 2 do?

---

### Post by DarkSnake-Kobra on 2012-12-27
Okay.

1. Yeah I'm not sure exactly what he's doing. I think it was more practice than anything else. Personally, when I run commands in the shell it ether runs or it doesn't so I don't see the reason for having it report back or not. If I did I'd probably want it to echo an error string back. This is what I came up with, but he wanted it done a bit differently.

```
#!/bin/bash
echo "Please enter a number between 1-2 then press enter"
read number

if [ $number -eq 1 ]
then
    sudo apt-get update && sudo apt-get dist-upgrade -y
elif [ $number -eq 2 ]
then
    sudo apt-get autoremove && sudo apt-get autoclean
else
    echo "Input [SIZE=2]E[/SIZE]rror [SIZE=2]Q[/SIZE]uitting..."
```
2. That's a good question. :P I'd probably add two more echo statements before the read number line one for each number that way it's easier to read and not bunched up.

---

### Post by r-senior on 2012-12-28
> **DarkSnake-Kobra said:**
> ... when I run commands in the shell it ether runs or it doesn't so I don't see the reason for having it report back or not.
That's the reason for an exit status -- so that another script, command or program knows whether the command was successful.

When you do this ...

```
sudo apt-get update && sudo apt-get dist-upgrade -y
```

... you are making use of that exit status. It's a shorthand way of saying "if the update works, do the upgrade, otherwise do nothing".

Wouldn't you want an exit code in your script? Wasn't that the idea?

```
...
else
    echo "Input [SIZE=2]E[/SIZE]rror [SIZE=2]Q[/SIZE]uitting..."
    **[COLOR="Red"]exit 1[/COLOR]**
fi

```


> 2. That's a good question. :P I'd probably add two more echo statements before the read number line one for each number that way it's easier to read and not bunched up.
How about a prompt like "[U]pgrade or [C]lean?" Then take the letters 'U' and 'C' instead of numbers 1 and 2?

---

### Post by DarkSnake-Kobra on 2012-12-30
> **r-senior said:**
> That's the reason for an exit status -- so that another script, command or program knows whether the command was successful.

When you do this ...

```
sudo apt-get update && sudo apt-get dist-upgrade -y
```... you are making use of that exit status. It's a shorthand way of saying "if the update works, do the upgrade, otherwise do nothing".

Wouldn't you want an exit code in your script? Wasn't that the idea?

```
...
else
    echo "Input [SIZE=2]E[/SIZE]rror [SIZE=2]Q[/SIZE]uitting..."
    **[COLOR=Red]exit 1[/COLOR]**
fi

```How about a prompt like "[U]pgrade or [C]lean?" Then take the letters 'U' and 'C' instead of numbers 1 and 2?

Yes I'm aware of that. I was comparing my usage to my friends usage. I'm not sure exactly if he is planing to use this with something else or just to place in his path or something.

Yes and no. I don't really write scripts myself and normally just hand type the commands ( find it fun). I'm more of an average user not somebody who does a lot of administration stuff or tons of coding or what not. The script was for a friend that emailed me as he was learning batch, but was having some issues and thought I'd be of help.

He also replied with another question on using iwconfig to print everything except the eth or lo information, but I'm lost on his question as I'm wondering if he means ifconfig or finding out what's using a network connection. I just emailed him back.

---

### Post by DarkSnake-Kobra on 2013-01-03
BUMP.

And it's ifconfig (incorrectly said ipconfig which is for Windows) that he wants it to print everything except the eth or lo detail

---

