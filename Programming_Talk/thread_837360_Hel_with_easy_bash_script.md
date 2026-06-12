---
title: "Hel with easy bash script"
date: 2008-06-22
forum: Programming Talk
---

### Post by Ballena on 2008-06-22
Hi. I want to make a simple Bash script that can 1. start screen 2. attach screen 3. stop screen.

I would probably look something like this

```

if %1 = start
then execute command1
fi

if %1 = stop
then execute command 2
fi

if %1 do not exist
then execute command3
fi

(I assume that %1 refers to the parameter number 1)

```

Is that possible to help. I beg you bash scripiters out there to give me a little push of help :) Thanks!

---

### Post by LaRoza on 2008-06-22
Check out my wiki, and there are guides to shell scripting.

---

### Post by ghostdog74 on 2008-06-23
> **Ballena said:**
> Hi. I want to make a simple Bash script that can 1. start screen 2. attach screen 3. stop screen.

I would probably look something like this

```

if %1 = start
then execute command1
fi

if %1 = stop
then execute command 2
fi

if %1 do not exist
then execute command3
fi

(I assume that %1 refers to the parameter number 1)

```

Is that possible to help. I beg you bash scripiters out there to give me a little push of help :) Thanks!
go to your /etc/rc?, /etc/init.d directory and look at some of the startup scripts to see how its done.

---

### Post by kaibob on 2008-06-23
I'm new to shell scripting but I believe a case statement could be used as discussed in the following site:

[http://www.freeos.com/guides/lsst/ch03sec08.html](http://www.freeos.com/guides/lsst/ch03sec08.html)

The general format would be as shown below with the appropriate start, attach, and stop commands substituted for the echo commands. The variable, $1, is a commandline argument. You could fancy this up with a menu printed to the screen. Give it a try and let us know how things work out or if you need help.

```
#!/bin/bash
case $1 in
"start") echo "Start computer";;
"attach") echo "Attach computer";;
"stop") echo "Stop computer";;
esac
```

---

### Post by _sphinx_ on 2008-06-23
+1 to kaibob
It's $1 and not %1, if you are talking of command line argument.

---

### Post by dtmilano on 2008-06-23
Or, if you assume (and check) that $1 contains start, attach or stop you can try this

> #! /bin/bash

start_computer()
{
 # do start
}

stop_computer()
{
 # do stop
}

attach_computer()
{
 # do attach
}

# main
# check parameters
# ...
${1}_computer


---

### Post by Ballena on 2008-06-27
Thanks for the answers guys! I'm almost there.

```

#!/bin/bash

case $1 in
start)
  echo 'Startning irctor...'
  /home/erikw/.screen-start.sh
  ;;
stop)
   echo 'Stopping irctor...'
   screen -S irctor -X quit
   ;;
**NOTHING**)
   echo 'Attaching irctor...'
   screen -x irctor
   ;;
esac


```

The only problem is that **NOTHING** is suppose to be just nothing which means no parameter/argument at all. How do I achive that? I have really no idea..

Thanks.



Edit.
Maybe you should put everything in a if statement that checks if any arguments exists: but I have no idea about how to make that either :/


Edit 2.
I got some answers on some IRC channels. **NOTHING** shall be replaced with **""** which makes the problems solved!

---

### Post by ghostdog74 on 2008-06-27
> **Ballena said:**
> 
Edit 2.
I got some answers on some IRC channels. **NOTHING** shall be replaced with **""** which makes the problems solved!

you don't want to be just checking "nothing". You check for everything else.
use "*"
eg

```

case $1 in 
"start" ) ...
"stop" ) ...
* ) echo "everything else"
esac

```

---

### Post by geirha on 2008-06-28
You can match an empty string with ""
```

case $1 in
    ...
    "" ) echo "no argument";;
    * ) echo "everything else";;
esac

```

EDIT: Err, didn't catch that EDIT part where you'd actually got the "". Sorry.

---

