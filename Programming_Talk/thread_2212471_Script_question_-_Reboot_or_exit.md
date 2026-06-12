---
title: "Script question - Reboot or exit?"
date: 2014-03-21
forum: Programming Talk
---

### Post by Korkel on 2014-03-21
Hi,

Got an nice installation script, but got a problem, on the end you must do [Enter] for a reboot or CTRL+C to exit the terminal, but it reboots automatic.
This is the code:
```
echo "Bedankt voor het gebruiken van het installatie script. :)"
read -r -p "Druk op [Enter] om het systeem te herstarten of op CTRL+C om te annuleren..."
sudo reboot
```

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
If you are running that in a windowed terminal, instead of cntrl-c you could instruct the user to close the window.

More elegantly, you can use that read -p to set a variable from input and then an if/then/fi statement to branch to either an "exit" command or a "reboot" command, depending on the response. BTW, if you want a normal user to be able to run this without entering a password you'll have to exempt it in etc/sudoers.

And another BTW: You've taught me something. I didn't know there WAS a reboot command. I've been using "shutdown -r now".

---

### Post by oldos2er on 2014-03-21
Moved to Programming Talk.

---

### Post by Korkel on 2014-03-22
> **Dreamer Fithp Apprentice said:**
> If you are running that in a windowed terminal, instead of cntrl-c you could instruct the user to close the window.

More elegantly, you can use that read -p to set a variable from input and then an if/then/fi statement to branch to either an "exit" command or a "reboot" command, depending on the response. BTW, if you want a normal user to be able to run this without entering a password you'll have to exempt it in etc/sudoers.

And another BTW: You've taught me something. I didn't know there WAS a reboot command. I've been using "shutdown -r now".
Hi,

how can I make the variable exactly?

Thank you,
Korkel

---

### Post by steeldriver on 2014-03-22
You could do something like

```

#!/bin/bash

while true; do 
  read -p "Would you like to reboot the system now (Y/N)? " ans
  case "$ans" in
    [yY]*) echo "You chose yes"
    # do something 
    break
    ;;

    [nN]*) echo "You chose no"
    # do something else
    break
    ;;

    *) echo "Oops - try again"
    ;;
  esac
done

```

The while loop isn't strictly necessary - you could decide that everything except 'y/Y/es' means 'no' for example. Another possibility (in bash) is the 'select' statement which basically does the presentation of the choices / looping for you:

```

#!/bin/bash

select action in "reboot" "exit"
do
  case "$REPLY" in

  1) echo "You selected $action"
  # do something
  break
  ;;

  2) echo "You selected $action"
  # do something else
  break
  ;;

  *) echo "Please try again"
  ;;

  esac
done

```

---

### Post by Korkel on 2014-03-22
OK, I don't get it, when I test it in terminal, it closes without any error.

---

### Post by steeldriver on 2014-03-22
... you will need to add whatever actual commands you want to execute in place of the comments

```

# do something

# do something else

```

---

### Post by Korkel on 2014-03-22
Must I keep the # ?

If I got this:
```
#!/bin/bash

while true; do 
  read -p "Would you like to reboot the system now (Y/N)? " ans
  case "$ans" in
    [yY]*) echo "You chose yes"
    # sudo reboot
    break
    ;;


    [nN]*) echo "You chose no"
    # exit
    break
    ;;


    *) echo "Oops - try again"
    ;;
  esac
```

The terminal closes without information.

---

### Post by steeldriver on 2014-03-22
**#** indicates that the rest of the line should be treated as a comment - you need

```

  case "$ans" in
    [yY]*) echo "You chose yes"
[B]    sudo reboot
[/B]    break
    ;;

```

and so on (the **break** is not necessary assuming the reboot executes successfully, but it won't do any harm to leave it there)

---

### Post by Korkel on 2014-03-22
Tried it, but when I open it in terminal closes directly.

---

### Post by steeldriver on 2014-03-22
OK sorry in that case I have no idea how to help you - let's hope someone else steps in with some suggestions

---

### Post by Korkel on 2014-03-22
> **steeldriver said:**
> OK sorry in that case I have no idea how to help you - let's hope someone else steps in with some suggestions
You tried to help me, that is awesome.

Thank you and yes, I hope someone else can give advice.

---

### Post by Dreamer Fithp Apprentice on 2014-03-22
Let's take this a step at a time, learning to walk before running.
> **Korkel said:**
> how can I make the variable exactlyThe general form of "read -p" is```
read -p "Some message to show while paused here." VARIABLE_NAME
```

When the script comes to a line like that it will "read", meaning display the message you put in between the 2 " marks and then pause (which is what "-p" stands for) until the user presses the [enter] key. Whatever is typed during the pause BEFORE the pause is ended by pressing the [enter] key becomes the value assigned to the  variable named at the end of the line. It's customary, but not obligatory, to make the variable name in all caps. Most people find that makes the script a little easier to read and follow. Different scripting languages have different constraints on allowed variable names but if you confine the characters used to letters, underlines (NOT dashes), and numerals, and always make the first character a letter, that should work with bash, tcsh, or sh, and probably any other.

Now, a simple example that does pretty much what you intended with the code you posted:

```


read -p "Press the enter key to reboot or press any other character followed by enter to exit this script without rebooting." ANSWER

if [  "$ANSWER" = "" ]; then
   sudo reboot
fi


```Use the slider in the box above to see the whole line. In this example if the user entered anything at all before pressing the enter key, what they entered becomes the value assigned to the variable ANSWER.  So if he presses the "a" key and tnen the "enter" key, the value assigned to the variable ANSWER becomes "a" and the if statement is "expanded" to ```
[ if "a" = "" ]; then
   sudo reboot
fi
```Since "a" does not equal "", i.e. nothing, the "sudo reboot" is not run and the "fi" closes the "if" and the script procedes to the next command. If the fi is the last line of the script, it simply closes.

If instead, the user simply pressed the enter key without typing anything first the value of ANSWER becomes notning so the if statement is "expanded" to ```
[ if "" = "" ]; then
   sudo reboot
fi
```Since "" does equal "",i.e. nothing = nothing, the "sudo reboot" line is run and the system reboots.

If you want to get fancier, you can enclose the read -p in a  "while loop" and combine 2 negations so that the while keeps starting over until one of them is false. That way you can force the user to pick one of a prescribed set of alternatives explicitly. So for instance, it could keep starting over asking for input again until the user either entered "exit" or "reboot" before the enter and only proceed when ANSWER had one of those words assigned as its value.

If you want to go that way, use a search engine (try startpage.com) to search these topics:
bash while loop examples
bash negating a condition
bash combining conditions
bash string comparison

Also, in a terminal:
man while
man read

============
Small english lesson:
"an expert", not "a expert"
general principle:
"a" before words that SOUND like they begin with a consonant, "an" otherwise
So:
an anvil
a pan
a home
an honorable sentiment (because the "h" is not pronounced)

English is weird. Because England got conquered so many times. The mystery is why so many people wanted a place with awful weather.

---

### Post by Korkel on 2014-03-22
Thanks for the help, it reboots now.. You're awesome! :)

---

