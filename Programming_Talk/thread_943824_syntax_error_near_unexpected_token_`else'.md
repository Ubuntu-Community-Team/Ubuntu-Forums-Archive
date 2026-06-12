---
title: "syntax error near unexpected token `else'"
date: 2008-10-10
forum: Programming Talk
---

### Post by Dark_X on 2008-10-10
I am a noob trying to write a script.  I took a Visual Basic class at my high school and now I am taking c++ so I know a little about programming.  What I want to do is make a script that will compile a source code that I download through a svn.  The program is filezilla.  This is my first time ever trying to write a script.
```
#!/bin/bash

# Enter home directory
cd /home

# Check for user name "joe"
# If user "joe" is found run the script, if not end script.
directy="./joe"
if [-e $directy ];
then

	# Enter user directory
	cd joe
	
	# Check for filezilla directory
	# If filezilla is found run the script, if not end script.
	directy2="./filezilla"
	if [-e $directy2 ];
	then
		
		# Enter filezilla directory
		cd filezilla

		#check for the autogen script
		# If autogen is found run the script with autogen, if not run script without autogen.
		file="./autogen.sh"
		if [-e $file ];
		then

			# Build commands with autogen
			#./autogen.sh
			#./configure
			#make
			#make install
			#make clean
		else
		
			# Run build without autogen
			echo "No autogen file found... attempting to run configure."

			# Check for configure file.
			# If file is there run build, if not you aren't in the source's directory.
			file2="./configure"
			if [-e $file2 ];
			then

				# Build commands without autogen.
				#./configure
				#make
				#make install
				#make clean
			else
			
				# If there is no configure file check for makefile and try to run it.
				# Check for make file.
				file3="./makefile"
				if [-e $file3 ];
				then

					# Buid without configure
					#make
					#make install
					#make clean
				else

					# Error message
					echo "There is no makefile here.  Maybe you need to redownload the source."
				fi
			fi
		fi
	else

		#error message
		echo "Filezilla source directory not found.  Place filezilla in /home/joe."
	fi
else

	#Error message
	echo "This script will not work for this user name."
fi
done
```
I commented out the some of it so that it doesn't actually compile anything.  When I try to run it I get ```
/home/joe/filezilla.sh: line 36: syntax error near unexpected token `else'
/home/joe/filezilla.sh: line 36: `		else'
```
Please tell me what I did wrong.
I used this [website]("http://www.linuxconfig.org/Bash_scripting_Tutorial") as a reference.

---

### Post by squaregoldfish on 2008-10-10
Random stab in the dark - is the script getting confused because you've commented out *every* line in the if...then block?

Try putting a simple echo command in.

Steve.

---

### Post by mali2297 on 2008-10-10
There are several empty statements between *then* and *else*. You need to put something there, for example the *true* command (it just does nothing).

Also, remove the *done* at the end.

```

#!/bin/bash

# Enter home directory
cd /home

# Check for user name "joe"
# If user "joe" is found run the script, if not end script.
directy="./joe"
if [ -e $directy ];
        then

        # Enter user directory
        cd joe
        # Check for filezilla directory
        # If filezilla is found run the script, if not end script.
        directy2="./filezilla"
        if [-e $directy2 ];
                then
                # Enter filezilla directory
                cd filezilla
                #check for the autogen script
                # If autogen is found run the script with autogen, if not run script without autogen.
                file="./autogen.sh"
                if [-e $file ];
                        then [color=red]true[/color]
                        # Build commands with autogen
                        #./autogen.sh
                        #./configure
                        #make
                        #make install
                        #make clean
                else
                        # Run build without autogen
                        echo "No autogen file found... attempting to run configure."
                        # Check for configure file.
                        # If file is there run build, if not you aren't in the source's directory.
                        file2="./configure"
                        if [-e $file2 ];
                                then [color=red]true[/color]
                                # Build commands without autogen.
                                #./configure
                                #make
                                #make install
                                #make clean
                        else
                                # If there is no configure file check for makefile and try to run it.
                                # Check for make file.
                                file3="./makefile"
                                if [-e $file3 ];
                                        then [color=red]true[/color]
                                        # Buid without configure
                                        #make
                                        #make install
                                        #make clean
                                else
                                        # Error message
                                        echo "There is no makefile here.  Maybe you need to redownload the source."
                                fi
                        fi
                fi
        else
                #error message
                echo "Filezilla source directory not found.  Place filezilla in /home/joe."
        fi
else
        #Error message
        echo "This script will not work for this user name."
fi

```

---

### Post by Dark_X on 2008-10-10
Thanks. Now I can let this and wine compile overnight by itself. :)

---

