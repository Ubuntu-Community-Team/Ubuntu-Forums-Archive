---
title: "C and script cannot co-operate-Very Weird"
date: 2010-02-21
forum: Programming Talk
---

### Post by hakermania on 2010-02-21
Hi, I made this script which works perfectly:
```
clear
echo "          		1 = Login

      			2 = Change the Login Password

			3 = Forgot your password?

			4 = Set the recall answer to question
"
	read number
	case $number in
	1)
	      if [ -s /home/alex/Documents/PASS/password_PASS ]; then
			    existpass=`cat /home/alex/Documents/PASS/password_PASS`
			    echo "Type the existing pass:"
			    read givenpassasexisted
		         if [ "$existpass" == "$givenpassasexisted" ]; then
			  	clear; echo "Success!"
		         else    	echo "Bad" 
			          exit
			 fi
		else echo "There is no password."
		
	fi;;
		
	2)
		   if [ -s /home/alex/Documents/PASS/password_PASS ]; then
			    existpass=`cat /home/alex/Documents/PASS/password_PASS`
			    echo "Type the existing pass:"  
				read givenpassasexisted
		         if [ "$existpass" == "$givenpassasexisted" ]; then
				echo "Type new password:"
				read newpass
		  		cd /home/alex/Documents/PASS/
				rm password_PASS
				echo $newpass > /home/alex/Documents/PASS/password_PASS
				echo $newpass > /home/alex/Documents/PASS/bringagain_PASS
			else
				echo "Wrong password.Plz retry"
			fi
		  else echo "there is no password file.Create one plz."
			fi;;
	3)
		
		echo "Which is your best friend?"
		read maybebestfriend
		  realbestfriend=`cat /home/alex/Documents/PASS/recallquestion_PASS`
		if [ "$maybebestfriend" == "$realbestfriend" ]; then
			recall=`cat /home/alex/Documents/PASS/bringagain_PASS`
			echo "The password which you forgot is $recall"
		else 
			echo "Wrong answer to the question which is your best friend.Try again."
		fi;;
		
	4)
		echo "Which is the current password?"
		read givenpassasexisted
			existpass=`cat /home/alex/Documents/PASS/password_PASS`
		         if [ "$existpass" == "$givenpassasexisted" ]; then
			 echo "Which is your best friend?"
			 read bestfriend
			 echo $bestfriend > /home/alex/Documents/PASS/recallquestion_PASS
		else 
			echo "Wrong password.Try again!"
			fi
		
	esac
```
I also made a C program like this:
```
#include <stdlib.h>

int main()
{
    system("/home/alex/Documents/PASS/hi");

    return 0;
}
```
The problem is that when I type the script in console (./scriptname)
It works fine.When I call it via the C then it says
[: 67: popopo: unexpected operator

WHY?

---

### Post by dwhitney67 on 2010-02-21
EDIT:  Nevermind; I have my doubts that your script runs, even from the command line.  I tested my two hypotheticals outlined below, and neither seemed to be an issue with a working script.

------------------------------
Perhaps you are missing the "#/bin/bash" in your script, or perhaps the script does not have the permissions to be executed?


P.S.  Btw, there is an environment variable called $HOME that you should consider using in your script and C program.  In a C program:
```

#include <stdlib.h>
#include <stdio.h>

int main(void)
{
   const char* home = getenv("HOME");
   char        buf[256];

   if (home)
   {
      snprintf(buf, sizeof(buf) - 1, "%s/Documents/PASS/hi", home);
      system(buf);
      return 0;
   }

   fprintf(stderr, "HOME not defined.\n");
   return -1;
}

```

---

### Post by hakermania on 2010-02-21
Scripts can run without the #/bin/bash from inside the terminal. Script runs normally when being run.
For example I run script via console:
```
root@lol-pc:/home/alex/Documents/PASS# ./hi
          		1 = Login

      			2 = Change the Login Password

			3 = Forgot your password?

			4 = Set the recall answer to question
1
Type the existing pass:
popopo
Success!
root@lol-pc:/home/alex/Documents/PASS# 
```
Now, run the C program which calls the script:
```
root@lol-pc:/home/alex/Documents/PASS# password
          		1 = Login

      			2 = Change the Login Password

			3 = Forgot your password?

			4 = Set the recall answer to question

1
Type the existing pass:
popopo
[: 67: popopo: unexpected operator
Bad
root@lol-pc:/home/alex/Documents/PASS#
```
That's the real problem. It hasn't to do with #/bin/bash or something like that... ...
EDIT: Oh, and in line 67 the only thing that exists in the srcipt named "hi" is the "esac" command. nothing else....

---

### Post by Barrucadu on 2010-02-21
system() runs things with `sh`&#8212;I guess you're running your script in `bash`. Without even reading your script, I'm 99% certain there are some bashisms in it that `sh` doesn't like.

---

### Post by hakermania on 2010-02-21
Well. I confirm you for 3rd time that this is script works PERFECTLY when being run via console.

---

### Post by hakermania on 2010-02-21
OK, I now added the #/bin/bash
Still not working. Is one of the weirdest things I have ever seen!
Firstly, I run the script normally and works.Then I make A C program that calls the script and it misbehaves.
(To tell the truth I did not understand the Barrucadu. Plz explain)

---

### Post by geirha on 2010-02-21
> **hakermania said:**
> Well. I confirm you for 3rd time that this is script works PERFECTLY when being run via console.

The POSIX [-command does not define the == operator, you want the = operator instead. Bash's builtin [-command however, does accept the == operator, which is the reason it is working when you run it from the terminal; without a she-bang, it will run it with the same shell it's invoked from. The system function (in C), runs the commands in /bin/sh, so your script will also be run with sh, since it's lacking a she-bang.

```
$ bash -c '[ "a" == "a" ] && echo works'
works
$ sh -c '[ "a" == "a" ] && echo works'
[: 1: a: unexpected operator

```

EDIT: You are missing the exclamation mark (!)

```
#!/bin/bash
```

---

### Post by hakermania on 2010-02-21
> **geirha said:**
> The POSIX [-command does not define the == operator, you want the = operator instead. Bash's builtin [-command however, does accept the == operator, which is the reason it is working when you run it from the terminal; without a she-bang, it will run it with the same shell it's invoked from. The system function (in C), runs the commands in /bin/sh, so your script will also be run with sh, since it's lacking a she-bang.

```
$ bash -c '[ "a" == "a" ] && echo works'
works
$ sh -c '[ "a" == "a" ] && echo works'
[: 1: a: unexpected operator

```

EDIT: You are missing the exclamation mark (!)

```
#!/bin/bash
```

So.....if I got it, you suggest to put = instead of ==?

---

### Post by hakermania on 2010-02-21
> **geirha said:**
> The POSIX [-command does not define the == operator, you want the = operator instead. Bash's builtin [-command however, does accept the == operator, which is the reason it is working when you run it from the terminal; without a she-bang, it will run it with the same shell it's invoked from. The system function (in C), runs the commands in /bin/sh, so your script will also be run with sh, since it's lacking a she-bang.

```
$ bash -c '[ "a" == "a" ] && echo works'
works
$ sh -c '[ "a" == "a" ] && echo works'
[: 1: a: unexpected operator

```

EDIT: You are missing the exclamation mark (!)

```
#!/bin/bash
```

Ok making the "==" "=" and adding the #!/bin/bash worked!
Thx.
But, can you explain me why it wasn't work with the C and was working when being run?

---

### Post by geirha on 2010-02-21
> **hakermania said:**
> So.....if I got it, you suggest to put = instead of ==?

If you do that, your script will be POSIX compatible, as far as I can see (though your script is hard to read due to the bad indentation), and you can set the she-bang to #!/bin/sh .

> **hakermania said:**
> But, can you explain me why it wasn't work with the C and was working when being run?

Because system() invokes the shell command with /bin/sh. In the terminal, you run /bin/bash (unless you've changed it from the default), so the script was being run with /bin/bash in the terminal, and with /bin/sh from C.

---

### Post by hakermania on 2010-02-21
Oh, got it. Interesting

---

