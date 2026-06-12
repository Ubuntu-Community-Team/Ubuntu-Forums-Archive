---
title: "[Shell Script] Spawn multiple konsole windows to execute tasks"
date: 2011-10-25
forum: Programming Talk
---

### Post by GuilhermeBrant on 2011-10-25
Hello everybody,

I'm a Linux as well as a ShellScript beginner. Objectively, I want one script to run several other scripts in parallel with each one runnning in its own konsole window.

To be more descriptive,I have one script that calls other scripts to execute multiple tasks in parallel via SSH :

```

#!/bin/bash
#runeverybody.sh

for i in ${@:3} #iterate the args to see which scripts are being called and run them
do
    case $i in
    
    "0") script0 $1 $2 & #launch script0 with arguments $1 e $2 and so on
	 ;;

    "1") script1 $1 $2 &
	 ;;

    "2") script2 $1 $2 &
	 ;;

    esac
     
done


```

Where each of the scripts are very similar to each other and looks like the following:

```

#!/bin/bash
#script[number].sh

program=$1
folder=$2

ssh user@host << EOI #task1 and task2 are ran inside the ssh session
task1 &
sleep 3 #just to give enough time to task 1 to be ready, since task 2 depends on it
task2
EOI


```

It works fine and I can execute the tasks okay (just to exemplify: in this case, task1 runs one program and task2 runs another program which interacts with the former.)

But, since the tasks keeps running indefinetely, and they output data to the terminal, it would be very handy to keep each of the scripts executing in a separate konsole window, so I can distinguish who is "outputting" what to the screen.

The problem is I have no idea at all on how to do this, and so far I haven't run into any thread which helped me. So I would appreciate if someone could send me any hints on this.

Thanks in advance,
Luiz.

---

### Post by ofnuts on 2011-10-25
> **GuilhermeBrant said:**
> Hello everybody,

I'm a Linux as well as a ShellScript beginner. Objectively, I want one script to run several other scripts in parallel with each one runnning in its own konsole window.

To be more descriptive,I have one script that calls other scripts to execute multiple tasks in parallel via SSH :

```

#!/bin/bash
#runeverybody.sh

for i in ${@:3} #iterate the args to see which scripts are being called and run them
do
    case $i in
    
    "0") script0 $1 $2 & #launch script0 with arguments $1 e $2 and so on
     ;;

    "1") script1 $1 $2 &
     ;;

    "2") script2 $1 $2 &
     ;;

    esac
     
done


```Where each of the scripts are very similar to each other and looks like the following:

```

#!/bin/bash
#script[number].sh

program=$1
folder=$2

ssh user@host << EOI #task1 and task2 are ran inside the ssh session
task1 &
sleep 3 #just to give enough time to task 1 to be ready, since task 2 depends on it
task2
EOI


```It works fine and I can execute the tasks okay (just to exemplify: in this case, task1 runs one program and task2 runs another program which interacts with the former.)

But, since the tasks keeps running indefinetely, and they output data to the terminal, it would be very handy to keep each of the scripts executing in a separate konsole window, so I can distinguish who is "outputting" what to the screen.

The problem is I have no idea at all on how to do this, and so far I haven't run into any thread which helped me. So I would appreciate if someone could send me any hints on this.

Thanks in advance,
Luiz.In KDE, one would use "konsole -e {command}" since the terminal window is the konsole app. It has several useful parameters,  such as starting a new tab instead of a new window. If you are in Gnome, there must be an equivalent.

---

### Post by gsmanners on 2011-10-25
I think in just about any DE you can do a

```
xterm -e whatever.sh
```

so long as the script is the last argument in the list (unless you're using -T or -n of course).

---

### Post by GuilhermeBrant on 2011-11-03
Sorry guys for taking too long to answer. 
It works here under Kubuntu using >  xterm -e command .

I'll look after theses other options to open in newtab instead of new window.

Thank you very much!

Luiz.

---

