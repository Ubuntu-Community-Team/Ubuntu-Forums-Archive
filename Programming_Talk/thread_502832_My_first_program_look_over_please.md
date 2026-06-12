---
title: "My first program look over please"
date: 2007-07-17
forum: Programming Talk
---

### Post by Motoxrdude on 2007-07-17
I saw that there where a lot of poeple wondering how to get xgl and compiz fusion to work with an xgl session, so i thought it would be a good place to start learning how to program in bash.
Anyways, here is the file, please look over and make some suggestions! Thanks!
EDIT- Okay i attached an updated Xgl installer. I fixed some bugs and several issues people where having. Compiz-fusion has been confirmed to work, beryl is so far untested.

Note-Extract and run the Install.sh from the terminal with root permission.

---

### Post by Motoxrdude on 2007-07-17
Here is the installer script. Please please please look over! Feel free to make suggestions

```

#!/bin/bash



#Is zenity installed?
if [ ! -e "/usr/bin/zenity" ]; then
	gksudo apt-get install -y zenity
fi

#is it running off the Live CD?

if [ $USERNAME = "ubuntu" ]; then
    `zenity  --info --text="This upgrade scipt can only be ran after hard disk installation." --title="XGL Installer"`;
    exit 0
fi

# Are we running on Feisty?
if ( ! grep "Ubuntu 7.04" /etc/issue >/dev/null 2>&1); then
     `zenity  --info --text="This scipt can only be ran on Feisty based distros." --title="XGL Installer"`;
    exit 0
fi

#Direct rendering?
DR=`glxinfo | grep "direct rendering: No"`;

if [[ $DR = "direct rendering: No" ]]; then
zenity --error --title="Uh-o" --text="I have detected a problem with you video card drivers. There is no direct rendering. This could be a problem when running xgl"
`zenity --question --title="Proceed" --text="Continue anyways (only do this if you know that your video card drivers are correctly installed)?"`
echo $?
	if [[ $? = 1 ]]; then 
	exit 0
	fi
fi

#Are you sure you want to proceed?
zenity --question --title="Proceed" --text="Xgl is now going to be installed. Are you sure you want to continue?"
if [[ $? = 1 ]]; then exit 0
fi

#Defining variables
session="no"
beryl=`if [ -f /usr/bin/beryl ]; then echo "TRUE" ; else echo "FALSE"; fi`
compiz=`if [ -f /usr/bin/compiz ]; then echo "TRUE" ; else echo "FALSE"; fi`


#adding repos and updating
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
sudo cp sources.list /etc/apt/sources.list
gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg --export --armor 81836EBF | sudo apt-key add -
sudo apt-get update | zenity --progress --pulsate --auto-close --title="Adding sources"

#Install beryl and or compiz fusion
Install=`zenity --list --checklist --text="What do you want to install?" --column "Install" --column "Program" $compiz "Compiz Fusion" $beryl "Beryl "`

#Install Beryl?
if echo $Install | grep "Beryl" ; then 
echo "Installing beryl"
#Installing beryl
zenity --progress --pulsate --title="Installing Beryl" --auto-close
sudo apt-get install xserver-xgl beryl-ubuntu  
sudo cp preferences /etc/apt/preferences 
sudo apt-get install beryl-core=0.2.0~0beryl1
sudo apt-get update
session="yes"
fi




#Install Compiz Fusion?
if echo $Install | grep "Compiz Fusion" ; then 
echo "Installing Compiz"
Zenity --progress --title="Removing Compiz" --auto-close | sudo apt-get remove compiz-core desktop-effects
Zenity --progress --title="Installing Compiz Fusion" --auto-close | sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
	if [[ $session="no" ]]; then session="yes"
	fi
fi

#Creating an Xgl session
if [[ $session = "yes" ]]; then
echo "Installing xgl session"
sudo cp start.xgl /usr/local/bin/startxgl.sh
sudo chmod a+x /usr/local/bin/startxgl.sh
sudo mkdir -p /etc/X11/sessions
fi

#Want beryl or compiz to start on startup?
startup=`zenity --list --title="Startup" --text="Which program do you want to startup when you log into an xgl session?" --column="Program" "Compiz" "Beryl" "Neither"`

if echo $startup | grep Compiz ; then
	if -f /usr/local/bin/Beryl_start ; then rm /usr/local/bin/Beryl_start
	fi
cp Compiz_start /usr/local/bin/Compiz_start
zenity --info --text="Go to System>>Preferences>>Sessions. Click New. Name=Compiz Command=/usr/local/bin/Compiz_start"
zenity --info --text="Now, restart your computer. At the login screen, select the Xgl session and everything should work!"
mv /etc/apt/sources.list.backup /etc/apt/sources.list
fi

if echo $startup | grep Beryl ; then
	if -f /usr/local/bin/Compiz_start ; then rm /usr/local/bin/Compiz_start
	fi
cp Beryl_start /usr/local/bin/Beryl_start
zenity --info --text="Go to System>>Preferences>>Sessions. Click New. Name=Beryl Command=/usr/local/bin/Beryl_start"
zenity --info --text="Now, restart your computer. At the login screen, select the Xgl session and everything should work!"
mv /etc/apt/sources.list.backup /etc/apt/sources.list
fi

echo "End of script"
exit 0




```

---

### Post by Torajima on 2007-07-17
Wow... THAT is your first program? Most people just start with "Hello World"...

---

### Post by AlexenderReez on 2007-07-17
you can find this many kind of program (bash) in beryl wiki and change a bit to suite compiz fusion:)

---

### Post by Motoxrdude on 2007-07-17
> **Torajima said:**
> Wow... THAT is your first program? Most people just start with "Hello World"...
Nah, too easy.
> **reez0105 said:**
> you can find this many kind of program (bash) in beryl wiki and change a bit to suite compiz fusion:)

Most of it was just copy and paste but i have a lot of other features built into the script.

---

### Post by AlexenderReez on 2007-07-17
> **Motoxrdude said:**
> Nah, too easy.


Most of it was just copy and paste but i have a lot of other features built into the script.

yea..i noticed it....first glance ...but i don't try it as i already have compiz and beryl install from extra repo...it is difference from this...and i don't use xgl....

---

### Post by AlexenderReez on 2007-07-17
i will recommend this script to my friends that want to install compiz fusion and using xgl:)

---

### Post by Motoxrdude on 2007-07-17
> **reez0105 said:**
> i will recommend this script to my friends that want to install compiz fusion and using xgl:)

Well hang on there. I haven't actually tested this script yet, so idk if it works. I mean it shouldn't no anything irreversable, but just a heads up.

---

### Post by AlexenderReez on 2007-07-17
> **Motoxrdude said:**
> Well hang on there. I haven't actually tested this script yet, so idk if it works. I mean it shouldn't no anything irreversable, but just a heads up.

don't worry ..i will change a bit some coding especially to suite version like gutsy before recommend it ...especially repo there...
great works...

---

### Post by Note360 on 2007-07-18
WOW. er my first program was hello world in Java...

---

### Post by AlexThomson_NZ on 2007-07-18
10 print "Alex is ace"
20 goto 10

^ My first program :)

Good effort Motoxrdude.  I gotta re-install tonight, so I'll give your script a go then...

---

### Post by Motoxrdude on 2007-07-18
> **AlexThomson_NZ said:**
> 10 print "Alex is ace"
20 goto 10

^ My first program :)

Good effort Motoxrdude.  I gotta re-install tonight, so I'll give your script a go then...

Awesome, thanks. Just do a backup of your sources.list first.
> sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup~

---

### Post by Motoxrdude on 2007-07-21
so has anyone tested this yet?

---

### Post by Motoxrdude on 2007-07-31
I updated the script. I fixed a lot of bugs and issues people where having with it. Check the original post for the tar.gz.

---

