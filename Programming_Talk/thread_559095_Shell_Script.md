---
title: "Shell Script"
date: 2007-09-24
forum: Programming Talk
---

### Post by Mbengi Bongi on 2007-09-24
Can someone please help me here:

I am a total newbie to Shell Scripting so please bear with me.

What I want is a Shell Script that asks me for some input, if the input matches an existing text file* the script displays the contents of it, if it does not find a match an error message appears

* i only want to iput the filename not the extansion 
e.g. i want to input **stp** not **stp.txt**

Any help would be appreciated :)

---

### Post by Ramses de Norre on 2007-09-24
Something like this:
```
#!/bin/bash

read FILE

if [ -f ${FILE} ]; then
    cat ${FILE}
else
    echo "File ("${PWD}"/"${FILE}") not found."
fi

```
You need to give the full name though (extension included). I'm not sure how to make this extension-insensitive in an easy way. I'll post again if I find something.

---

### Post by Note360 on 2007-09-24
hehe. ok basically you cant make it extension insensitve because in linux  abc.txt is completely different form abc.so or abc or abc.sh

first of all instead of .txt you should be using .sh. Further, if you want to make it run as abc instead od abc.sh just rename it to abc and chmod it to executable

example

```

$ mv abc.sh abc
$ chmod +x abc

```

---

### Post by Ramses de Norre on 2007-09-25
> **Note360 said:**
> hehe. ok basically you cant make it extension insensitve because in linux  abc.txt is completely different form abc.so or abc or abc.sh

first of all instead of .txt you should be using .sh. Further, if you want to make it run as abc instead od abc.sh just rename it to abc and chmod it to executable

example

```

$ mv abc.sh abc
$ chmod +x abc

```

He means that he gives the program only "abc" as input and that it displays all textfiles which have abc.* as name (abc.txt, abc.sh, abc.c, ...) of course you can name your executable as you wish.

If he only wants to match "abc.txt" if he inputs "abc" it's easy, but if he wants all text files it gets quite hard... I don't know how to test for text files in bash.

---

### Post by Compyx on 2007-09-25
You can use the 'file' command to check the type of a file.
For example, when I run the command on a C source file:
```

compyx@gutsy:~$ file charbits.c 
charbits.c: ASCII C program text
compyx@gutsy:~$ mv charbits.c charbits
compyx@gutsy:~$ file charbits
charbits: ASCII C program text

```

it would seem the program actually looks at the contents of the file, not just the name.

So you should be able to grep the output of a file command to check whether a file is a text file. It can also handle ISO-8859-x, UTF-8, UTF-16 and EBCDIC. You might want to check the man page for more information.

---

### Post by gnusci on 2007-09-25
I just did and small modification to the script provided by  **Ramses de Norre**

[PHP]
#!/bin/sh

echo -n "file: "
read FILE

TEXT_FILE=${FILE}".txt"

if [ -f ${TEXT_FILE} ]; then
    cat ${TEXT_FILE}
else
    echo "File ("${PWD}"/"${TEXT_FILE}") not found."
fi

[/PHP]

---

### Post by Cappy on 2007-09-25
The syntax for this script looks like this:
```

sh whateveryounamethescript "partial_name_of_file"

```

And the script:
```

#!/bin/sh
userinput="$1"
listoffiles=`ls -B *$userinput*`
#echo "$listoffiles" #Prints list of files that matched
if [ -z "$listoffiles" ]; then
	#Could put custom error here
	exit
fi
echo "$listoffiles" |
while read line; do #using a read allows spaces in filename
	cat "$line"
done

```

If you put in "plane" it would match
astroplane.txt
plane.txt
anythingplaneanything

if you only want "plane" to match "plane.txt" or "plane.ext" then you could use
```

listoffiles=`ls -B $userinput\.*`

```
instead

ls -B prevents listing of backup files like plane~ or astroplane.txt~ that occur when you edit a file.

---

### Post by Mbengi Bongi on 2007-09-25
> **gnusci said:**
> I just did and small modification to the script provided by  **Ramses de Norre**

[PHP]
#!/bin/sh

echo -n "file: "
read FILE

TEXT_FILE=${FILE}".txt"

if [ -f ${TEXT_FILE} ]; then
    cat ${TEXT_FILE}
else
    echo "File ("${PWD}"/"${TEXT_FILE}") not found."
fi

[/PHP]


This is exactly what I need! :guitar:

I knew I needed an **if** statement involving **cat** and **read** but just couldn't string it together! 


One other thing, is there a command I could put at the end of the script to delay the prompt, similar to the DOS command **pause** ?

---

### Post by mssever on 2007-09-25
> **Mbengi Bongi said:**
> One other thing, is there a command I could put at the end of the script to delay the prompt, similar to the DOS command **pause** ?

I don't know what the DOS command does, but you could do something like ```
read -n 1 -p "Press any key to continue: "
```

---

### Post by gnusci on 2007-09-25
If what you want is to stop the file so you have time to read instead to have a bunch of lines passing at hight speed through the screen, just change **cat** by **more**.

---

### Post by mssever on 2007-09-25
> **gnusci said:**
> just change **cat** by **more**.[FONT=Courier New]less[/FONT] is better than [FONT=Courier New]more[/FONT].

---

### Post by Mbengi Bongi on 2007-09-25
That's superb guys, I think I can take if from here ....


Thanks very much! :)

---

### Post by shafi on 2008-05-31
Some Cool Shell Scripts

if you want to learn scripting go through the scripts in the following link:


    [http://geocities.com/shafitokhi/linux.html](http://geocities.com/shafitokhi/linux.html)

---

### Post by Mbengi Bongi on 2008-10-15
Thanks very much again guys :)

---

