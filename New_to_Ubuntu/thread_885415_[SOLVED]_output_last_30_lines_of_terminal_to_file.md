---
title: "[SOLVED] output last 30 lines of terminal to file"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by PGScooter on 2008-08-10
Hi, how can I output the last 30 lines of a terminal into a file in bash?

thanks

---

### Post by mevets on 2008-08-10
You can use something like:
```

cmd > output.txt

```
But it will be more than the last 30 lines.

---

### Post by tino27 on 2008-08-10
cmd | tail -30 > file

---

### Post by Thingymebob on 2008-08-10
If you wanted the last 30 commands you entered you would do
```

tail -30 ~/.bash_history > *filename*

```

---

### Post by Thingymebob on 2008-08-10
if you wanted the last 30 lines including output
you would start your terminal session with
```

script -a *~/ttylog*

```

which logs everything to a file called ttylog in your home dir

type exit to stop the logging
then
```

tail -30 ~/ttylog > *filename*

```

***Note:*** script logs everything including backspaces and linefeeds anything that manipulates the screen such as vim will output garbage into your log file.

---

### Post by PGScooter on 2008-08-10
I do not understand what ```
cmd
``` is. I do not have that command installed and I could not find it. Any ideas?

thingy-
it seems like a pain to have to do that log thing everytime, but that is a cool method to know. Thanks

---

### Post by Thingymebob on 2008-08-10
cmd would be the command you want to run ie ls , mv rm etc.

---

### Post by PGScooter on 2008-08-10
ahhhh, I see. So that's only if I know what I want to save beforehand. Ok, so thingy, your sol appears to be the only one so far. Thank you.

I just wish that I could automate that scripting, or find a command that can output the whole terminal contents.

---

### Post by Thingymebob on 2008-08-10
so make a bash script that contains:
call it something like logscript
```

#!/bin/bash

if test ! -s "${HOME}/Documents/Logs"
then
  mkdir "${HOME}/Documents/Logs/"
fi

script -a "${HOME}/Documents/Logs/`date "+%m-%d-%y %H;%M.%S"`"

```

make it executable 
```
chmod +x logscript
```

then change the gnome terminal profile to start this script everytime its run 

in a gnome terminal window select
edit > profiles (select default) > edit >title & command

select the run a custom command instead of my shell button
and enter the full path of the logscript script.

This will create a log (time & date stamped) in your home/Documents/Logs folder everytime you start a gnome terminal.

Just remember to clear this folder out regularly

You could create a new profile called logging which you just switch to when you want to log what you're doing

---

### Post by Vivaldi Gloria on 2008-08-10
> **PGScooter said:**
>  or find a command that can output the whole terminal contents.

As explained in post 5, "script" can record terminal. To start recording use:

```
script
```

To stop recording use

```
exit
```

The output is saved to 

```
typescript
```

file in your home folder. Now you can edit that file in an editor of your choice.

---

### Post by PGScooter on 2008-08-10
thingymebob, thanks for all of your help! That will do the trick.

Vivaldi Gloria- thank you as well.

---

