---
title: "shell script to install programs"
date: 2007-07-13
forum: Programming Talk
---

### Post by Tea4all on 2007-07-13
I want to make a shell script to ask a question, run a command if y is entered, or move on if n is entered. The commands are sudo apt-get install xxxx.  I only know a little html, and I have tried to Google for the answer.  The answers look to me like fghgfhgfhgfh if x =w gfngfhh.  HELP! :confused:

---

### Post by dhomba on 2007-07-13
what has html to do with that?

so do you want to ask the question via web and then run the script in the server?

---

### Post by cwaldbieser on 2007-07-13
> **dhomba said:**
> what has html to do with that?

so do you want to ask the question via web and then run the script in the server?

I think he is saying that the extent of his programming knowledge is HTML, which doesn't help him understand shell scripting.

---

### Post by jyba on 2007-07-13
A simple version would be...

```
#! /bin/bash

echo "Do you want to install xxxx?"
echo "Press 'y' for yes, or 'n' for no"

read Keypress

if [[ $Keypress == "y" ]]; then
    sudo apt-get install xxxx
fi
```

But the problem with asking the user for input is that they may not give the input that your script expects; they may have the CapsLock key down and accidentally type "Y", or they may misread the instruction and type "yes" causing the script to fail, so it's a good idea to put some error-handling into the script...

```
#! /bin/bash

while true; do
    echo "Do you want to install xxxx?"
    echo "Press 'y' for yes, or 'n' for no"

    read Keypress

    case $Keypress in
        y)
              sudo apt-get install xxxx
              exit
              ;;
        n)
              exit
              ;;
        *)
              #   (If any other key is pressed the 
              #+  script loops back and asks again).
              ;;
    esac
done
```

---

