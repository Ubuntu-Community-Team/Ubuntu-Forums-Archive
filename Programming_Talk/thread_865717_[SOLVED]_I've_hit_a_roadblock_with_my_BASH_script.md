---
title: "[SOLVED] I've hit a roadblock with my BASH script"
date: 2008-07-20
forum: Programming Talk
---

### Post by brennydoogles on 2008-07-20
I am trying to write a bash script that will allow me to automatically install all of my favorite apps (including the addition of all of my custom software sources) whenever I re-install, as well as sharing these apps with all of my friends that I have been converting to Ubuntu. For this reason, I need my script to have a menu, so that those who don't want to install certain TYPES of apps don't have to. Here is what I have so far, but I am getting errors that have no real meaning to me. Have I made an obvious mistake??

```
#!/bin/bash
#Script to add appropriate sources for a new ubuntu installation, and install cool packages.

mainMenu () {
OPTIONS="'Add Software Sources (must be done once)' 'Install Games' 'Install Multimedia' 'Install Useful Applications' 'QUIT'"
           select opt in $OPTIONS; do
               if [ "$opt" = "Add Software Sources (must be done once)" ]; then                
                addSources()
               elif [ "$opt" = "Install Games" ]; then
                installGames()
	       elif [ "$opt" = "Install Multimedia" ]; then
                 installMultimedia()
               elif [ "$opt" = "Install Useful Applications" ]; then
		 installApps()
	       elif [ "$opt" = "QUIT" ]; then
		 exit 0
               else
                clear
                echo "That wasn't one of the options."
               fi
               break
           done


}

addSources () {
echo "Adding software sources";
mainMenu()
}

installGames () {
echo "Installing Games";
mainMenu()
}
installMultimedia () {
echo "Installing Multimedia";
mainMenu()
}
installApps () {
echo "Installing Apps"
mainMenu()
}


mainMenu ()
```
Any help would be greatly appreciated!!!

P.S.-- I know the script does not actually install anything right now, I was just writing out the logic behind it so that I can test it without running unnecessary commands.

---

### Post by nick_h on 2008-07-21
Try something like:
```
#!/bin/bash
#Script to add appropriate sources for a new ubuntu installation, and install cool packages.


mainMenu() {
OPTIONS="Sources Games Multimedia Applications QUIT"
until false; do
	select opt in $OPTIONS; do
		if [ "$opt" = "Sources" ]; then                
			addSources
		elif [ "$opt" = "Games" ]; then
			installGames
		elif [ "$opt" = "Multimedia" ]; then
			installMultimedia
		elif [ "$opt" = "Applications" ]; then
			installApps
		elif [ "$opt" = "QUIT" ]; then
			exit 0
		else
			clear
			echo "That wasn't one of the options."
		fi
	done
done
}

installGames() {
echo "Installing Games"
}
installMultimedia() {
echo "Installing Multimedia"
}
installApps() {
echo "Installing Apps"
}
addSources() {
echo "Adding software sources"
}

mainMenu

```

There is a section on menu building [here](http://www.linuxcommand.org/wss0120.php#building_a_menu).

---

### Post by brennydoogles on 2008-07-21
Thanks for your reply!! Without knowing it, you actually pointed out the error in my script... the trailing () after each function call. I guess I didn't notice since I am used to Java and PHP. After removing the ()'s after each function call, the script runs beautifully. Thanks!!

Here is the completed script, where anyone can replace the games apps and sources functions with their own aptitude or apt-get commands to create a run-once installer for all of their favorite apps!!

```
#!/bin/bash
#Script to add appropriate sources for a new ubuntu installation, and install cool packages.

mainMenu () {
echo "What would you like to install? (Sources must be installed once, and before anything else)"
OPTIONS="Sources Games Multimedia Applications QUIT"
           select opt in $OPTIONS; do
               if [ "$opt" = "Sources" ]; then                
                addSources
               elif [ "$opt" = "Games" ]; then
                installGames
	       elif [ "$opt" = "Multimedia" ]; then
                 installMultimedia
               elif [ "$opt" = "Applications" ]; then
		 installApps
	       elif [ "$opt" = "QUIT" ]; then
		 exit 0
               else
                clear
                echo "That wasn't one of the options."
               fi
               break
           done


}

addSources () {
echo "Adding software sources";
mainMenu
}

installGames () {
echo "Installing Games";
mainMenu
}
installMultimedia () {
echo "Installing Multimedia";
mainMenu
}
installApps () {
echo "Installing Apps"
mainMenu
}


mainMenu 
```

---

