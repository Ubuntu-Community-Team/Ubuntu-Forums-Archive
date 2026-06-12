---
title: "sh script runs in Terminal, not on double click"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by stevejluke on 2012-12-25
I have this script I got from an installation of an app called MapTool.  It is set to executable and runs fine when I have a terminal open and type ./MaptTool.sh.  The problem is that when I double click on it it won't run.  I get a dialog that asks to Run, Display, or Run in Terminal (this is expected).  If I select Run in Terminal a terminal window briefly displays then goes away.  If I choose Run nothing happens.

Normally I would open up a terminal window and execute the script to see what errors occur, but when I do this the application runs as expected, no error message.  So I am not exactly sure how to proceed.  How do I figure out what the problem is?  

I suspect that the problem is that the application uses Java, and when I run the script in a terminal the JAVA_HOME variable is available.  But for some reason when double clicking the script the JAVA_HOME variable is not set.  My JAVA_HOME is set in ~/.bashrc.

Any idea on the likely cause or how to better troubleshoot?  Below is the script.

```
#!/bin/bash
MAXMEMSZ="768m"	# The 'm' suffix means megabytes.
MINMEMSZ="32m"	# If your Java crashes, try making this the same value.
STACKSZ="2m"	# Larger and more complicated macros require larger stack size.
if [ "X$RANDOM" = "X$RANDOM" ]; then
    echo 1>&2 "Error: this script requires a Korn or Bash shell."
    exit 1
fi
java=$JAVA_HOME/bin/java
if [[ ! -x "$java" ]]; then
    java=$(type -p java)
    if [[ ! -x "$java" ]]; then
	echo 1>&2 "${0##*/}: Error: Can't find Java executable."
	exit 2
    fi
fi
dir=${0%/*}
cd "$dir" || {
    echo 1>&2 "${0##*/}: Error: Can't find script directory."
    exit 3
}

VERS=maptool*.jar
APPDOCKNAME=""
APPDOCKICON=""

case "$JAVA_HOME" in
    *[Ss]oy[Ll]atte*)	# No additional options if using SoyLatte...
	;;
    *)	case $(uname -s) in
	Darwin)
	    APPDOCKNAME="-Xdock:name=MapTool"
	    APPDOCKICON="-Xdock:icon=http://www.rptools.net/images/logo/RPTools_Map_Logo.png"
	    ;;
	esac
	;;
esac
ALL_OPTS="-Xmx$MAXMEMSZ -Xms$MINMEMSZ -Xss$STACKSZ $APPDOCKNAME $APPDOCKICON"
count=0
for jar in $VERS
do
    let count=count+1
    MAPTOOL="$jar"
done
if ((count > 1)); then
    rvid=$(tput smso)	# Reverse video
    normal=$(tput sgr0)	# Turn off all attributes
    MAPTOOL=""
    PS3="
Type the number of your choice and press <Enter>.
Or use Ctrl-C to terminate: "
    IFS=""	# Turn off word breaks on whitespace
    echo 1>&2 ""	# Blank line
    select jar in $VERS
    do
	if [[ "$jar" == "" ]]; then jar="$REPLY"; fi
	if [[ -e "$jar" ]]; then
	    MAPTOOL="$jar"
	    break
	fi
	echo 1>&2 ""	# Blank line
	echo 1>&2 "${rvid}Error: Invalid input -- try again.${normal}"
	echo 1>&2 ""
	REPLY=""	# Force menu to appear again.
    done
    if [[ "$MAPTOOL" == "" ]]; then exit 4; fi	# Ctrl-D at the select prompt
    echo 1>&2 "" # Blank line
fi

echo 1>&2 "Executing $MAPTOOL ..."
eval $java $ALL_OPTS $APPOTHER -jar "$MAPTOOL" run
```

---

### Post by Impavidus on 2012-12-25
I'm not familiar with programming in java, but what could be the case (not java related at all) is that after your script has finished the terminal closes immediately, giving you no time to view its output. When you start it from the terminal this is no problem, as the prompt shows up and waits for your next input. Adding the following lines at the end of the script (and at every other location where it could terminate) could help:```
echo 'Press enter to close'
read
```It will wait for you to close the terminal.

There might be a problem (I don't really think there is) with the shell being interactive or not, but I've got no idea of the details in that matter.

---

### Post by MishaX2 on 2012-12-25
You could also try running another script which acts as a launcher.

For example you could use the following script for double clicking:
```

#!/bin/bash
./yourscript.sh 2>&1 | gedit

```
This will open a new gedit window with the output of your program.

---

### Post by stevejluke on 2012-12-25
Thanks guys, that helped.  The 'Press enter to close. /read' option didn't work (the windows didn't stay open) but feeding the output to gedit did. 

I see the error message I get is this:
> LaunchMapTool.sh: Error: Can't find Java executable.

This message is displayed when the script can't fine the JAVA_HOME variable.  But it only has that problem when I double click on the script.  When I run from terminal the error doesn't show up and the Java application runs.

The JAVA_HOME variable is set in my ~/.bashrc file (and the PATH variable modified to include ${JAVA_HOME}/bin) as such:
```
# Add Java to the path
export JAVA_HOME=/fast/Java/jdk/jdk7
export PATH=${PATH}:${JAVA_HOME}/bin

```

This is definitely caused by the fact that the $JAVA_HOME variable is not visible to the script when I double click.  I created a new script:
```
#!/bin/bash
echo "Java is found here: " ${JAVA_HOME} 2>&1 | gedit
```
When I double click I get this in gedit:
> Java is found here: 
But when I run it from the terminal I get this:
> Java is found here:  /fast/Java/jdk/jdk7
I have restarted the computer a couple times, so it isn't that I set the value in .bashrc and it hasn't been executed since.

Is there someplace else (besides or instead of ~/.bashrc) where I should be exporting the $JAVA-HOME variable so it is always visible when needed?

---

### Post by MishaX2 on 2012-12-25
Don't know for sure, but maybe you could try this:
```

#!/bin/bash
source ~/.bashrc
echo "Java is found here: " ${JAVA_HOME} 2>&1 | gedit

```
I can't test it since my set up is kind of different, sorry...

---

### Post by stevejluke on 2012-12-26
Ok, I found the answer.  The ~/bashrc is not the correct place to put it.  You should put environment variables in the ~/.pam_environment file.  This file didn't exist for me.  Minimally, I did this:
```
JAVA_HOME=/fast/Java/jdk/jdk7
```
That worked as far as this application was concerned.  I also wanted to add the /bin directory to the $PATH variable which proved much more dificult.  After reading some discussions on whether you need to add the " DEFAULT" to the line or not, I tried it both ways and could only get it to work as below:
```
PATH DEFAULT=${PATH}:${JAVA_HOME}/bin
```
I did need the DEFAULT to get it to work, and I needed to put the curly brackets around the two variables as well (although none of the samples I saw used them.)  The symptom for it not working was the user would log in then immediately get booted back to the login screen.

Anyways, got it all working now.  Thanks.

---

