---
title: "Annoying Syntax error in bash script"
date: 2007-09-08
forum: Programming Talk
---

### Post by isaacj87 on 2007-09-08
I'm writing a simple bash script to install themes into Pidgin. I keep running into this error..I'm using Gedit to write the script. can someone help me out?

Here are the troublesome lines in the sript:
```

elif [ $answer = r ] ; then
	{
		rm ~/pidgin_bg.jpg
			echo
			echo -e "\033[1mPidgin has been reverted back to original theme\033[0m"
			fi
	}

```

Here's the output:
```

Pidgin Customization Script

Reminder: Please install Pidgin first. You can find the .deb files within this pack.

Now the fun stuff, this script will take you step by step asking you what icon theme to use and what background image to set.

Do you was run the customization process or revert back to the original Pidgin theme? [(c]ontinue/(r)evert]
r
/home/isaac/Desktop/CF_Installer-Updater_v.3.sh: line 105: syntax error near unexpected token `fi'
/home/isaac/Desktop/CF_Installer-Updater_v.3.sh: line 105: `                   fi'

```

thanks guys

---

### Post by gnusci on 2007-09-08
```
elif [ $answer = r ] ; then
	{
		rm ~/pidgin_bg.jpg [COLOR="Red"]<--why you just don't use full path instead "~/"?[/COLOR]
			echo
			echo -e "\033[1mPidgin has been reverted back to original theme\033[0m"
			fi [COLOR="Red"]<-------- what are you closing here?[/COLOR]
	}
```

---

### Post by isaacj87 on 2007-09-08
I don't put the full path because I plan on letting others use it, they can't if I hardcode the path.

I finish there because this is only one section of a bigger section...that's why I have "{" and "}"

---

### Post by walkerk on 2007-09-08
> **isaacj87 said:**
> I don't put the full path because I plan on letting others use it, they can't if I hardcode the path.

I finish there because this is only one section of a bigger section...that's why I have "{" and "}"

fi is the end of an if conditional..

example:
```
if [ $what = "something" ]
then
 echo "ok"
**fi**
```

---

### Post by gnusci on 2007-09-08
so you can write the full path using:

```

/home/$USER/pidgin_bg.jpg

```

---

### Post by Cappy on 2007-09-08
I think he means the code should look like this::
```

elif [ $answer = r ] ; then
	{
		rm ~/pidgin_bg.jpg
		echo
		echo -e "\033[1mPidgin has been reverted back to original theme\033[0m"
	}
fi

```

---

### Post by walkerk on 2007-09-08
> **gnusci said:**
> so you can write the full path using:

```

/home/$USER/pidgin_bg.jpg

```

this will work but  [ ~/pidgin_bg.jpg ] will work as well..

---

### Post by isaacj87 on 2007-09-08
> **walkerk said:**
> this will work but  [ ~/pidgin_bg.jpg ] will work as well..

I tried this but it didn't work...

do I need the "[" "]"

---

### Post by isaacj87 on 2007-09-08
> **gnusci said:**
> so you can write the full path using:

```

/home/$USER/pidgin_bg.jpg

```

sorry! I was looking at the wrong thing..I understand what you mean now. :)

---

### Post by isaacj87 on 2007-09-08
I figured I'd post the entire thing...tell me if I'm doing something wrong.
I also want to have user input as well. What I mean is if someone doesn't want an image for the background then they can skip to a part in the script (which I haven't created yet obviously) where it asks for a RGB code. 

I've included a .gtkrc file that will contain all the pixmap paths and RGB code settings:

```

pixmap_path "/home/isaac/Pictures/Extras"
style "my-blist" {
bg_pixmap[NORMAL] = "pidgin_bg.jpg"
[B]text[NORMAL] = "#000000"
bg[NORMAL] = "#F5D8BC"
base[NORMAL] = "#F5D8BC"[/B]
GtkTreeView::odd_row_color = ""
GtkTreeView::even_row_color = ""
}
widget "*pidgin_blist_treeview" style "my-blist"

```

What I want the script to do (if the user so wants to your colors instead of an image) is to ask the user for a RGB code...the user types it in and then the script regenerates/copies over the existing the .gtkrc file. Is this possible?

Here's the script so far:
```

#!/bin/bash

clear
echo -e "\033[7mPidgin Customization Script\033[0m"
echo
echo -e "\033[1mReminder: Please install Pidgin first. You can find the .deb files within this pack.\033[0m"
echo

echo -e "\033[1mNow the fun stuff, this script will take you step by step asking you what icon theme to use and what background image to set.\033[0m"
echo
echo -e "\033[1mDo you was run the customization process or revert back to the original Pidgin theme? [(c]ontinue/(r)evert]\033[0m" ; read answer
if [ $answer = c ] ; then
echo	
	{		
	echo -e "\033[1mWhat icon theme would you like to use? Please choose from the following:\033[0m" 
				echo -e "\033[1m(1)Pidgin_OsX\033[0m" 
				echo -e "\033[1m(2)Glossy\033[0m"
				echo -e "\033[1m(3)Human\033[0m"
				echo -e "\033[1m(4)Pidgin_Vista\033[0m"
				echo -e "\033[1m(5)Pidgin_Pango\033[0m"
				echo -e "\033[1m(6)Pidgin_neu\033[0m"
				echo -e "\033[1m(n)Use the Original icon theme\033[0m" ; read answer

		if [ $answer = 1 ] ; then
			sudo cp IconThemes/Pidgin_OsX/pidgin /usr/share/pixmaps/
				echo
				echo -e "\033[1mPidgin_OsX theme has been installed\033[0m"
		elif [ $answer = 2 ] ; then
			sudo cp IconThemes/Glossy/pidgin /usr/share/pixmaps/
				echo
				echo -e "\033[1mGlossy theme has been installed\033[0m"
		elif [ $answer = 3 ] ; then
			sudo cp IconThemes/Human/pidgin /usr/share/pixmaps/
				echo
				echo -e "\033[1mHuman theme has been installed\033[0m"
		elif [ $answer = 4 ] ; then
			sudo cp IconThemes/Pidgin_Vista/pidgin /usr/share/pixmaps/
				echo
				echo -e "\033[1mPidgin_Vista theme has been installed\033[0m"
		elif [ $answer = 5 ] ; then
			sudo cp IconThemes/Pidgin_Pango/pidgin /usr/share/pixmaps/
				echo
				echo -e "\033[1mPidgin_Pango theme has been installed\033[0m"
		elif [ $answer = 6 ] ; then
			sudo cp IconThemes/Pidgin_neu/pidgin /usr/share/pixmaps/
				echo
				echo -e "\033[1mPidgin_neu theme has been installed\033[0m"
		elif [ $answer = n ] ; then
				echo	
				echo -e "\033[1mSkipping...\033[0m"
			else
				echo -e "\033[1mInvalid answer\033[0m"
				exit 
		fi

			####This part is for the background images			
					echo
						echo -e "\033[1mWhat background image would you like to use? Please choose from the following:\033[0m" 
						echo -e "\033[1m(1)Pidgin_OsX\033[0m" 
						echo -e "\033[1m(2)Glossy\033[0m"
						echo -e "\033[1m(3)Human\033[0m"
						echo -e "\033[1m(4)Pidgin_Vista\033[0m"
						echo -e "\033[1m(5)Pidgin_Pango\033[0m"
						echo -e "\033[1m(6)Pidgin_neu\033[0m"
						echo -e "\033[1m(n)Use the Original icon theme\033[0m" ; read answer

		
				if [ $answer = 1 ] ; then
					sudo cp Backgrounds/Pidgin_OsX/pidgin /usr/share/pixmaps/
						echo
						echo -e "\033[1mPidgin_OsX theme has been installed\033[0m"
				elif [ $answer = 2 ] ; then
					sudo cp Backgrounds/Glossy/pidgin /usr/share/pixmaps/
						echo
						echo -e "\033[1mGlossy theme has been installed\033[0m"
				elif [ $answer = 3 ] ; then
					sudo cp Backgrounds/Human/pidgin /usr/share/pixmaps/
						echo
						echo -e "\033[1mHuman theme has been installed\033[0m"
				elif [ $answer = 4 ] ; then
					sudo cp Backgrounds/Pidgin_Vista/pidgin /usr/share/pixmaps/
						echo
						echo -e "\033[1mPidgin_Vista theme has been installed\033[0m"
				elif [ $answer = 5 ] ; then
					sudo cp Backgrounds/Pidgin_Pango/pidgin /usr/share/pixmaps/
						echo
						echo -e "\033[1mPidgin_Pango theme has been installed\033[0m"
				elif [ $answer = 6 ] ; then
					sudo cp Backgrounds/Pidgin_neu/pidgin /usr/share/pixmaps/
						echo
						echo -e "\033[1mPidgin_neu theme has been installed\033[0m"
				elif [ $answer = n ] ; then
						echo	
						echo -e "\033[1mSkipping...\033[0m"
				else
						echo -e "\033[1mInvalid answer\033[0m"
						exit 	
			fi	
	}
elif [ $answer = r ] ; then
	{
		rm /home/$USER/pidgin_bg.jpg
			echo
			echo -e "\033[1mPidgin has been reverted back to original theme\033[0m"			
	}

echo -e "\033[1mLicensed under a Creative Commons Attribution-Noncommercial 3.0 License. To view a copy of this license, visit http://creativecommons.org/licenses/by-nc/3.0/\033[0m"
echo -e "\033[1mCreated by isaacj87. Thanks for using the Pidgin Customization Tool!\033[0m"
fi

```

Please correct me if necessary...I'm still learning!
**and BTW I know there's alot in there that are doubles, I'm just copying and pasting and changing as I go.**

---

### Post by isaacj87 on 2007-09-08
AND...sorry guys...I have lots of questions!!

How would one do a GOTO in bash??

---

### Post by Lux Perpetua on 2007-09-08
Why do you think you need it? Use of GOTO can almost always (and in those cases should) be avoided.

---

### Post by isaacj87 on 2007-09-08
I'm a noobie programmer. This is my first script (well large script). I'm having a hell of a time trying to do loops...have user inputs....and generating output files...:(

---

