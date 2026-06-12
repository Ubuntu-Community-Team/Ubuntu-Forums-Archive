---
title: "I cannot figure out how to make my BASH script end when a key is pressed..."
date: 2011-09-17
forum: Programming Talk
---

### Post by redfox1160 on 2011-09-17
I wanted to write a script that will run the "sensors" command every three seconds until I press a key to make it stop. The only problem I am running into is that I don't know how to detect when a key is pressed.

This is what I have so far:
```
#!/bin/bash
until [ <keypress> ]; do
    sensors
    sleep 3
done

```

---

### Post by karlson on 2011-09-17
> **redfox1160 said:**
> I wanted to write a script that will run the "sensors" command every three seconds until I press a key to make it stop. The only problem I am running into is that I don't know how to detect when a key is pressed.

This is what I have so far:
```
#!/bin/bash
until [ <keypress> ]; do
    sensors
    sleep 3
done

```

Can the key be CTRL-C?

---

### Post by Blasphemist on 2011-09-17
Use read to get the keyboard input and then test the resulting variable. [http://linuxcommand.org/wss0110.php#read](http://linuxcommand.org/wss0110.php#read)

---

### Post by redfox1160 on 2011-09-17
> **Blasphemist said:**
> Use read to get the keyboard input and then test the resulting variable. [http://linuxcommand.org/wss0110.php#read](http://linuxcommand.org/wss0110.php#read)

I don't really know where I would put that... the condition?

---

### Post by karlson on 2011-09-17
> **redfox1160 said:**
> I don't really know where I would put that... the condition?

I am still not clear why not use CTRL-C as an exiting keypress.

Additionally the keyboard input in bash is blocking so if you are waiting for the key input your loop stops so at most you will do 1 iteration.

If you need to have a more sophisticated program to execute something I would suggest using Perl or Python.

---

### Post by redfox1160 on 2011-09-17
> **karlson said:**
> I am still not clear why not use CTRL-C as an exiting keypress.

Additionally the keyboard input in bash is blocking so if you are waiting for the key input your loop stops so at most you will do 1 iteration.

If you need to have a more sophisticated program to execute something I would suggest using Perl or Python.

I don't really want to use CTRL-C, I'll probably just use Python.

---

### Post by erind on 2011-09-17
Here is a shell function that might do what you're after:

```
readOne () {
tput smso
tput rmso
oldstty=`stty -g`
stty -icanon -echo min 1 time 0
dd bs=1 count=1 >/dev/null 2>&1
stty "$oldstty"
echo
}
```taken from:
[http://www.unix.com/unix-dummies-questions-answers/3197-making-sh-wait-user-input.html](http://www.unix.com/unix-dummies-questions-answers/3197-making-sh-wait-user-input.html)

And this link has an example of the above function:
[http://www.unix.com/shell-programming-scripting/59605-trap-key-press-script.html](http://www.unix.com/shell-programming-scripting/59605-trap-key-press-script.html)

---

### Post by Blasphemist on 2011-09-17
I happened to have a writing shell scripts page open on a tab when I first saw this question and had only looked at it a bit. Still, when I looked about this it seemed it would work. I just looked again and I still think it will. Please refer to this from the link I provided before. It even uses the 3 seconds you prefer.
> The read command also takes some command line options. The two most interesting ones are -t and -s. The -t option followed by a number of seconds provides an automatic timeout for the read command. This means that the read command will give up after the specified number of seconds if no response has been received from the user. This option could be used in the case of a script that must continue (perhaps resorting to a default response) even if the user does not answer the prompts. Here is the -t option in action:

#!/bin/bash

echo -n "Hurry up and type something! > "
if read -t 3 response; then
    echo "Great, you made it in time!"
else
    echo "Sorry, you are too slow!"
fi

---

### Post by redfox1160 on 2011-09-17
> **Blasphemist said:**
> I happened to have a writing shell scripts page open on a tab when I first saw this question and had only looked at it a bit. Still, when I looked about this it seemed it would work. I just looked again and I still think it will. Please refer to this from the link I provided before. It even uses the 3 seconds you prefer.

It doesn't seem to be working (maybe I'm doing something wrong?). When I run the code, and hit a key, it runs everything again, instead of breaking out of the loop:

```
#!/bin/bash
key=
while [ $key -e  ]; do
    sensors
    echo "Press any key to quit"
    read -t 3 key
done

```

---

### Post by karlson on 2011-09-17
> **redfox1160 said:**
> It doesn't seem to be working (maybe I'm doing something wrong?). When I run the code, and hit a key, it runs everything again, instead of breaking out of the loop:

```
#!/bin/bash
key=
while [ $key -e  ]; do
    sensors
    echo "Press any key to quit"
    read -t 3 key
done

```
```
#!/bin/bash
key=""
while [ "X$key" != "Xq" ]; do
    sensors
    echo "Press any key to quit"
    read -t 3 key
done

```

---

### Post by redfox1160 on 2011-09-17
> **karlson said:**
> ```
#!/bin/bash
key=""
while [ "X$key" != "Xq" ]; do
    sensors
    echo "Press any key to quit"
    read -t 3 key
done

```

This only works if I type "q" and then press enter. Also, What do the X's do? Thanks for all the help!

---

### Post by slavik on 2011-09-17
are you really sure ^C is unacceptable?

---

### Post by redfox1160 on 2011-09-17
> **slavik said:**
> are you really sure ^C is unacceptable?

I can use ^C to end the program, but I wanted the ability to use any key. Sorry if I was confusing.

---

### Post by Blasphemist on 2011-09-17
> **erind said:**
> Here is a shell function that might do what you're after:

```
readOne () {
tput smso
tput rmso
oldstty=`stty -g`
stty -icanon -echo min 1 time 0
dd bs=1 count=1 >/dev/null 2>&1
stty "$oldstty"
echo
}
```taken from:
[http://www.unix.com/unix-dummies-questions-answers/3197-making-sh-wait-user-input.html](http://www.unix.com/unix-dummies-questions-answers/3197-making-sh-wait-user-input.html)

And this link has an example of the above function:
[http://www.unix.com/shell-programming-scripting/59605-trap-key-press-script.html](http://www.unix.com/shell-programming-scripting/59605-trap-key-press-script.html)
I ran the script from the link at it does wait for a press to exit and keeps looping until that happens. I thought this might be within my limited skills to figure out but I now know I'd have to spend more time than I have right now. I don't yet understand just how this script works but it is what you want you'd just have to put your task in the loop. The other simpler answers may also work too, I haven't tested any others.

---

### Post by redfox1160 on 2011-09-17
> **Blasphemist said:**
> I ran the script from the link at it does wait for a press to exit and keeps looping until that happens. I thought this might be within my limited skills to figure out but I now know I'd have to spend more time than I have right now. I don't yet understand just how this script works but it is what you want you'd just have to put your task in the loop. The other simpler answers may also work too, I haven't tested any others.

I was able to get it working using that code, but I'm not sure how it works. If anyone could explain it to me, I would be grateful. Thanks!

---

### Post by redfox1160 on 2011-09-17
This is my code currently:
```

#!/bin/sh

echo here

while : ; do
  sleep .5
  sensors
  echo ; echo ; echo ; echo
  tput smso
  echo "Press any key to return \c"
  tput rmso
  echo
done &

main=$!
echo "# main is $main" >&2

oldstty=`stty -g`
stty -icanon -echo min 1 time 0
dd bs=1 count=1 >/dev/null 2>&1
stty "$oldstty"
echo

kill $main

```

I changed the time to .5 seconds so that it updates quicker. Also, the line ```
echo ; echo ; echo ; echo
``` is only there to provide correct spacing on my monitor.

If anyone knows what this code does, and can explain it to me, I would be grateful:
```
while : ; do

```
```
  tput smso

```
```
  tput rmso

```
```
main=$!
echo "# main is $main" >&2

oldstty=`stty -g`
stty -icanon -echo min 1 time 0
dd bs=1 count=1 >/dev/null 2>&1
stty "$oldstty"
echo

kill $main

```

Thanks for all the help!

---

### Post by redfox1160 on 2011-09-17
> **slavik said:**
> are you really sure ^C is unacceptable?

Actually, ^C does not work in my most recent script:

```
!/bin/sh

echo here

while : ; do
  sleep .5
  sensors
  echo ; echo ; echo ; echo
  tput smso
  echo "Press any key to return \c"
  tput rmso
  echo
done &

main=$!
echo "# main is $main" >&2

oldstty=`stty -g`
stty -icanon -echo min 1 time 0
dd bs=1 count=1 >/dev/null 2>&1
stty "$oldstty"
echo

kill $main



```

---

