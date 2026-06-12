---
title: "bash: exit parent process from subprocess"
date: 2010-08-31
forum: Programming Talk
---

### Post by PryGuy on 2010-08-31
Hi everybody!

Let's say we have a script:
```

#!/bin/bash

cantQuit() {
echo $1
exit 1
}

#cantQuit #now it works
CANTQUIT=$(cantQuit "No way out of here!") #now it doesn't
echo "Does not work if you saw me!"
exit 0
```you'll see the 0 exit status if you 'echo $?' after it.

As you see i need to get a variable using a function. I kick it simple here but in my script I check this variable and want to exit if it does not exist in my conf file. As far as I get it the $() or `` syntax starts a child process it exits when it sees 'exit' and it does not affect the main script. I have dug this so far:
```

#!/bin/bash
PID=$(pidof -x $(basename "$0"))

canQuit() {
echo $1
kill $PID
}

CANQUIT=$(canQuit "A way out of here!")
echo "You will not see me!"
exit 0
```But is it kosher?
Thanks in advance!

EDIT: Okay, another solution:```
#!/bin/bash
#Read it here: http://www.linuxjournal.com/content/return-values-bash-functions

getVar() {
  if [ "$2" = "bar" ]; then
    eval $1="'$2'"
  else
    echo "That's wrong!"
    exit 1
  fi
}

getVar FOO "bar"
echo $FOO
exit 0
```

---

