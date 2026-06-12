---
title: "Encrypt passwords in script"
date: 2010-02-21
forum: Programming Talk
---

### Post by hakermania on 2010-02-21
Nice. I managed to make this script which works fine:
```
#!/bin/bash
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
		         if [ "$existpass" = "$givenpassasexisted" ]; then
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
		         if [ "$existpass" = "$givenpassasexisted" ]; then
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
		if [ "$maybebestfriend" = "$realbestfriend" ]; then
			recall=`cat /home/alex/Documents/PASS/bringagain_PASS`
			echo "The password which you forgot is $recall"
		else 
			echo "Wrong answer to the question which is your best friend.Try again."
		fi;;
		
	4)
		echo "Which is the current password?"
		read givenpassasexisted
			existpass=`cat /home/alex/Documents/PASS/password_PASS`
		         if [ "$existpass" = "$givenpassasexisted" ]; then
			 echo "Which is your best friend?"
			 read bestfriend
			 echo $bestfriend > /home/alex/Documents/PASS/recallquestion_PASS
		else 
			echo "Wrong password.Try again!"
			fi
		esac
```Now, I'd like to ask how could I encrypt the key, and then when comparing the given password with the correct key to decrypt it and says success and bla bla.I want to make this because this program just makes a file with the password in it. Anyone who wants can read it.Thx!

---

### Post by sisco311 on 2010-02-21
You can use mkpasswd to crypt a string.

```
mkpasswd [OPTIONS]... [PASSWORD [SALT]]
```

```
mkpasswd -m sha-512
```

---

### Post by hakermania on 2010-02-21
It seems interesting and already installed! Nice. And, ok, it types the password to a file.How does it decrypt it to get it back?
```
mkpasswd -s alex | cat  > /home/alex/Desktop/lil.txt #write the alex pass encrypted to a file, but how to decrypt it or to see if the given password is equal to the encrypted???
```

---

### Post by geirha on 2010-02-21
Are you implementing your own version of pwsafe?

You generally don't want to be able to decrypt the password. Instead, you hash the password typed in and compare it with the stored hash.

Also, run ''help read'' in a terminal; you might find the -s option to your liking.

---

### Post by hakermania on 2010-02-21
didn't got it.make an example!

---

### Post by Some Penguin on 2010-02-21
> **hakermania said:**
> Now, I'd like to ask how could I encrypt the key, and then when comparing the given password with the correct key to decrypt it and says success and bla bla.I want to make this because this program just makes a file with the password in it. Anyone who wants can read it.Thx!

Consider the following:

1.  This is a shell script.  To execute it, people must have read permissions on it.
2.  You are attempting to build password recovery into it.  This means that the program itself must be able to determine the password.
3.  (1) + (2) means that people will be able to understand how to retrieve the password.


For this to not be completely broken, it would seem that you must do one of the following:

1.  Break one of these requirements, such as not being able to retrieve passwords.
2.  Use access control provided by a filesystem or other layer, such that users will only be able to retrieve their own even if they know the method.

---

### Post by hakermania on 2010-02-22
Ok, let's say that I break the password recovery...This is a login screen for my program to disable it use from unauthorized persons.These persons have access to all of my files. How can I protect my password to this program? Please explain because I am a beginner in scripting so....:D you were in my position ;)

---

### Post by Some Penguin on 2010-02-22
If it's the case of a stolen laptop, you need to use either filesystem-level or whole-disk encryption, perhaps with the algorithm based on a TPM chip.  Otherwise, somebody can readily remove the drive from the laptop, clone it (or simply keep it, if he doesn't care about subtlety), shove it in a standard 2.5" external enclosure, and then get to work reading your data without actually needing to run any programs that you actually want them to run.

---

### Post by tukuyomi on 2010-02-22
(sorry, I can't seem to find mkpasswd on my system, so I'll use md5sum instead)

The idea is to encrypt your password (create a hash) to a file, so you won't have to decrypt it later:
From the terminal, write this:
```
echo 'realpasswd='$(echo "testpasswd" | md5sum | cut -d\  -f1)>password
```From this exact code, you get a file in your $HOME directory named 'password', containing
```
realpasswd=adf53e7c48385307d4c90dc74aedd57f
```

Then in your script, first, you read the file 'password', then you can read the password and create a hash from user's input (you do not decrypt realpasswd, instead, you encrypt user's input the same manner as before) and compare to the one in the file

```
#At the top of the script, read 'password' file
. ./password

#Ask for user's password
givenpassword=$(read -p "Enter the password: " | md5sum | cut -d\  -f1)

#Test...
if [ "$givenpassword" = "$realpasswd" ]; then
       #Code is correct, continue with what you want to do
       #End your script successfully
       exit 0
else
       #Code is Wrong, exit with an error (a non-zero error):
       exit 1
fi

```
Hope it helps a bit :)

---

### Post by Some Penguin on 2010-02-22
A one-way hash can be used for authentication purposes.  

However, most Linux distributions aren't set up to recognize the setuid bit on shell scripts.  My impression is that Ubuntu does not permit this.  That means that the shell script he's writing can't escalate privileges, which means that anything it can run must be runnable by the user on his own, which means that the user can run anything the script can do without bothering to go through any password checks.

---

### Post by hakermania on 2010-02-24
> **tukuyomi said:**
> (sorry, I can't seem to find mkpasswd on my system, so I'll use md5sum instead)

The idea is to encrypt your password (create a hash) to a file, so you won't have to decrypt it later:
From the terminal, write this:
```
echo 'realpasswd='$(echo "testpasswd" | md5sum | cut -d\  -f1)>password
```From this exact code, you get a file in your $HOME directory named 'password', containing
```
realpasswd=adf53e7c48385307d4c90dc74aedd57f
```

Then in your script, first, you read the file 'password', then you can read the password and create a hash from user's input (you do not decrypt realpasswd, instead, you encrypt user's input the same manner as before) and compare to the one in the file

```
#At the top of the script, read 'password' file
. ./password

#Ask for user's password
givenpassword=$(read -p "Enter the password: " | md5sum | cut -d\  -f1)

#Test...
if [ "$givenpassword" = "$realpasswd" ]; then
       #Code is correct, continue with what you want to do
       #End your script successfully
       exit 0
else
       #Code is Wrong, exit with an error (a non-zero error):
       exit 1
fi

```
Hope it helps a bit :)

Well.Yeah this helped but in this way will I have he opportunity to xhange the password?I don't think so...

---

### Post by tukuyomi on 2010-02-24
Of course, you just have to recreate the file password with the first command!
Make a script from this very command and call it, say, "gen_password"
```
#!/bin/sh

echo 'realpasswd='$(echo "$1" | md5sum | cut -d\  -f1) > password

exit 0
```
($1 is the first argument as this example below)
Usage:
```
./gen_password your_password
```

---

### Post by hakermania on 2010-02-26
> **tukuyomi said:**
> Of course, you just have to recreate the file password with the first command!
Make a script from this very command and call it, say, "gen_password"
```
#!/bin/sh

echo 'realpasswd='$(echo "$1" | md5sum | cut -d\  -f1) > password

exit 0
```
($1 is the first argument as this example below)
Usage:
```
./gen_password your_password
```

Hm, I'll check this out and I'll tell you.Wait...

---

### Post by hakermania on 2010-03-09
```
#!/bin/sh
echo "Give me the pass!!!"
read givenpasswd
realpasswd=`cat /home/alex/Documents/script/login/PASSWORD_PASS`
echo "$givenpasswd" | md5sum | cut -d\  -f1 > /home/alex/Documents/script/login/givenaspassword
givenpasswd=`cat /home/alex/Documents/script/login/givenaspassword`
if [ "$realpasswd" = "$givenpasswd" ];
then
echo "Right"
exit
else echo "Wrong go to hell"
fi

```
thx guys!
You are fabulous!

---

