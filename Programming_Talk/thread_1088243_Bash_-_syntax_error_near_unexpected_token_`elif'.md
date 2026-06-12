---
title: "Bash - syntax error near unexpected token `elif'"
date: 2009-03-05
forum: Programming Talk
---

### Post by Squigy Dunkens on 2009-03-05
i am learning bash, and i made this program just for a little project

```
#!/bin/bash
read -p "Hello, I'm Yooten. I am programmed to greet you and give you a few options in a friendly manner. What is your name? " name;

function tehstart {
	echo What would you like to do today?

	options = "ListFiles Make/EditFile Quit"
	select choice in $options; do
		if [ "$choice" = "ListFiles" ]; then
			echo Would you like to list the files of the current directory, or a different directory?
			options2 = "Current Different Back"
			select choice2 in $options2; do
				if [ "$choice2" = "Current" ]; then
					echo Ok, the files in this directory are...
					ls
				elif [ "$choice2" = "Different" ]; then
					read -p "Ok, which directory do you want to list the files of? " directory;
					echo Ok, the files in $directory are...
					ls
				elif [ "$choice2" = "Back" ]; then
					tehstart
				else
					echo !NOT AN OPTION!
				fi
			done
		elif [ "$choice" = "Make/EditFile" ]
			read -p "What should the file name be, or if your editing a file, what is the file name" filename;
			vim $filename
		elif [ "$choice" = "Quit" ]
			exit
		else
			echo !NOT AN OPTION!
		fi
	done
}
tehstart
```

but when i run it it asks for my name, then after i type my name it shows

```
./yooten.sh: line 29: syntax error near unexpected token `elif'
./yooten.sh: line 29: `         elif [ "$choice" = "Quit" ]'

```

anyone know whats wrong with it?

---

### Post by ghostdog74 on 2009-03-05
hint: ```
echo !NOT AN OPTION!
```

---

### Post by Squigy Dunkens on 2009-03-05
thinking... thinking!... THINKING!!!... HITTING HEAD ON A WALL!!!...
umm, i think i need another hint...

---

### Post by ghostdog74 on 2009-03-05
try that echo statement on the command line. do you get an error? you can use  ```
set -x 
``` in your script to help in debugging.

---

### Post by Squigy Dunkens on 2009-03-05
oh! exclamation marks make an event somehow? i didnt know that.

---

### Post by Squigy Dunkens on 2009-03-05
thanx

---

### Post by Squigy Dunkens on 2009-03-05
```
#!/bin/bash
set -x
read -p "Hello, I'm Yooten. I am programmed to greet you and give you a few options in a friendly manner. What is your name? " name;

function tehstart {
        echo What would you like to do today?

        options = "ListFiles Make/EditFile Quit"
        select choice in $options; do
                if [ "$choice" = "ListFiles" ]; then
                        echo Would you like to list the files of the current directory, or a different directory?
                        options2 = "Current Different Back"
                        select choice2 in $options2; do
                                if [ "$choice2" = "Current" ]; then
                                        echo Ok, the files in this directory are...
                                        ls
                                elif [ "$choice2" = "Different" ]; then
                                        read -p "Ok, which directory do you want to list the files of? " directory;
                                        echo Ok, the files in $directory are...
                                        ls
                                elif [ "$choice2" = "Back" ]; then
                                        tehstart
                                else
                                        echo Sorry, Thats not an option
                                fi
                        done
                elif [ "$choice" = "Make/EditFile" ]
                        read -p "What should the file name be, or if your editing a file, what is the file name" filename;
                        vim $filename
                elif [ "$choice" = "Quit" ]
                        exit
                else
                        echo Sorry, thats not an option
                fi
        done
}
tehstart
```
ok, im confuzzled. i still get the same error but it says line 30 instead of 27

---

### Post by nunki on 2009-03-05
> **Squigy Dunkens said:**
> i am learning bash, and i made this program just for a little project

```
#!/bin/bash
read -p "Hello, I'm Yooten. I am programmed to greet you and give you a few options in a friendly manner. What is your name? " name;

function tehstart {
	echo What would you like to do today?

	options = "ListFiles Make/EditFile Quit"
	select choice in $options; do
		if [ "$choice" = "ListFiles" ]; then
			echo Would you like to list the files of the current directory, or a different directory?
			options2 = "Current Different Back"
			select choice2 in $options2; do
				if [ "$choice2" = "Current" ]; then
					echo Ok, the files in this directory are...
					ls
				elif [ "$choice2" = "Different" ]; then
					read -p "Ok, which directory do you want to list the files of? " directory;
					echo Ok, the files in $directory are...
					ls
				elif [ "$choice2" = "Back" ]; then
					tehstart
				else
					echo !NOT AN OPTION!
				fi
			done
		elif [ "$choice" = "Make/EditFile" ]**;then**
			read -p "What should the file name be, or if your editing a file, what is the file name" filename;
			vim $filename
		elif [ "$choice" = "Quit" ]**;then**
			exit
		else
			echo !NOT AN OPTION!
		fi
	done
}
tehstart
```

but when i run it it asks for my name, then after i type my name it shows

```
./yooten.sh: line 29: syntax error near unexpected token `elif'
./yooten.sh: line 29: `         elif [ "$choice" = "Quit" ]'

```

anyone know whats wrong with it?


See my edits in bold

---

### Post by jenkinbr on 2009-03-05
> **nunki said:**
> See my edits in bold
That, and also try changing your echo line from ```
echo !not an option!
```
to
```
echo -e "\!Not an Option\!"
```

---

### Post by Squigy Dunkens on 2009-03-05
more problems from me, the problem master
./yooten.sh: line 7: options: command not found

---

### Post by ghostdog74 on 2009-03-05
put set -x in your script and run it. see what happens
```

#!/bin/bash
set -x
....

```

---

### Post by nunki on 2009-03-05
> **Squigy Dunkens said:**
> more problems from me, the problem master
./yooten.sh: line 7: options: command not found

```

#!/bin/bash
read -p "Hello, I'm Yooten. I am programmed to greet you and give you a few options in a friendly manner. What is your name? " name;

function tehstart {
        echo What would you like to do today?

        **select choice in "ListFiles" "Make/EditFile" "Quit"**
        do
                if [ $choice = "ListFiles" ]; then
                        echo Would you like to list the files of the current directory, or a different directory?
                        **select choice2 in   "Current" "Different" "Back"**
                        do
                                if [ $choice2 = "Current" ]; then
                                        echo Ok, the files in this directory are...
                                        ls
                                elif [ $choice2 = "Different" ]; then
                                        read -p "Ok, which directory do you want to list the files of? " directory;
                                        echo Ok, the files in $directory are...
                                        ls
                                elif [ $choice2 = "Back" ]; then
                                        tehstart
                                else
                                        echo !NOT AN OPTION!
                                fi
                        done
                elif [ $choice = "Make/EditFile" ];then
                        read -p "What should the file name be, or if your editing a file, what is the file name" filename;
                        vim $filename
                elif [ $choice = "Quit" ];then
                        exit
                else
                        echo !NOT AN OPTION!
                fi
        done
}
tehstart

```

More edits in bold. Also removed the quotes around the $choice variables

---

### Post by Squigy Dunkens on 2009-03-05
> **nunki said:**
> Also removed the quotes around the $choice variables

thanks, everything is working fine now, but i think you have to have the quotes, because when i did it without quotes around the choice variables, it spit out more errors, then i put them back and it worked again.

---

