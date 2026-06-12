---
title: "shell script to search filenames for special characters and replaces them"
date: 2008-06-30
forum: Programming Talk
---

### Post by whitethorn on 2008-06-30
Hi,

I want to write a shell script that'll search through all the filename in a directory and change certain characters with another.  I'm wondering if the best way is using regular expressions, or something else.  Pretty much what I'm looking for are some examples or ideas which way to go about this.

---

### Post by HalPomeranz on 2008-06-30
I'd use the rename command.  For example, here's the command to turn all spaces into underscores:

```

rename 's/\s+/_/g' *

```

The rename command uses Perl syntax for the replacement operator (the 's/\s+/_/g' stuff in the command above), so boning up on Perl will help here.  

Note that there's a "-n" option you can use to have the command show you what it would do without actually making the change:

```

$ **rename -n 's/\s+/_/g' ***
foo bar renamed as foo_bar
$ **rename 's/\s+/_/g' ***
$ **ls**
foo_bar

```

This "try before you buy" approach can be very useful if you're not sure of your Perl expression.  Heck, I use "-n" all the time and I've been programming Perl for over 15 years...

---

### Post by ghostdog74 on 2008-06-30
if you have rename, then you can give it a try. However without rename you can just as well use common tools available, or even with the shell
1) eg for one directory
```

for FILES in *.txt
do
 newfile=${FILES/abc/def} #change abc to def
 mv "$FILES" "$newfile"
done

```

2) eg for subdirectories, use find
```

find /mydir -type f -name "*.txt" | while read FILES
do
 newfile=${FILES/abc/def} #change abc to def
 mv "$FILES" "$newfile"
done

```

---

### Post by whitethorn on 2008-07-03
Hi, so I've been working on this, and so far I've gotten it to replace almost what I need.  The reason I'm doing this is because at my institut they have a dsmc client running the server is at the computer center.  Neway at the moment I'm having problems getting it to change these characters  

! ? ' (space) / \

Here's my program code :  The parts I've greyed out don't work.  Ne ideas?  Is there a way to use ascii code to identify the different symbols?  


> #!/bin/bash
find . -iname "*ä*" | while read a then
	do 
		echo "$a"
			case $a in
				*ä*) mv -f "$a" "${a%ä}ae";;
				*Ä*) mv -f "$a" "${a%Ä}AE";;
			esac
	done

find . -iname "*ö*" | while read b then
	do 
		echo "$b"
			case $b in
				*ö*) mv -f "$b" "${b%ö}oe";;
				*Ö*) mv -f "$b" "${b%Ö}OE";;
			esac
	done

find . -iname "*ü*" | while read c then
	do 
		echo "$c"
			case $c in
				*ü*) mv -f "$c" "${c%ü}ue";;
				*Ü*) mv -f "$c" "${c%Ü}UE";;
		esac
	done

#find . -iname "* *" | while read d then
#	do
#		mv -f "$d" "${d% }_"
#	done

find . -iname "*ß*" | while read e then
	do
		mv -f "$e" "${e%ß}sz"
	done

find . -iname "*@*" | while read f then
	do
		mv -f "$f" "${f%@}(at)"
	done

find . -iname *'?'* | while read g then
	do
		mv -f "$g" "${g%'?'}JKJK"
	done

#find . -iname "*'*" | while read h then
#	do
#		mv -f "$h" "${h%'}."
#	done

find . -iname "*!*" | while read i then
	do 
		mv -f "$i" "${i%!}_"
	done

#find . -iname "*\*" | while read j then
#	do 
#		mv -f "$j" "${j%\}_"
#	done

#find . -iname "*/*" | while read j then
#	do 
#		mv -f "$j" "${j%/}."
#	done

---

