---
title: "[SOLVED] Shell Script continue option?"
date: 2008-10-03
forum: Programming Talk
---

### Post by smirnoff76 on 2008-10-03
I have been using ubuntu now for about 2 months and I have just put together my very first script which is simply a script doing an update of the apt source and then installing various software packages finishing off with an autoclean. 

I am wanting to put in the script an option that prompts the user for input basically saying "do you wish to continue, press (Y) for yes and (N) for no)" obviously hitting n would end the script dead and pressing Y would carry it on to the next section of the script i.e. installing the packages, the problem is I dont know how to script the user input part can anyone help??

Thanks in advance

---

### Post by knattlhuber on 2008-10-03
```

echo "Do you wish to continue, press (Y) for yes and (N) for no"
read answer
echo "You chose: $answer"
```

Instead of line 3, you would obviously put an if..then statement

---

### Post by cdenley on 2008-10-03
Something like this?
```

#!/bin/sh
echo -n "input (y/n): "
read INPUT
if [ $INPUT = "yes" -o $INPUT = "y" ]; then
    echo you said yes
else
    echo you said no
fi

```

or you could use zenity
```

#!/bin/sh
zenity --question --text "continue?"
if [ $? -eq 0 ]; then
    echo you said yes
else
    echo you said no
fi

```

---

### Post by geirha on 2008-10-03
If you use bash instead of sh (#!/bin/bash as the first line of the script), you could do something like:

```

read -n1 -p "Sure you want me to do whatever I'm about to do? [y/N] "
[[ [Yy] =~ $REPLY ]] || exit 0

```

The second line's logic is: If the reply from the read command is 'Y' or 'y', do nothing, else exit. So anything but Y and y will exit the script.

Check out the beginners and advanced bash scripting guides at [http://tldp.org](http://tldp.org) . They contain alot of examples.

---

### Post by smirnoff76 on 2008-10-04
Brilliant thanks for the help guys!!

---

