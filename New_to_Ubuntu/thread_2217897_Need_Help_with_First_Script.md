---
title: "Need Help with First Script"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by jeremy29 on 2014-04-18
Hello,

I'm trying to write my first script as shown:

#!/bin/bash

echo "Hello World!"
sleep 100

I saved the file and changed permissions to make it executable. I've also added the script directory to my PATH. When I run the script however I'm given the following error:

/home/me/bin/script1: 1: /home/me/bin/script1: &#65279;#!/bin/bash: not found
Hello World!

It runs the script however for some reason it sounds like there is an error on the first line.

Any help would be appreciated.

Jeremy

---

### Post by 23dornot23d on 2014-04-18
Works ok .... is your PATH set up  for /usr/bin

K53SV:~$ chmod u+x test1.sh
K53SV:~$ ./test1.sh
Hello World!

K53SV:~$

K53SV:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

---

### Post by jeremy29 on 2014-04-18
Yes, my PATH includes my usr/bin directory. Like I said, this script will run however I get that message in front of the Hello World
      "1: /home/me/bin/script1: &#65279;#!/bin/bash: not found"

If I include clear in my script before echoing Hellow World I don't see that message but I shouldn't have to do that.

---

### Post by 23dornot23d on 2014-04-18
What happens if you change your first line to

#!/usr/bin/bash

---

### Post by jeremy29 on 2014-04-18
Same result but now it says that usr/bin/bash: not found.

Other scripts I've been experimenting with seem to work fine except for that strange message at the beginning. Not sure if I need to be concerned.

---

### Post by steeldriver on 2014-04-18
Can you show us the outputs of

```

which bash

cat -net /home/me/bin/script1

```

please?

---

### Post by jeremy29 on 2014-04-18
[FONT=arial][SIZE=3]which bash outputs
/bin/bash

[/SIZE][/FONT][FONT=arial]cat -net /home/me/bin/script1 outputs[/FONT]
     1    M-oM-;M-?#!/usr/bin/bash$
     2    $
     3    $
     4    echo "Hello World!"$
     5    sleep 10$
     6    $

---

### Post by 23dornot23d on 2014-04-18
Never realised that - is the editing done in windows then ....... as I just used gedit in linux to do my scripts .......

> 
K53SV:~$ cat -net /home/keith/test1.sh output
     1    #!/bin/bash$
     2    $
     3    echo "Hello World!"$
     4    sleep 100$



[http://unix.ittoolbox.com/groups/technical-functional/unixadmin-l/how-to-remove-mommm-characters-from-a-file-through-unix-ksh-script-4986558](http://unix.ittoolbox.com/groups/technical-functional/unixadmin-l/how-to-remove-mommm-characters-from-a-file-through-unix-ksh-script-4986558)

---

### Post by steeldriver on 2014-04-18
OK so those funny M-oM-;M-? characters probably come from Windows (they're byte order marks, I think)

The script is probably "working" because you are running it using **[FONT=courier new][COLOR=#ff0000]sh [/COLOR]script1[/FONT]** instead of just **[FONT=courier new]script1[/FONT] **- which causes the #! line to be overridden by /bin/sh (usually the dash shell) - please get out of that habit, it causes a lot of confusion.

Try again from scratch using a native Linux editor (gedit / nano / emacs etc.)

---

### Post by jeremy29 on 2014-04-18
I just rewrote this script in gedit and it worked 100% correctly! The original code was copied from a website and pasted into LibreOffice Writer and saved as text. This must be what caused this problem. I'll have to remember to stick with gedit. Thanks so much for your help!

---

### Post by 23dornot23d on 2014-04-18
Glad to see your sorted and it has taught me something new as well ........ 

am aware of control characters getting into things but did not know a quick way to check for them ...... but do now.

Thank you too ......... ;) .... time to mark it as solved .......

and another one with a tick in the box.

---

