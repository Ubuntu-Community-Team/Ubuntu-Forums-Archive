---
title: "Shell: turn arbitrary user input into pre-defined format variable?"
date: 2013-04-29
forum: Programming Talk
---

### Post by Ranko Kohime on 2013-04-29
I'm writing a shell script for automated fine-tuning of new installs.  I've found that I install Ubuntu often enough to warrant a shell script to do all my personalization.  :D

Anyway, I'm trying to ask up front which actions should be taken, then storing those variables in a fixed format.  For example, capital Y would become lower-case y, and likewise for N > n.  I want to store all of these variables as lower-case to simplify.

A problem I'm running into, though, is I can't recall the variable.  Does read store a persistent variable, or one that disappears after the first use?  I would have thought the former, but I'm experiencing the latter, as shown in my test code below.

My first attempt is shown as well, with the case statement, which also doesn't provide a variable I can access later in the script.

```
#!/bin/bash
set -x
        choose_swap_on()
                ( echo -e "\n\t Should we setup a swap file? Y/N: " 
                read -n 1 swap_choose_on
                if [[ $swap_choose_on == Y ]]
                then
                        echo -e "Success"
                else
                        echo -e "Failure"
                fi
                )
        choose_swap_on_case()
                ( echo -e "\n\t Should we setup a swap file? Y/N: "
                read -n 1 swap_choose_on_case
                case $swap_choose_on_case in
                        Y|y) swap_choice='y';;
                        N|n) swap_choice='n';;
                        *) echo -e "Error"
                esac
                )
choose_swap_on;
choose_swap_on_case;
echo -e "The choice was: $swap_choose_on or it was $swap_choose_on_case or it was $swap_choice"
```

I must be doing something wrong, but I can't for the life of me figure out what.

---

### Post by dwhitney67 on 2013-04-29
Your variables are declared local to the functions.  Declare them globally, and then you should be fine.

Or better yet, if you need to install Ubuntu on many systems in the exact same manner, then use a Kickstart file.  Read [here ]("https://help.ubuntu.com/lts/installation-guide/i386/automatic-install.html")for more info.

---

### Post by Vaphell on 2013-04-29
you can change text to lowercase by using var=${var,,} and to uppercase by using var=${var^^}

---

### Post by Ranko Kohime on 2013-04-29
I'm not mass-producing systems, I just have a small collection (currently 3, soon to be 4) of computers that I reinstall more often than is really necessary, due to my changing configuration tastes.

I tried 'export variable=y', but that didn't work, either.  Is there another way of making a variable global?

---

### Post by schragge on 2013-04-29
Just replace parentheses with curly braces in function declarations:
```
choose_swap_on() [COLOR=#ff0000]{[/COLOR]
&#8230;
[COLOR=#ff0000]}[/COLOR]
```

You also may declare variables with *declare -l* to be automatically converted to lowercase on assignment.

---

### Post by Ranko Kohime on 2013-04-29
Ahh, I wasn't aware of the shell contexts.  Now I know.  :)

---

