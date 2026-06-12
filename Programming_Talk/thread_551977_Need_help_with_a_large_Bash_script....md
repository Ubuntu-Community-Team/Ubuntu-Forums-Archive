---
title: "Need help with a large Bash script..."
date: 2007-09-15
forum: Programming Talk
---

### Post by tinman47 on 2007-09-15
Well, I got Ubuntu 3 months ago. I enjoy it sure, way better then Windows. I program in C with Vim and use the terminal for complex shell scripts. Well, I am making a programming language with C, so I made a draft of the C program in a Shell script...And for me to follow up on the idea in C, I need the script to work...But the shell script isn't working. 

Can some Bash programmer help me?

[FONT="Courier New"]#include <stdio.h>[/FONT]

[FONT="Courier New"]int main()[/FONT]
[FONT="Courier New"]{[/FONT]
[FONT="Courier New"]  printf("All help is appreciated.");[/FONT]
[FONT="Courier New"]  return 0;[/FONT]
[FONT="Courier New"]}[/FONT]

The shell script is here at:
[http://rapidshare.com/files/56029804/TM47-BASIC_2](http://rapidshare.com/files/56029804/TM47-BASIC_2)

---

### Post by ghostdog74 on 2007-09-15
a lot of the bash  syntax  are wrong. And, don't let us guess, tell us  what exactly is not working..show any error messages when you run the script...you did run the script , right?

---

### Post by dwhitney67 on 2007-09-16
> **tinman47 said:**
> Well, I got Ubuntu 3 months ago. I enjoy it sure, way better then Windows. I program in C with Vim and use the terminal for complex shell scripts. Well, I am making a programming language with C, so I made a draft of the C program in a Shell script...And for me to follow up on the idea in C, I need the script to work...But the shell script isn't working. 

Can some Bash programmer help me?

[FONT="Courier New"]#include <stdio.h>[/FONT]

[FONT="Courier New"]int main()[/FONT]
[FONT="Courier New"]{[/FONT]
[FONT="Courier New"]  printf("All help is appreciated.");[/FONT]
[FONT="Courier New"]  return 0;[/FONT]
[FONT="Courier New"]}[/FONT]

The shell script is here at:
[http://rapidshare.com/files/56029804/TM47-BASIC_2](http://rapidshare.com/files/56029804/TM47-BASIC_2)

I don't quite understand your post.  What is that you want?  A Bash script to do exactly what the C program is doing?  If so, here it is:

[FONT="Courier New"]#!/bin/bash
echo "All help is appreciated."
exit 0[/FONT]

---

### Post by CptPicard on 2007-09-16
Writing a BASIC in bash in order to prototype it is a loony idea. :)

Bash is a shell, not really for "real programming" (although it's a great process and file manipulation tool and general system glue). You'd be better off writing it straight in C, or if you want to develop quicker, something like Python.

---

### Post by tinman47 on 2007-09-16
Can you give me back a copy of my script with comments around it pointing out the wrong syntax?

And I did run the script. It exited immediately without error messages. Too fast for me to see.

---

### Post by dwhitney67 on 2007-09-16
Why don't you post your script instead of the _non-working_ URL?

---

### Post by gnusci on 2007-09-16
I think is better if you post a sort version of your script pointing out the basic essence, I see your code is just bloated with almost the same structure once an again.

---

### Post by tinman47 on 2007-09-16
Problem. Script a little big. Another Problem...I don't know how.

---

### Post by gnusci on 2007-09-16
just try to use one or two functions, and use less options, once you have a sort script running the rest is just copy and paste and make the few changes to have all the other functions running too.

---

### Post by pmasiar on 2007-09-17
read about how to ask questions in my sig

---

### Post by tinman47 on 2007-09-24
A1=0;A2=0;A3=0;A4=0;A5=0;A6=0;A7=0;A8=0;A9=0;A0=0;
B1=0;B2=0;B3=0;B4=0;B5=0;B6=0;B7=0;B8=0;B9=0;B0=0;
C1=0;C2=0;C3=0;C4=0;C5=0;C6=0;C7=0;C8=0;C9=0;C0=0;
D1=0;D2=0;D3=0;D4=0;D5=0;D6=0;D7=0;D8=0;D9=0;D0=0;
E1=0;E2=0;E3=0;E4=0;E5=0;E6=0;E7=0;E8=0;E9=0;E0=0;
F1=0;F2=0;F3=0;F4=0;F5=0;F6=0;F7=0;F8=0;F9=0;F0=0;
G1=0;G2=0;G3=0;G4=0;G5=0;G6=0;G7=0;G8=0;G9=0;G0=0;
H1=0;H2=0;H3=0;H4=0;H5=0;H6=0;H7=0;H8=0;H9=0;H0=0;
I1=0;I2=0;I3=0;I4=0;I5=0;I6=0;I7=0;I8=0;I9=0;I0=0;
J1=0;J2=0;J3=0;J4=0;J5=0;J6=0;J7=0;J8=0;J9=0;J0=0;
K1=0;K2=0;K3=0;K4=0;K5=0;K6=0;K7=0;K8=0;K9=0;K0=0;
L1=0;L2=0;L3=0;L4=0;L5=0;L6=0;L7=0;L8=0;L9=0;L0=0;
M1=0;M2=0;M3=0;M4=0;M5=0;M6=0;M7=0;M8=0;M9=0;M0=0;
N1=0;N2=0;N3=0;N4=0;N5=0;N6=0;N7=0;N8=0;N9=0;N0=0;
O1=0;O2=0;O3=0;O4=0;O5=0;O6=0;O7=0;O8=0;O9=0;O0=0;
P1=0;P2=0;P3=0;P4=0;P5=0;P6=0;P7=0;P8=0;P9=0;P0=0;
Q1=0;Q2=0;Q3=0;Q4=0;Q5=0;Q6=0;Q7=0;Q8=0;Q9=0;Q0=0;
R1=0;R2=0;R3=0;R4=0;R5=0;R6=0;R7=0;R8=0;R9=0;R0=0;
S1=0;S2=0;S3=0;S4=0;S5=0;S6=0;S7=0;S8=0;S9=0;S0=0;
T1=0;T2=0;T3=0;T4=0;T5=0;T6=0;T7=0;T8=0;T9=0;T0=0;
U1=0;U2=0;U3=0;U4=0;U5=0;U6=0;U7=0;U8=0;U9=0;U0=0;
V1=0;V2=0;V3=0;V4=0;V5=0;V6=0;V7=0;V8=0;V9=0;V0=0;
W1=0;W2=0;W3=0;W4=0;W5=0;W6=0;W7=0;W8=0;W9=0;W0=0;
X1=0;X2=0;X3=0;X4=0;X5=0;X6=0;X7=0;X8=0;X9=0;X0=0;
Y1=0;Y2=0;Y3=0;Y4=0;Y5=0;Y6=0;Y7=0;Y8=0;Y9=0;Y0=0;
Z1=0;Z2=0;Z3=0;Z4=0;Z5=0;Z6=0;Z7=0;Z8=0;Z9=0;Z0=0;
NULL=$null
ADDITION='+'
SUBTRACTION='-'
MULTIPLICATION='*'
DIVISION='/'
POWER='^'
GREATER_THAN='>'
LESS_THAN='<'
EQUAL_TO='~'
LOGIC_SHIFT1='>>'
LOGIC_SHIFT2='<<'
LOGIC_SHIFT3='}'
LOGIC_SHIFT4='{'
LOGIC_SHIFT5='|'
echo 'Welcome to TM47-BASIC 2 Beta!'
echo 
#________________________________________
#COMMANDS:
#----------------------
#Initilize the keywords
#----------------------
#REMARK   =  INSERT COMMENT
#SBLOCK   =  START OF A BLOCK OF CODE
#EBLOCK   =  END OF A BLOCK OF CODE
#SETVAR   =  SET A VARIABLE
#IF       =  DEPENDING ON A VARIABLE DO ACTION
#KILL     =  EXIT CURRENT SESSION OF TM47-BASIC
#NEWIN    =  OPEN A NEW WINDOW OF TM47-BASIC
#OUTPUT   =  SPECIFY OUTPUT TO BE DISPLAYED
#CALL     =  CALL A BLOCK OF CODE
#INPUT    =  REQUEST USER INPUT
#WINAME   =  SET WINDOW CAPTION
#CLS      =  CLEAR OUTPUT
#SLEEP    =  PAUSE FOR n SECONDS
#MOUSE    =  MOUSE LOCATION AND CONTROL
#LABEL    =  SPECIFIES LABEL NUMBER
#GOTO     =  GOTO A LABEL NUMBER 
#_________________________________________
 function USER INPUT()
 {
  read $1, $2
 }

 function PROCESS()
{
  if [ $INkey == "REMARK $1" ]; then 
  echo "REMARK $1"
  fi
  elif [ $INkey == "SBLOCK $1" ]; then 
  echo "SBLOCK $1"
  fi
  elif [ $INkey == "EBLOCK $1" ]; then 
  echo "EBLOCK $1"
  fi
  elif [ $INkey == "SETVAR $1 AS $2" ]; then 
  echo "SETVAR $1 $2"
  fi
  elif [ $INkey == "IF $1 IS $2 THEN $3" ]; then 
  echo "IF $1 $2 $3"
  fi
  elif [ $INkey == "KILL" ]; then 
  echo "KILL"
  fi
  elif [ $INkey == "NEWIN $1" ]; then 
  echo "NEWIN $1"
  fi
  elif [ $INkey == "OUTPUT -d $1" ]; then 
  echo "OUTPUT "-d" $1"
  fi
  elif [ $INkey == "OUTPUT -g $1 $2" ]; then 
  echo "OUTPUT "-g" $1 $2"
  fi
  elif [ $INkey == "OUTPUT -f $1 $2" ]; then 
  echo "OUTPUT "-f" $1 $2"
  fi
  elif [ $INkey == "CALL $1" ]; then 
  echo "CALL $1"
  fi
  elif [ $INkey == "INPUT $1 , $2" ]; then 
  echo "INPUT $1 $2"
  fi
  elif [ $INkey == "WINAME $1" ]; then 
  echo "WINAME $1"
  fi
  elif [ $INkey == "CLS" ]; then 
  echo "CLS"
  fi
  elif [ $INkey == "SLEEP" ]; then 
  echo "SLEEP"
  fi
  elif [ $INkey == "SLEEP $1" ]; then 
  echo "SLEEP $1"
  fi
  elif [ $INkey == "MOUSE $1 THEN $2" ]; then 
  echo "MOUSE $1 THEN $2"
  fi

  elif [ $INkey == "MOUSE $1 THEN $2" ]; then 
  echo "MOUSE $1 THEN $2"
  fi
  elif [ $INkey == "MOUSE $1 THEN $2" ]; then 
  echo "MOUSE $1 THEN $2"
  fi
  elif [ $INkey == "MOUSE $1 $2" ]; then 
  echo "MOUSE $1 $2"
  fi
  elif [ $INkey == "LABEL $1" ]; then 
  echo "LABEL $1"
  fi
  elif [ $INkey == "GOTO $1" ]; then 
  echo "GOTO $1"
  fi
  #------------------------
  #HELP INITLILIZATION=>
  #------------------------
  if [ $INkey = "HELP" ]; then
  {
   echo 
   echo REMARK      Inserts a comment in your script.
   echo SBLOCK      Indicates the start of a sub procedure.
   echo EBLOCK      Indicates the end of a sub procedure.
   echo SETVAR      Creates a new variable and sets its value.
   echo IF          Does an action depending on a variable's value.
   echo KILL        Exits or quits the current session of TM47-BASIC.
   echo NEWIN       Opens a new window of TM47-BASIC.
   echo OUTPUT      Specifies what to display as output.
   echo CALL        Executes a sub procedure, or file.
   echo INPUT       Request input and sets the input as a value of a variable.
   echo WINAME      Sets the window caption.
   echo CLS         Clears the screen of output.
   echo SLEEP       Pauses for a certain amount of seconds.
   echo MOUSE       Performs mouse actions.
   echo LABEL       Sets a label number in your script.
   echo GOTO        Jumps to the specified label.
   echo
  }
  fi
  elif [ $INkey == "HELP REMARK" ]; then
  {
   echo
   echo Inserts a comment in your script.
   echo 
   echo Syntax:
   echo
   echo REMARK [comment]
   echo
   echo Comments are user messsages inside
   echo scripts. All comments are ignored.
   echo
  }
  fi
  elif [ $INkey == "HELP SBLOCK" ]; then
  {
   echo 
   echo Indicates the start of a sub procedure.
   echo
   echo Syntax:
   echo
   echo SBLOCK [name of sub procedure]
   echo [block of commands]
   echo EBLOCK [name of procedure]
   echo 
   echo The SBLOCK command starts a sub procedure
   echo or a block of code, then the name of the
   echo sub procedure is typed in so it can be 
   echo called and ended. To indicate the block of
   echo commands, type after the SBLOCK command a
   echo "[" and end it with a "]". For example:
   echo 
   echo CALL print
   echo SBLOCK print 
   echo [
   echo  OUTPUT -d Hello World!
   echo  SLEEP 4
   echo ]
   echo EBLOCK print
   echo
   echo This will execute the sub procedure print,
   echo which will print on the screen "Hello World!",
   echo and pause for 4 seconds then exit.
   echo
  }
  fi
  elif [ $INkey == "HELP EBLOCK" ]; then
  {
   echo 
   echo Indicates the end of a sub procedure.
   echo
   echo Syntax:
   echo
   echo SBLOCK [name of procedure]
   echo [block of commands]
   echo EBLOCK [name of procedure
   echo
   echo The EBLOCK command ends a sub procedure
   echo or a block of code, then the name of the
   echo sub procedure is typed in so it knows what
   echo sub procedure to end. For example:
   echo
   echo SBLOCK Leaving
   echo [
   echo  OUTPUT -d Im Leaving!
   echo  SLEEP 2
   echo ]
   echo EBLOCK Leaving
   echo
   echo CALL Leaving
   echo 
   echo This will call the block of code called
   echo Leaving and it will print on the screen
   echo "Im Leaving!" and it will pause for 2
   echo seconds and simply exit.
   echo
  }
  fi
  elif [ $INkey == "HELP SETVAR" ]; then
  {
   echo
   echo Creates a new variable and sets its value.
   echo 
   echo Syntax:
   echo 
   echo SETVAR [variable] AS [value]
   echo
  }
  fi
  elif [ $INkey == "HELP IF" ]; then
   echo
  fi
  elif [ $INkey == "HELP KILL" ]; then
   echo
  fi
  elif [ $INkey == "HELP NEWIN" ]; then
   echo
  fi
  elif [ $INkey == "HELP OUTPUT" ]; then
   echo
  fi
  elif [ $INkey == "HELP CALL" ]; then
   echo
  fi
  elif [ $INkey == "HELP INPUT" ]; then
   echo
  fi
  elif [ $INkey == "HELP WINAME" ]; then
   echo
  fi
  elif [ $INkey == "HELP CLS" ]; then 
   echo
  fi
  elif [ $INkey == "HELP SLEEP" ]; then
   echo
  fi
  elif [ $INkey == "HELP MOUSE" ]; then
   echo
  fi
  elif [ $INkey == "HELP LABEL" ]; then
   echo
  fi
  else [ $INkey == "HELP GOTO" ]; then
   echo
  fi

 

 ERROR()
 {
  echo Error! Unable to perform.
 }

 REMARK()
 {
  echo
 }

 SBLOCK()
 {
  echo
 }

 EBLOCK()
 {
  echo
 }

 SETVAR()
 {
  $1=$2
 }

 IF()
 {
  echo
 }

 KILL()
 {
  echo
 }

 NEWIN()
 {
  echo
 }

 OUTPUT()
 {
  echo
 }

 CALL()
 {
  echo
 }

 INPUT()
 {
  read $1, $2
 }

 WINAME()
 {
  echo
 }

 CLS()
 {
  clear
  echo
 }

 SLEEP()
 {
  echo
 }

 MOUSE()
 {
  echo
 }

 LABEL()
 {
  echo
 }

 GOTO()
 {
  echo
 }
}

#=====================================
#Read user input as variable name $INkey
#=====================================
USER INPUT

_______________________
Well here is the script.
At line 170, it screws up,
according to my debugger.

---

### Post by deadlydeathcone on 2007-09-26
Hey timan.

I looked over your script and, to be succinct, EVERYTHING is broken! I have to go to bed at the moment, but I'll have some time to look it over tomorrow evening and be of more help.

---

### Post by Cappy on 2007-09-26
I would look at [http://www.linuxcommand.org/writing_shell_scripts.php](http://www.linuxcommand.org/writing_shell_scripts.php)
It offers beginning lessons in shell scripting.

Your code should look like this:

```

if [ "$INkey" = "REMARK $1" ]; then 
	echo "REMARK $1"
elif [ "$INkey" = "SBLOCK $1" ]; then 
	echo "SBLOCK $1"
elif [ "$INkey" = "EBLOCK $1" ]; then 
	echo "EBLOCK $1"
else
	echo "else"
fi

```

a select case would be much better
```

case $INkey in
REMARK $1) echo "REMARK $1";;
SBLOCK $1) echo "SBLOCK $1";;
EBLOCK $1) echo "EBLOCK $1"

```
I think that would work even with the $1 on the front but I've never tried it.

For long lines of echoes you can do something like
```

echo "\
Line of text
Another line of text
Other liens of text"

```

You should start with a small chunk of code and test it before you make a program so long. Nearly all the syntax is wrong - you need to read that shell scripting tutorial. Your functions have spaces in them, you are using double == signs, I can't tell where the program actually begins so I can't give feedback on that but when you do your main statements will have to be at the bottom.

Read the tutorial and then consider rewriting your program and testing each small bit as you go along.

---

### Post by wirelessmonkey on 2007-09-26
This 'script' is a wacky tabakky mix of C and bash script.... C != shell script.

---

