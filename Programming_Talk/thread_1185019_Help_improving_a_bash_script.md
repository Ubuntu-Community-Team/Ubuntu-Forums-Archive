---
title: "Help improving a bash script"
date: 2009-06-11
forum: Programming Talk
---

### Post by fhsm on 2009-06-11
I'm trying to learn bash scripting.  The problem I'm working on is wrapping my apt-get installs in a script that will log the name of the package I've installed.  I've got a script that 'works' but that's about all.  I'm hoping someone with a bit more knowledge and experience could suggest improvements (not so much in functionality but in execution).  

```

#!/bin/bash
# wrapper around apt-get install that logs the application being installed

LOG_FILE=~/backup/apt-get_install.log

if [ "$1" == "install" ]; then 
	if [ $2 ]; then
		if [ "$2" != "-s" ]; then
			args=("$@")
			for (( i = 1 ; i < ${#args[@]} ; i++ )); do
				DISC=$(apt-cache show ${args[$i]} | grep --max-count=1 -i "description:" | cut -c14-)
				if [ "$DISC" == "" ]; then 
					echo -e "\e[0;31mAborting at ${args[$i]} \e[0m\n" 
					exit 1
				else
					sudo apt-get install ${args[$i]}
					if [ $? ]; then
						RIGHT_NOW=$(date +"%Y-%m-%d %a %H:%M")
						echo -e "${args[$i]} \t=>\t $DISC \t@\t$RIGHT_NOW  \n" >> $LOG_FILE
						echo -e "LOGGED: ${args[$i]} installed at $RIGHT_NOW \n"
					else
						echo -e "\e[0;31mInstall of ${args[$i]} failed.\e[0m"
						exit 1
					fi
				fi
			done

		else 
			if [ $3 ]; then
				echo -e "Running simulated install now: \n"
				args=("$@")
				for (( i = 2 ; i < ${#args[@]} ; i++ )); do
					sudo apt-get install -s ${args[$i]}
					if [ "$?" != "0" ]; then
						echo -e "\e[0;31mERROR: on ${args[$i]}\e[0m"
					fi
					echo -e "\n"
				done				
			else
				echo "Please select a program to simulate installing"
			fi
		fi
	else
		echo "Please select a program to install"
	fi 
else
	echo "This script should be run as a proxy for apt-get install to log installs in ~/backup/apt-get_install.log"
fi

```

---

### Post by Eeqmcsq on 2009-06-11
This is more of a coding style thing, but I'm not a big fan of massive if-else blocks in general unless there are no other alternatives. I prefer to do the error checking first and immediately returning from a function or in this case, exiting the script. Here's a rough example. I am _NOT 100% SURE_ if this syntax is correct, but you should get the idea:

```
if [ "$1" != "install" ]; then 
  echo "This script should be run as a proxy for apt-get install to log installs in ~/backup/apt-get_install.log"
  exit 1
fi

if [ ! $2 ]; then
  echo "Please select a program to install"
  exit 1
fi 

#More error checking

#Code that does stuff

```

I have found that in this style, it organizes all of the error checking to the upper half of the script and puts the real stuff in the bottom half.

As far as the code itself, I would add some "exit 1" in the error cases. That way, if you chain your script with other commands at the command line, a failure in your script won't cause the other commands to be executed.

---

### Post by fhsm on 2009-06-11
> **Eeqmcsq said:**
> This is more of a coding style thing, but I'm not a big fan of massive if-else blocks in general unless there are no other alternatives. I prefer to do the error checking first and immediately returning from a function or in this case, exiting the script. Here's a rough example. I am _NOT 100% SURE_ if this syntax is correct, but you should get the idea:

```
if [ "$1" != "install" ]; then 
  echo "This script should be run as a proxy for apt-get install to log installs in ~/backup/apt-get_install.log"
  exit 1
fi

if [ ! $2 ]; then
  echo "Please select a program to install"
  exit 1
fi 

#More error checking

#Code that does stuff

```

I have found that in this style, it organizes all of the error checking to the upper half of the script and puts the real stuff in the bottom half.

As far as the code itself, I would add some "exit 1" in the error cases. That way, if you chain your script with other commands at the command line, a failure in your script won't cause the other commands to be executed.

Thanks for both suggestions.  I'm going to add exit codes right now as you suggested.  That is an obvious and simple thing to change.  I agree that the if pyramid is really hard to read and your idea is better.  I'll work on that later.

UPDATE: So I added the exit codes to the loop where actual install is happening.  I think having an install fail and exit 0 would be a problem.  For the -s I want it to go through the whole thing which means my exit is would be whatever the last install -s exited with.  That's not all that helpful.  What I really want to do is have it attempt all the install simulations and then exit 1 if any of them exited one, right?

---

### Post by Eeqmcsq on 2009-06-11
Otherwise, once I stripped down all of the error handling and got down to the meat of the script, it's a neat little script. I also discovered a new command to play with after reading the script, "apt-cache". 

One thing that threw me off was the variable $DISC. I think you meant $DESC, for description.

Also, for this line:

echo -e "$2 \t=>\t $DISC \t@\t$RIGHT_NOW  \n" >> $LOG_FILE

I'd put the $RIGHT_NOW as the first paramater. The description will most likely vary in length, while $RIGHT_NOW will most likely be the same length, so your log file will be easier to read if your $RIGHT_NOW came first.

The only other issue I have might be that the script checks for the "-s" flag as the second parameter only. If this script is for yourself, that's probably OK. But there's probably a way to check for the "-s" flag in all of the incoming parameters. I'm not sure how off the top of my head. You might just have to loop through all parameters to check.

---

### Post by Eeqmcsq on 2009-06-11
> For the -s I want it to go through the whole thing which means my exit is would be whatever the last install -s exited with. That's not all that helpful. What I really want to do is have it attempt all the install simulations and then exit 1 if any of them exited one, right? I don't understand what you mean. In your script, 

echo -e "Running simulated install now: \n"
sudo apt-get install -s $3

According to this code, you can only simulate a package install one package at a time. Do you have some other script containing a list of packages and that other script is calling this script?

---

### Post by fhsm on 2009-06-11
All very good points.  I've been trying to edit my first post but I think it's time for a bit of bootleg version control.  Here's how it looks now (thanks again).

```
#!/bin/bash
# wrapper around apt-get install that logs the application being installed

LOG_FILE=~/backup/apt-get_install.log
args=("$@")

if [ "$1" != "install" ]; then 
	echo "This script should be run as a proxy for apt-get install to log installs in $LOG_FILE"
	exit 1
fi

if [ ! $2 ]; then
	echo "Please select a program to install or use -s to simulate an install"
	exit 1
fi

if [ "$2" == "-s" ]; then
	if [ $3 ]; then
		SIM_EXIT=0
		echo -e "Running simulated install now: \n"
		for (( i = 2 ; i < ${#args[@]} ; i++ )); do
			sudo apt-get install -s ${args[$i]}
			if [ "$?" != "0" ]; then
				echo -e "\e[0;31mERROR: on ${args[$i]}\e[0m"
				SIM_EXIT=1
			fi
			echo -e "\n"
		done
		exit $SIM_EXIT			
	else
		echo "Please select a program to simulate installing"
		exit 1
	fi
	
else
	for (( i = 1 ; i < ${#args[@]} ; i++ )); do
		DESC=$(apt-cache show ${args[$i]} | grep --max-count=1 -i "description:" | cut -c14-)
		if [ "$DESC" == "" ]; then 
			echo -e "\e[0;31mAborting at ${args[$i]} \e[0m\n" 
			exit 1
		else
			sudo apt-get install ${args[$i]}
			if [ $? ]; then
				RIGHT_NOW=$(date +"%Y-%m-%d %a %H:%M")
				echo -e "$RIGHT_NOW\t${args[$i]}\t=>\t$DESC\n" >> $LOG_FILE
				echo -e "LOGGED: ${args[$i]} installed at $RIGHT_NOW \n"
			else
				echo -e "\e[0;31mInstall of ${args[$i]} failed.\e[0m"
				exit 1
			fi
		fi
	done
fi

```

What do you think about my choice to put the errors in red?  Is that a mistake?  I think it makes the results much easier to red but colors and terminals are something I really don't have a good grasp on.  

Also do you think I should be sending them to stderr?  If so how would I do that?  Something like ```
echo "error" >&2 
```?

---

### Post by Eeqmcsq on 2009-06-11
OK, I see what you mean now by the loop that simulates installing each package. And your use of $SIM_EXIT looks right to me. I see a few places where I could reorganize the code to collapse the indentations furthur, but that's just my style.

By the way, did you double check this line to make sure the syntax is correct?

if [ ! $2 ]; then

I made that up off the top of my head. This is the line I'm not 100% sure about, syntax-wise.

---

### Post by Eeqmcsq on 2009-06-11
Sorry, I skimmed through your reply, so I didn't see these questions at the bottom.

> What do you think about my choice to put the errors in red? Is that a mistake? I think it makes the results much easier to red but colors and terminals are something I really don't have a good grasp on.


I've never done colors in my own scripts, but when I compile code at work, the errors always show up in red, so it's really eye catching. But then, my color scheme is while text on black background, so the red would look good for me.

The bad thing about colors is that if you wanted to take the output of your script and redirect them to another command, I THINK the color codes will end up as part of the output. I've never tried this either, so I'm not 100% sure.

> Also do you think I should be sending them to stderr? If so how would I do that? Sorry, can't help you there. Never played with stderr. In my personal scripts, I direct everything to stdout so I can redirect ALL of my script's output to a temp file that I can view for debugging later.

---

### Post by fhsm on 2009-06-11
```
 
if [ ! $2 ]; then 
    ...
fi

```

Is correct, I read the docs and tested it (and some of the other similar ways one might imagine doing the same thing).

With colors and error vs. out you came up with the same concerns I did.  On the plus side if you do colors and errors together then you don't have to worry about the unprintable characters showing up in your redirected output (unless you grab both stdout and stderr).  

I'm sure a purest would say no way on the colors, but I'm not at all sure what a purest would say about using standard error.

Where else would you collapse the code?

---

### Post by Eeqmcsq on 2009-06-11
Here's my personal style. Logically, the code is the same as yours.
```
if [ "$2" == "-s" ]; then
	if [ ! $3 ]; then
		echo "Please select a program to simulate installing"
		exit 1
	fi
	SIM_EXIT=0
	echo -e "Running simulated install now: \n"
	for (( i = 2 ; i < ${#args[@]} ; i++ )); do
		sudo apt-get install -s ${args[$i]}
		if [ "$?" != "0" ]; then
			echo -e "\e[0;31mERROR: on ${args[$i]}\e[0m"
			SIM_EXIT=1
		fi
		echo -e "\n"
	done
	exit $SIM_EXIT
fi	

for (( i = 1 ; i < ${#args[@]} ; i++ )); do
	DESC=$(apt-cache show ${args[$i]} | grep --max-count=1 -i "description:" | cut -c14-)
	if [ "$DESC" == "" ]; then 
		echo -e "\e[0;31mAborting at ${args[$i]} \e[0m\n" 
		exit 1
	fi
	sudo apt-get install ${args[$i]}
	if [ ! $? ]; then
		echo -e "\e[0;31mInstall of ${args[$i]} failed.\e[0m"
		exit 1
	fi
	RIGHT_NOW=$(date +"%Y-%m-%d %a %H:%M")
	echo -e "${args[$i]} \t=>\t $DESC \t@\t$RIGHT_NOW  \n" >> $LOG_FILE
	echo -e "LOGGED: ${args[$i]} installed at $RIGHT_NOW \n"
done

```

---

### Post by fhsm on 2009-06-11
I suspected you would say something like that.  I like the consistency of moving the checking to the top of the file / top of a logical block.  I was actually working on that in parallel with you, but I guess I've got trust issues with exit (or a love affair with else).  Sitting here right now I'd love to just exit out and dump the else blocks... in a month when I'm looking at it I think I'd rather have the explicit else.  Maybe it's a matter of taste / style / or just that you've got more experience.  

Any ideas on a nice way to catch the -s if it isn't the 2nd argument?  Given that I'm going to be the only one using it and I always put -s right after install the complexity of an additional loop just to find -s is overkill.  But it seems like bash should have some real argument parsing built in (after all the flag / switch / argument syntax conventions aren't exactly in flux).

---

### Post by Eeqmcsq on 2009-06-11
> Maybe it's a matter of taste / style / or just that you've got more experience. I think it's a style and experience. If there's an error and nothing more should be done, I like to return or exit early to ENSURE that no other code can be executed. I do this in my C/C++ code as well as my bash scripts. I ran into an actual case last month where the coder's if/else blocks had a loophole in the error handling that eventually led to a null pointer crash further down the function. Had he did an early return on the null pointer, the loophole would not exist. In other words, if the code fails, get the heck out of there before anything else gets messed up.

> Any ideas on a nice way to catch the -s if it isn't the 2nd argument?Maybe there's a bash way of doing it, but other than a loop, no easy way I can think of off the top of my head.

---

