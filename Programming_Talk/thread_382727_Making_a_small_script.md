---
title: "Making a small script"
date: 2007-03-12
forum: Programming Talk
---

### Post by kwaanens on 2007-03-12
Hi

I'm trying to make a small, easy script that my girlfriend can use to update her iRiver E10 without the use of a console. For now, it looks like this:

```
#!/bin/sh

# Enter the player directory
{
if $(zenity --question --text="Vil du oppdatere spilleren din?" --title="Bekreft")
then
	cd /media/E10


# Update player using pmplib and the "update" option
	easypmp -u

# Exit to home-folder. (The player will not unmount if you stay in its dir)
	cd ~

# Unmount the player, making it ready to unplug
eject /media/E10 | zenity 	--info \
				--title 'Oppdatering utført' \
				--text 'Spilleren din er nå oppdatert og klar til bruk'

fi
}
```

I'm trying to find out what lines to put in to make the script exit with an error on all actual errors. The errors that are possibe are:
- /media/E10 isn't present (it "soft mounts" every time the player is plugged in)
- easypmp -u returns: "ERROR: Failed to find a player (0x80000001)"
- eject fails for some reason

Of course, when it runs now, it hits an error and just continues.

Should be easy enough, but I obviously know nothing about this...
Thanks!

- Ketil

---

### Post by Mr. C. on 2007-03-12
Each program returns with an exit status, that the shell passes on to your.

Evaluate $? for that error code:

```
someprog
returnstatus=$?

if [ $returnstatus = 0 ] ; then
    echo Error
else
    echo "success"
fi
```

This should give you the idea.

MrC

---

### Post by tomchuk on 2007-03-12
or just:
```

someprog || echo "Error" ; exit 1

```

---

### Post by kwaanens on 2007-03-12
Thanks! I have no access to the player right now, but I'm hoping that this now works how it should:

```
#!/bin/sh

# Enter the player directory
{
if $(zenity --question --text="Du har startet et EasyPMP-skript.\nVil du oppdatere spilleren din?" --title="Bekreft")
then
	cd /media/E10 || echo $(zenity --error --text="/media/E10 finnes ikke.\nSjekk at spilleren er tilkoblet eller snakk med Ketil." --title="Feil") ; exit 1


# Update player using pmplib and the "update" option
easypmp -u || echo $(zenity --error --text="Kommandoen easypmp -u feilet.\nAvslutter!" --title="Feil!") ; exit 1

# Exit to home-folder. (The player will not unmount if you stay in its dir)
cd ~  || echo $(zenity --error --text="Kan ikke navigere til hjemmemappe.\nDette kan umulig stemme..." --title="Umulig feil") ; exit 1

# Unmount the player, making it ready to unplug
eject /media/E10 || echo $(zenity --error --text="Kan ikke avmontere spilleren.\nDu må slå av maskinen før du plugger ut spilleren." --title="Feil") ; exit 1 

# Bye-message
zenity 	--info --title "Oppdatering utført" --text "Spilleren din er nå oppdatert og klar til bruk!"

fi
}
```

---

### Post by kwaanens on 2007-03-13
> **tomchuk said:**
> or just:
```

someprog || echo "Error" ; exit 1

```

I tried this. It seems to exit at first "; exit 1" even though it executed "someprog" correctly. Now, if I remove "exit 1" from each line I've put it in, it runs like it should if avereything is successful. If something goes wrong, it still runs the next command, and the next, and the next.

What exactly does "; exit 1" mean?

Sorry, I'm ignorant.

- Ketil

---

### Post by LotsOfPhil on 2007-03-13
I don't think the example that has been posted is "right."

Each program returns an exit status. 0 means all is well, 1 means there is an error (in general, I think there is more to it than this).

command1 || command 2     means do command1, if you get an error, do command2.

It is the opposite of command1 && command2    which means do command1, then do command2 if command1 worked okay (i.e., exited with status 0).

---

### Post by kwaanens on 2007-03-13
I realise this.
The problem is, I want the script to exit on the second condition. Only the first conditions should make the script progress.
I've been fiddling around with this for quite some time now. It works when the player is plugged in, but it does not exit when something doesn't work. All the 2nd conditions run, but no exit. Why?

Here I am now:

```
#!/bin/sh

{
# Start with an introductory message, in case user started by mistake.
if $(zenity --question --text="Du har startet et EasyPMP-skript.\nVil du oppdatere spilleren din?" --title="Bekreft")
then

# Enter the player directory
cd /media/E10 || echo $(zenity --error --text="/media/E10 finnes ikke.\nSjekk at spilleren er tilkoblet eller snakk med Ketil." --title="Feil") exit

# Update player using pmplib and the "create" option. "Update"-function segfaults for some reason.
easypmp -c || echo $(zenity --error --text="Kommandoen easypmp -u feilet.\nAvslutter!" --title="Feil!") exit

# Exit to home-folder. (The player will not unmount if you stay in its dir)
cd ~  || echo $(zenity --error --text="Kan ikke navigere til hjemmemappe.\nDette kan umulig stemme..." --title="Umulig feil") exit

# Unmount the player, making it ready to unplug
eject /media/E10 || echo $(zenity --error --text="Kan ikke avmontere spilleren.\nDu må slå av maskinen før du plugger ut spilleren." --title="Feil") exit

# Bye-message
zenity 	--info --title "Oppdatering utført" --text "Spilleren din er nå oppdatert og klar til bruk!"

fi
}
```

Realised that putting in an "& " in front of the "exit" does actually stop the script, but it appears to not stop the process completely:

```
$ e10update
cd: 24: can't cd to /media/E10
ketil@12inch-laptop:~$ 
[empty line with the cursor flashing as if a new script/program is running]

```

It looks to me that the script should be stopped in a different manner. Edit: Also this stops the script if the player's actually plugged in :(

I've googled about 25 times with different criteria, but I find nothing that helps me get through this. Most guides mention || and && in 1 paragraph, but say nothing about how you issue two commands as the 2nd condition.

Thanks for you help!

- ketil

---

### Post by LotsOfPhil on 2007-03-13
& makes it run in the background. That's definitely not it.

I think you have summed it up pretty well: "How do you run more than one command after || or && ?"

---

### Post by Mr. C. on 2007-03-13
> **LotsOfPhil said:**
> 
I think you have summed it up pretty well: "How do you run more than one command after || or && ?"

Don't.  It makes the code too difficult to follow and is error prone.  If-then-else should be used instead.

MrC

---

### Post by s1ightcrazed on 2007-03-13
When shell scripting properly and working around errors, you have to worry about several types of errors. Your script itself may error out (for instance if someone picks the wrong option on a read, you may wish to return an error code/exit status). Your script may also use outside utilities that ALSO may return error codes of their own, and you'll need to prepare for these in order to exit your script properly. 

As Mr. C noted, $? will show the error code of the last command run - you may want to incorporate this so that you can assign a variable to the exit status of the utilities run in the script, and then parse these to determine if the script itself should also exit. 

For instance:

```
easypmp -u
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ]; then
    exit 1
fi
```

is one way to do it. You run your command, save it's exit status to the variable EASY_EXIT, check the exit status with an if statement, and if it's anything other than 0 (i.e. anything other than successful completion) then you exit your script with exit code 1. 

The shorter way to do it is:

```
if [[ $(easypmp -u)$? != 0 ]]; 
    then exit 1
fi
```

Either way will work fine. The second method just avoids a needless variable assignment. 

Without error checking such as this, an outside utility in your script may fail, but the script itself will keep going. 

Enjoy!

---

### Post by kwaanens on 2007-03-14
Thanks for this!

I now have:

```
#!/bin/sh

{
# Start with an introductory message, in case user started by mistake.
if $(zenity --question --text="Du har startet et EasyPMP-skript.\nVil du oppdatere spilleren din?" --title="Bekreft")
then

# Enter the player directory
cd /media/E10
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ]; then
    exit echo $(zenity --error --text="/media/E10 finnes ikke.\nSjekk at spilleren er tilkoblet eller snakk med Ketil." --title="Feil")
fi

# Update player using pmplib and the "create" option. "Update"-function segfaults for some reason.
easypmp -c
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ];then 
    exit echo $(zenity --error --text="Kommandoen easypmp -u feilet.\nAvslutter!" --title="Feil!")
fi

# Exit to home-folder. (The player will not unmount if you stay in its dir)
cd ~
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ]; then
    exit echo $(zenity --error --text="Kan ikke navigere til hjemmemappe.\nDette kan umulig stemme..." --title="Umulig feil")
fi

# Unmount the player, making it ready to unplug
eject /media/E10
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ]; then
    exit echo $(zenity --error --text="Kan ikke avmontere spilleren.\nDu må slå av maskinen før du plugger ut spilleren." --title="Feil")
fi

# Bye-message
zenity 	--info --title "Oppdatering utført" --text "Spilleren din er nå oppdatert og klar til bruk!"

fi
}

```

But when it exits, I get: 
```
$ e10update2 
cd: 40: can't cd to /media/E10
exit: 40: Illegal number: echo 
```

It appears to work, although I only tried without the player, and once after 
mkdir /media/E10 to see if it got past that point (which it did).
I'm assuming that the script is still not OK, so how do I easily output the zenity commands?

- Ketil

########################################

EDIT: See script in post #14 for the correct syntax!

#######################################

---

### Post by kwaanens on 2007-03-14
It now works :)

Here it is, if someone needs it:

```

#!/bin/sh

{
# Start with an introductory message, in case user started by mistake.
if $(zenity --question --text="Du har startet et EasyPMP-skript.\nVil du oppdatere din iRiver E10?" --title="Bekreft")
then

# Enter the player directory
cd /media/E10
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ]; then
    exit echo $(zenity --error --text="/media/E10 finnes ikke.\nSjekk at spilleren er tilkoblet eller snakk med Ketil." --title="Feil")
fi

# Update player using pmplib and the "create" option. "Update"-function segfaults for some reason.
easypmp -c | zenity --progress --pulsate --auto-close --title="Oppdaterer" --text="Oppdaterer iRiver E10...\nVennligst vent til operasjonen er ferdig."
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ];then 
    exit echo $(zenity --error --text="Kommandoen easypmp -u feilet.\nAvslutter!" --title="Feil!")
fi

# Exit to home-folder. (The player will not unmount if you stay in its dir)
cd ~
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ]; then
    exit echo $(zenity --error --text="Kan ikke navigere til hjemmemappe.\nDette kan umulig stemme..." --title="Umulig feil")
fi

# Unmount the player, making it ready to unplug
eject /media/E10
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ]; then
    exit echo $(zenity --error --text="Kan ikke avmontere spilleren.\nDu må slå av maskinen før du plugger ut spilleren." --title="Feil")
fi

# Bye-message
zenity 	--info --title "Oppdatering utført" --text "Spilleren din er nå oppdatert og klar til bruk!"

fi
}

```

- Ketil



########################################

EDIT: Use correct syntaxed script in post #14.

########################################

---

### Post by LotsOfPhil on 2007-03-14
I am surprised that code works. I think your if loops should look like this (for example):
```

cd /media/E10
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ]; then
    echo $(zenity --error --text="/media/E10 finnes ikke.\nSjekk at spilleren er tilkoblet eller snakk med Ketil." --title="Feil")
    exit 1
fi

```

echo first, then exit 1 on the next line

---

### Post by kwaanens on 2007-03-14
Well, what can I say :)
Thanks for the corretion!

Here it is in all its "glory" (still, if anyone wants to use it):

```

#!/bin/sh

{
# Start with an introductory message, in case user started by mistake.
if $(zenity --question --text="Du har startet et EasyPMP-skript\n\nVil du oppdatere din iRiver E10?" --title="Bekreft")
then

# Enter the player directory
cd /media/E10
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ]; then
    echo $(zenity --error --text="/media/E10 finnes ikke!\n\nSjekk at spilleren er tilkoblet eller snakk med Ketil" --title="Feil")
    exit 1
fi

# Update player using pmplib and the "create" option. "Update"-function segfaults for some reason.
easypmp -c | zenity --progress --pulsate --auto-close --title="Oppdaterer" --text="Oppdaterer iRiver E10...\n\nVennligst vent til operasjonen er ferdig"
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ];then 
    echo $(zenity --error --text="Kommandoen easypmp -u feilet\n\nAvslutter!" --title="Feil!")
    exit 1
fi

# Exit to home-folder. (The player will not unmount if you stay in its dir)
cd ~
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ]; then
    echo $(zenity --error --text="Kan ikke navigere til hjemmemappe\n\nDette kan umulig stemme..." --title="Umulig feil")
    exit 1
fi

# Unmount the player, making it ready to unplug
eject /media/E10
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ]; then
    echo $(zenity --error --text="Kan ikke avmontere spilleren\n\nDu må slå av maskinen før du plugger ut spilleren" --title="Feil")
    exit 1
fi

# Bye-message
zenity 	--info --title "Oppdatering utført" --text "Spilleren din er nå oppdatert og klar til bruk!"

fi
}

```

Save script as /usr/bin/e10update 
$ sudo chmod +x /usr/bin/e10update

Make a shortcut anywhere you'd like, and you're good to go.

Thanks for all help!

- Ketil

---

### Post by kwaanens on 2007-03-15
Sorry to be bugging you all with this...
Still, I have a problem, in this part:

```
# Update player using pmplib and the "create" option. "Update"-function segfaults for some reason.
easypmp -c | zenity --progress --pulsate --auto-close --title="Oppdaterer" --text="Oppdaterer iRiver E10...\n\nVennligst vent til operasjonen er ferdig"
EASY_EXIT=$?
if [ $EASY_EXIT != 0 ];then 
    echo $(zenity --error --text="Kommandoen easypmp -u feilet\n\nAvslutter!" --title="Feil!")
    exit 1
fi
```

It appears that EASY_EXIT=$? here refers to the Zenity progress-command, and that of course never fails. How do I define "easypmp -c" as the successful-or-not--process in this script?

- Ketil

---

### Post by LotsOfPhil on 2007-03-15
Following the suggestion from post 10:
```

if [[ $(easypmp -c)$? != 0 ]]; then
    echo $(zenity --error --text="Kommandoen easypmp -u feilet\n\nAvslutter!" --title="Feil!")
    exit 1
fi

```

I am not sure if this will run easypmp -c twice, though.

---

### Post by kwaanens on 2007-03-15
> **LotsOfPhil said:**
> Following the suggestion from post 10:
```

if [[ $(easypmp -c)$? != 0 ]]; then
    echo $(zenity --error --text="Kommandoen easypmp -u feilet\n\nAvslutter!" --title="Feil!")
    exit 1
fi

```

I am not sure if this will run easypmp -c twice, though.

Yes, it did (attempt to) run it twice.
And it didn't return the error message it should either... :)
Back to the drawing board. Thanks though!

- Ketil

---

### Post by tomchuk on 2007-03-15
> **LotsOfPhil said:**
> I don't think the example that has been posted is "right."

Oops, sorry, I tacked the exit on without thinking. What I usually do is define a die function and use it like so:

```

#!/bin/sh

die() {
    echo ${1}
    exit 1
}

someprog || die "Couldn't execute someprog"

```

---

### Post by kwaanens on 2007-04-03
I finally made the script do what it's supposed to do. Ignore the former posts, it's here: [http://anotherugly.wordpress.com/2007/04/03/iriver-e10-update-script-for-linux/](http://anotherugly.wordpress.com/2007/04/03/iriver-e10-update-script-for-linux/)

Thanks for your help!

- Ketil

---

