---
title: "Bash scripting:  Local script execute function on remote server and return variables"
date: 2017-01-16
forum: Programming Talk
---

### Post by jdh239 on 2017-01-16
First off, I don't have a preference as to using a function or just a command.  Function would be cool though.  I need to create some populated variables (lists) on remote servers in order to execute commands against them.  I can execute the command remotely, but can't get my variables populated.

```


create_lists () {
  for i in $( ls $HOME_DIR | grep ^d | awk '{print $NF}' ); do
    if id $i > /dev/null 2>&1 ; then
      LIST="$LIST $i"
    else
      COMPARELIST="$COMPARELIST $i"
    fi
  done
  export LIST
  export COMPARELIST

  for i in $COMPARELIST; do
    if ! echo $IGNORELIST | grep $i > /dev/null 2>&1  ;then
      GONELIST="$GONELIST $i"
    fi
  done
  export GONELIST
  echo $GONELIST
}


```

I was trying the following command to execute it remotely, but I really need to populate the variables.  I know I could do this all with files, I was just hoping to avoid jumping through all of the hoops.  Unsure if this is even possible (due to security or some other reason):


```

sshpass -p ${ROOT_PW} typeset -f | ssh ${BACKUP_USER}@${SERVER} "$(cat);create_lists"

```

---

### Post by The Cog on 2017-01-16
If it helps, this passes a list across (I'm using passwordless login but that shouldn't matter):
```
~$ a="www xxx yyy zzz"
~$ ssh pi@192.168.0.103 "a='$a' ;  echo \$a"
www xxx yyy zzz
```

---

