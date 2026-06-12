---
title: "bash script string manipulation help needed"
date: 2006-08-17
forum: Programming Talk
---

### Post by Lunar_Lamp on 2006-08-17
I'm pretty new to bash scripting and any kind of coding whatsoever.  I am writing a script to keep me updated with the cricket scores, and have managed to get an output from a website in the following format (I use square brackets to mark limits, but they are not present):

TEAM[space]RUNS[hypen]WICKETS[space]OVERS[space]JUNK

How can I extract the values of each?  I want to create each of those as variables, i.e. so I can call upon each variable, and use them further in the script.

I hope I've made what I want to do clear, I don't know how to do it myself, so I don't know if I'm asking in the right way.  I think it may be possible with sed, but I don't know how to use it properly, and the guides I can find don't really help me too much.

Thanks, I'd appreciate some help!

---

### Post by moma on 2006-08-17
Suppose your data is in "cricket.txt" file.  
And fields are delimited by a single space.

```
IFS=" "
while read team runs wickets overs rest
do 
   if test "$team" != ""; then 
      echo "$team  got $runs runs and $wickets wickets."
  fi 
done < cricket.txt
```

---

### Post by Lunar_Lamp on 2006-08-18
IFS! Of course!  I was just reading about it the other day.

Could I instead of using "done <cricket.txt" use "done < $ExtractedScore", or does it have to come from a file?

I see how using IFS works with spaces, but the wickets and runs are separated by a hypen, how would I go about getting those two pieces of information out?

---

### Post by Lunar_Lamp on 2006-08-18
OK, I have managed to get most of the script working how I want it to.  However, there is one thing I am not sure about.

```
function Wickets {
	IFS="-"
	echo "$CurrentScore" > $PWD/wickets.txt 
	while read teamruns wicketsplus
	do 
   		if test "$teamruns" != ""; then 
	WicketsDown="${wicketsplus:0:1}"
  fi 
done < wickets.txt
}
```

That code snippet works, and if I echo "WicketsDown" I get the number I want.  However, I want to use a line like this:

```
if [ "$WicketsDown" -gt "$OldWicketsDown" ] ; then
    #do stuff
fi
```

However, as the values of WicketsDown and OldWicketsDown are strings, I cannot do integer maths with them, and using "declare -i WicketsDown" to convert them to ints doesn't seem to work either.  What am I doing wrong?  How can I check if the value of WicketsDown is greater than OldWicketsDown?

---

### Post by moma on 2006-08-19
You can create a function that converts $1 to integer. 

```
function intval {
# $1: String or numeric value
# Sample:  v=$(intval "123 t")

# Remove all non numeric characters
 n="$(echo "$1" |  sed 's/[^0-9]//g')"
 echo "$n"
}

# Remember to initialize OldWicketsDown.
OldWicketsDown=0 

...
if test "$teamruns" != ""; then
         wicketsplus=$(intval $wicketsplus)
         WicketsDown="${wicketsplus:0:1}"

          if  [ ! -z WicketsDown -a  "$WicketsDown" -gt "$OldWicketsDown" ] ; then
                echo "$WicketsDown -gt  $OldWicketsDown"
          fi
          ...
fi 

```

---

### Post by Lunar_Lamp on 2006-08-19
I'm confused.  As far as I can tell "intval" just removes any non-numeric characters, but I already have a way of extracting just the number I want.  The value of WicketsDown when I want to use it is already just a number, e.g. "3".  The same happens with OldWicketsDown, it already is just a number.  But if I try to do arithmetic comparisons with them, I'm told they are not ints.

My whole script is here:

```
#!/bin/bash
#
#
# A script that goes to the bbc's "ball by ball update" page, and takes the score off the page, and then does stuff with # it.
#
# TODO:
#
# wicket assessment
# sound file for wickets
# get nice graphical appearance rather than command line ugliness
# put some of the more recent stuff into functions to make the code easier to read
# tidy up stuff, especially comments - they are making the code hard to read.


##########################################
# Function to give a pretty intro buffer #
##########################################

function PrettyIntro {
echo ""
echo "		   #*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#"
echo "		   #*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#"
echo "		   #*~*#                           #*~*#"
echo "		   #*~*# Welcome to CricketEd v0.1.#*~*#"
echo "		   #*~*#                           #*~*#"
echo "		   #*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#"
echo "		   #*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#"
echo ""
echo "	    This script relies on the BBC's cricket score service."
echo "		            Use ctrl+c to exit."
echo ""
echo ""
}


##############################################
# Function to decide where to get the scores #
##############################################

function ScorePage {
echo "This is a placeholder for ScorePage - no function inserted here yet"	
#idea 1
#if "wget url = 404"... then go onto next possibility (scroll through options 1-10 or so). Don't know 404 error exit status.
#idea 2
#wget from file of urls provided - but then how do I make it choose the correct one?  Perhaps write a first 'config' script, getting input from the user as to which score they wish to use!  This could work!
}


############################################
# Function to get the latest cricket score #
############################################

function LatestUpdate {

	# Download the page from bbc.  The "1" at the end may change.  The -nv option means "not verbose" and supresses output apart from error messages, but is too noisy for the output, so 'q' used instead.
	wget -q http://newsimg.bbc.co.uk/sport1/shared/bsp/hi/cricket/in_vision/html/in_vision1.stm ;

	# Rename the downloaded file to 'latestupdate' - works in the present  working directory; think the $PWD is redundant
	mv *.stm $PWD/latestupdate ;

	# Magic. Declares the variable $CurrentScore - extracting the score from the downloaded webpage.
	CurrentScore=`less $PWD/latestupdate | grep \<title\> | sed -e "s/\<title\>/ /g" | sed -e "s/</ /g" | sed -e "s/>/ /g"`
}


###################################################################
# Function to delete the oldscore, and copy new score to oldscore #
###################################################################

function ArchiveLatest {
	rm $PWD/oldupdate.txt
	mv $PWD/latestupdate $PWD/oldupdate.txt
	OldScore=`less $PWD/oldupdate.txt | grep \<title\> | sed -e "s/\<title\>/ /g" | sed -e "s/</ /g" | sed -e "s/>/ /g"`
}



###########################################################
# Function to get wickets out of the downloaded page code #
###########################################################

function Wickets {
	IFS="-"
	echo "$CurrentScore" > $PWD/wickets.txt 
	while read teamruns wicketsplus
	do 
   		if test "$teamruns" != ""; then 
	WicketsDown="${wicketsplus:0:1}"
  fi 
done < wickets.txt
}


###############################################################
# Function to get old wickets out of the downloaded page code #
###############################################################


function OldWickets {
	IFS="-"
	echo "$OldScore" > $PWD/oldwickets.txt 
	while read oldteamruns oldwicketsplus
	do 
   		if test "$oldteamruns" != ""; then 
	OldWicketsDown="${oldwicketsplus:0:1}"
  fi 
done < oldwickets.txt
}


#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#
#*~*#*~*#	MAIN SCRIPT	 *~*#*~*#*~*#
#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#

# This clears the screen that makes it look nicer.
clear

#this creates the file $PWD/oldupdate.txt if it's not already there, avoiding an unsightly error message
echo " " > $PWD/oldupdate.txt

# This is an infinite while loop; to quit needs to be "ctrl+c". Unless setup a quit-key.
while true
	do

		PrettyIntro ;
		LatestUpdate ;
		Wickets ;
		OldWickets ;
		ArchiveLatest ;
		
		#check if there is a score being given out, if not exit, else echo the score.  It doesn't appear to work properly, though it doesn't hinder proper working.
		if [ "$CurrentScore" = "*will appear here*" ] ; then
			echo "     There is no play at the moment."
			echo "Perhaps you should try later, or tommorrow."
			exit
		else
			echo "		$CurrentScore" ;
		fi		

		#check if a wicket has gone down since last update
		if [ "$WicketsDown" -gt "$OldWicketsDown" ] ; then
			echo "He's gone!" #placeholder response
		elif [ "$WicketsDown" -eq "$OldWicketsDown" ] ; then
			echo "They're both still there." #placeholder response
		fi
		
		# the sleep number can be decreased to update more often
		sleep 100;

		#purely asthetic, clear the screen to make things look like it's just the score changing
		clear

	done

```

---

### Post by Tomosaur on 2006-08-19
Try changing this:
```

#check if a wicket has gone down since last update
		if [ "$WicketsDown" -gt "$OldWicketsDown" ] ; then
			echo "He's gone!" #placeholder response
		elif [ "$WicketsDown" -eq "$OldWicketsDown" ] ; then
			echo "They're both still there." #placeholder response
		fi

```

to this:

```

   #check if a wicket has gone down since last update
                if [[ $WicketsDown -gt $OldWicketsDown ]] ; then
                        echo "He's gone!" #placeholder response
                elif [[ $WicketsDown -eq $OldWicketsDown ]] ; then
                        echo "They're both still there." #placeholder response
                fi

```

I'm not sure if this actually works, since I know nothing about cricket, and haven't done any extensive testing using the actual website info (ie, checking in a browser). However, when you use 
```
"$myVariable"
``` instead of ```
$myVariable
```, bash will treat it as a string, whereas omitting the quotes allows bash to use the actual value. The double square brackets tells the if statement that you're using numerical values rather than strings.

Again, I haven't done any actual testing, but I didn't get any errors when I ran your script with my changes, take a look:
```

                   #*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#
                   #*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#
                   #*~*#                           #*~*#
                   #*~*# Welcome to CricketEd v0.1.#*~*#
                   #*~*#                           #*~*#
                   #*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#
                   #*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#*~*#

            This script relies on the BBC's cricket score service.
                            Use ctrl+c to exit.


                           Eng  49-1   10.5 ovs
He's gone!

```

---

### Post by Lunar_Lamp on 2006-08-19
Thanks, I confess that in my newness to the world of bash, I hadn't realised that you could use $myvar in an if statement without the "", nor what effect it would have.  Thanks a lot!

---

