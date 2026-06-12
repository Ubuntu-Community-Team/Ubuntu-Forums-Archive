---
title: "Awkward Result in Python"
date: 2009-05-01
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-05-01
Yo guys I am programming a script in python and when I make it execute 100% working bash code it ends up giving me an error. Here it is:
```

----------------MENU-----------------
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------
Select option: 1
./[1-5]
./empty1
Traceback (most recent call last):
  File "cleaner.py", line 34, in <module>
    delEmptyDirs()
  File "cleaner.py", line 6, in delEmptyDirs
    for item in os.system('find ./ -type d -empty'):
TypeError: 'int' object is not iterable
aaron@T60:~/Documents/Programming/BashProjects/test$ find . -type d -empty
./[1-5]
./empty1

```
It finds the correct directories but then errors up for some reason. Here are the relevant portions of my script code:
```

#!/usr/bin/python

import os

def delEmptyDirs():
	for item in os.system('find ./ -type d -empty'):
		print item
#...
delEmptyDirs()
#...

```
Thanks in advance!

---

### Post by loell on 2009-05-01
you can't iterate from **os.system** because it only returns an int ( 0 or 1)

possibly use os.exec instead.

---

### Post by sekinto on 2009-05-01
It's because
```
os.system('find ./ -type d -empty')
```
returns a 0 if it completes successfully, not a list.

---

### Post by ghostdog74 on 2009-05-01
why are you mixing bash and Python when you don't have to? If you want to use find , do it in the shell. If you want to use Python to delete empty folders, use the os.walk() method 
```

for r,d,f in os.walk("/my/path"):
    if not f and not d:
        print "empty folder: ",r
        # use os.rmdir() here to remove empty directory

```

start to read up the docs and the various Python inbuilt functions and libraries if you want to know more about Python.

if you are doing it with shell
```

menu() {
cat <<EOF
----------------MENU-----------------
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------

EOF

}

while true
do
    menu
    printf "Enter choice: "
    read choice
    case $choice in
        2) printf "you choose 2"
           find $path -type f \( -iname "*.nfo" -o -iname "*.sfv" -iname "*.txt" -o -iname "*.m3u" \) -exec rm {} +;;
        1) print "you choose 1";;
           find $path -type d -empty -delete;;
        0) exit;;        
    esac
done


```

look up my sig for bash link to learn more.

---

### Post by StunnerAlpha on 2009-05-01
Thanks guys, I actually did it this way beforehand and it works(not recursively though):
```

#def delEmptyDirs():
#	for item in os.listdir(os.getcwd()):
#		if os.path.isdir(item):
#			 print item
#			 if os.listdir(item) == []:
#			 	yn = raw_input("Would you like to remove " + item + "?(Y/N)")
#			 	print yn

```

I thought that mixing bash with python would be a simple way to minimize my code and make it look simpler and nicer. Oh and I have decided to just stick with python now since it can be run on multiple systems and I have given up on trying to get bash to recognize folders with a space in thier names(one of my other threads). And os.exec is not working for me. And I am actually looking at the help files for os and shutil and other modules before I google for the answer, when I can't find it, I come here. Thanks for all the help!

---

### Post by StunnerAlpha on 2009-05-01
Getting another wierd result... here is the relevant code:
```

def delEmptyDirs():
	for r,d,f in os.walk("."):
		if not f and not d:
			yn = raw_input("Would you like to remove " + r + "?(Y/N)")
			print yn
			if yn == 'Y' or yn == 'y':
				print r," removed."
			if yn == 'N' or yn == 'n':
				print r," not removed."
			else:
				while True:
					yn = raw_input("Incorrect input! Re-enter choice(Y/N): ")
					if yn == 'Y' or yn == 'y':
						print r," removed."
						break
					if yn == 'N' or yn == 'n':
						print r," not removed."
						break

```
and here is the result:
```

----------------MENU-----------------
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------
Select option: 1
Would you like to remove ./[1-5]?(Y/N)y
y
./[1-5]  removed.
Incorrect input! Re-enter choice(Y/N): y
./[1-5]  removed.
Would you like to remove ./empty1?(Y/N)y
y
./empty1  removed.
Incorrect input! Re-enter choice(Y/N): y
./empty1  removed.
Would you like to remove ./chaat/filez/makillaz/emptah?(Y/N)y
y
./chaat/filez/makillaz/emptah  removed.
Incorrect input! Re-enter choice(Y/N): y
./chaat/filez/makillaz/emptah  removed.
DONE(hit ENTER)

```
I am just not seeing it... what is wrong?

---

### Post by ghostdog74 on 2009-05-01
your "else" parts belongs to the inner "if" where you test for "N" or "n". that's why you have that result. Instead of blindly going through these, get your Python basics right.

---

### Post by StunnerAlpha on 2009-05-01
Ah right! need to use elif... was copying over from my bash script and missed that thing... I have the basics down man, I am just not the greatest programmer...

---

