---
title: "case and menus"
date: 2011-11-22
forum: Programming Talk
---

### Post by crownedzero on 2011-11-22
I'm trying to make a bash menu displaying options but it contains sub menus as well. Is there anyway to add an identifier that will display with the menu?

Right now it displays

Option 1
Option 2
Option 3

I'd like to see 

Main Menu
Option 1
Option 2
Option 3 etc

---

### Post by crownedzero on 2011-11-22
```

echo "********************************************************************************"
echo "*                                  Main Menu                                   *"
echo "*                              User Interface Menu                             *"
echo "********************************************************************************"


	select main_menu in "Edit File" \
					"User Utilities" \
					"File/Directory Utilities" \
					"Exit"

	do
		case $main_menu in "Edit File" )
							;;
					    "User Utilities" )
							clear
							utilities_menu ;;
					    "File/Directory Utilities" )
							file_dir_menu ;;
					    "Exit" ) 
							break ;;
					    *)
							echo "You must select one of the above options"
		esac
	done

```

In this case I would like the Main Menu portion to be displayed everytime; not just the menu items

```

********************************************************************************
*                                  Main Menu                                   *
*                              User Interface Menu                             *
********************************************************************************
1) Edit File		     3) File/Directory Utilities
2) User Utilities	     4) Exit
Please select one of the options (hit RETURN to repeat the menu): 

```

Not just

```

1) Edit File		     3) File/Directory Utilities
2) User Utilities	     4) Exit
Please select one of the options (hit RETURN to repeat the menu): 


```

---

### Post by Vaphell on 2011-11-22
maybe something like this:

```
#!/bin/bash

break_msg=false
while true
do
  echo = MENU =
  select option in opt1 opt2 opt3 exit
  do
    case $option in opt1) echo "#1 selected";;
                    opt2) echo "#2 selected";;
                    opt3) echo "#3 selected";;
                    exit) break_msg=true;;                   
    esac    
    break
  done
  if $break_msg; then break; fi
done

```

by default select is an endless loop. Here it would be run only once and the endless part would be done by the outer while. You'd also need to differentiate between 'normal' break and the one for legit Exit option (you'd need to pass message to the outer while loop that it needs to break too)

---

### Post by crownedzero on 2011-11-22
Let me see if I'm understanding and try to expand on what you've said...

so in the case of 4) Exit have it set a parameter to whatever and check in the conditional statement to exit the script?

---

### Post by Vaphell on 2011-11-22
i updated my post: the code went from 'raw draft' to 'now working in practice'. And indeed some parameter needs to be set to trigger the break.

---

### Post by crownedzero on 2011-11-22
```

main_menu_function()
{
while true
	do
		echo "********************************************************************************"
		echo "*                                  Main Menu                                   *"
		echo "*                              User Interface Menu                             *"
		echo "********************************************************************************"
		
	select main_menu in "Edit File" \
						"User Utilities" \
						"File/Directory Utilities" \
						"Exit"
		do
			case $main_menu in 	"Edit File" ) 
									edit_file_function ;;
								"User Utilities" )
									utility_menu_function ;;
								"File/Directory Utilities" ) 
									file_dir_menu_function ;;
								"Exit" ) 
									exit_status=true
									break ;;
								*) echo "You must select one of the above options"
			esac    
			break
		done
	if [ $exit_status ]; then
		break
	fi
done
}

```

Think I got it, thanks!

I'm assuming this will translate to a submenu as well or would it need to be modified?

Scratch that just use a different break param and it works great thanks =)

---

### Post by crownedzero on 2011-11-22
Ok so here goes, I'm making a menu driven program for a project and I'm looking for feedback. I still need to tighten up the error handling (if exists etc.) but I welcome any feedback. Please let me know what you might think.

```

# Beginning of FUNCTIONS
main_menu_function()
{
while true
	do
		clear
		echo "********************************************************************************"
		echo "*                                  Main Menu                                   *"
		echo "*                              User Interface Menu                             *"
		echo "********************************************************************************"
		
	select main_menu in "Edit File" \
						"User Utilities" \
						"File/Directory Utilities" \
						"Exit"
		do
			case $main_menu in 	"Edit File" ) 
									edit_file_function ;;
								"User Utilities" )
									utility_menu_function ;;
								"File/Directory Utilities" ) 
									file_dir_menu_function ;;
								"Exit" ) 
									main_break=true
									break ;;
								*) echo "You must select one of the above options"
			esac    
			break
		done
	if [ $main_break ]; then
		break
	fi
done
}
utility_menu_function()
{
while true
	do
		clear
		echo "********************************************************************************"
		echo "*                                  Utilities                                   *"
		echo "********************************************************************************"
		
	select utility_menu in "Change Password" \
						"Display Date and Time" \
						"Display WHO Information" \
						"Return to Main Menu"
		do
			case $utility_menu in 	"Change Password" ) 
									change_passwd_function ;;
								"Display Date and Time" )
									display_date_time_function ;;
								"Display WHO Information" ) 
									display_who_info_function ;;
								"Return to Main Menu" ) 
									utility_break=true
									break ;;
								*) echo "You must select one of the above options"
			esac    
			break
		done
	if [ $utility_break ]; then
		break
	fi
done
}
file_dir_menu_function()
{
while true
	do
		clear
		echo "********************************************************************************"
		echo "*                             File/Directory Menu                              *"
		echo "********************************************************************************"
		
	select file_dir_menu in "List Files and Directories" \
						"Create a DIR" \
						"Remove a DIR" \
						"Remove a FILE" \
						"Rename(MOVE) a FILE" \
						"Copy a FILE" \
						"Return to Main Menu"
		do
			case $file_dir_menu in 	"List Files and Directories" ) 
										list_file_dir_function ;;
									"Create a DIR" )
										create_dir_function ;;
									"Remove a DIR" ) 
										remove_dir_function ;;
									"Remove a FILE" ) 
										remove_file_function ;;
									"Rename(MOVE) a FILE" ) 
										rename_file_function ;;
									"Copy a FILE" )
										copy_file_function ;;
									"Return to Main Menu" )	
										file_dir_break=true
										break ;;
									*) echo "You must select one of the above options"
			esac    
			break
		done
	if [ $file_dir_break ]; then
		break
	fi
done
}
edit_file_function()
{
		clear
		echo "********************************************************************************"
		echo "*                                VI File Editor                                *"
		echo "********************************************************************************"
		sleep .5
		
		echo -e "Please enter the file you'd like to edit using the FULL PATH"
		echo "If the file does not exist it will be created or [RETURN] to open a new file"
		read edit_file
		
		if [ -z $edit_file ]; then
			echo "Are you sure you want to open a blank file?"
			echo "'No' to escape, [RETURN] to continue"
			read edit_confirm
				if [ -z $edit_confirm ]; then
					vi
				elif [ $edit_confirm == "No" -o "no" ]; then
					break
				else
					echo "Could not understand your response, exiting..."
					sleep .5
					break
				fi
		check_file_function $edit_file
		edit_exists=$?
			if [ $edit_exists -eq 2 ]; then
				echo "Could not locate the file, would you like to create it?."
				echo "'No' to escape, [RETURN] to continue"
			read edit_confirm
				if [ -z $edit_confirm ]; then
					vi
				elif [ $edit_confirm == "No" -o "no" ]; then
					break
				else
					echo "Could not understand your response, exiting..."
					break
				fi				
				break
			elif [ $edit_exists -eq 1 ]; then
				vi $edit_file
			else
				echo "Could not understand your response, exiting..."
				break
			fi		
		fi
}
change_passwd_function()
{
	clear
	echo "********************************************************************************"
	echo "*                           Password Info and Change                           *"
	echo "********************************************************************************"	
	sleep .5

	clear
	echo -e "Are you sure you want to change your password?"
	echo -e "[RETURN] to go back, 'Yes' to continue"
	read pass_choice
	
	if [ -z $pass_choice ]; then
		break
	elif [ $pass_choice == "Yes" ] || [ $pass_choice == "yes" ]; then
		clear
		passwd
	else
		echo "Could not understand your response, exiting..."
		sleep .5
		break
	fi
}
display_date_time_function()
{
	clear
	echo "********************************************************************************"
	echo "*                              Date and Time Info                              *"
	echo "********************************************************************************"	
	sleep .5
	
	date
	echo -e "\n"
	cal
	echo -e "\nYou'll be returned to the menu in 5 seconds\n"
	sleep 5
	
}
display_who_info_function()
{
	clear
	echo "********************************************************************************"
	echo "*                                   WHO Info                                   *"
	echo "********************************************************************************"	
		
	who -a
	
	sleep 5
	echo -e "\nYou'll be returned to the menu in 5 seconds\n"
}
list_file_dir_function()
{
	clear
	echo "********************************************************************************"
	echo "*                          File and Directory Listing                          *"
	echo "********************************************************************************"	
	
	echo "Please enter the directory you would like information on"
	echo "Use the entire path to the directory: /home/user for example"
	echo "Press [RETURN] for the current directory"
	read ls_dir
	
	if [ -z $ls_dir ]; then
		ls_dir=$(pwd)
		clear
		echo $ls_dir
		ls -l $ls_dir
		echo "[RETURN] to continue"
		read random
	elif [ -n $ls_dir ]; then
		check_dir_function $ls_dir
		dir_good=$?
			if [ $dir_good -eq 1 ]; then
				clear
				echo $ls_dir
				ls -l $ls_dir
				echo "[RETURN] to continue"
				read random
				
			else
				clear
				echo "Directory does not exist or could not be found"
				sleep 2
				break
			fi
	else
		clear
		echo "Could not understand your response. Exiting..."		
		sleep 2
		break
	fi
		
	
}
create_dir_function()
{
	clear
	echo "********************************************************************************"
	echo "*                              Directory Creation                              *"
	echo "********************************************************************************"	
	
	echo -e "\nPlease enter the whole path to the DIR you'd like to create"
	read new_dir
	
	check_dir_function $new_dir
	dir_exists=$?
		if [ dir_exists = 1 ]; then
			echo "This directory already exists"
		else
			echo "Are you sure you want to create $new_dir"
			echo "[Yes] to accept, [RETURN] to skip"
			read create_dir
				if [ -z $create_dir ]; then
					break
				elif [ $create_dir == "Yes" ] || [ $create_dir == "yes" ]; then
					mkdir -p $new_dir
				else
					echo "Could not understand your response, exiting..."
					break
				fi
		fi		
			
}
remove_dir_function()
{
	clear
	echo "********************************************************************************"
	echo "*                             Directory Removal                                *"
	echo "********************************************************************************"	
	
	echo -e "\nPlease enter the whole path to the DIR you'd like to remove"
	read dead_dir
	
	check_dir_function $dead_dir
	dir_exists=$?
		if [ dir_exists = 2 ]; then
			echo "This directory does not exist"
		else
			echo "Are you sure you want to remove $dead_dir"
			echo "[Yes] to accept, [RETURN] to skip"
			read remove_dir
				if [ -z $remove_dir ]; then
					break
				elif [ $remove_dir == "Yes" ] || [ $remove_dir == "yes" ]; then
					rm -r $dead_dir
				else
					echo "Could not understand your response, exiting..."
					break
				fi
		fi		
		
	
	
}
remove_file_function()
{
	clear
	echo "********************************************************************************"
	echo "*                                File Removal                                  *"
	echo "********************************************************************************"	
	
	echo -e "\nPlease enter the whole path to the FILE you'd like to remove"
	read dead_file
	
	check_file_function $dead_file
	file_exists=$?
		if [ $file_exists = 2 ]; then
			echo "This file does not exist"
		else
			echo "Are you sure you want to remove $dead_file"
			echo "[Yes] to accept, [RETURN] to skip"
			read remove_file
				if [ -z $remove_file ]; then
					break
				elif [ $remove_file == "Yes" ] || [ $remove_file == "yes" ]; then
					rm -r $dead_file
				else
					echo "Could not understand your response, exiting..."
					break
				fi
		fi		
		
	
	
}
rename_file_function()
{
	clear
	echo "********************************************************************************"
	echo "*                            Rename(MOVE) a FILE                               *"
	echo "********************************************************************************"
	
	echo "Please enter the FILE you'd like to rename(MOVE)"
	echo "Remember to use the FULL PATH"
	read old_file
	check_file_function $old_file
	file_exists=$?
		if [ $file_exists = 1 ]; then
			echo "Please enter the FILE you'd like to rename(MOVE) it to"
			echo "Remember to use the FULL PATH"
			read new_file
			check_file_function $new_file
				if [ $file_exists = 1 ]; then
					echo "This file already exists, proceeding will prompt to overwrite it"
				fi
		else
			echo "This file does not exist, or could not be found"
				
		fi

		
}
copy_file_function()
{
	echo "You've selected the copy file function"	
}
check_dir_function()
{
	dir_to_check=$1
		if [ -e $1 ];then
			return 1
		else
			return 2
		fi
}
check_file_function()
{
	file_to_check=$1
		if [ -e $1 ]; then
			return 1
		else
			return 2
		fi
}

# End of FUNCTIONS

# Beginning of SCRIPT

#establish default prompt
PS3="Please select one of the options (hit RETURN to repeat the menu): "

clear

main_menu_function
		



```

---

