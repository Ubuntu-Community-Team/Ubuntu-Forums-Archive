---
title: "Help with a shell script."
date: 2008-04-18
forum: Programming Talk
---

### Post by msjones on 2008-04-18
Hi,

I am trying to write a shell script that will launch a new command in a new terminal then continue to run it current command in the original terminal. So far I have this.....

```
[CODE]if [ $(whoami) = "root" ]
	then
	gnome-terminal&
		echo "Please enter BSSID MAC address"
			read BSSID
		echo "Please enter your MAC address"
			read MYMAC
```[/CODE]

I want everything after gnome-terminal& to run in the newly executed terminal while the mother script continues with the rest of its commands.

Is this possible?

Thanks

---

### Post by mssever on 2008-04-18
> **msjones said:**
> Is this possible?
Yes.





----------------------------
Oh, you wanted to know how to do it? There's more than one way to do it. My suggestion is to put the commands you want to run in a separate file. Then call ```
gnome-terminal -e "/your/second/script arg1 arg2" &
```

---

### Post by dwhitney67 on 2008-04-18
Personally, I have never had good success launching a string of shell commands using gnome-terminal, thus I rely on xterm.

To simplify your woes, I would recommend that you write two scripts, the launcher, and then another that gathers user-input and processes it.

So for script 1:
```
#!/bin/sh

if [ `whoami` = "root" ]
then
        xterm -e 'sh script2';
else
        echo "sorry, you are not root!"
fi
exit 0
```

And for script 2:
```
#!/bin/sh

echo -n "Enter SSID: "
read ssid
echo -n "Enter MAC address: "
read mac
...
exit 0
```

P.S.  The other alternative is probably to create a single script, then create a Gnome applet where you would run the script in a terminal.

---

### Post by Can+~ on 2008-04-18
When you call a new gnome terminal using the command, it starts, runs the command and closes, you'll need a wait event, but I guess asking the user for input also pauses it.

---

### Post by stroyan on 2008-04-18
You may be much better served by the zenity command.
```

BSSID=$(zenity --entry --title "BSSID" --text "Enter BSSID: ")

```
That returns the user input to a dialog as stdout.
The string is then assigned by to the BSSID variable by the $() command substitution mechanism.
If you start a gnome terminal and prompt for input you will not be able to
just set a shell variable in that second script to affect the variables in your
initial shell script.

---

### Post by msjones on 2008-04-18
Thanks alot guys! this really helps!!

---

