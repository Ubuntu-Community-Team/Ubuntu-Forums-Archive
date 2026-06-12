---
title: "Checking files in a script..."
date: 2005-06-18
forum: Programming Talk
---

### Post by audax321 on 2005-06-18
I'm writing a nautilus script to run par2 on some par2 files. The complete script is like this:

```

#!/bin/sh

# Checks all par2 files in current directory.

if [ -f *.par2 ]; then
	gnome-terminal --working-directory=pwd -x par2 r *.par2
else
	echo "WARNING: There were no *.par2 files found in the current directory."
	echo "Press <ENTER> to exit..."
	read PAR2_GARBAGE
	exit 1
fi

``` 

Everything works if I remove the if statement and just execute the gnome-terminal command. But I'd like to get the if statement to check and only run the script if *.par2 files exist in the current directory. Is there a way to do this... the script doesn't run in its present state.


Thanks...

---

### Post by LordHunter317 on 2005-06-18
What's the problem?  It seems to work for me here.

This isn't a traditional UNIX script.  You shouldn't have that nasty interactive prompt on error.  That would cause me personally to go insane.

A better way to do this may just be to run the gnome-terminal.

---

### Post by audax321 on 2005-06-18
Well, omg... it does work, I just realized that nautilus doesn't pop up a terminal window so that is why I'm not seeing the error prompt..

That was retarded on my part  :wink: 

Thanks...

---

### Post by TuxCrafter on 2006-06-16
I found a beautiful solution for par2 and nautilus

right button -> open with on a par2 file 

custom command -> gnome-terminal -x par2repair

this will start a terminal en run par2repair on the file that you have selected

now you can see the scanning and repair process

---

### Post by audax321 on 2006-06-20
Nice one, I never even though about doing that. :D 

I've been using this script I wrote that actually checks the par file in the background while displaying a progress bar through the zenity program. Unfortunately the cancel button on the progress bar won't cancel the par2repair process, but instead hides the progress bar. At the end a dialog box comes up displaying the terminal contents (as long as you didn't hit cancel on the progressbar in which case it gives you no indication of how it finished). I just put it in the /home/user/.gnome2/nautilus-scripts folder and ran it from right-click 'Scripts':

```

#!/bin/sh

# Checks selected par or par2 file.


# FUNCTION: RUN_PAR()
RUN_PAR()
{
	(   
		if [ -f "par_repair.log" ]; then
			echo "1"
			rm "par_repair.log"

			if [ "$?" = "0" ]; then
				PAR2_OUTPUT=$(par2 r "$1")
				echo $PAR2_OUTPUT > /tmp/par2_script.log
				echo "100"
				zenity --title="PAR Repair Output..." --text-info  --filename="/tmp/par2_script.log"
			else
				exit 1
			fi
		else
			echo "1"
			PAR2_OUTPUT=$(par2 r "$1")
			echo $PAR2_OUTPUT > /tmp/par2_script.log
			echo "100"
			zenity --title="PAR Repair Output..." --text-info  --filename="/tmp/par2_script.log"
		fi
	) |
	zenity --title="Checking PAR Files..." --progress --text="Pressing CANCEL will hide the progress bar and skip display of par2 repair output." --auto-close --pulsate
}


# CHECK IF FILE EXTENSION IS CORRECT
RUN=0

if [ -f "$1" ]; then
	ARG_EXTENSION=$(echo "${1}" | sed -n 's/\(^.*\)\.\([\A-Za-z0-9]*\)/\2/p')
	ARG_EXTENSION=$(echo "$ARG_EXTENSION" | tr A-Z a-z)

	if [ "$ARG_EXTENSION" = "par2" -o "$ARG_EXTENSION" = "par" ]; then
		RUN=1
	fi
fi

if [ "$RUN" = 0 ]; then
	if [ -f "$1" ]; then
		zenity --title="WARNING!" --question --text="The file '$1' does not appear to have a valid *.par or *.par2 extension. Would you like to run it anyway?"
			
		if [ "$?" = "0" ]; then
			RUN_PAR "$1"	
		else
			exit 1
		fi
	else
		zenity --title="WARNING!" --info --text="The selected item does not appear to be a file and therefore will not be executed."
		exit 1
	fi
else
	RUN_PAR "$1"
fi

```

If anyone knows what is wrong with the Cancel button (I want it to cancel and exit the entire script and everything it is doing when pressed) please let me know. Right now when it's pressed it keeps running the par2repair command in the background and just hides the progress bar and text output at the end. I want to use the progress bar in a few other scripts, but I don't know what I am exactly doing wrong with it.

---

### Post by TuxCrafter on 2006-07-02
I created a small script that i can call from nautilus but there is a problem.

When de job is compleet with or without errors it will close the terminal automaticly. 

I also believe that using gnome-terminal is not the right way.

But I can not find a way to get a terminal to appear when calling a script from nautilus. 

Is there a way to force a script to run in a terminal this would be the solution.

```
#!/bin/sh

for arg
do
	gnome-terminal -x par2repair "$arg"
	#echo "Press <ENTER> to exit..."
	#read PAR2_GARBAGE
	#exit 1
done
```

---

### Post by Athropos on 2006-07-06
Hi,

For those who may be interested, I wrote a small frontend for par2 :

[http://pypar2.silent-blade.org/](http://pypar2.silent-blade.org/)

---

