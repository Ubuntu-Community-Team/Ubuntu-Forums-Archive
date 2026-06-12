---
title: "YAD Installer Tool"
date: 2014-08-26
forum: Programming Talk
---

### Post by macstar on 2014-08-26
i am currently discovering yad and would like to know if it's possible to create a software installer tool with it.
basically i am thinking of the following one:
[IMG]http://i.imgur.com/WFfGFfc.jpg[/IMG]

multiple checkboxes and before i click on install the script should ask the values saved in each checkbox.
the installation itself i would like to do depending on the software either with cmd="sudo apt-get install program1" or by simply executing a script in the program directory with "sudo ./script1.sh"

by now my code looks like the following:

```

#!/bin/bash
#YAD Dialog 
yad --title="Software Installer" --text="Install Software" --form --field="Program1:CHK" --field="Software 2:CHK" --field="Some Addon pack:CHK" --field="And More:CHK" --button="Install" --button="Exit" --image="logo.png"
#Save Return value
ret=$?

if [ $ret = 0 ] 
then            
./jd1.sh          

fi

if [ $ret = 1 ] 
then            
./jd.sh          


else            
 exit 2      
fi 



```

i know the code below only checks and executes the buttons i have pressed, what i need now is a code which also takes care of the checkboxes. google was no help for me and i am not very good with coding yet so could anyone please help me out?

---

### Post by ofnuts on 2014-08-26
Yad seems to print out a string that indicates what was done, so you typically get the string in a bash variable. See examples [here](https://code.google.com/p/yad/wiki/Examples).

---

### Post by macstar on 2014-08-26
@ofnuts

i have checked this before, yet it does not seem to help, because there is no example on how checkboxes are handled and that's what i am after.

---

### Post by Habitual on 2014-08-26
I have this nugget stashed on my Dorkblog:
```
#!/bin/bash
com=`yad --title=Blitzstart --height=400 --list --separator=" & "  --checklist --column="1/0" --column=befehl --column=Programm "" "xmaple"  "maple 12" "" "jdown" "JDownloader" "" "firefox" "Firefox" ""  "rhythmbox" "Rhythmbox" "" "deluge" "Deluge" "" "pidgin" "Pidgin" ""  "nautilus" "Filemanager" "" "eclipse" "Eclipse" "" "checkgmail" "Gmail"  "" "xchat" "Xchat" "" "skype" "Skype"`
eval "$com"
```

Seems to execute Skype and XChat when I select them.
I think what you're after is "eval"

Have fun with it!

---

### Post by Vaphell on 2014-08-26
checkboxes return TRUE/FALSE strings in order, glued together with | by default

I'd go with something like this
```
#!/bin/bash

menu=( "Program1|install_p1"
       "Software 2|install_p2"
       "Some Addon pack|install_p3"
       "And More|some_stuff" )

yad_opts=( --form
           --title="Software Installer"
           --text="Install Software"
           --image="logo.png"
           --button="Install" --button="Exit" )

for m in "${menu[@]}"
do
  yad_opts+=( --field="${m%|*}:CHK" )
done

IFS='|' read -ra ans < <( yad "${yad_opts[@]}" )

for i in "${!ans[@]}"
do
  if [[ ${ans[$i]} == TRUE ]]
  then
    m=${menu[$i]}
    echo "selected: ${m%|*} (${m#*|})"
  fi
done
```


> Seems to execute Skype and XChat when I select them.
I think what you're after is "eval"


eval is kinda unnecessary, because you could just do something like

```
while read com
do
  ${com%|} &
done < <( yad ... --print-column=2 )
```

---

### Post by macstar on 2014-08-26
> **Habitual said:**
> I have this nugget stashed on my Dorkblog:
```
#!/bin/bash
com=`yad --title=Blitzstart --height=400 --list --separator=" & "  --checklist --column="1/0" --column=befehl --column=Programm "" "xmaple"  "maple 12" "" "jdown" "JDownloader" "" "firefox" "Firefox" ""  "rhythmbox" "Rhythmbox" "" "deluge" "Deluge" "" "pidgin" "Pidgin" ""  "nautilus" "Filemanager" "" "eclipse" "Eclipse" "" "checkgmail" "Gmail"  "" "xchat" "Xchat" "" "skype" "Skype"`
eval "$com"
```

Seems to execute Skype and XChat when I select them.
I think what you're after is "eval"

Have fun with it!

thank you a LOT! ;)
this looks nearly perfect now yet simple. it executes the apt-get install command and also if i redirect to an marked as executable  .sh file in the same directory.

a small issue still: i need to insert the command in between the 2nd "", looks now like:
```

#!/bin/bash
com=`yad --title=Blitzstart --height=400 --list --separator=" & "  --checklist --column="1/0" --column=befehl --column=Programm "" "xmaple"  "maple 12" "" "Kate" "sudo apt-get install kate" "kate" "firefox" "Firefox" ""  "rhythmbox" "Rhythmbox" "" "deluge" "Deluge" "" "pidgin" "Pidgin" ""  "nautilus" "Filemanager" "" "eclipse" "Eclipse" "" "checkgmail" "Gmail"  "" "xchat" "Xchat" "" "skype" "Skype"`
eval "$com"

```

and in the gui now it reads Kate and in the 2nd column it reads "sudo apt-get install kate" .... the 3rd "" seem to do nothing here.
any fix for this?

@Vaphell

i think i kinda understand your script, but the thing is: install_p1.... what does it do?
i saved a install_p1 file, made it executable, wrote in sudo apt-get install kwrite no luck. it just always returns the command in () in konsole.
if i understand the code right, it just echoes what i have selected but this is not ennough. i would want the script to check what i have selected and then execute the scripts and/or commands.

---

### Post by Vaphell on 2014-08-26
> i think i kinda understand your script, but the thing is: install_p1.... what does it do?

nothing of value at the moment, but it could be used to store a command or whatever

```
menu= ( "Program 1|sudo apt-get install program1" ... )

...
...

    m=${menu[$i]}
    name=${m%|*}
    cmd=${m#*|}
    echo "selected: $name ($cmd)"
    $cmd



```

---

### Post by macstar on 2014-08-26
@[                                                      [IMG]http://ubuntuforums.org/customavatars/avatar504341_4.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=504341")                                                                                     [**[COLOR=#000000]Habitual[/COLOR]**]("http://ubuntuforums.org/member.php?u=504341")

i think i have figured out what was wrong with your script:
```
#!/bin/bash
com=`yad --title=AddonPack 0.1 --text='Installs important Addon Software' --height=500 --width=800 --image="logo.png" --list --separator=" & "  --checklist --column="1/0" --column=Programm --column=test --column=Befehl "xample" "xmaple tool" "sudo apt-get install maple 12" "" "Kate" "Kate TextEditor" "sudo apt-get install kate"`
eval "$com"
```

see the difference? i added an column called test to it, so now i have the program name, the program description and the command itself (i still would like to have the command hidden but still executed) but so far this is closest to what i want and probably will do the job. 
thank you a lot so far!!!

for more ideas i am still open ofc ;)

i think  i was too fast... have added a third program to test
```

#!/bin/bash
com=`yad --title=AddonPack 0.1 --text='Installs important Addon Software' --height=500 --width=800 --image="logo.png" --list --separator=" & "  --checklist --column="1/0" --column=Programm --column=test --column=Befehl "xample" "xmaple tool" "sudo apt-get install maple 12" "" "Kate" "Kate TextEditor" "sudo apt-get install kate" "" "kwriterr" "kwriter text editor" "sudo apt-get install kwrite" "" "leafpad" "leafpad editor" "sudo apt-get install leafpad"`
eval "$com"

```

i think that's the way it should be. OR NOT!!! :( i have edited this now 5 times. something still seems to be wrong :(

@[                                                      [IMG]http://ubuntuforums.org/customavatars/avatar347382_2.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=347382")                                                                                     [**[COLOR=#000000]Vaphell[/COLOR]**]("http://ubuntuforums.org/member.php?u=347382")

i'm afraid this is a little bit too much for me i just don't know how to use it sorry.

---

### Post by Vaphell on 2014-08-26
yad --help? ;-)

your yad with modified separator returns stuff like this
```
$ ./yadtest.bash
TRUE & firefox & Firefox & 
TRUE & deluge & Deluge &
```
and you eval it. Fugly hack that looks like barely working, judging by the largely accidental inputs with random strings. 

in --help there is --print-column=N that allows to select a particular columns instead of printing whole rows. command is in #2
and if you leave the default separator | you get a nice output like this
```
$ ./yadtest.bash  # default separator, print_col=2
firefox|
deluge|
```
even better, if you set sep to null, you get clean commands ready to use.
```
$ ./yadtest.bash  # separator="", print_col=2
firefox
deluge
```

iterating over that output with *while read* and running the 'line'

```
while read com
do
  $com &
done < <( yad ... --separator='' --print-column=2 )
```

my point is eval is superfluous here (and almost everywhere else so you can give yourself -10 points every time you think of using it ;-) ), because $var alone is enough to use its contents as commands (it undergoes word splitting if unquoted, evaluation and what not).
```
$ x=echo
$ $x lol
lol
```

---

### Post by macstar on 2014-08-26
```

macstar@macstar-desktop:~/Projekte/addonpack 0.1$ yad --help
Aufruf:
  yad [OPTION &#8230;] Nur ein anderes Dialog-Programm

Hilfeoptionen:
  -h, --help                                   Hilfeoptionen anzeigen
  --help-all                                   Alle Hilfeoptionen anzeigen
  --help-general                               Allgemeine Einstellungen anzeigen
  --help-calendar                              Kalender-Einstellungen anzeigen
  --help-color                                 Show color selection options
  --help-dnd                                   Show drag-n-drop options
  --help-entry                                 Textfeld-Einstellungen anzeigen
  --help-file                                  Dateiauswahl-Einstellungen anzeigen
  --help-font                                  Show font selection options
  --help-form                                  Formular-Einstellungen anzeigen
  --help-icons                                 Show icons box options
  --help-list                                  Listen-Einstellungen anzeigen
  --help-multi-progress                        Show multi progress bars options
  --help-notebook                              Show notebook dialog options
  --help-notification                          Benachrichtigungssymbol-Einstellungen
  --help-print                                 Show print dialog options
  --help-progress                              Fortschrittsbalken-Einstellungen anzeigen
  --help-scale                                 Schieberegler-Einstellungen anzeigen
  --help-text                                  Informationstext-Einstellungen anzeigen
  --help-misc                                  Verschiedene Einstellungen anzeigen
  --help-gtk                                   GTK+-Optionen anzeigen

Anwendungsoptionen:
  --rest=DATEINAME                             Load extra arguments from file
  --calendar                                   Kalender-Dialog
  --color                                      Farbwahl-Dialog
  --color-selection                            Alias for --color
  --dnd                                        Display drag-n-drop box
  --entry                                      Texteingabefeld oder Auswahlfeld
  --file                                       Datei-Auswahlfeld
  --file-selection                             Alias for --file
  --font                                       Display font selection dialog
  --font-selection                             Alias for --font
  --form                                       Formular-Dialog
  --icons                                      Display icons box dialog
  --list                                       Listen-Dialog
  --multi-progress                             Display multi progress bars dialog
  --notebook                                   Display notebook dialog
  --notification                               Benachrichtigung
  --print                                      Display printing dialog
  --progress                                   Fortschrittsbalken
  --scale                                      Schieberegler
  --text-info                                  Textinformations-Dialog
  --display=ANZEIGE                            X-Anzeige, die verwendet werden soll



```

i hope your german is good ennough that you see there is sadly no such thing as print-column=N  :(

and i don't want an output dialog box showing me what i selected i just want to have the commands executed.
this is not working. :(

i have fired up the wiki link in posting #2 and looked for --print-column. nothing mentioned there.
however i'm really trying. you probably have the code which really reads only the checked dialoge boxes and executes the command stored in column 2 did i get this right?

---

### Post by Vaphell on 2014-08-26
don't you see that the main --help shows subcategories and by diving deeper to --help-XXX you get to the options related to a particular type of dialog?


```
$ yad --help-list
Usage:
  yad [OPTION...] Yet another dialoging program

List options
  --list                                         Display list dialog
  --no-headers                                   Don't show column headers
  --column=COLUMN[:TYPE]                         Set the column header (TYPE - TEXT, NUM, FLT, CHK, RD, IMG, HD or TIP)
  --checklist                                    Use checkboxes for first column
  --radiolist                                    Use radioboxes for first column
  --no-click                                     Disable clickable column headers
  --separator=SEPARATOR                          Set output separator character
  --multiple                                     Allow multiple rows to be selected
  --editable                                     Allow changes to text
  --print-all                                    Print all data from list
  --ellipsize=TYPE                               Set ellipsize mode for text columns (TYPE - NONE, START, MIDDLE or END)
[COLOR="#0000FF"]  --print-column=NUMBER                          Print a specific column. By default or if 0 is specified will be printed all columns[/COLOR]
  --hide-column=NUMBER                           Hide a specific column
  --expand-column=NUMBER                         Set the column expandable by default. 0 sets all columns expandable
  --search-column=NUMBER                         Set the quick search column. Default is first column. Set it to 0 for disable searching
  --tooltip-column=NUMBER                        Set the tooltip column
  --limit=NUMBER                                 Set the limit of rows in list
  --dclick-action=CMD                            Set double-click action
  --regex-search                                 Use regex in search
  --listen                                       Listen for data on stdin in addition to command-line
  --quoted-output                                Quote dialogs output
```

---

### Post by macstar on 2014-08-26
oh yeah found that one now.

however now i still have a code and know nothing to do. so either i spend now the next 10 hours trying and then just giving up or you guide me step by step ;)

```

while read com
do
  $com &
done < <( yad ... --separator='' --print-column=2 )

```

just makes the program to crash.

i also moved up --print-column=2 a bit but does not help at all.

---

### Post by Vaphell on 2014-08-26
i already gave you upgrade to the script in #7 (few additional lines), which should be able to run actual commands.

--print-column, --separator, etc are for the other script which i find somewhat lacking (forms with checkboxes don't have columns so the param doesn't even make sense, but the list tables do).

---

### Post by macstar on 2014-08-26
sorry but now. you are throwing here in a few commands, some even with the wrong formatting for yad and expect me to make it to work? sorry, i just can't. :(

i then rather go with 
 	[**[COLOR=#000000]Habitual[/COLOR]**]("http://ubuntuforums.org/member.php?u=504341") 	 
whose script so far came closest of giving me the expected result. there just seems to be a little detail wrong but i have not found out what yet.

---

### Post by Vaphell on 2014-08-26
```
#!/bin/bash

menu=( "Program1|[COLOR="#0000FF"]sudo apt-get install firefox[/COLOR]"
       "Software 2|install_p2"
       "Some Addon pack|install_p3"
       "And More|some_stuff" )

yad_opts=( --form
           --title="Software Installer"
           --text="Install Software"
           --image="logo.png"
           --button="Install" --button="Exit" )

for m in "${menu[@]}"
do
  yad_opts+=( --field="${m%|*}:CHK" )
done

IFS='|' read -ra ans < <( yad "${yad_opts[@]}" )

for i in "${!ans[@]}"
do
  if [[ ${ans[$i]} == TRUE ]]
  then
    [COLOR="#0000FF"]m=${menu[$i]}
    name=${m%|*}
    cmd=${m#*|}
    echo "selected: $name ($cmd)"
    $cmd[/COLOR]
  fi
done
```

goddamnit, is that so hard to plug few lines of code?

---

### Post by macstar on 2014-08-26
i am _***very ashamed***_ now. 

i tried endlessly to add the --print-column=2 to the script habitual posted and then added the 
```
while read com
do
  $com &
done < <( yad ... --separator='' --print-column=2 )
```

below it. yes i am that bad and stupid. 

@[**[COLOR=#000000]Vaphell[/COLOR]**]("http://ubuntuforums.org/member.php?u=347382")

do you got paypal?

---

### Post by Habitual on 2014-08-26
> **macstar said:**
> @[                                                      [IMG]http://ubuntuforums.org/customavatars/avatar504341_4.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=504341")                                                                                     [**[COLOR=#000000]Habitual[/COLOR]**]("http://ubuntuforums.org/member.php?u=504341")

i think i have figured out what was wrong with your script:
```
#!/bin/bash
com=`yad --title=AddonPack 0.1 --text='Installs important Addon Software' --height=500 --width=800 --image="logo.png" --list --separator=" & "  --checklist --column="1/0" --column=Programm --column=test --column=Befehl "xample" "xmaple tool" "sudo apt-get install maple 12" "" "Kate" "Kate TextEditor" "sudo apt-get install kate"`
eval "$com"
``` wrong? 
There's nothing 'wrong' with the nugget. It was meant merely to inspire you to seek a solution of your own choosing.

Vaphell has the mojo. 
He's cleaned up my stuff numerous times.
Glad it worked out.

---

