---
title: "Bash error &amp;amp;quot;unexpected token `}'&amp;amp;quot;"
date: 2007-12-27
forum: Programming Talk
---

### Post by altonbr on 2007-12-27
Now I've ran into this error time and time again, but never have I been so stuck.

I have a small script (~500 lines) and I've just changed it around to read all of the functions and THEN call them instead of having function/call, function/call, function/call, etc.

I've done some searching around and I'll I could find as a debugger was adding -x to the top of my script:

> #!/bin/bash -x

This has given me this output:

> + clear



















+ CREDITS='Alton Labs'
+ NAME='Ubuntu Assistant'
+ VERSION=2007-12-26
+ LEVELINFO=' -- INFO: '
+ LEVELWARN=' -- WARNING: '
+ LEVELERR=' -- ERROR: '
++ date +%Y%m%d-%s
+ THEDATE=20071227-1198793256
./ubuntu_assistant.sh: line 474: syntax error near unexpected token `}'
./ubuntu_assistant.sh: line 474: `}'


Line 474 is the EXACT last line of all of my functions and I'm wondering why it continually stops there.

I've ran
```
grep --count { ./filename && grep --count } ./filename
```

Which returned:
> 27
27

Any suggestions?

**EDIT**: I've attached the program I'm writing...

---

### Post by altonbr on 2007-12-27
I read here: [http://linux.derkeiler.com/Mailing-Lists/RedHat/2003-11/0750.html](http://linux.derkeiler.com/Mailing-Lists/RedHat/2003-11/0750.html) that my> if [ $? = 0 ]; then could be the cause for throwing the errors, so I switched them to
> if [ $? -eq 0 ]; then
but I still receive the same error...

---

### Post by cabalas on 2007-12-27
Without being able to see the script I'd assume that the error occurs in the statement before the '}'.  Without seeing the script I can't offer any better suggestions, is at all possible for you to post a few lines of the script around where the error occurs?

---

### Post by Majorix on 2007-12-27
It could also be that you are using a wrong interpreter. The Shell tends to spit out such exceptions when it runs a script with a wrong program to interpret. I would try making the script executable with
```
chmod a+x script.sh
```
and then running it like you would run an executable. If it is in your path, simply run it by typing its name, or if not, cd to the folder it's in and run it with
```
./script.sh
```
Hope I helped you.

---

### Post by ghostdog74 on 2007-12-27
> **altonbr said:**
> I read here: [http://linux.derkeiler.com/Mailing-Lists/RedHat/2003-11/0750.html](http://linux.derkeiler.com/Mailing-Lists/RedHat/2003-11/0750.html) that my could be the cause for throwing the errors, so I switched them to

but I still receive the same error...
make sure you have spaces around  your "if" statement and the open square brackets
```

if [<put space here>something=something<put space here>];then
 ....
fi

```
make sure every if ends with fi. If not, show your code.

---

### Post by ghostdog74 on 2007-12-27
> **Majorix said:**
> It could also be that you are using a wrong interpreter. The Shell tends to spit out such exceptions when it runs a script with a wrong program to interpret. I would try making the script executable with

he has already indicated its /bin/bash

---

### Post by Majorix on 2007-12-27
It's the first line of the code, not what he uses to execute the code, as I understand it. Sorry if I am wrong.

---

### Post by ghostdog74 on 2007-12-27
> **Majorix said:**
> It's the first line of the code, not what he uses to execute the code, as I understand it. Sorry if I am wrong.
If #!/bin/bash is the first line of the code, then when you execute the script
using ./script.sh for example, the interpreter used is bash (provided there's actually a /bin/bash present on your system). You can also execute the script this way
# bash myscript.sh 
Anyway, OP has used -x , and has shown the output, so you can be sure that the script did run.

---

### Post by altonbr on 2007-12-28
> **cabalas said:**
> Without being able to see the script I'd assume that the error occurs in the statement before the '}'.  Without seeing the script I can't offer any better suggestions, is at all possible for you to post a few lines of the script around where the error occurs?

I'll post it above, sorry :S

> **Majorix said:**
> It could also be that you are using a wrong interpreter. The Shell tends to spit out such exceptions when it runs a script with a wrong program to interpret. I would try making the script executable with
```
chmod a+x script.sh
```
and then running it like you would run an executable. If it is in your path, simply run it by typing its name, or if not, cd to the folder it's in and run it with
```
./script.sh
```
Hope I helped you.

```
ls -l
```
> -rw-rw-r--  1 brett brett  5885 2007-12-27 15:51 ChangeLog
-rw-rw-r--  1 brett brett     0 2007-12-26 22:46 FEATURES
-rw-rw-r--  1 brett brett 35127 2007-12-26 22:46 LICENSE
-rw-rw-r--  1 brett brett  2211 2007-12-27 13:37 TODO
**-rwxrwxr-x**  1 brett brett 15733 2007-12-27 17:21 ubuntu_assistant.sh

Already got it executable :)

> **ghostdog74 said:**
> make sure you have spaces around  your "if" statement and the open square brackets
```

if [<put space here>something=something<put space here>];then
 ....
fi

```
make sure every if ends with fi. If not, show your code.

I'm pretty sure I'm good there... I'll post the code now so you guys can see it.

---

### Post by geirha on 2007-12-28
Bash complains because the function that ends on line 474 is empty. i.e. 
```

function foo(){
  # Function is empty, doesn't work
}

```
Considering the comments inside that function, you intend to add some code there eventually, but meanwhile, just put some simple command like /bin/true which doesn't do anything.
```

function foo(){
  /bin/true #works
}

```

---

### Post by altonbr on 2007-12-28
Wow. Bash is much pickier than PHP and JavaScript (which I started programming with).

Thanks for the help. Enjoy the script?

---

### Post by altonbr on 2007-12-29
Grr, I'm receiving the error again, this time with no empty function...

> + clear

+ CREDITS='Alton Labs'
+ NAME='Ubuntu Assistant'
+ VERSION=2007-12-28
+ LICENSE=GPLv3
+ set ZENITY=0
+ set ROOTUSER=0
+ LEVEL_QUESTION=' -- QUESTION: '
+ LEVEL_INFO=' -- INFO: '
+ LEVEL_WARN=' -- WARNING: '
+ LEVEL_ERROR=' -- ERROR: '
++ date +%Y%m%d-%s
+ THEDATE=20071229-1198952315
./ubuntu_assistant.sh: line 112: syntax error near unexpected token `}'
./ubuntu_assistant.sh: line 112: `}'


```
# ========================
# INITIALIZATION
# ========================

clear # clear the screen for aesthetical purposes

# ------------------------
# initialize variables
# ------------------------
CREDITS='Alton Labs'
NAME='Ubuntu Assistant'
VERSION='2007-12-28'
LICENSE='GPLv3'
set ZENITY=0
set ROOTUSER=0

LEVEL_QUESTION=' -- QUESTION: '
LEVEL_INFO=' -- INFO: '
LEVEL_WARN=' -- WARNING: '
LEVEL_ERROR=' -- ERROR: '
THEDATE=`date '+%Y%m%d-%s'` # 20071010-1192044000
#DESKTOPFILE="[Desktop Entry]\nEncoding=UTF-8\nVersion=$VERSION\nName=$TITLE\nComment=Created by Alton Labs\nExec=/usr/bin/ubuntu-assistant.sh\nTerminal=false\nType=Application\nIcon=/usr/share/icons/gnome/scalable/categories/applications-system.svg\nCategories=Application;System;"

# ========================
# FUNCTIONS
# ========================

# ++++++++++++++++++++++++
# CHECK
# ++++++++++++++++++++++++
# check() finds information and runs a conditional based on the output
function check(){
	case "$1" in
		'zenity_install')
			if [[ ! -e '/usr/bin/zenity' ]]; then
				echo $LEVEL_WARN 'Zenity is not installed. Continuing...'
				set ZENITY=0
			else
				echo $LEVEL_INFO 'Zenity is installed. Continuing...'
				set ZENITY=1
			fi
			;; # end 'zenity'

		'username')
			USERNAME=`whoami`
			if [[ $UID -eq 0 || $USERNAME != 'root' ]]; then
				echo $LEVEL_INFO 'User found: ' $USERNAME '. Not root. Continuing...'
				ROOTUSER=false
			else
				echo $LEVEL_INFO 'User found: root. Will not install personal preferences.'
		
				if [[ $ZENITY -eq 1 ]]; then
					# while $ANSWER is null, does not equal 'y', does not equal 'n'
					while [[ -z $ANSWER || $ANSWER != 'y' || $ANSWER != 'n' ]]; do
						read -p "$LEVEL_QUESTION Would you like to continue if no personal preferences will be installed? (y or n)" -t 60 -n 1  ANSWER #timeout after 60 seconds, only read one character
						if [[ $? -ne 0 ]]; then
							echo $LEVEL_ERROR 'No user response after 60 seconds. Exiting...'
							exit 1
						fi
					done
				else
					# zenity
					/bin/true # placeholder
				fi
		
				if [[ $ANSWER = 'y' ]]; then
					set ROOTUSER=1
				else
					echo $LEVEL_ERROR 'You selected not to continue if the personal preferences are not to be set. Please login as a normal user and try again. Exiting...'
					exit 1
				fi
		
			fi
			;; # end 'username'

		'window_manager')
			if [ "$(pidof ksmserver)" ]; then
			   echo "KDE running."
			   # KDE-specific stuff here
			elif [ "$(pidof gnome-session)" ]; then
			   echo "GNOME running."
			   # GNOME-specific stuff here
			elif [ "$(pidof xfce-mcs-manage)" ]; then
			   echo "Xfce running."
			   # Xfce-specific stuff here
			fi
			;; # end 'window_manager'

		*)
			echo $LEVEL_ERROR 'Programming error in function check(). Exiting...'
			exit 1
			;; # end *
} **# this is line 112**
```

---

### Post by geirha on 2007-12-29
Seems that **case** is missing its **esac**?

---

### Post by altonbr on 2007-12-29
> **geirha said:**
> Seems that **case** is missing its **esac**?

Wow. I was missing 'esac' in EVERY case statement I made... ](*,)

Thanks :S

---

### Post by ghostdog74 on 2007-12-29
> **altonbr said:**
> Wow. I was missing 'esac' in EVERY case statement I made... ](*,)

Thanks :S

the best way when you want to write if/else or case statements, is to write them together at once, not after you finish typing. eg
```

if 

else

fi

case

esac

```
then insert your code in between. Then you won't be missing the closing counterparts too often

---

### Post by altonbr on 2007-12-30
> **ghostdog74 said:**
> the best way when you want to write if/else or case statements, is to write them together at once, not after you finish typing. eg
```

if 

else

fi

case

esac

```
then insert your code in between. Then you won't be missing the closing counterparts too often

Yeah, I usually do! I just don't know what happened there. Sorry to waste everyone's time (on the second post).

---

