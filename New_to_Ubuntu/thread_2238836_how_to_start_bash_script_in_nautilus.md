---
title: "how to start bash script in nautilus?"
date: 2014-08-10
forum: New to Ubuntu
---

### Post by bernatik.vit on 2014-08-10
I have simple beginning of the script which goes like this:
```
#!/bin/bash
read -s -p "Enter Password: " mypassword
echo $mypassword
```

when I run it from terminal it works perfectly.

When I double click it in nautilus nothing happend [EDIT: nothing happend is just how it seems but in fact script would start but terminal won't open so I can not fill the password]. Obvious question why? And how to make it run?

BTW:
- yes it has executable flag (otherwise it would't run in terminal either)
- yes I set nautilus Edit->Preferences->Behavior->Executable Text Fiels->Run Executable Text files when they are open
(I'm using latest Ubuntu 14.04.1 LTS)

---

### Post by nerdtron on 2014-08-10
hhhmmmm what do you expect it to do when you double-click it in nautilus? With those lines I don't expect the script to open a window and tell to "Enter password:". What do you want to do? Maybe we can find another approach to your problem?

---

### Post by Jonathan Precise on 2014-08-10
In nautilus, you need to change settings to "Prompt". Try again and hit "Run in terminal"

---

### Post by bernatik.vit on 2014-08-16
hey thanx for hint albeit I haven't found anything saying "prompt" but when I set "Edit->Preferences->Behavior->Executable Text Fiels->Ask each time" then after double click appear option "Run in terminal" which does exatly what I want.

But this is a global option and bothers me with questioning with all other files.

Is there a way to write the script in the way that it will show terminal for it's run?

---

### Post by bernatik.vit on 2014-08-16
So I have found solution I'm happy with.

I keep my test.sh

And I create file "testRun.desktop" with content: 
```
[Desktop Entry]
Exec=/home/lob/0/scripts/test.sh
Icon=/usr/lib/firefox/browser/chrome/icons/default/default48.png
Name=my script
Path=
Terminal=true
TerminalOptions=
Type=Application

```

I believe that line "Terminal=true" will force unity to open terminal for it and it let me fill password and then later do whatever

---

### Post by monkeybrain20122 on 2014-08-16
Make a script that prompts for password with a textbox (like synaptic), give it a name, say askpasswd.sh


```
#!/bin/bash
zenity --password --title=Authentication
```

Then you can invoke it in other scripts that need authentication.

```
#!/bin/bash

export SUDO_ASKPASS="/path/to/askpasswd.sh"

....
```

The ... repesents the content of your script.

---

### Post by bernatik.vit on 2014-08-16
Thanx that looks fancy - maybe I will use it sometimes ;) But for now I will stick with terminal cos I'm familiar with it and I'm not looking for fancy yet

---

### Post by Jonathan Precise on 2014-08-16
My sudo-zenity-dialog:

```
#!/bin/bash
#
# Dialog asking for password. Like ssh-askpass.

PROMPTNEXT=0

usage() {
	echo "" 1>&2
	echo "E: OptError: Invalid option(s). See `echo $(basename $0)` --help for more help." 1>&2
	exit $1
}

for i in $@; do
	if [ $PROMPTNEXT != 0 ]
	then
		TEXTPROMPT="$i"
		PROMPTNEXT=0
	else
		case $i in
			'--help'|'-h'|'-?')
				echo -ne "\nUsage: `basename $0` [ --help | -h | -? ] [ --prompt \"TEXT\" ]\n\n" ; exit 0;;
			'--prompt')
				E: This is deprectated
				PROMPTNEXT=1 ;;
			*)
				;;
		esac
	fi
done


zenity --entry --text=$'WARNING!!! Runing a malicious program with ``super user" priviliges\ncan let a remote attacker take control of your system!!!\nIf not using care, running a non-malicious program as the ``super user"\ncan wipe your system, render it unusable, or otherise severely damage it!!!\n\n\nJust to make sure you are running the program intentionally and with care,\nenter your password to use the program with ``super user" privileges' --hide-text --title=$"[sudo] password for $USER"


exit 0
```

Then add this code to your script:

```
#!/bin/bash

export SUDO_ASKPASS=/path/to/sudo-zenity-dialog
**...**
# Replace all sudo's with sudo -A
sudo -A -u root **XYZ**
**...**

```

EDIT: Didn't see the OP's edit.

---

### Post by monkeybrain20122 on 2014-08-16
Yeah, forgot to mention replacing all ocurrences of "sudo" with "sudo -A"

---

### Post by Jonathan Precise on 2014-08-16
Regarding the OP's edit, could be replaced by

```
#!/bin/bash
mypassword=`zenity --entry --text='Enter password' --hide-text --title="Enter password"`
zenity --info --title="Password" --text="$mypassword"

```

Everything is graphical.

---

