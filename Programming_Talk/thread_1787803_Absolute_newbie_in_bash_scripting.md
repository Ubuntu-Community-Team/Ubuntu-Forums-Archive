---
title: "Absolute newbie in bash scripting"
date: 2011-06-21
forum: Programming Talk
---

### Post by Amez on 2011-06-21
Howdy, everyone!
After a break from the world of scripting, I decided to have some fun with bash.
So, Kubuntu 11.04 at hand, i wrote this piece of code:
```

#!/bin/bash
clear
echo "Welcome to the MegaDrive/Genesis test script!"
echo "Please insert the path for your ROM(S)"
read rom
echo "Verifying if the selected folder exists.." #..theorically. Should i use a pipe here?
echo "..done!"
echo ""
echo "$rom"
echo "Do you want to see the contents for the selected folder? (Type YES or press enter to continue)"
read selection
if ["$selection" == "YES"]; then #If the user types YES the content of the folder is shown
echo""
  cd $rom
dir
fi
echo"" #Else the script keeps on running
echo "Insert the name of the ROM"
read romname
echo "$romname in folder $rom, is that right? (Type YES or press enter to cancel)"
read selection2
if ["$selection" == "YES"]; then
cd $rom
dgen $romname
fi

```Now, I noticed that I do remember kinda [COLOR=Red]absolutely[/COLOR] nothing :(
But that's not a problem, i though, Google is my friend!
SO, i had finally found the syntax for the String comparison, but..
```
./dgentest: line 22: [YES: command not found
```Wich is, indeed, pretty strange: why is bash interpreting it as a command?
Also: how can i make the script check if the folder exists/reprompt it? (I assume there's a for cycle involved, right?)
The whole point of the script was to create another script  (Pretty pointless, I know, but that's the smartest thing i can come with at 22:30 ;)) wich runs the dgen command with the selected rom.
So, i was thinking to do the following:
1. push <nameoftheromhere>
(Now,  can i make nano put some lines of text with a direct approach? The man file says nothing about that..)
2. Write the actual script inside it (Eventually asking the user for parameters (I.E: "Do you want to use OpenGL as renderer? (y/n)")
3. Ask the user for a name to rename the script with

Many thanks in advance,   ;)
Amez

EDIT: On a side note, why i can't use ([http://img35.imageshack.us/img35/2967/angrypandamydeviantidby.jpg](http://img35.imageshack.us/img35/2967/angrypandamydeviantidby.jpg)) as avatar? 
I resized it and it's smaller than 64k!

---

### Post by amauk on 2011-06-21
```
echo "Verifying if the selected folder exists.."
if [ ! -d "$rom" ]; then
    echo "$rom is not a directory"
    exit 1
fi
```

```
echo "$romname in folder $rom, is that right? (Type YES or press enter to cancel)"
read selection2
if ["$selection" == "YES"]; then
cd $rom
dgen $romname
fi

```You're reading into variable **selection[COLOR="Red"]2[/COLOR]**, but testing variable **selection**

---

### Post by Petrolea on 2011-06-21
You may want to read this tutorial on 'test'. 
[http://ss64.com/bash/test.html](http://ss64.com/bash/test.html)

Test is the utility you use in if, but you used [] instead (same thing). Test is a bit different than anything you've been used to. For example: it uses one 'equals' to check for equality when handling strings, or '-eq' flag for comparing numbers.

---

### Post by Amez on 2011-06-21
>  	Code:
 	echo "Verifying if the selected folder exists.." if [ ! -d "$rom" ]; then     echo "$rom is not a directory"     exit 1 fi 
 	Code:
 	echo "$romname in folder $rom, is that right? (Type YES or press enter to cancel)" read selection2 if ["$selection" == "YES"]; then cd $rom dgen $romname fi 
You're reading into variable **selection[COLOR=Red]2[/COLOR]**, but testing variable **selection**
Excellent! Most excellent!
I had forgot the spaces at the end and start of [ ], too!
Now..
Is there a way to enable the autocomplete feature (You know, TAB) in scripts?
Because, for example, if i've a file named The_New_Zealand_Story.bin and i type The_ at the moment of imputing the ROM name, it will fill with blank spaces :(!
Also, can you help me with the file writing issue?
Many thanks!

---

### Post by Amez on 2011-06-21
> **Petrolea said:**
> You may want to read this tutorial on 'test'. 
[http://ss64.com/bash/test.html](http://ss64.com/bash/test.html)

Test is the utility you use in if, but you used [] instead (same thing). Test is a bit different than anything you've been used to. For example: it uses one 'equals' to check for equality when handling strings, or '-eq' flag for comparing numbers.
Uh, I will check it later, that's for sure!
The code is now the following: 
```
#!/bin/bash
clear
echo "Welcome to the MegaDrive/Genesis test script!"
echo "Please insert the path for your ROM(S)"
read rom
echo "Verifying if the selected folder exists.." 
if [ ! -d "$rom" ]; then
echo "$rom is not a directory! Now exiting.."
exit 1
fi
echo "..done!"
echo ""
echo "$rom"
echo "Do you want to see the contents for the selected folder? (Type YES or press enter to continue)"
read selection
if [ "$selection" == "YES" ]; then #If the user types YES the content of the folder is shown
echo""
  cd $rom
dir
fi
echo"" #Else the script keeps on running
echo "Insert the name of the ROM"
read romname
echo "$romname in folder $rom, is that right? (Type YES or press enter to exit)"
read selection2
if [ "$selection2" == "YES" ]; then
cd $rom
echo "Do you want to run the emulator with a new resolution? This feature requires OpenGL (Type YES or press enter to continue)"
read selectiongl
if[ "$selectiongl" == "YES" ]; then
echo "Insert the X resolution (Example: 800)"
read x
echo "Insert the Y resolution (Example: 600)"
read y
dgen -G $xx$y $romname
fi
else
dgen $romname

```
BUT!
```
./dgentest: line 30: syntax error near unexpected token `then'
./dgentest: line 30: `if[ "$selectiongl" == "YES" ]; then'

```
I don't get it. :confused:

---

### Post by geirha on 2011-06-21
The syntax for if requires a space before the following command. See 
```

$ help if
if: if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMANDS; ]... [ else COMMANDS; ] fi
    Execute commands based on conditional.
...snipp...

```
I recommend reading [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) to get to grips with the syntax, and also learn good scripting practices (which none of the other bash guides/tutorials bothers teaching).

---

