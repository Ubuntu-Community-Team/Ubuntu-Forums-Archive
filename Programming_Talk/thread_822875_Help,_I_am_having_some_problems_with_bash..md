---
title: "Help, I am having some problems with bash."
date: 2008-06-08
forum: Programming Talk
---

### Post by Yuzem on 2008-06-08
I am trying to make a tui (text user interface) script in bash and I'm having some problems.

**1 - I will start with the simpler one:**
```
while read -r line; do
	echo $line
done < 'somefile'

echo $line
```
The last echo doesn't work, the variable is empty and I don't know why.
What I really want to do is this:
```
while read -a line; do
	continue
done < 'somefile'

echo ${line[*]}

```
That should generate an array but it doesn't. Am I doing something wrong?
The simpler way:
```
read -a var < 'somefile'
```
Doesn't work neither... :(

**2 - Another problem:**
I need to grab some input keys from the user:
```
while [ 1 = 1 ]; do
	read -n1 input

	case "$input" in
		[a-z] )
			echo "   "lowercase
		;;
		[A-Z] )
			echo "   "uppercase
		;;
		* )
			echo "unknown key"
	esac
done
```
If I press an uppercase character it takes it as a lowercase... :confused:
I could put all the uppercase characters before but why it doesn't work the other way?

**3 - The most complicated one:**
With the previous example: How do I grab special keys like "backspace" "enter" "space bar" "control+*" "alt+*"?

---

### Post by ghostdog74 on 2008-06-08
> **Yuzem said:**
> 
[/CODE]
That should generate an array but it doesn't. Am I doing something wrong?
The simpler way:
```
read -a var < 'somefile'
```
Doesn't work neither... :(

what are you trying to do with the "somefile".? show an example

> 
**2 - Another problem:**
I need to grab some input keys from the user:
```
while [ 1 = 1 ]; do
	read -n1 input

	case "$input" in
		[a-z] )
			echo "   "lowercase
		;;
		[A-Z] )
			echo "   "uppercase
		;;
		* )
			echo "unknown key"
	esac
done
```
If I press an uppercase character it takes it as a lowercase... :confused:
I could put all the uppercase characters before but why it doesn't work the other way?

it works for me. make sure you use bash, not dash

---

### Post by Yuzem on 2008-06-08
> **ghostdog74 said:**
> what are you trying to do with the "somefile".? show an example
For example:
```
read -a var < <(grep query 'somefile')
```
I want every line on a different variable. An array with the result line by line.
Because the above command only sets one variable I use the while loop:
```
while read -a line; do
	continue
done < 'somefile'

echo ${line[*]}
```
But it doesn't work...

> **ghostdog74 said:**
> 
it works for me. make sure you use bash, not dash
I am using bash under Hardy. The script starts with: #!/bin/bash

---

### Post by stroyan on 2008-06-08
Your first attempt at reading one line at a time is reading each line
into the 'line' variable and overwriting the value of the previous line.
The final failing read in the loop is clearing the value of 'line'.
You can read a file directly into an array variable with
```

A=( $(<somefile) )
echo "full file:"
echo "${A[@]}"
echo "first line:"
echo ${A[0]}
A=( $(grep query somefile) )
echo "matching lines:"
echo "${A[@]}"

```

The [a-z] and [A-Z] sequences will vary depending on locale.
The collation order for locale en_US.UTF-8 is "...aAbBcC...".
You can get a portable range of upper and lower case characters with
```

#!/bin/bash

while [ 1 = 1 ]; do
	read -n1 input

	case "$input" in
		[[:lower:]] )
			echo "   "lowercase
		;;
		[[:upper:]] )
			echo "   "uppercase
		;;
		* )
			echo "unknown key"
	esac
done

```

If you want your script to see the backspace character you will need
to disable the line by line editing that a tty normally does for user
input.  You can do that with "stty raw" and return to normal with
"stty cooked".  If you do that you need to be careful restore the
normal tty settings when your script ends either successfully or
abnormally.  Leaving it set strangely can make you original login
shell seem broken.

---

### Post by ghostdog74 on 2008-06-08
> **Yuzem said:**
> For example:
```
read -a var < <(grep query 'somefile')
```
I want every line on a different variable. An array with the result line by line.
Because the above command only sets one variable I use the while loop:
```
while read -a line; do
	continue
done < 'somefile'

echo ${line[*]}
```
But it doesn't work...

my suggestion is to process the lines as you go. That way, you don't need to store in arrays. If you put those lines in arrays, you are going to use them sometime later anyway. So why not process them as you iterate the file.
```

while read line 
do
 #process line
done

```

---

### Post by Yuzem on 2008-06-08
> **stroyan said:**
> Your first attempt at reading one line at a time is reading each line
into the 'line' variable and overwriting the value of the previous line.
The final failing read in the loop is clearing the value of 'line'.
But I am using the -a flag that should create an array.
> **stroyan said:**
> 
You can read a file directly into an array variable with
```

A=( $(<somefile) )
echo "full file:"
echo "${A[@]}"
echo "first line:"
echo ${A[0]}
A=( $(grep query somefile) )
echo "matching lines:"
echo "${A[@]}"

```
It doesn't work. It doesn't assign by lines, it breaks by spaces.

> **stroyan said:**
> 
The [a-z] and [A-Z] sequences will vary depending on locale.
The collation order for locale en_US.UTF-8 is "...aAbBcC...".
You can get a portable range of upper and lower case characters with
```

#!/bin/bash

while [ 1 = 1 ]; do
	read -n1 input

	case "$input" in
		[[:lower:]] )
			echo "   "lowercase
		;;
		[[:upper:]] )
			echo "   "uppercase
		;;
		* )
			echo "unknown key"
	esac
done

```
That works thanks. :)

> **stroyan said:**
> 
If you want your script to see the backspace character you will need
to disable the line by line editing that a tty normally does for user
input.  You can do that with "stty raw" and return to normal with
"stty cooked".  If you do that you need to be careful restore the
normal tty settings when your script ends either successfully or
abnormally.  Leaving it set strangely can make you original login
shell seem broken.
Could you give me an example of how to get those keys in raw mode?

> **ghostdog74 said:**
> my suggestion is to process the lines as you go. That way, you don't need to store in arrays. If you put those lines in arrays, you are going to use them sometime later anyway. So why not process them as you iterate the file.
```

while read line 
do
 #process line
done

```
I need to use the variables in different parts of the script.

---

### Post by geirha on 2008-06-09
> **Yuzem said:**
> But I am using the -a flag that should create an array.

It doesn't work. It doesn't assign by lines, it breaks by spaces.


This should break it only on newlines for the array:
```

OLDIFS=$IFS     # Remember the initial value of the internal field seperator
IFS=$'\n'       # Set the internal field seperator to newline only
lines=( $(<somefile) )
IFS=$OLDIFS     # Restore the internal field seperator
echo line 1: ${lines[0]}
echo line 2: ${lines[1]}

```

---

### Post by Yuzem on 2008-06-09
> **geirha said:**
> This should break it only on newlines for the array:
```

OLDIFS=$IFS     # Remember the initial value of the internal field seperator
IFS=$'\n'       # Set the internal field seperator to newline only
lines=( $(<somefile) )
IFS=$OLDIFS     # Restore the internal field seperator
echo line 1: ${A[0]}
echo line 2: ${A[1]}

```

Ok, that worked, thanks.

About the hotkeys:
```
#!/bin/bash

CTRL_X=$'\x18'
stty -echo
stty raw

while [ 1 ]; do
	read -n3 input

	case "$input" in
		'Q' )	stty echo
			stty cooked
			exit
		;;
		"${CTRL_X}" )
			echo "   "control x
	esac
done
```
With that I get control+x and it also works without stty raw.
How do I get the other keys?

---

### Post by geirha on 2008-06-09
That's nice, I wasn't aware you could catch such keypresses in bash. However, using your code I managed to capture some more. Ctrl+C is as you probably know a special action, sending SIGINT to the process. Had to use a trap to capture that one.

Use Ctrl+V followed by your special keypress to get a character for it. (Copy pasting the ^X, ^V and ^? from below won't work)
[php]
#!/bin/bash

CTRL_X=^X       # To get the Ctrl+X character, hit Ctrl+V Ctrl+X
CTRL_V=^V       # Ctrl+V Ctrl+V
BACKSPACE=^?    # Ctrl+V Backspace
stty -echo

# SIGINT is the signal sent when ^C is pressed.
trap 'echo "Ctrl+c"' SIGINT
trap 'stty echo' EXIT

while true; do
    read -n1 input
    case "$input" in
        [qQ] )  break ;;
        "${CTRL_X}" ) echo "Ctrl+x" ;;
        "${CTRL_V}" ) echo "Ctrl+v" ;;
        "${BACKSPACE}" ) echo "backspace" ;;
    esac
done
[/php]

---

### Post by Yuzem on 2008-06-09
I copied your script and the control+c is working! but the others don't...

Maybe there is a way to do the same thing for the backspace and the enter key...
I need backspace, enter and the spacebar.

I can get the last two with:
```
#!/bin/bash

while true; do
	read -n1 input

	case "$input" in
		'' ) echo "enter or spacebar" ;;
	esac
done
```
But I can't differentiate one from the other. :(

---

### Post by geirha on 2008-06-09
That's due to the IFS again. The default IFS is $' \t\n' and those three are treated the same by read, so let's change it to only '\n'. Also, I've used the hex-values instead now for the other ctrl+* examples

[php]
#!/bin/bash

CTRL_X=$'\x18'
CTRL_V=$'\x16'
BACKSPACE=$'\x7f'
stty -echo

# SIGINT is the signal sent when ^C is pressed.
trap 'echo "Ctrl+c"' SIGINT
trap 'stty echo' EXIT

IFS=$'\n'
while true; do
    read -n1 input
    case "$input" in
        [qQ] )  break ;;
        ' ' ) echo "Space" ;;
        '' ) echo "Enter" ;;
        "${CTRL_X}" ) echo "Ctrl+x" ;;
        "${CTRL_V}" ) echo "Ctrl+v" ;;
        "${BACKSPACE}" ) echo "Backspace" ;;
        * ) echo "Other: '$input'" ;;
    esac
done  
[/php]

To find the hex-value for backspace, you can do the following in a terminal:
```

hd<enter>
<ctrl>v<backspace><ctrl>d<ctrl>d

```
The output should look like this:
```
$ hd
^?00000000  7f                                                |.|
00000001

```

Hope that made sense.

---

### Post by Yuzem on 2008-06-09
That worked perfectly, thanks a lot!

---

### Post by geirha on 2008-06-12
A friend showed me some stuff you can do with the stty-command. And one of the things is redefining the interrupt key-press (which is ctrl+c by default). With:
[php]
CTRL_C=$'\x03'
stty intr ^@
[/php]
the ctrl+c will no longer be caught by the terminal, and you can check for $CTRL_C in your **case**.

You should make sure to put it back when the script exits though, so change the exit-trap
[php]trap 'stty intr ^C;stty echo' EXIT[/php]
The SIGINT trap will no longer be needed in this case. 

And the ^@ and ^C above is written by typing ^ then @, you do not have to use ctrl+v magic in this case.

---

### Post by Yuzem on 2008-06-13
Nice, thanks. :)

Do you know how to differentiate the arrows keys from the escape key in a clean way?

I get the arrows with A B C D, all uppercase:
```

esc=$'\x1b'

while true; do
    read -n1 input
    case "$input" in
        A ) echo "arrow" ;;
        B ) echo "arrow" ;;
        C ) echo "arrow" ;;
        D ) echo "arrow" ;;
        "${esc}" ) echo "escape" ;;
    esac
done
```

The arrow theys seem to be 3 keys in one and every time a press an arrow key I also get the action bound to the escape key.

---

### Post by geirha on 2008-06-13
I'm afraid not. I can't think of any good way to do it. When you detect $esc, you could possibly do «read -t1 -n1» to try to read the next character for 1 second. If it fails, you assume it was the escape key, and if it succeeds, check if it is '[', then assume the next will be [A-D]. Doing it that way has a lot of side-effect, and will very quickly become very complex.

I think maybe you should consider a different language. Python would certainly make this alot easier ...

---

### Post by Yuzem on 2008-06-13
Ok, I think I will do something like this:
(Didn't test it)

```
esc=$'\x1b'

while true; do
    read -n1 input

    if [[ "$input" = "${esc}" ]]; then
        while read -n1 input; do
            break
        done

        if [[ "$input" != '[' ]]; then
            echo "escape key"
        fi
    fi

    case "$input" in
        A ) echo "arrow" ;;
        B ) echo "arrow" ;;
        C ) echo "arrow" ;;
        D ) echo "arrow" ;;
    esac
done
```

---

