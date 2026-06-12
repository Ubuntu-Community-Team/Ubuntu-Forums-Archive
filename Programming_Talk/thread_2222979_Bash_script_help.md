---
title: "Bash script help"
date: 2014-05-08
forum: Programming Talk
---

### Post by grumblebum2 on 2014-05-08
I am trying to write a  bash script to change cursors and cursor size in trusty.

How do you go back to a certain section of a script when an entry error occurs.
Section of script
```
**## Choose size**
echo -e "\033[36mChoose your new cursor-size from 24, 32, 48, or 64  Default=24\033[36m"
	read SIZE

## Confirm choice
echo -e "\n\033[36mYou have selected a cursor size of \033[0m$SIZE\nContinue?(Y/n):"
	read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
	then
    		echo 
	else
		echo -e "\nYou chose not to continue..."
	  	echo -e "\n\033[36mYou have enabled the \033[0m$CURSOR \033[36mcursor theme with size unchanged of \033[0m$CURRENTSIZE\033[36m \nYou need to log out to complete the change:\033[0m";
		echo
	        read -n 1 -p "Press any key to exit this script..."
exit
fi

## Edits dconf to reflect chosen size

## match size to scale-factor
case "$SIZE" in

# 24=cursor-scale-factor 1
24)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 1
;;

# 32=cursor-scale-factor 1.35
32)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 1.35
;;

# 48=cursor-scale-factor 2
48)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 2
;;

# 64=cursor-scale-factor 2.65
64)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 2.65
;;

**# input error**
*)
echo "*** cursor size input error.... Try again ***"
;;
esac
```

At the **# input error** section how would I send that back to the **## Choose size** section.

---

### Post by steeldriver on 2014-05-08
I think the most common way would be to wrap the case construct in a while loop, and only break from the loop if a valid input is selected - this is a simple 2-case example that I just happen to have lying around

```

while true; do
  read -p "Would you like to reboot the system now (Y/N)? " ans
  case "$ans" in
    [yY]*) echo "You chose yes"
    break
    ;;

    [nN]*) echo "You chose no"
    break
    ;;

    *) echo "Oops - try again"
    ;;
  esac
done

```

Another option (although it changes the UI a little) is a select construct

```

select action in "reboot" "exit"
do
  case "$REPLY" in

  1) echo "You selected $action"
  # do something
  break
  ;;

  2) echo "You selected $action"
  # do something else
  break
  ;;

  *) echo "Please try again"
  ;;

  esac
done

```

For your particular application, have you considered putting the mapping from SIZE to cursor-scale-factor into an array and just doing an array lookup to get rid of the whole case thing altogether?

---

### Post by grumblebum2 on 2014-05-08
> **steeldriver said:**
> 

For your particular application, have you considered putting the mapping from SIZE to cursor-scale-factor into an array and just doing an array lookup to get rid of the whole case thing altogether?

I would consider that if I knew what I was doing. ;)

My knowledge is just from looking at other scripts and google with a pinch of copy and paste.

This is the entire script which I frankensteined together. :D
It gives a choice of cursors listed in /usr/share/icons, adds and selects your choice to alternatives and dconf while giving 
an option to change cursor size.
It works with any cursor theme (must have a cursor.theme file), but just trying to make it more foolproof for others to use.
Maybe if you have time you or someone else could clean it up.
The script works on trusty/unity as it has a new cursor-scale-factor dconf setting that overrides and changes the old cursor-size setting.
```
gsettings get com.canonical.Unity.Interface cursor-scale-factor
```

```
#!/bin/bash

####################################################################
##                                                                ##
##     Script to change cursors. Only lists themes installed to   ##
##     /usr/share/icons.                                          ##
##     Theme must have a cursor.theme file                        ##
##                                                                ##
####################################################################

####################################################################
##                                                                ##
##     To change the cursor theme, the script will                ##
##	1) Change dconf setting                                   ##
##	2) Register the theme with update-alternatives            ##
##	3} Select the theme in update-alternatives                ##
##                                                                ##
##     To change the cursor size the script will                  ##
##	1) Change dconf setting                                   ##
##	2) Edit the ~/.Xresources file or create if               ##
##         it doesn't exist                                       ##
##                                                                ##
##      ....................................                      ##
##      :   Tested in Ubuntu Raring 14.04  :                      ##
##      :..................................:                      ##
####################################################################

## Adapted for Trusty as it uses a new setting for cursor size
## gsettings set com.canonical.Unity.Interface cursor-scale-factor
echo -e "\n\033[36m This script only works for Ubuntu Trusty 14.04\033[36m"
CURRENTSIZE=$(gsettings get org.gnome.desktop.interface cursor-size)
THEME=$(gsettings get org.gnome.desktop.interface cursor-theme)
touch ~/.Xresources

## create installed cursor list text file
find /usr/share/icons -name "cursor.theme" | cut -f 5 -d '/' | sort > ~/.cursorlist.txt
#ls -R /usr/share/icons | grep "\/cursors:" | sed -e 's/\/cursors://g' -e 's/\/usr\/share\/icons\///g' > ~/.cursorlist.txt
echo -e "\n\033[36mYour current cursor theme is \033[0m$THEME \033[36m"

 
## show a numbered list of cursors to choose from
cat -b ~/.cursorlist.txt 
 
	echo -e "\033[36mEnter your new theme selection number:\033[0m"
	read CHOICE


## match the theme selection number to the cursor name
CURSOR=$(cat ~/.cursorlist.txt | sed -n $CHOICE'p') 
	echo -e "\n\033[36mYou have selected \033[0m$CURSOR\n\033[36mContinue?(Y/n):\033[0m"
	read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
  then
    echo -e "\n\033[36mUsing update-alternatives requires Authentication of Admin privileges...\033[0m"
  else
    echo -e "\nYou chose not to continue...\n"
	echo -e "\n\033[36mYour current cursor theme is \033[0m$THEME \033[36m"
	read -n 1 -p "Press any key to exit this script..."
exit
fi


## Change to selected  cursor
	gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" &
		sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20 & wait;
			sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme &
	#sudo sh -c "echo '[Icon Theme]\nInherits=$CURSOR' > /usr/share/icons/DMZ-White/cursor.theme"
wait;


## Set size of cursor unity. Trusty uses a dconf cursor-scale-factor setting which sets the cursor-size
CURRENTSIZE=$(gsettings get org.gnome.desktop.interface cursor-size)
#CURRENTSCALE=$(gsettings get com.canonical.Unity.Interface cursor-scale-factor)
	echo -e "\n\033[36mYour current cursor size is \033[0m$CURRENTSIZE \n\033[36mWould you like to change the size?(Y/n):\033[0m"
		read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
  then
    echo  
  else
    echo -e "\nYou chose not to continue..." 

## writes to or creates a ~/.Xresources file to reflect curent cursor size. Need to do this when choosing not to change size and ~/.Xresources doesn't exist
	echo -e "\n\033[36mYou have enabled the \033[0m$CURSOR \033[36mcursor theme with size unchanged of \033[0m$CURRENTSIZE\033[36m \nYou need to log out to complete the change:\033[0m";
		if grep "Xcursor.size:" ~/.Xresources > /dev/null; then
			#echo "Xcursor.size line exists"
			sed -i "/Xcursor.size/c\Xcursor.size:${CURRENTSIZE}" ~/.Xresources
		else
			#echo "Xcursor.size line does not exist"
			echo "Xcursor.size:${CURRENTSIZE}" >> ~/.Xresources
		fi
	read -n 1 -p "Press any key to exit this script..."
exit
fi

## Choose size
echo -e "\033[36mChoose your new cursor-size from 24, 32, 48, or 64  Default=24\033[36m"
	read SIZE

## Confirm choice
echo -e "\n\033[36mYou have selected a cursor size of \033[0m$SIZE\nContinue?(Y/n):"
	read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
	then
    		echo 
	else
		echo -e "\nYou chose not to continue..."
	  	echo -e "\n\033[36mYou have enabled the \033[0m$CURSOR \033[36mcursor theme with size unchanged of \033[0m$CURRENTSIZE\033[36m \nYou need to log out to complete the change:\033[0m";
		echo
	        read -n 1 -p "Press any key to exit this script..."
exit
fi

## Edits dconf to reflect chosen size

## match size to scale-factor
case "$SIZE" in

# 24=cursor-scale-factor 1
24)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 1
;;

# 32=cursor-scale-factor 1.35
32)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 1.35
;;

# 48=cursor-scale-factor 2
48)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 2
;;

# 64=cursor-scale-factor 2.65
64)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 2.65
;;

# input error
*)
echo -e  "\n\033[36m*** cursor size input error ....Try again ***\033[0m"
;;
esac


## Creates a ~/.Xresources file or edits existing to reflect chosen size
if grep "Xcursor.size:" ~/.Xresources > /dev/null; then
	#echo "Xcursor.size line exists"
	sed -i "/Xcursor.size/c\Xcursor.size:${SIZE}" ~/.Xresources
else
	#echo "Xcursor.size line does not exist"
	echo "Xcursor.size:${SIZE}" >> ~/.Xresources
fi


echo -e "\n\033[36mYou have enabled the \033[0m$CURSOR \033[36mcursor theme of size \033[0m$SIZE";

echo -e "\033[36m\nYou need to log out to complete cursor change.\033[0m";
read -n 1 -p "Press any key to exit this script..." 
```

---

