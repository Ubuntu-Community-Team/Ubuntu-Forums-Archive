---
title: "Another script question"
date: 2010-02-21
forum: Programming Talk
---

### Post by hakermania on 2010-02-21
Hi all!
I've seen this example and I am trying to create my own script which has to do with pass words.Well, have a look at the example first:```
#!/bin/sh

echo "Enter a number between 1 and 3. "
read NUM

case $NUM in 
	1) echo "one" ;;
	2) echo "two" ;;
	3) echo "three" ;;
	*) echo "INVALID NUMBER!" ;;
esac
```
But, what's happening if in the case sommand I want to use "if" and "else" as well? I know that we put ";" in the end of every case (i.e. echo "Bad ID"; exit;;)
But I don't know how to make the following:
```
echo "	1 = Type the existing password
      	2 = Change the password
	3 = Call the existing password" #a little menu here
	read number
	case $number in
	 #first case.1:see if the passwordfile already exists.If #it does read the file and see the password.Compare it with the #given password.If they are the same then print "success" and #exit.If they are not print "Bad" and exit
	        1)
		   if [ -s /home/alex/Desktop/${password} ]; then
			    existpass=`cat /home/alex/Desktop/${password}
			    read givenpassasexisted
		         if [ "$existpass" == "$givenpassasexisted" ]; then
			  	echo "Success!" exit
		         else    	echo "Bad" 
			          exit
			 fi
		   else echo "There is no password.Create one";;
                 *)
                   exit;; #I will develop this later
      esac
```
i have multiple errors. I guess I don't know how to use "if" and "else" inside "case".
Any ideas?

---

### Post by lloyd_b on 2010-02-21
The only problem I see is that there's no "fi" corresponding to the outermost "if" statement:```

      case $number in
	 #first case.1:see if the passwordfile already exists.If #it does read the file and see the password.Compare it with the #given password.If they are the same then print "success" and #exit.If they are not print "Bad" and exit
	        1)
		   if [ -s /home/alex/Desktop/${password} ]; then
			    existpass=`cat /home/alex/Desktop/${password}[COLOR="Red"]`[/COLOR]
			    read givenpassasexisted
		         if [ "$existpass" == "$givenpassasexisted" ]; then
			  	echo "Success!" 
                                exit
		         else    	
                                echo "Bad" 
			        exit
			 fi
		   else 
                         echo "There is no password.Create one"
                   [COLOR="Red"]fi;;[/COLOR]
                 *)
                   exit;; #I will develop this later
      esac
```

Lloyd B.

Edit - oops - you're also missing a closing backtic.  Added it in (in red) on the "existpass=..." line.  Also problems with multiple commands on a single line without a separating semicolon: "echo "Success!"  exit", for example.

---

### Post by hakermania on 2010-02-21
xm....OK....thx this worked perfectly!

---

