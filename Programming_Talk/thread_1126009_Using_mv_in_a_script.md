---
title: "Using mv in a script"
date: 2009-04-15
forum: Programming Talk
---

### Post by silentrebel on 2009-04-15
Hello I'm trying to write a bash script but I'm not having too much success.
Here is the code for the script I named *tr*:
```
#!/bin/bash
path=$1
path=${path//' '/'\ '}
echo $path
sudo mv $path ~/.local/share/Trash/files
```
Here is the command I used to execute the script:
> tr es\ se
Here is the output:
> es\ se
mv: cannot evaluate `es\\': No file or folder of this type
mv: cannot evaluate `se': No file or folder of this type

Please note that if I remove the 3rd line from the code, the output is as follows:
> es\ se
mv: cannot evaluate `es': No file or folder of this type
mv: cannot evaluate `se': No file or folder of this type

The first line of the output is exactly right; however when I give this to the mv command it doesn't use it properly.  I am sure this file exists in the current directory.
Thank for the help.

---

### Post by ghostdog74 on 2009-04-15
don't name your script tr. tr is a well known command line tool. use double quotes around your variables.

---

### Post by silentrebel on 2009-04-15
Thank you very much, that worked: 
```
#!/bin/bash
sudo mv "$1" ~/.local/share/Trash/files
```
It is a bit weird that I need to state that my one variable is really one argument, but I suppose it could make sense.
What pray-tell does *tr* do (obviously not mine)?

---

### Post by ghostdog74 on 2009-04-15
> **silentrebel said:**
> 
What pray-tell does *tr* do (obviously not mine)?
why don't you do a man tr on your terminal. ( or "info tr" )

---

### Post by Arndt on 2009-04-15
> **silentrebel said:**
> Thank you very much, that worked: 
```
#!/bin/bash
sudo mv "$1" ~/.local/share/Trash/files
```
It is a bit weird that I need to state that my one variable is really one argument, but I suppose it could make sense.
What pray-tell does *tr* do (obviously not mine)?

I think it's a bad idea to hide a 'sudo' inside a script. I find it better to force the user to become root explicitly and then run the script.

As for the actual problem, one variable contains just a piece of text. Depending on its use, it can turn out to be interpreted as several arguments to a command, so you need to force the one-argument interpretation.

---

### Post by silentrebel on 2009-04-15
Fair enough, the sudo definitely should not be there.  Thank you for pointing that out.  However, I have a question on that point: if I use sudo to execute a script, will all the commands in the script be granted super-user privileges ?

I believe I now better understand why the quotation marks are necessary.

[QUOTE=ghostdog74]why don't you do a man tr on your terminal. ( or "info tr" )[/QUOTE]
I would do that if I were at home with my Ubuntu computer; alas, I am not.  I'm perhaps a little too impatient in my curiosity.  I guess I could search it myself (what a novel thought) :P...
Thanks again.

---

### Post by Arndt on 2009-04-15
> **silentrebel said:**
> Fair enough, the sudo definitely should not be there.  Thank you for pointing that out.  However, I have a question on that point: if I use sudo to execute a script, will all the commands in the script be granted super-user privilieges?

You can sudo to other users than root, but, yes, if you sudo to root, the whole script runs as root, and all programs called by it.

There is a distinction between "effective uid" and "real uid", and it may be used to switch back and forth between two ids, but I don't think a shell script can do that. And it seems 'sudo' sets them both to the same thing anyway. The distinction is relevant for setuid programs.

Once you're root, you can of course set the uid to some other user, for example the one you were before.

---

### Post by silentrebel on 2009-04-15
**So, for those interested, here is a recapitulation** for the brilliant script I tried to write that would allow one to *move* files to the trash from the terminal as an alternative to *rm* that completely and irremediably obliterates the specified operand.

Thanks to ghostdog74, we know that this works:
```
#!/bin/bash
sudo mv "$1" ~/.local/share/Trash/files
```
This method was also suggested:
[QUOTE=mb_webguy]```
#! /bin/sh
sudo mv "$@" ~/.local/share/Trash/files
```[/QUOTE]
I believe *tsh* is an unused and catchy script name :P...
Thanks again all.

---

### Post by monkeyking on 2009-04-16
> **ghostdog74 said:**
> why don't you do a man tr on your terminal. ( or "info tr" )

The man page is not really explaining how usefull 'tr' is

Say you had a file containing some strange chars you wanted to delete like ':', then you would do
```

tr -d ':' <yourInFile >yourOutFile

```

Or if you wanted to change all tabs to spaces

```

tr '\t' ' ' <yourInFile >yourOutFile

```

Some people will argue you can do the same with sed,
which is correct.
But for basic stuff sed is quite complicated

---

