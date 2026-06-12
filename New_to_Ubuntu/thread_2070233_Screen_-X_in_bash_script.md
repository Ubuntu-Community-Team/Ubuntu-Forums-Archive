---
title: "Screen -X in bash script"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by a13x1 on 2012-10-12
Hello,

This might be in the wrong place, I apologies if it is. 

I am stuck on this: 

I want to create a new screen, create a folder, pause for 20 seconds, then close the screen.

All the commands need to be run in the that screen.

This is what I have so far:
```

screen -dmS $SCREENNAME 
screen -X $SCREENNAME touch $FILE_PATH $SCREENNAME    
screen -X $SCREENNAME sleep 20
screen -X $SCREENNAME rm $FILE_PATH$SCREENNAME

```For some reason its not putting the commands into the screen.

Thanks for your time in advance.

AI

---

### Post by Lars Noodén on 2012-10-12
Would the following work?

```

screen -dmS $SCREENNAME 
screen -x $SCREENNAME -X stuff touch $FILE_PATH$SCREENNAME $'\015'
screen -x $SCREENNAME -X stuff sleep 20 $'\015'
screen -x $SCREENNAME -X stuff rm $FILE_PATH$SCREENNAME $'\015'

```

---

