---
title: "Shell menu: returning to menu if a function fails."
date: 2011-03-15
forum: Programming Talk
---

### Post by Ranko Kohime on 2011-03-15
I'm building a menu for my frequently accessed CLI commands, and I'm trying to work it out so that if a function fails where there were several in the menu option, it will return to the main menu.

Where the following script calls exit 1, what would I put to cause it to skip the remaining commands in the sequence without exiting the script?

```
     cd /media/IKUSB || { echo -e " "
     	                  echo -e "\t Failed to change directory";
     	                  echo -e "\t Has the Ironkey been mounted & Unlocked?";
                          echo -e " ";
     	                  echo -e "\t Script will exit upon pressing Enter.";
                          echo -e " ";
                          read enterKey;
                          exit 1; };

```

---

### Post by ChipOManiac on 2011-03-15
I think "break" should do the job

---

### Post by Ranko Kohime on 2011-03-15
> **ChipOManiac said:**
> I think "break" should do the job
Unfortunately, that has the effect of exiting the script entirely, the same as exit

---

### Post by ChipOManiac on 2011-03-16
> **Ranko Kohime said:**
> Unfortunately, that has the effect of exiting the script entirely, the same as exit

Just put it under a while loop with "true" or something like that so the main part keeps running until the break... the break will then break the while and continue with the script.. (although I really can't tell what your script is attempting to do from the code specified)

^^^ IGNORE ^^^

---

### Post by ChipOManiac on 2011-03-16
Okay... from the code it seems to me that you have tried to access a folder in /media/ which means it has to be a mount thingy...

I use this script to run my homeworld for linux program :D

```

  if [ -d /media/HOMEWORLD ]
  then
    echo -e "   ISO Mounted\n   Executing HomeWorld 1 SDL\n   "
    sudo ./homeworld0.3 /window /pilotView /device fx /CDpath "/media/HOMEWORLD"
  else
#    echo -n "   CD Not In Drive, Try Again? Y/N?     "
#    read -e ICDReTry
    echo -e "   ISO Not Mounted\n   Mounting Homeworld 1 ISO\n   "
    sudo mkdir /media/HOMEWORLD
    sudo mount -t iso9660 -o loop /psw/homeworld1/homeworld.iso /media/HOMEWORLD
    echo -e "   ISO Mounted\n   Executing HomeWorld 1 SDL\n   "
    sudo ./homeworld0.3 /window /pilotView /device fx /CDpath "/media/HOMEWORLD"
    sudo umount /media/HOMEWORLD
    sudo rmdir /media/HOMEWORLD
  fi

```

that "[FONT=Courier New][ -d /media/HOMEWORLD ][/FONT]" checks  to see if that directory exists...

Have I understood correctly? :(

---

### Post by Ranko Kohime on 2011-03-16
> **ChipOManiac said:**
> Just put it under a while loop with "true" or something like that so the main part keeps running until the break... the break will then break the while and continue with the script.. (although I really can't tell what your script is attempting to do from the code specified)

^^^ IGNORE ^^^
That just might do the trick.  I'll try it out and see how it works.  :)

---

### Post by Ranko Kohime on 2011-03-16
> **ChipOManiac said:**
> that "[FONT=Courier New][ -d /media/HOMEWORLD ][/FONT]" checks  to see if that directory exists...
That -d command looks handy, I think I'll use it in my script.  :)

[COLOR="SeaGreen"]*Ranko Kohime is relatively new to shell-scripting[/COLOR]

---

### Post by Ranko Kohime on 2011-03-19
Ok, here's another question: How does one do a "while" loop based upon the exit code of a command?

Is it
```
while : 0
```
or something else?

Edit: I should probably mention, this is inside of a menu script, so there's a "while" loop controlling the menu.  Would having a "while" loop inside the menu break correctly?  (i.e., break the menu option and return to the main menu?)

Edit 2: Well, I guess the topic implied that already...  :roll:  Shows how much I'm paying attention.  :D

---

