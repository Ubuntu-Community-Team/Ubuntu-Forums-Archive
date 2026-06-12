---
title: "Shell Script Ctrl-D to exit loop"
date: 2009-05-08
forum: Programming Talk
---

### Post by dyous87 on 2009-05-08
I have a bash shell script that I wrote with a loop that randomly picks questions from a specified text file, and asks the user those questions. The user must answer them and the program keeps track of right and wrong answers. This works perfectly, and the script constantly asks the user random questions. 

What I want to make it do is exit from the loop when the user presses "ctrl-d" and then print the user's score.

In somewhat sudo code, this is what I want to be able to do: 

```

if (Ctrl-D is pressed)
 then 
  echo "$username has gotten $right right and $wrong wrong"
  exit 
 fi

```

How can I get an if statement in a shell script to have this type of behaviour.

I would really appreciate any help from anybody.

Thank you,
David

---

### Post by kaibob on 2009-05-08
I don't know how to make the ctrl-d key combination do what you want. There are many alternatives, but their suitability depends on the structure of the shell script. The trap command is one option that appears close to what you want, the primary difference being that it utilizes the ctrl-c key combination:

[http://linux.die.net/man/1/trap](http://linux.die.net/man/1/trap)

By way of example, the following is an endless loop that echo's "This is your score!" when you exit the loop by pressing the ctrl-c key combination:

```
#!/bin/bash

trap "echo ; echo This is your score! ; exit" INT

while true ; do 
read -n 1 -p "Press any key to continue or ctrl-c to exit. "
done
```

As an aside, my inclination would be to build the exit command directly into the shell script without utilizing the trap command or any special key combination, but that's your decision of course.

---

### Post by dyous87 on 2009-05-08
Thanks for your quick response!

I actually ended up figuring it out another way. I did:

```

if echo "$input" | grep -q '^$'
     then 
     echo "$username has gotten $right right and $wrong wrong"
     exit
    fi

```

In case this will ever be of use to anyone else, what this means, is I echoed the user's input, and piped it into grep. If grep found a sole end of line character, which is ^D or in regular expressions '^$' then is would print out the message and exit the script.

Thanks again for your help!
David

---

