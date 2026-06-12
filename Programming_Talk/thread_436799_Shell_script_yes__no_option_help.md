---
title: "Shell script yes / no option help"
date: 2007-05-08
forum: Programming Talk
---

### Post by Snoopy381 on 2007-05-08
im trying to write a shell script and in certain parts i want it to stop and ask if the user wants to continue. iv got a pretty simple bit of code that does this at the moment

```
echo starting Test
echo "Do you wish to proceed <y or n> ? \c"
read WISH
echo

if [ $WISH = "n" ] ; then
 echo you chose no, good bye  
exit

fi


if [ ! $WISH = "y" ] ; then
 echo in vaild optin g - exiting 
 exit
fi        


echo you chose y
echo test successful
```


this basically asks do you want to continue, if no if says good bye and exits, if invalid option (not y or n), it says invalid option then exits, if y it just continues with the script


the problem with this script is that if the user accidentally hits any button other than y the script will end.

what im looking for is a new script of modification to my existing script that will make it so that the script will only accept y or n as options. eg you enter n, script quits, you enter y, script continues, you enter anything else, the script says "invalid option please choose again," then prompts you for Do you wish to proceed <y or n> ? 

im sure this shouldn't be hard (loop?) i just don't know how to do it. can anyone give me a hand please?

---

### Post by LaRoza on 2007-05-08
How about an "else" statement that catches all other options and gives you a message and starts over again?

---

### Post by rjack on 2007-05-08
If you like it you can adapt the first function below. The second one is just an example about how to use it.

The loop runs through the allowed options and set the default one if there's no match. 
You can add a ```
echo "Valid options are $@"
``` in the fallback-to-default-if and call the function from within a loop until it returns something not zero.

```

# AskUser choice1 choicei2 ...
#
# Prompt user with a set of choice.
# Parameters: each parameter is a possible choice. A parameter within square
# braces is the default choice.
# Return
#       0 if user choosed default
#       1 if user choosed first choice
#       2 if user choosed second choice
#       ...
#       max 255!

function AskUser {
        local choices=
        local input=
        local match=$FALSE
        # Construct a nice list of possible choices
        for i in $@
        do
                choices="$choices / $i"
        done
        # Display list, removing heading garbage due to loop.
        echo -n "(${choices# / }) "

        read input

        i=0
        while [[ "$1" && match -eq FALSE ]]
        do
                i=$(($i+1))
                if [[ "$1" = "$input" ]]
                then
                        match=$TRUE
                fi

                # echo "[DEBUG] $i test: $1 = $input? $match"

                shift
        done

        # No match, fallback to default.
        if [[ match -eq FALSE ]]
        then
                i=0
        fi

        # echo "[DEBUG] returning $i"

        return $i
}

# Warn if called by root and let user abort.
# Parameters:
#       $1 = custom warning message.
# Exit if root and user don't types "yes".

function WarnRoot {
        local input=
        local msg="You are running this script as root!"

        # Argument overrides default warning message.
        if [[ $1 ]]
        then
                msg=$1
        fi

        # If root ask for confirmation.
        if [[ $UID = $ROOT_UID ]]
        then
                echo $msg
                echo -n "Do you wish to continue? "
                AskUser "yes" "[no]"
                if [[ $? -eq 0 || $? -eq 2 ]]
                then
                        echo "Aborted"
                        exit 
                fi
        fi
}
```

---

### Post by finer recliner on 2007-05-08
psuedo code:
```

do{
echo do you want to continue?
read $WISH
}while ($WISH != n||y)
if($WISH == y){...}
if($WISH == n){...}

```


by using a do-while loop, your code will repeatly ask the user until for input until a y or n is hit. you may need  to clear the readin buffer as well. im not as familiar with bash scripting.

LaRoza's idea sounds like recursion (which is way less efficient than a simple loop).

---

### Post by LaRoza on 2007-05-08
It was recursion, I am unfamiliar with shell scripting and was not sure of it capabilities, I didn't of the looping structures for bash, I recommend the loop also (now).

---

### Post by hartz on 2007-05-08
The below code will also accept variations like "Yes".

```
while true
do
  echo -n "Please confirm (y or n) :"
  read CONFIRM
  case $CONFIRM in
    y|Y|YES|yes|Yes) break ;;
    n|N|no|NO|No)
      echo Aborting - you entered $CONFIRM
      exit
      ;;
    *) echo Please enter only y or n
  esac
done
echo You entered $CONFIRM.  Continuing ...
```

---

### Post by Snoopy381 on 2007-05-08
thanks guys, this is EXACTALLY what i wanted :).

and thanks hartz3 your script worked straight out of the box and has even more functionality than i was hoping for :)

---

### Post by hartz on 2007-05-10
Only a pleasure.

Now you need to put it in a function.

then call the function every time you need the user to confirm

For example
```

#!/bin/sh

# First we define the function
function [COLOR="Blue"]ConfirmOrExit[/COLOR]() {
[COLOR="Red"]while true
do
  echo -n "Please confirm (y or n) :"
  read CONFIRM
  case $CONFIRM in
    y|Y|YES|yes|Yes) break ;;
    n|N|no|NO|No)
      echo Aborting - you entered $CONFIRM
      exit
      ;;
    *) echo Please enter only y or n
  esac
done
echo You entered $CONFIRM.  Continuing ...[/COLOR]
}

# At the end we put the main program

... # Do stuff here
[COLOR="Blue"]ConfirmOrExit[/COLOR]
... # Do more stuff here
[COLOR="Blue"]ConfirmOrExit[/COLOR]
... # etcettera
```

---

