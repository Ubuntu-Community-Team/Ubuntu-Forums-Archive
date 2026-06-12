---
title: "Bash script : wget sometimes works other times no such file or directory error"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by InkyDinky on 2008-09-05
I'm writing a simple script to download a file from a website using wget. Wget is installed and works in a small script but when added to a much larger script it doesn't work and the command line returns "line 31: wget: No such file or directory" (I deleted some unnecessary commenting so the error proly is no longer on line 31 but is still there.)

Here is the simple script that works fine:
```

#!/bin/bash
echo some stuff
FLAG=1
if [ $FLAG = 1 ];
then 
eval wget http://zvbxrpl.org/index.html
fi 


```

and here is the code that I receive the error on.
The basics of the code are to try the base filename and if the download for that filename is unsuccessful to try a filename with a letter added on to the end.
```

#!/bin/bash
# argument list 1) date in mdy format 2) path to file folder where file should exist 3) login 4) password
#http://ubuntuforums.org/showthread.php?t=745486 for code to check if file exists
#http://ubuntuforums.org/archive/index.php/t-659624.html looking for way to increment file extension letter

#variables
PASSWORD=XXXXX
LOGIN=XXXXXX
extension=.pdf
alf=(a b c d e f g h i j k l m n o p q r s t u v w x y z) #indices start at 0
index=0 #indices start at 0
PATH=$2
date=$1
STOPFLAG=0

#echo ${alf[$index]} #test array index

if [ $# != 1 ];
then echo We need the date as an argument.
else

	filename=eibd$date$extension #for some reason eibd$datea.pdf wouldn't produce e.g. eibd040908a.pdf
	echo Initially trying to get $filename.

	if [ -e /home/min/a/nkloster/$filename ];
#	if [ -e $PATH$filename ];
		then echo File $filename all ready downloaded!
	else
		
		eval wget http://eibd.investors.com/pdfibd/$filename --http-use=$LOGIN --http-passwd=$PASSWORD
		
		echo eval wget http://eibd.investors.com/pdfibd/$filename --http-use=$LOGIN --http-passwd=$PASSWORD
 
 #if file doesn't exist then increment to a b c d 


#need a while loop to check if the file exists and to keep checking for it otherwise
		while [ ! -e /home/nicky/$filename ] && [ $STOPFLAG -ne 1 ]
		do
			filename=eibd$date${alf[$index]}$extension
			echo $filename
			let "index += 1" 
# $index+1 #increment index and plop in letter to filename mechanism index=$index+1 #increment index and plop in letter to filename mechanism
			eval wget http://eibd.investors.com/pdfibd/$filename --http-use=$LOGIN --http-passwd=$PASSWORD
		
			if [ $index -ge 26 ];
			then STOPFLAG=1
			fi
		done

	fi
fi



```

---

### Post by unutbu on 2008-09-05
I don't think the eval's are necessary. 
Comment out the wget lines and just use echo to print the wget commands. Then copy and paste the echo'd wget command into the terminal. Does the wget command work from the terminal?

PS. While there is nothing wrong with doing this in bash, I find writing these kinds of scripts in Python much more pleasant because you don't have to fight with as many errors caused by quirkiness of bash syntax, and when you seek to accomplish even more complicated tasks you will be able to draw upon  Python's rich library of modules.

---

### Post by elmoosecapitan on 2008-09-05
Likewise, I prefer python or tcsh.

You can try taking out 'eval', or you can define a string as your "wget link" at the beginning of your script and then execute the string when and where you want to.

cheers

---

### Post by Dedoimedo on 2008-09-05
Hello,

I don't see where you check if the "file" you're working on is indeed a file or a directory. Use the -f and -d switches to examine the input parameter before working on it.

And if the file / directory is not found, increment your index rather than run wget ...

Dedoimedo

---

### Post by InkyDinky on 2008-09-10
Well I figured it out.  It was the reassignment of the PATH variable that was causing things to screw up.
And yes I didn't need the eval statements.

---

