---
title: "[SOLVED] Undefined zenity progress bar problem"
date: 2008-02-03
forum: Programming Talk
---

### Post by roggo on 2008-02-03
Hello all!

I'm working on a script that will empty "all of my trash cans", meaning the normal user one, the root one, the normal at another drive etc.

The script works, but if someone has some optimization or corrections please do tell me! :)

I am aware of rm -rf and such, but I would want a more graphical way to work with the terminal code, and also I want to learn bash and other stuff...

My problem is that I am unable to add the zenity --progress bar to the script. I have read almost all posts on the internet about the matter and I cannot get it to work. I have it working on my JPEG compression script and it is flawless.

On this script it just pops up and then the script doesn't continue correctly. It says that the "number of files in the trash" is 0 so it goes all the time to the "all trash is empty" part if I have the ```
startup | zenity --progress
``` and works if I just have ```
startup
```

```
#!/bin/bash

gksudo -u root -k -m "Enter root password:" /bin/echo

LOCATIONS=(
"/root/.Trash/"
"/home/USERNAME/.Trash/"
"/media/sda5/.Trash-USERNAME/"
"/media/sda5/.Trash-root/"
)

NUMFILES=0
ALLFILES=0
FILES=()
DIRS=()
LOCNUM=()

IFS="
"

function emptyall {
   for ((i=0;i<${#LOCATIONS[@]};i++)); do
      for FILE in $(sudo find "${LOCATIONS[${i}]}" -type f); do
         sudo rm -f -- "$FILE"
      done
      for FILE in $(sudo find "${LOCATIONS[${i}]}" -depth -type d); do
         if [ "$FILE" != "${LOCATIONS[${i}]}" ]; then
            sudo rmdir -- "$FILE"
         fi
      done
   done
}

function startup {
   for ((i=0;i<${#LOCATIONS[@]};i++)); do
      for FILE in $(sudo find "${LOCATIONS[${i}]}" -type f); do
         (( NUMFILES++ ))
         (( ALLFILES++ ))
      done
      LOCNUM[${i}]="${LOCATIONS[${i}]} ${NUMFILES} file(s)"
      NUMFILES=0
   done
}

startup # | zenity --progress THIS WILL CAUSE IT TO NOT WORK

if [ $ALLFILES -ne 0 ]; then
   zenity --list --width 400 --height 250 --text "Empty Trash folders?" --column "Locations" "${LOCNUM[@]}"
   if [ "$?" -eq "0" ]; then
      emptyall
      zenity --info --text "All trash done!"
   fi
else
   zenity --info --text "Trash already empty!"
fi
```

Anyone able to tell me what is wrong with the script? :confused:

---

### Post by Trumpen on 2008-02-03
When you use pipelines with built-in commands, the shell generally spawns a subshell to execute them. 

Unfortunately any change to a subshell variable is lost when you go back to the upper shell.

Try this:

```
foo=0;
echo $foo;
{ foo=1;echo $foo; } | cat;
echo $foo;

```

---

### Post by roggo on 2008-02-03
> **Trumpen said:**
> When you use pipelines with built-in commands, the shell generally spawns a subshell to execute them. 

Unfortunately any change to a subshell variable is lost when you go back to the upper shell.

Try this:

```
foo=0;
echo $foo;
{ foo=1;echo $foo; } | cat;
echo $foo;

```

Thanks for the info!

Is there anyway to set a global variable that lives through the pipe? Maybe even a hack through simple temp file I/O... Or is there some better way to pipe the zenity in my script to produce the desired effect?

---

### Post by geirha on 2008-02-04
You could use i/o redirection like this:

```

exec 3> >(zenity --progress --pulsate)
startup >&3
exec 3>&-

```

---

### Post by roggo on 2008-02-04
> **geirha said:**
> You could use i/o redirection like this:

```

exec 3> >(zenity --progress --pulsate)
startup >&3
exec 3>&-

```

Thanks!

That worked perfect!

I'm looking now what it exactly means, but can you explain as well? :confused:

EDIT: Found a quite detailed page on I/O redirection -> [http://www.aero.jussieu.fr/services/INFO/documentation/mendel/HTML/io-redirection.html#FDREF](http://www.aero.jussieu.fr/services/INFO/documentation/mendel/HTML/io-redirection.html#FDREF)

---

