---
title: "Creating password prompts using Bash"
date: 2006-10-02
forum: Programming Talk
---

### Post by BatteryCell on 2006-10-02
Ok so I was writing a script today that requires a user to enter a password.    Now I know about the stty command 
```

stty -echo

```
that makes the typed letters not show up, but I was wondering if there is a way to make asterisks show up instead??

---

### Post by ghostdog74 on 2006-10-02
> **BatteryCell said:**
> Ok so I was writing a script today that requires a user to enter a password.    Now I know about the stty command 
```

stty -echo

```
that makes the typed letters not show up, but I was wondering if there is a way to make asterisks show up instead??

found this on the web, but its ksh:
```

++++++++++++++  START SCRIPT ++++++++++++++
#!/bin/ksh
#Init some stuff...
pass=''
blank='false'

#Main loop executed once for each char typed...
while [ "$blank" != "true" ]
do
  stty raw
  c=`dd bs=1 count=1 2> /dev/null`
  stty -raw

  #Check for a CR.
  if [ -z `echo $c | tr -d "\015"` ]
  then
    blank='true'
  else
    stty echo
    echo "*\c"
    pass=$pass$c
    stty -echo
  fi
done                              
+++++++++++++  END OF SCRIPT ++++++++++++ 

```

---

### Post by BatteryCell on 2006-10-02
Thanks a lot, ok I switched some stuff over and got it working in bash, it works for everything but backspaces which is seem to think is a character.
If anyone has any ideas on how to do that.
```

#!/bin/bash
#Init some stuff...
pass=''
blank='false'

#Main loop executed once for each char typed...
while [ "$blank" != "true" ]
do
  stty -icanon -echo
  c=`dd bs=1 count=1 2> /dev/null`

  #Check for a CR.
  if [ -z `echo $c` ]
  then
   blank='true'
  else
    stty echo
    echo -n "*"
    pass=$pass$c
    stty -echo
  fi
done
stty icanon  echo
echo
echo $pass

```
I think icanon turns off the backspace, but i cant figure out another way to print the asterisk at the same time as typing.

---

### Post by BatteryCell on 2006-10-05
bump

---

