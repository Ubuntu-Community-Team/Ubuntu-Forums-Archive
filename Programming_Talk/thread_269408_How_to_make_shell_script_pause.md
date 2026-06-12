---
title: "How to make shell script pause?"
date: 2006-10-01
forum: Programming Talk
---

### Post by fatsheep on 2006-10-01
Whenever I run a bash script in the terminal (double click on it, "Run in Terminal") it will open up a terminal window, complete the script and exit RIGHT after it finishes giving me no time to review the output.  I would like the script to leave the terminal window open after it finishes and allow further commands if possible.  How would I do this?  I know the sleep command can pause the script for a designated ammount of time and then close the terminal but this is an imperfect solution.

---

### Post by po0f on 2006-10-01
fatsheep,

I assume you are using Gnome Terminal.  In this case, open up a new terminal window.  Go to the "Edit" menu and click "Current Profile".  Click on the "Title and Command" tab.  In there, there is a setting called "When command exits". Change it to "hold the terminal open".

---

### Post by fatsheep on 2006-10-01
> **po0f said:**
> fatsheep,

I assume you are using Gnome Terminal.  In this case, open up a new terminal window.  Go to the "Edit" menu and click "Current Profile".  Click on the "Title and Command" tab.  In there, there is a setting called "When command exits". Change it to "hold the terminal open".

Cool.  Thanks a bunch.  However, is there any way to do this inside a script itself?

---

### Post by po0f on 2006-10-01
fatsheep,

I think you would manually have to open up a terminal and run the script if you wanted to do it that way.  AFAIK, there is no way to do this from a script.  When the script exits, whatever program called it (Nautilus in this case, I'm guessing), gets the exit signal and closes the terminal.  That's why Gnome Terminal has that setting.

---

### Post by ghostdog74 on 2006-10-01
> **fatsheep said:**
> Whenever I run a bash script in the terminal (double click on it, "Run in Terminal") it will open up a terminal window, complete the script and exit RIGHT after it finishes giving me no time to review the output.  I would like the script to leave the terminal window open after it finishes and allow further commands if possible.  How would I do this?  I know the sleep command can pause the script for a designated ammount of time and then close the terminal but this is an imperfect solution.

use the read command ?

---

### Post by fatsheep on 2006-10-01
> **ghostdog74 said:**
> use the read command ?

Works like a charm.  Thanks a bunch! :p

---

### Post by amo-ej1 on 2006-10-02
And if you simply want a pause, use sleep

```

sleep 10

```
will sleep 10 seconds (10 can be any number ;-) ) (a long as it's positive)

---

### Post by hackeron on 2007-01-31
If you don't want to change the code of the script, you can simply hit ctrl+z on the keyboard to suspend any process running in foreground and run fg to resume it in foreground (or bg to resume it in background).

---

### Post by Tritonio on 2007-10-10
> **fatsheep said:**
> Works like a charm.  Thanks a bunch! :p

For some weird reason the read command doesn't keep the terminal open for me. But if I run the script through a terminal manualy then it gives the desired effect. I am using something like this:

```
#/bin/bash

'./LUA Binaries/LUA Binaries for Linux/lua5.1' './source/AskWise.lua'
read

```

Should it work? :confused:

---

### Post by dwhitney67 on 2007-10-11
If you merely want access to the shell after your script is complete, try this:

```
xterm -e 'bash myscript.bash && bash'
```

With this concept you would *not* require the 'read' statement in your script.  Btw, for some reason I could not get the same results when I substituted gnome-terminal for xterm.  Maybe a gnome guru can explain this.

---

### Post by americancaesar2 on 2008-06-17
read -p "Press enter to continue"

to make the script pause

or 

read -n 1 -p "Press any key to continue"

to mimic the DOS pause more exactly

the prompt message (what you put in quotes) is up to you

---

### Post by Skip Da Shu on 2009-04-27
READ and SLEEP both worked for me at bottom of my 1st .sh :-)

```
	fi
done

echo " "
echo "Done, Press ENTER to end"
read
#echo "Done"
#sleep 6
```

Works now as a 'launcher' on my gnome desktop also.

---

### Post by Endolith on 2009-05-05
> **americancaesar2 said:**
> read -p "Press enter to continue"

to make the script pause


This does not work in Ubuntu.  

```
Press enter to continueread: 19: arg count
```

---

### Post by Endolith on 2009-05-05
This works, though:
```

#!/bin/sh

read -p "Press enter to continue" nothing
```

the version of read used by /bin/sh doesn't like it if you don't give it a variable

---

### Post by Skip Da Shu on 2009-05-05
Delete me

---

### Post by Skip Da Shu on 2009-06-02
> **Endolith said:**
> This does not work in Ubuntu.  

```
Press enter to continueread: 19: arg count
```

But using "echo" and then read w/o any parms does (as shown in the post above yours).


In larger scripts I did later where I needed to do this a couple times I just stick both of these as a function at the top of the .sh
```
function wait_enter {
	echo ""
	read -p "Please press enter to continue..." nothing
	}

function cont_y_n {
	printf "Do you want to continue (Y/n): "
	read INPT
	if [ "$INPT" = "n" ]; then 
	echo "Ending..."
	echo ""
	exit
	fi
	}
```Then invoke as:```

	echo "Terminating this process..."
	wait_enter
``` or
```
cont_y_n
```

---

### Post by newtekken on 2009-07-31
I think, the "sleep" command is the perfect suggestion for the pausing purpose. Thanks.

---

### Post by hyperAura on 2009-08-01
thnx for this 1 i needed it too.. read command suits my needs..

---

### Post by ihitf13anddied on 2009-08-02
> **Endolith said:**
> This works, though:
```

#!/bin/sh

read -p "Press enter to continue" nothing
```

the version of read used by /bin/sh doesn't like it if you don't give it a variable

Thank you SO MUCH!

I was going crazy wondering why read -p "Text here" was not doing the job when running the .sh from a launcher.

Other sites say to just use the read command without mentioning the variable. That works great if you run the .sh from terminal, but since I am running from a launcher your variable method solved my issue.

---

### Post by simon_w on 2009-08-19
> **ihitf13anddied said:**
> Thank you SO MUCH!

I was going crazy wondering why read -p "Text here" was not doing the job when running the .sh from a launcher.

Other sites say to just use the read command without mentioning the variable. That works great if you run the .sh from terminal, but since I am running from a launcher your variable method solved my issue.

For what it's worth, the issue here is that your terminal is running bash, and you have the shebang at the top of your launcher script invoking sh instead.  If you change the top line to "#!/bin/bash" then commands will behave as you're used to in the Terminal.

---

### Post by JBA2337 on 2010-02-20
An easy way to pause the terminal after running a script command is to use read -p followed by the text of your choice in quotation marks, as in the following example.

#!/bin/bash
df -h 
read -p  "-End-"

The above command should be copied to a text editor, and saved as a *.sh file. In the example above, I saved the above code in a file named "Mounted File Systems.sh"  
Double clicking on that file will offer you the choice of running the fle in a terminal, or displaying its contents.


JBA2337

---

### Post by Byb on 2010-04-26
> **JBA2337 said:**
> 
The above command should be copied to a text editor, and saved as a *.sh file. In the example above, I saved the above code in a file named "Mounted File Systems.sh"  
Double clicking on that file will offer you the choice of running the fle in a terminal, or displaying its contents.
JBA2337
For me, I just not even have to save as .sh. Even without any extension I'm prompted to display or run in terminal (maybe because I set the x attribute).
Thank you very much all you for this very useful and detailled topic.

---

### Post by jimbabwean on 2012-11-20
echo Press enter to exit this script
read xyz

---

### Post by nothingspecial on 2012-11-20
Old thread.

Closed.

---

