---
title: "echo command and variables ?"
date: 2013-11-01
forum: Programming Talk
---

### Post by stinkeye on 2013-11-01
I have a bash script xclip.sh ....
```
#!/bin/bash

## mouse middle click
echo "$1" | tr -d '\n' | xclip
```

I want to send $1 to xclip without it being interpreted.
eg 
I have a command line that I want to use as the $1 variable... 
```
ip -o -4 addr show | awk -F '[ /]+' '/global/ {print $4}'
```


This doesn't work
```
xclip.sh [COLOR="#FF0000"]"[/COLOR]ip -o -4 addr show | awk -F '[ /]+' '/global/ {print **$4**}'[COLOR="#FF0000"]"[/COLOR]
```

Clipboard shows this (no $4)...
```
ip -o -4 addr show | awk -F '[ /]+' '/global/ {print }'
```

What's the correct way of quoting or is the echo command wrong to literally send $1 to xclip.
Thanks.

---

### Post by steeldriver on 2013-11-01
You should be able to backslash escape it

```

$ echo "ip -o -4 addr show | awk -F '[ /]+' '/global/ {print **\$4**}'"
ip -o -4 addr show | awk -F '[ /]+' '/global/ {print $4}'

```

Enclosing in single quotes also prevents substitution - however it's difficult when there are already single quotes in the string

FWIW it shouldn't be necessary to pipe the echo through 'tr' to strip the trailing newline - echo has an option not to print it

```
echo **-n** "$1" | xclip
```

---

### Post by stinkeye on 2013-11-01
> **steeldriver said:**
> You should be able to backslash escape it

```

$ echo "ip -o -4 addr show | awk -F '[ /]+' '/global/ {print **\$4**}'"
ip -o -4 addr show | awk -F '[ /]+' '/global/ {print $4}'

```

Enclosing in single quotes also prevents substitution - however it's difficult when there are already single quotes in the string

FWIW it shouldn't be necessary to pipe the echo through 'tr' to strip the trailing newline - echo has an option not to print it

```
echo **-n** "$1" | xclip
```

Is there any way without escaping because I don't want to have to manually edit every command I use?

---

### Post by Vaphell on 2013-11-01
in this case no
you either go with "" which expand $variables which needs to be prevented
or you go with '' but then you have awk related ones which need escaping

what do you need this hack for exactly?

---

### Post by stinkeye on 2013-11-01
> **Vaphell said:**
> in this case no
you either go with "" which expand $variables which needs to be prevented
or you go with '' but then you have awk related ones which need escaping

what do you need this hack for exactly?
Hi Vaphell,
I was trying to make a unity launcher to hold  snippets using the quicklist.
I wanted to be able write a new .desktop file whenever a snippet was added.
I got the idea from a unity-reboot script that lists your boot menu and
writes a launcher with quicklists to change your next boot.

I needed to write stuff to the .desktop file but what I was doing 
wasn't working because the echo command wasn't working with quotes and variables.
I couldn't add some code snippets for the same reason.

I ended up doing it this way which seems to work so far.
```
#!/bin/bash

# Use snippets from a unity quicklist.
# Creates a ~/.local/share/applications/snippets.desktop file to drag and drop on the unity launcher
# or any dock that supports quicklists.
# The right click quicklist items are created from ~/.snippets-launcher/snippets.txt....one snippet per line...
# ....and will be sorted alphbetically.
# Can add cipboard content via quicklist menu.



mkdir -p ~/.local/share/applications
sed -i '/^\s*$/d' ~/.snippets-launcher/snippets.txt                            # remove blank lines
sort ~/.snippets-launcher/snippets.txt -o ~/.snippets-launcher/snippets.txt    # alphbetical
rm -rf /tmp/.actions*                                                         #clean before start


## count snippets
snipcount=$(cat ~/.snippets-launcher/snippets.txt | wc -l)

## create single line to use with desktop "Actions"
n=1
while [ $n -le "$snipcount" ];
do
echo Snippet$n\; | tee -a /tmp/.actions
n=$(( n+1 )) 
done

awk '{ printf "%s", $0 }' /tmp/.actions > /tmp/.actions2
rm -rf "/tmp/.actions"
cp /tmp/.actions2 /tmp/.actions

shortcuts=$(cat /tmp/.actions)

echo "[Desktop Entry]
Version=1.0
Name=Snippets
Comment=Snippets to clipboard using xclip
GenericName=Snippets
Exec=gedit $HOME/.snippets-launcher/snippets.txt
Icon=$HOME/.snippets-launcher/Snippets.png
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=GNOME;System;
X-Ayatana-Desktop-Shortcuts=${shortcuts}Snippet96;Snippet97;Snippet98;Snippet99" | tee ~/.local/share/applications/snippets.desktop


## get quicklist titles from snippets.txt and create the quicklists
	n=1
	while [ $n -le "$snipcount" ];
	do
	MENUENTRY=$(sed -n "$n{p;q;}" $HOME/.snippets-launcher/snippets.txt)   #/tmp/.ur_bootlist2
	echo "[Snippet$n Shortcut Group]
	Name=$(echo "$MENUENTRY")
	Exec=sh -c \"head -$n ~/.snippets-launcher/snippets.txt | tail -1 | tr -d '\n' | xclip -i\"
	TargetEnvironment=Unity" | tee -a ~/.local/share/applications/snippets.desktop
	n=$(( n+1 ))
	done
	rm -rf /tmp/.actions* > /dev/null 2>&1

### permanent quicklists
## date
echo "[Snippet96 Shortcut Group]
	Name=Date
	Exec=$HOME/.snippets-launcher/date.sh
	TargetEnvironment=Unity" | tee -a ~/.local/share/applications/snippets.desktop

## quicklist item used as a separator
echo "[Snippet97 Shortcut Group]
	Name=__________________________________________________
	Exec=notify-send -i $HOME/.snippets-launcher/mp2.jpeg 'Go Away...or I shall taunt you a second time !'
	TargetEnvironment=Unity" | tee -a ~/.local/share/applications/snippets.desktop

## Add clipboard to snippets and update 
echo "[Snippet98 Shortcut Group]
	Name=Add Clipboard Content
	Exec=sh -c \"xclip -selection clipboard -o >> $HOME/.snippets-launcher/snippets.txt; $HOME/.snippets-launcher/snippets.sh\"
	TargetEnvironment=Unity" | tee -a ~/.local/share/applications/snippets.desktop

## update launcher after changing snippets
echo "[Snippet99 Shortcut Group]
	Name=Update Launcher
	Exec=gnome-terminal -e $HOME/.snippets-launcher/snippets.sh
	TargetEnvironment=Unity" | tee -a ~/.local/share/applications/snippets.desktop



#chmod +x ~/.local/share/applications/snippets.desktop
```

---

### Post by Vaphell on 2013-11-02
you made it way harder than it is ;-)
if you run subshell with sh -c you can as well create a fullblown script that will do the trick

check this out - this creates entries that call the script with number of the snippet. Nice and tidy, and no unnecessary tempfiles.
```
#!/bin/bash

snipfile=$HOME/.snippets-launcher/snippets.txt
desktopfile=$HOME/.local/share/applications/snippets.desktop
snipdir=${snipfile%/*}

mkdir -p "${desktopfile%/*}"
readarray -t -O1 snips < <( sed -r '/^#|^\s*$/d' "$snipfile" | sort )
printf -v xadshorts "Snippet%s;" ${!snips[@]} {96..99} 

tee "$desktopfile" << END
[Desktop Entry]
Version=1.0
Name=Snippets
Comment=Snippets to clipboard using xclip
GenericName=Snippets
Exec=gedit ${snipdir}/snippets.txt
Icon=${snipdir}/Snippets.png
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=GNOME;System;
X-Ayatana-Desktop-Shortcuts=${xadshorts%;}
END

for i in ${!snips[@]}
do
  cat << END
[Snippet$i Shortcut Group]
Name=${snips[$i]}
Exec=${snipdir}/snip2clip.sh $i
TargetEnvironment=Unity
END
done | tee -a "$desktopfile"

tee -a "$desktopfile" << END
[Snippet96 Shortcut Group]
Name=Date
Exec=${snipdir}/date.sh
TargetEnvironment=Unity
[Snippet97 Shortcut Group]
Name=__________________________________________________
Exec=notify-send -i ${snipdir}/mp2.jpeg 'Go Away...or I shall taunt you a second time !'
TargetEnvironment=Unity
[Snippet98 Shortcut Group]
Name=Add Clipboard Content
Exec=sh -c "xclip -selection clipboard -o >> ${snipdir}/snippets.txt; ${snipdir}/snippets.sh"
TargetEnvironment=Unity
[Snippet99 Shortcut Group]
Name=Update Launcher
Exec=gnome-terminal -e ${snipdir}/snippets.sh
TargetEnvironment=Unity
END
```

snip2clip.sh
```
#!/bin/bash

snipfile=$HOME/.snippets-launcher/snippets.txt

snip=$( sed -r '/^#|^\s*$/d' "$snipfile" | sort | sed -n $1p )
printf "$snip" | xclip -i
```

also the input file doesn't get modified so it's possible to have comments as well, in this code lines starting with # are also ignored.

---

### Post by stinkeye on 2013-11-03
> **Vaphell said:**
> you made it way harder than it is ;-)
if you run subshell with sh -c you can as well create a fullblown script that will do the trick

check this out - this creates entries that call the script with number of the snippet. Nice and tidy, and no unnecessary tempfiles.

Thanks for doing this Vaphell.
Works a lot better than my script.
What I know about scripting comes mostly from these forums, google and looking at other people's scripts.
I tried to adapt the script from [**_[COLOR="#B22222"]THIS[/COLOR]_**]("http://www.webupd8.org/2013/01/unity-reboot-launcher-to-quickly-reboot.html") application to work as a snippet holder.
Turned out harder than I thought.
I have very limited knowledge of sed, which is why I originally used this to avoid sed/scripting pitfalls I don't understand...
```
sh -c \"head -$n ~/.snippets-launcher/snippets.txt | tail -1 | tr -d '\n' | xclip -i\"
```

Everything seems to be working okay with your script except the snip2clip.sh script
is interpreting some parts of pasted code.
eg if I use the "Add Clipboard Content" quicklist item to add something like....
```
echo -e "\n\033[36mYou have selected \033[0m$CURSOR\n\033[36mContinue?(Y/n):\033[0m"
```
....it writes to the snippets.txt file ok but some interpretation is done when writing the quicklist item and outputting to xclip.
```
echo -e "
[36mYou have selected [0m$CURSOR
[36mContinue?(Y/n):[0m"
```
Thanks.

---

### Post by Vaphell on 2013-11-03
and what happens when you change *printf "$snip"* to *printf '%s' "$snip"* ?

---

### Post by stinkeye on 2013-11-03
> **Vaphell said:**
> and what happens when you change *printf "$snip"* to *printf '%s' "$snip"* ?
Yep that works.
The writing of the quicklist item seems to be interpreting "\n" but when clicked on is sending the correct output to xclip.

---

### Post by stinkeye on 2013-11-03
Your code seems to be ok and it's the unity launcher that is interpreting "\n" as newline.
eg I added **test1\ntest2** from the clipboard and no newline is created in the .desktop file.
Just something I'll have to live with.
The quicklist item still sends the snippet without interpretation to the clipboard.
Thanks for your work Vaphell.

---

### Post by Vaphell on 2013-11-04
> Just something I'll have to live with.

no not really, change this
```
Name=${snips[$i]}
```
to this
```
Name=${snips[$i]//\\/\\\\}
```

---

### Post by stinkeye on 2013-11-04
Yes that does it.
Care to explain. Just looks like a box of matches me. :confused: :P

---

### Post by Vaphell on 2013-11-04
if unity interprets \n as newline then one can assume that a trick of escaping \ with another \ also works.
\n = newline, but \\n = \+n

```
$ echo $'abc\ndef'
abc
def
$ echo $'abc\\ndef'
abc\ndef
```

so in the text pasted as description we need to replace every single \ with \\ and we use ${var//pattern/replacement} for that.
For pattern we want to use '\' and for replacement we want to use '\\' but again, due to \ = escape next char, we need to double every required \
so we get ${var//[COLOR="#0000FF"]\\[/COLOR]/[COLOR="#0000FF"]\\\\[/COLOR]}

---

### Post by stinkeye on 2013-11-04
> **Vaphell said:**
> if unity interprets \n as newline then one can assume that a trick of escaping \ with another \ also works.
\n = newline, but \\n = \+n

```
$ echo $'abc\ndef'
abc
def
$ echo $'abc\\ndef'
abc\ndef
```

so in the text pasted as description we need to replace every single \ with \\ and we use ${var//pattern/replacement} for that.
For pattern we want to use '\' and for replacement we want to use '\\' but again, due to \ = escape next char, we need to double every required \
so we get ${var//[COLOR="#0000FF"]\\[/COLOR]/[COLOR="#0000FF"]\\\\[/COLOR]}
Why doesn't it replace the "\" with "\\"
in abc\def to give abc\\def
I don't understand where in  the code, ${var//\\/\\\\}, it knows only to perform on "\n"

---

### Post by Vaphell on 2013-11-04
> Why doesn't it replace the "\" with "\\"
in abc\def to give abc\\def

what do you mean by 'it'?

> I don't understand where in the code, ${var//\\/\\\\}, it knows only to perform on "\n"
It doesn't. It replaces all '\'s with '\\' to make them literal and show up in the result.
There are more \X symbols, eg \r=carriage return, \t=tab and most likely they would be interpreted by unity as well.
[http://en.wikipedia.org/wiki/String_literal#Escape_sequences](http://en.wikipedia.org/wiki/String_literal#Escape_sequences)

if you wanted to deal only with \n you'd have to write ${var//\\n//\\\\n} but again, \t or \r would break it too.

Put something like '\1 \t \r' in your snippet file and test it with and without the replacement.

---

### Post by stinkeye on 2013-11-04
Ok, I need to do a bit of learning.

---

