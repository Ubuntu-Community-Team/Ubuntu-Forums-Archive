---
title: "Shell Scripting (continued)"
date: 2009-10-01
forum: Programming Talk
---

### Post by J05HYYY on 2009-10-01
This is an update for [the shell scripting]("http://ubuntuforums.org/showthread.php?t=757995") thread I started a while back.

Here is a script which can find the start or end of a pattern.
It can also search from the start of the text, normally. Or from the end of the text, in reverse.
It should work on most systems.

```

(this script has been updated, see the one in my post after next instead)

```

I don't know how to feed options into a script as of yet - so I had to make use of the read command. Also I couldn't be bothered to put a simple check in to see if the pattern exists at all, or not, as the case may be.

Feel free to post any improvements/comments

Josh

---

### Post by phrostbyte on 2009-10-01
I'm no Bash scripting pro, but I'm not sure why you seem to be nesting conditional statements (if / else if).

You can also use the case operator to get a similar effect. It's typically used when you want to test a single variable against a multitude of conditions.

```

case "$VAR" in
   '1')
      # code to execute when $VAR = 1 goes here
   ;;
   '2')
      # code to execute when $VAR = 2 goes here
   ;;
esac

```

---

### Post by J05HYYY on 2009-10-03
Case statements sound good ... may update it but I'm pretty busy atm :)

Trying to write a recursive ftp script (similar to HardFeed) - that and being forced to learn C# using VS express for uni. :(

Thank goodness vbox exists. Had to reformat a hard drive from Fat32 to ext3 yesterday as it can only hold files up to 4 gig - just so's I could run their crappy windows IDE.

Would be good if wine had support for VS 2008, then I could dump the OS completely.

... But that's a different kettle of fish.

---

### Post by NoaHall on 2009-10-03
Here.

```
 #!/bin/sh
# Different types of search by J05HYYY - with help from husseincoder et al.

read_texts () {
echo
echo
echo "Enter the line of text to be searched:"
read intext
echo
echo "Enter the pattern to be searched for:"
read searchtext
}

choose_method () {
echo
echo
echo "You can either:"
echo
echo "1) Get the position of the beginning of the pattern, starting from the end of the text."
echo "2) Get the position of the end of the pattern, starting from the end of the text."
echo "3) Get the position of the beginning of the pattern, starting from the start of the text."
echo "4) Get the position of the end of the pattern, starting from start of the text."
read method
case $method in
1)
	echo
	echo
	echo "The position of the beginning of the pattern, starting from the end of the text is:"
	index=$(expr "$intext" : '.*'$searchtext - $(expr $searchtext : '.*'))
	echo $index
;;
2)
	echo
	echo
	echo "The position of the end of the pattern, starting from the end of the text is:"
	searchlength=$((`expr length $searchtext`))
	index=$(expr "$intext" : '.*'$searchtext - $(expr $searchtext : '.*') + $searchlength)
	echo $index	
;;
3)
	echo
	echo		
	echo "The position of the beginning of the pattern, starting from the start of the text is:"
	revintext=`echo intext | rev`
	revsearchtext=`echo searchtext | rev`
	index=$(($(expr $revintext : '.*'$revsearchtext + $(expr $revsearchtext : '.*'))+1))
	echo $index	
;;	
4)
	echo
	echo			
	echo "The position of the end of the pattern, starting from start of the text is:"
	searchlength=$((`expr length $searchtext`+1))
	revintext=`echo intext | rev`
	revsearchtext=`echo searchtext | rev`
	index=$(expr $revintext : '.*'$revsearchtext + $(expr $revsearchtext : '.*') + $searchlength)
;;
*) 
	echo $index
	echo
	echo "I didn't understand, try again."
	choose_method
esac
}

read_texts
choose_method 

```

You also had your "if"s structured in a nightmare way. You can use  function called "elif" to do "else" with another "if" inside it.

---

### Post by J05HYYY on 2009-10-03
fixed problems, and shows text before and after
```

#!/bin/sh
# Different types of search by J05HYYY - with help from husseincoder, NoaHall et al.

read_texts () {
echo
echo
echo "Enter the line of text to be searched:"
read intext
inlength=${#intext}
echo
echo "Enter the pattern to be searched for:"
read searchtext
}

method1 () {
	echo
	echo
	echo "The position of the beginning of the pattern, starting from the end of the text is:"
	index=$(expr "$intext" : '.*'$searchtext - $(expr $searchtext : '.*'))
	echo $index
}

method2 () {
	echo
	echo
	echo "The position of the end of the pattern, starting from the end of the text is:"
	searchlength=${#searchtext}
	index=$(expr "$intext" : '.*'$searchtext - $(expr $searchtext : '.*') + $searchlength)
	echo $index
}

method3 () {
	echo
	echo		
	echo "The position of the end of the pattern, starting from the start of the text is:"
	revintext=`echo $intext | rev`
	revsearchtext=`echo $searchtext | rev`
	index=$((inlength-$(expr $revintext : '.*'$revsearchtext - $(expr $revsearchtext : '.*'))))
	echo $index
}

method4 () {
	echo
	echo			
	echo "The position of the beginning of the pattern, starting from start of the text is:"
	searchlength=${#searchtext}
	revintext=`echo $intext | rev`
	revsearchtext=`echo $searchtext | rev`
	index=$((inlength-$(expr $revintext : '.*'$revsearchtext - $(expr $revsearchtext : '.*') + $searchlength)))
	echo $index
}

choose_method () {
echo
echo
echo "You can either:"
echo
echo "1) Get the position of the beginning of the pattern, starting from the end of the text."
echo "2) Get the position of the end of the pattern, starting from the end of the text."
echo "3) Get the position of the end of the pattern, starting from the start of the text."
echo "4) Get the position of the beginning of the pattern, starting from start of the text."
read method
case $method in
1)
method1
;;
2)
method2	
;;
3)
method3	
;;	
4)
method4
;;
*) 
	echo
	echo "I didn't understand, try again."
	choose_method
esac
}

print_beforeafter () {
echo "The text before the position is:"
echo $intext | cut -c 1-$index
echo "The text after the position is:"
cutindex=$(($index+1))
echo $intext | cut -c $cutindex-$inlength
}

read_texts
choose_method
print_beforeafter

```

---

### Post by NoaHall on 2009-10-03
Make sure you put the shebang in. Helps to stop problems.

---

### Post by renkinjutsu on 2009-10-03
wouldn't the script just be ran as a Bash script if the shebang were left out?

---

### Post by NoaHall on 2009-10-03
Well, /bin/sh != /bin/bash
It's best to set it clear which one it is. sh doesn't work in the same way as bash.

---

### Post by J05HYYY on 2009-10-03
np - must of missed it when copying it over. noa is right, bash =! sh ... but this should be able to run in either anyways.

I realised that method 3/4 wasn't working so I fixed it

---

### Post by NoaHall on 2009-10-03
Have you thought about making a GUI version of your program?
It's pretty easy, and ideal if you're going to make to try and get people to use it.

---

### Post by J05HYYY on 2009-10-03
When it's done, I may consider but mostly, I just want it running in an sh shell so's it's nice and portable.

The code below reads a file into an array (Bourne shell style):

```

#!/bin/sh

while read linevar
do
eval array$i=$linevar
eval echo "value of array$i = \$array$i"
i=$((i+1))
done < filestoget

```

[... took me ages to find]("http://www.linuxquestions.org/questions/linux-general-1/how-to-use-array-in-sh-shell-644142/")

---

### Post by J05HYYY on 2009-10-04
```

#!/bin/sh
# PhatFTP - Recursively downloading FTP files with this script is phat :P

output_helpusage(){
helpusage=\
"
PhatFTP is a program for downloading ftp files and folders recursively.
_______________________________________________________________________

USAGE:
${0##*/} [Server Name] [Remote Directory] [Local Directory] [User Name]
_______________________________________________________________________

Server Name:
This is the name of the host you are connecting to eg. ftp.someserver.org
Remote Directory:
This is the path of the directory on the server you want to download recursively eg. this/is/some/directory/
Local Directory:
This is the path of the directory on your machine you want the files to be downloaded into.
If it does not already exist, it will be created.
User Name:
This is the user name you should use to identify yourself to the remote FTP server.

(NOTE: A password will be asked for twice during the download.)
"
echo "$helpusage"
exit
}

case $1 in
"-h"|"--h"|"-help"|"--help"|"--args"|"-args"|"-arguments"|"--arguments"|"")
output_helpusage;;
esac

if [ $2 = NULL ] ; then
output_helpusage
fi

if [ $3 = NULL ] ; then
output_helpusage
fi

if [ $4 = NULL ] ; then
output_helpusage
fi

server=$1
directory=$2
loco=$3
username=$4

#read -p "Server: " server
#read -p "Remote Directory: " directory
#read -p "Local Directory: " loco
#read -p "Username: " username

i=0

if [ -d $loco ] ; then #if the local directory doesn't exist yet
cd $loco
else
mkdir $loco #create it
cd $loco
fi

basedir=$PWD

getfiles () {
while read lineout
do
$lineout
done
}

readlines () {
while read linein
do
if [ $i = 0 ] ; then
echo "ftp -n $server"
echo "user $username $password"
echo "cd $directory"
i=1
fi
linetoread=$linein
if ! [ "$linetoread" = "" ] ; then #if the line does not equal nothing
index=$(expr "$linetoread" : '.*/' - $(expr "/" : '.*') + 1) #get position of /

	if [ "$index" -gt "0" ] ; then # if it contains a /
	firsttwochars=`echo "$linetoread" | cut -c 1-2` #get the first 2 characters

		if [ "$firsttwochars" = "./" ] ; then # and if the line has ./ at the start
		linelength=$((${#linetoread}-1)) #get the length -1 (the colon)
		thefolder=`echo "$linetoread" | cut -c 3-$linelength` #trim off the colon and the ./
			

			if ! [ -d $thefolder ] ; then #if the folder doesn't exist
			mkdir $thefolder #create it
			fi

			echo "cd /$directory$thefolder"
		fi
	elif [ "$index" = "0" ] ; then # if it doesn't contain a / linetoread is a file
	echo "get $linetoread $basedir/$thefolder/$linetoread" 
	fi
fi

done
echo "bye"
}

ftp -n -i $server <<endftpone | readlines | getfiles
user $username $password
cd $directory
ls -pR1
bye
endftpone

```

---

### Post by ApEkV2 on 2009-10-04
>  echo 'Enter the server in the form "ftp.*.*"'
read server
echo 'Enter the directory in the form "*/*/"'
read directory
echo "Enter the username"
read username 
Couldn't you just do this?
```
read -p "Enter the server in the form [ ftp.*.* ]" server
read -p "Enter the directory in the form [ */*/ ]" directory
read -p "Enter the username" username 
```
Eliminate the unneeded echoes?

---

### Post by J05HYYY on 2009-10-04
Yep ... will do that instead then. cheers.

The get_list function needs some work doing to it. I'm looking at the command "ls -pR1" to get the files recursively instead of "mls * filestoget" as to avoid saving anything to disk - hopefully piping the output of the here-document into an array instead.

... will have to work on this.

EDIT: I have updated the code, it is very nearly finished :)

---

### Post by J05HYYY on 2009-10-05
Sorry for the double post. I've updated the recursive ftp script above and it works fine, but I get an error saying "?Invalid command" every now and again. Haven't managed to work out what it is... Please give any suggestions as to why this could be happening.

---

### Post by ApEkV2 on 2009-10-05
I do see a potential problem with "echo $thefolder" on line 36 where you don't use double quotes (should use them).
Every echo should use double quotes around whatever you want to echo (it could give "interesting results" if you don't).

Here are some other instances.
Line 27 "echo $linetoread" should be echo "$linetoread"
Line 31 "echo $linetoread" should be echo "$linetoread"
And line 36 should be echo "$thefolder"
It looks like all the other echoes are alright.
Other than those, does this bad command error give a line number?

---

### Post by bigboy_pdb on 2009-10-05
I haven't read the scripts. I figured that writing them is good practice and I don't want to comment on the programs themselves, but I did want to mention a few things that would help your style since you seem to be open to feedback.

You can avoid echo statements by using one larger string and echoing the variable. For example:

```

#!/bin/bash
scriptname="${0##*/}" # The name of this script

usage=\
"USAGE: $scriptname ARGUMENTS

<Detailed Information Here>
..."

echo "$usage"

```

Also, you can use bash quoting when you need many newlines. If you need to use variables within a string which is quotes, you can concatenate strings:

```

# Prints three lines
echo $'\n\n\n'

# Prints three lines followed by the home directory followed by three lines
echo $'\n\n\n'"$HOME"$'\n\n\n'

```

To learn more about it in the bash man page search on a line beginning with QUOTING or lines with $'. To search press the forward slash in the man page. The following are the lines you'd use, respectively (but don't type the forward slash):
```

/^QUOTING
/\$'

```

---

### Post by J05HYYY on 2009-10-06
It's pretty much all done and dusted now. Thanks for the help everyone, much appreciated. :)

---

