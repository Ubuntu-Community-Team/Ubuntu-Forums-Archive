---
title: "Help a newbie clean up a script?"
date: 2008-08-31
forum: Programming Talk
---

### Post by anotherdisciple on 2008-08-31
I am in the middle of writing a script, but I wanted to find out if I'm doing anything wrong, or if I'm doing things the hard way. I'm very very new to this stuff!

The script works like Automatix, but it only uses trustworthy sources and shouldn't break anything. It only uses the standard ubuntu sources and medibuntu. Nothing else... I'm only part way through it, so you will see things that are missing, but I just want to know what you think about it so far.

I attached the file.

Thanks for the help!

PS- It uses Zenity for the GUI.

---

### Post by anotherdisciple on 2008-09-01
WOW! Quite a few people have seen this post, but no one has replied. I have started to wonder if people feel weird about opening a stranger's BASH script... so here it is... I've added some stuff to it.

```
#!/bin/bash
if [[ $UID -ne 0 ]]; then
zenity --title "Nick's Easy Installer" --warning --text 'This program needs to be run as Root!

Please place the program in your home folder,
then hit Alt + F2 and enter this:
 
"gksudo  ./nubuntu" (Without Quotes)'
exit 1
else
zenity --title "Nick's Easy Installer" --info --text "Good, you ran this program as Root!"
fi

# This asks the user which version of Ubuntu they are using. This is important when adding software sources.
while [[ $VERSION = "" ]]; do
VERSION=$(zenity --title "Nick's Easy Installer" --text "What version of Ubuntu are you using?" --list --radiolist --column "" --column "Version" --column "Details" False gutsy '7.10  "Gutsy Gibbon"' False hardy '8.04  "Hardy Heron"' False intrepid '8.10  "Intrepid Ibex"' --height=207 --width=200)
done

# This sets the variable for $MEDIBUNTU
if [[ $VERSION = gutsy ]];then
MEDIBUNTU=$(sudo "wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list" -m "Nick's Easy Installer")
elif [[ $VERSION = hardy ]];then
MEDIBUNTU=$(sudo "wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list" -m "Nick's Easy Installer")
elif [[ $VERSION = intrepid ]];then
MEDIBUNTU=$(sudo "wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list" -m "Nick's Easy Installer")
fi

# This gives a list of software and other options for the user to choose from. This is where all the information is collected for what the rest of the script needs to do.
CHOICES=$(zenity --list --column="Check" --column="Feature or Program" --column="Description" --title "Nick's Easy Installer" --text "Select the options you would like to install." --checklist false "Adobe Acrobat Reader" "Installs Acrobat Reader and the Acrobat Firefox Plugin" false "Audacity" "Music Editor" false "Avant Window Navigator" "Dock bar like on Mac OSX" false "Banshee" "Multimedia player that works well with iPods (Removes Rhythmbox)" false "Better Fonts" "Change Settings for Clearer Fonts" false "Compiz Effects" "Desktop Effects Manager" false "Compiz-Fusion Icon" "Tray Icon To Launch And Manage Compiz-Fusion" false "DVD Codecs" "Enables DVD Playback" false "Ekiga Uninstall" "Choose this option if you don't plan to use Ekiga for a VoIP" false "Emerald Theme Manager" "Window Decorator" false "EnvyNG" "Installer for the latest ATI or NVidia Drivers" false "GHex" "Hexadecimal Editor" false "GParted" "Partition Editor" false "StumbleUpon" "Firefox Add-On for Sharing Interesting Websites" false "Ubuntu-Restricted-Extras          " "Media Codecs, MS Fonts, Java, and More" false "VLC" "All-In-One Media Player" false "VLC Firefox Plugin" "Allows VLC to handle media played in Firefox (Removes Totem Plugin)" false "Windows Media Codecs" "Allows you to play .avi .wma  and .wmv files" false "Wine" "Abstraction Layer For Running Windows Programs " --width=700 --height=800)

# This is basically a way to make all the software get installed in just a few commands. All of the variables will be placed in one "sudo aptitude install..." If the variables are not set, they will not be installed. The space left afer each quoted word is intentional. You will see why it was done this way in the install command.
if [[ $CHOICES =~ "Adobe Acrobat Reader" ]]; then
ACROREAD="acroread acroread-escript acroread-plugins mozilla-acroread "
fi

if [[ $CHOICES =~ "Audacity" ]]; then
AUDACITY="audacity "
fi

if [[ $CHOICES =~ "Avant Window Navigator" ]]; then
AWN="avant-window-navigator "
fi

if [[ $CHOICES =~ "Banshee" ]]; then
BANSHEE="banshee-1 "
RHYTHMBOXREMOVE="rhythmbox "

fi

if [[ $CHOICES =~ "Better Fonts" ]]; then
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
fi

if [[ $CHOICES =~ "Compiz Effects" ]]; then
COMPIZ="compizconf-settings-manager "
fi

if [[ $CHOICES =~ "Compiz-Fusion Icon" ]]; then
FUSIONICON="fusion-icon "
fi

if [[ $CHOICES =~ "DVD Codecs" ]]; then
DVD="libdvdcss2 "
fi

if [[ $CHOICES =~ "Emerald Theme Manager" ]]; then
EMERALD="emerald "
fi

if [[ $CHOICES =~ "EnvyNG" ]]; then
ENVYNG="envyng-gtk "
fi

if [[ $CHOICES =~ "Ekiga Uninstall" ]]; then
EKIGAREMOVE="ekiga "
fi

if [[ $CHOICES =~ "GHex" ]]; then
GHEX="ghex "
fi

if [[ $CHOICES =~ "GParted" ]]; then
GPARTED="gparted "
fi

if [[ $CHOICES =~ "StumbleUpon" ]]; then
STUMBLE="mozilla-stumbleupon "
fi

if [[ $CHOICES =~ "Ubuntu-Restricted-Extras" ]]; then
URE="ubuntu-restricted-extras "
fi

if [[ $CHOICES =~ "VLC" ]]; then
VLC="vlc"
fi

if [[ $CHOICES =~ "VLC Firefox Plugin" ]]; then
VLCFFP="mozilla-plugin-vlc "
TOTEMREMOVE="totem totem-common totem-gstreamer totem-plugins totem-mozilla "
TOTEM="totem "
fi

if [[ $CHOICES =~ "Windows Media Codecs" ]]; then
W32CODECS="w32codecs "
fi

if [[ $CHOICES =~ "Wine" ]]; then
WINE="wine"
fi

if [[ $CHOICES =  "" ]]; then
zenity --title "Nick's Easy Installer" --info --text "You didn't choose anything!?!?"
exit 1
fi

#if [[ $CHOICES =~ ??? ]]; then
#???="???"
#fi

# This says that if one of the programs to be installed requires medibuntu, add medibuntu to the software sources.
if [[ $CHOICES =~ "Adobe Acrobat Reader"|"DVD Codecs"|"Windows Media Codecs" ]];
then echo $MEDIBUNTU && sudo apt-get update && echo "Yes" | sudo aptitude install medibuntu-keyring && sudo aptitude update;
else echo "false";
fi

#This is the command that removes all the programs the user selected
sudo aptitude -y remove $TOTEMREMOVE$EKIGAREMOVE$RHYTHMBOXREMOVE
sudo aptitude -y purge $TOTEM$EKIGAREMOVE$RHYTHMBOXREMOVE

sudo aptitude update
sudo aptitude -y safe-upgrade | zenity --title "Nick's Easy Installer" --progress --auto-close  --text "Updating and Upgrading!" --width=300

#This is the command that installs all the programs the user selected
echo "Yes" | sudo aptitude -y install $ACROREAD$AUDACITY$AWN$BANSHEE$COMPIZ$FUSIONICON$DVD$EMERALD$ENVYNG$GHEX$GPARTED$STUMBLE$URE$VLC$VLCFFP$W32CODECS$WINE | zenity --title "Nick's Easy Installer" --progress --auto-close --text "Installing your selections!" --width=300

exit 1

```

---

### Post by LaRoza on 2008-09-01
Your if statements are rather complex. Can't you use cases [http://www.grymoire.com/Unix/Sh.html#uh-82](http://www.grymoire.com/Unix/Sh.html#uh-82) (or at least, else-if logic)

---

### Post by slavik on 2008-09-01
except for using sudo, it's fine as a beginner's script ... although I also don't like the echo "Yes" | aptitude either ... apt has a -y option.

I would also suggest printing the command that you will run and ask the user if he wants it to be run.

you can also add getopt for forcing your script to just run commands without promting the user.

btw, just noticed, why do you echo "yes" but still use -y for aptitude?

---

### Post by anotherdisciple on 2008-09-01
Maybe you could explain if I am understanding wrong, but if I use else if it would only perform one of the actions. If the user chooses multiple items... it needs to do multiple things... that is why I chose to do it that way. I'll look into how I can use case...

Let me know if you have any ideas on how to make it simpler. I am new like I said... so I'm confident that I'm making things too complicated.

---

### Post by slavik on 2008-09-01
> **anotherdisciple said:**
> Maybe you could explain if I am understanding wrong, but if I use else if it would only perform one of the actions. If the user chooses multiple items... it needs to do multiple things... that is why I chose to do it that way. I'll look into how I can use case...

Let me know if you have any ideas on how to make it simpler. I am new like I said... so I'm confident that I'm making things too complicated.
nope, you are misunderstanding.

think of if then elif then as:
if {} else { if {} }

meaning that once a single if clause is matched, that is done and that's it.

cascading if-elseif are less efficient than a switch when there are 3 or more if statements (when checking for a single variable).

but yeah, your if then elif can be switched to switch statements, make sure to use brake (or esac) to show the end of a case statement (otherwise the actions will cascade).

---

### Post by anotherdisciple on 2008-09-01
> **slavik said:**
> except for using sudo, it's fine as a beginner's script ... although I also don't like the echo "Yes" | aptitude either ... apt has a -y option.

I would also suggest printing the command that you will run and ask the user if he wants it to be run.

you can also add getopt for forcing your script to just run commands without promting the user.

btw, just noticed, why do you echo "yes" but still use -y for aptitude?

well... some of those programs are from medibuntu. For some reason it asks you "Yes" or "No" about installing those applications. Installing things from the default Ubuntu repos will ask "y" or "n".... so aptitude -y will correctly answer "y" or "n" questions... but it won't work when installing from medibuntu... I've even tested it.

oh... and why is using sudo bad? Is it because it is already run as Root and doesn't need it?

---

### Post by slavik on 2008-09-01
yes. and I think there was another reason (don't remember what it was though).

edit: btw, kudos to you for checking if the script is actually run as root :)

---

### Post by eightmillion on 2008-09-01
You don't have to ask the user what version of Ubuntu they are running. You can find that out without user interaction like so:
```

DISTRIB=`grep CODENAME /etc/lsb-release`
VERSION=${distrib/DISTRIB_CODENAME=/}

```
This will set your VERSION variable for you.

---

### Post by anotherdisciple on 2008-09-01
> **eightmillion said:**
> You don't have to ask the user what version of Ubuntu they are running. You can find that out without user interaction like so:
```

DISTRIB=`grep CODENAME /etc/lsb-release`
VERSION=${distrib/DISTRIB_CODENAME=/}

```
This will set your VERSION variable for you.

hmmm... when I 
```
echo $VERSION
```

it is blank... is there something wrong with the second line... I realize that there needs to be a way to filter out "DISTRIB_CODENAME="

---

### Post by eightmillion on 2008-09-01
Yeah, that second line should be:
> VERSION=${DISTRIB/DISTRIB_CODENAME=/}
I forgot to capitalize that variable.

---

### Post by anotherdisciple on 2008-09-01
> **slavik said:**
> nope, you are misunderstanding.

think of if then elif then as:
if {} else { if {} }

meaning that once a single if clause is matched, that is done and that's it.

cascading if-elseif are less efficient than a switch when there are 3 or more if statements (when checking for a single variable).

but yeah, your if then elif can be switched to switch statements, make sure to use brake (or esac) to show the end of a case statement (otherwise the actions will cascade).

Holy Smokes! Maybe I'm just tired.. but I think I need to read that a few more times to understand it... can you give me a short example of how I could edit my script to do this?

---

### Post by anotherdisciple on 2008-09-01
> **eightmillion said:**
> Yeah, that second line should be:

I forgot to capitalize that variable.

Okay... now that I have filtered out what version they are using... How can I make this section into one line?....
```
if [[ $VERSION = gutsy ]];then
MEDIBUNTU=$(sudo "wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list" -m "Nick's Easy Installer")
elif [[ $VERSION = hardy ]];then
MEDIBUNTU=$(sudo "wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list" -m "Nick's Easy Installer")
elif [[ $VERSION = intrepid ]];then
MEDIBUNTU=$(sudo "wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list" -m "Nick's Easy Installer")
fi
```

---

### Post by eightmillion on 2008-09-01
I don't get what you're trying to do there. Why are there quotes around the wget command? Are you just trying to add the medibuntu repos?

---

### Post by eightmillion on 2008-09-01
You could change that whole section to:
```

: $(`wget http://www.medibuntu.org/sources.list.d/${VERSION}.list -O /etc/apt/sources.list.d/medibuntu.list`)

```
or even 
```

wget http://www.medibuntu.org/sources.list.d/${VERSION}.list -O /etc/apt/sources.list.d/medibuntu.list

```
You don't need that sudo either since the first thing you check is whether the user is root.

---

### Post by ghostdog74 on 2008-09-01
> **anotherdisciple said:**
> 

```

...
# This sets the variable for $MEDIBUNTU
if [[ $VERSION = gutsy ]];then
MEDIBUNTU=$(sudo "wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list" -m "Nick's Easy Installer")
elif [[ $VERSION = hardy ]];then
MEDIBUNTU=$(sudo "wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list" -m "Nick's Easy Installer")
elif [[ $VERSION = intrepid ]];then
MEDIBUNTU=$(sudo "wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list" -m "Nick's Easy Installer")
fi

```


your if/else checking for the same variable is excessive. Here's a snippet to reduce them. Bash doesn't really support associative arrays, but you can always make use of them in awk. Associative arrays are "shorthand" way of constructing if/else statements
```

VERSION=gutsy
v=$(awk -v version="$VERSION" 'BEGIN{
 VERSION["gutsy"] = "gutsy.list"
 VERSION["hardy"] = "hardy.list"
 VERSION["intrepid"] = "intrepid.list"
 print VERSION[version]
}')

MEDIBUNTO=$(sudo "wget http://www.medibuntu.org/sources.list.d/"${v} "-O /etc/apt/sources.list.d/medibuntu.list" -m "Nick's Easy Installer")


```
you can do the same for $CHOICE.

---

### Post by eightmillion on 2008-09-01
Actually you could do something like this in the choice section:
```

for selection in ${CHOICE[*]}
do
case $selection in
 selection1) some command
 ;;
 selection2) something else
 ;;
 selection3) blah blah blah
 ;;
esac
done

```

---

### Post by anotherdisciple on 2008-09-01
Okay... this seems to do exactly what I want it to do:

```
MEDIBUNTU=("wget http://www.medibuntu.org/sources.list.d/"$VERSION".list -O /etc/apt/sources.list.d/medibuntu.list")

```

It sets the variable "MEDIBUNTU" based on what version of Ubuntu the user is running. This was just trial and error that helped me figure out what works. The problem I don't understand is why sometimes I have to put a "$" after VARIABLE= and sometimes I don't... can anyone explain this to me?

---

### Post by anotherdisciple on 2008-09-02
> **eightmillion said:**
> I don't get what you're trying to do there. Why are there quotes around the wget command? Are you just trying to add the medibuntu repos?

That was a mess up on my part. I was using gksudo for almost every command, then I decided to just have the user run the script as Root. Anyways, Gksudo wouldn't work right unless if I used quotes... not sure why. That is why it has -m "Nick's Easy Installer" that changes the message of gksudo. I forgot to delete that also!

---

### Post by eightmillion on 2008-09-02
In that situation, you are setting an array called MEDIBUNTU. If you put a $ after MEDIBUNTU= then you'll be setting MEDIBUNTU to the stdout of the command inside (). This part of your script seems extremely failure prone. Why don't you just do what you need to do like this, in this part of your script:
```
# This says that if one of the programs to be installed requires medibuntu, add medibuntu to the software sources.
if [[ $CHOICES =~ "Adobe Acrobat Reader"|"DVD Codecs"|"Windows Media Codecs" ]];then 
wget http://www.medibuntu.org/sources.list.d/${VERSION}.list -O /etc/apt/sources.list.d/medibuntu.list && sudo aptitude update && sudo aptitude -y install medibuntu-keyring && sudo aptitude update;
else echo "false";
fi
```

---

### Post by anotherdisciple on 2008-09-02
> **eightmillion said:**
> In that situation, you are setting an array called MEDIBUNTU. If you put a $ after MEDIBUNTU= then you'll be setting MEDIBUNTU to the stdout of the command inside (). This part of your script seems extremely failure prone. Why don't you just do what you need to do like this, in this part of your script:
```
# This says that if one of the programs to be installed requires medibuntu, add medibuntu to the software sources.
if [[ $CHOICES =~ "Adobe Acrobat Reader"|"DVD Codecs"|"Windows Media Codecs" ]];then 
wget http://www.medibuntu.org/sources.list.d/${VERSION}.list -O /etc/apt/sources.list.d/medibuntu.list && sudo aptitude update && sudo aptitude -y install medibuntu-keyring && sudo aptitude update;
else echo "false";
fi
```

Oh man... that's a really simple idea that I never even considered! I technically don't even need the 'else echo "false"' I think that is left over from me testing out how certain commands work.... 

THANKS!!!!

I still need help understanding how to condense my massive set of if statements... and please try to explain what your code is doing... I'm still really new at this... so a lot of this is starting to get over my head :lolflag:

---

### Post by anotherdisciple on 2008-09-02
> **eightmillion said:**
> In that situation, you are setting an array called MEDIBUNTU. If you put a $ after MEDIBUNTU= then you'll be setting MEDIBUNTU to the stdout of the command inside (). This part of your script seems extremely failure prone. Why don't you just do what you need to do like this, in this part of your script:
```
# This says that if one of the programs to be installed requires medibuntu, add medibuntu to the software sources.
if [[ $CHOICES =~ "Adobe Acrobat Reader"|"DVD Codecs"|"Windows Media Codecs" ]];then 
wget http://www.medibuntu.org/sources.list.d/${VERSION}.list -O /etc/apt/sources.list.d/medibuntu.list && sudo aptitude update && sudo aptitude -y install medibuntu-keyring && sudo aptitude update;
else echo "false";
fi
```


Another question... can the /${VERSION}.list just be /$VERSION.list or will this cause a problem?

---

### Post by eightmillion on 2008-09-02
Your suggested way would most likely work, but it's safer with the brackets. The brackets tell bash to substitute specifically the variable $VERSION and not something like $VERSION.list (even though I don't think $VERSION.list is a valid variable anyway). Also, you don't need to use sudo in those aptitude commands. The script is already running as root.

---

### Post by anotherdisciple on 2008-09-02
Shew! Here is the update... still trying to understand the suggested ways to condense my many if statements for $CHOICES...

```
#!/bin/bash
if [[ $UID -ne 0 ]]; then
zenity --title "Nick's Easy Installer" --warning --text 'This program needs to be run as Root!

Please place the program in your home folder,
then hit Alt + F2 and enter this:
 
"gksudo  ./nubuntu" (Without Quotes)'
exit 1
else
zenity --title "Nick's Easy Installer" --info --text "Good, you ran this program as Root!"
fi

# This finds out which version of Ubuntu the user is running. This is important when adding software sources.
DISTRIB=`grep CODENAME /etc/lsb-release`
VERSION=${DISTRIB/DISTRIB_CODENAME=/} 

# This gives a list of software and other options for the user to choose from. This is where all the information is collected for what the rest of the script needs to do.
CHOICES=$(zenity --list --column="Check" --column="Feature or Program" --column="Description" --title "Nick's Easy Installer" --text "Select the options you would like to install." --checklist false "Adobe Acrobat Reader" "Installs Acrobat Reader and the Acrobat Firefox Plugin" false "Audacity" "Music Editor" false "Avant Window Navigator" "Dock bar like on Mac OSX" false "Banshee" "Multimedia player that works well with iPods (Removes Rhythmbox)" false "Better Fonts" "Change Settings for Clearer Fonts" false "Compiz Effects" "Desktop Effects Manager" false "Compiz-Fusion Icon" "Tray Icon To Launch And Manage Compiz-Fusion" false "DVD Codecs" "Enables DVD Playback" false "Ekiga Uninstall" "Choose this option if you don't plan to use Ekiga for a VoIP" false "Emerald Theme Manager" "Window Decorator" false "EnvyNG" "Installer for the latest ATI or NVidia Drivers" false "GHex" "Hexadecimal Editor" false "GParted" "Partition Editor" false "StumbleUpon" "Firefox Add-On for Sharing Interesting Websites" false "Ubuntu-Restricted-Extras          " "Media Codecs, MS Fonts, Java, and More" false "VLC" "All-In-One Media Player" false "VLC Firefox Plugin" "Allows VLC to handle media played in Firefox (Removes Totem Plugin)" false "Windows Media Codecs" "Allows you to play .avi .wma  and .wmv files" false "Wine" "Abstraction Layer For Running Windows Programs " --width=700 --height=800)

# This is basically a way to make all the software get installed in just a few commands. All of the variables will be placed in one "aptitude install..." If the variables are not set, they will not be installed. The space left afer each quoted word is intentional. You will see why it was done this way in the install command.
if [[ $CHOICES =~ "Adobe Acrobat Reader" ]]; then
ACROREAD="acroread acroread-escript acroread-plugins mozilla-acroread "
fi

if [[ $CHOICES =~ "Audacity" ]]; then
AUDACITY="audacity "
fi

if [[ $CHOICES =~ "Avant Window Navigator" ]]; then
AWN="avant-window-navigator "
fi

if [[ $CHOICES =~ "Banshee" ]]; then
BANSHEE="banshee-1 "
RHYTHMBOXREMOVE="rhythmbox "

fi

if [[ $CHOICES =~ "Better Fonts" ]]; then
ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
fi

if [[ $CHOICES =~ "Compiz Effects" ]]; then
COMPIZ="compizconf-settings-manager "
fi

if [[ $CHOICES =~ "Compiz-Fusion Icon" ]]; then
FUSIONICON="fusion-icon "
fi

if [[ $CHOICES =~ "DVD Codecs" ]]; then
DVD="libdvdcss2 "
fi

if [[ $CHOICES =~ "Emerald Theme Manager" ]]; then
EMERALD="emerald "
fi

if [[ $CHOICES =~ "EnvyNG" ]]; then
ENVYNG="envyng-gtk "
fi

if [[ $CHOICES =~ "Ekiga Uninstall" ]]; then
EKIGAREMOVE="ekiga "
fi

if [[ $CHOICES =~ "GHex" ]]; then
GHEX="ghex "
fi

if [[ $CHOICES =~ "GParted" ]]; then
GPARTED="gparted "
fi

if [[ $CHOICES =~ "StumbleUpon" ]]; then
STUMBLE="mozilla-stumbleupon "
fi

if [[ $CHOICES =~ "Ubuntu-Restricted-Extras" ]]; then
URE="ubuntu-restricted-extras "
fi

if [[ $CHOICES =~ "VLC" ]]; then
VLC="vlc"
fi

if [[ $CHOICES =~ "VLC Firefox Plugin" ]]; then
VLCFFP="mozilla-plugin-vlc "
TOTEMREMOVE="totem totem-common totem-gstreamer totem-plugins totem-mozilla "
TOTEM="totem "
fi

if [[ $CHOICES =~ "Windows Media Codecs" ]]; then
W32CODECS="w32codecs "
fi

if [[ $CHOICES =~ "Wine" ]]; then
WINE="wine"
fi

if [[ $CHOICES =  "" ]]; then
zenity --title "Nick's Easy Installer" --info --text "You didn't choose anything!?!?"
exit 1
fi

# This says that if one of the programs to be installed requires medibuntu, add medibuntu to the software sources.
if [[ $CHOICES =~ "Adobe Acrobat Reader"|"DVD Codecs"|"Windows Media Codecs" ]]; then
wget http://www.medibuntu.org/sources.list.d/${VERSION}.list -O /etc/apt/sources.list.d/medibuntu.list && aptitude update && aptitude -y install medibuntu-keyring && aptitude update
fi

#This is the command that removes all the programs the user selected
aptitude -y remove $TOTEMREMOVE$EKIGAREMOVE$RHYTHMBOXREMOVE
aptitude -y purge $TOTEM$EKIGAREMOVE$RHYTHMBOXREMOVE

aptitude update
aptitude -y safe-upgrade | zenity --title "Nick's Easy Installer" --progress --auto-close  --text "Updating and Upgrading!" --width=300

#This is the command that installs all the programs the user selected
echo "Yes" | aptitude -y install $ACROREAD$AUDACITY$AWN$BANSHEE$COMPIZ$FUSIONICON$DVD$EMERALD$ENVYNG$GHEX$GPARTED$STUMBLE$URE$VLC$VLCFFP$W32CODECS$WINE | zenity --title "Nick's Easy Installer" --progress --auto-close --text "Installing your selections!" --width=300

exit 1
```

---

### Post by eightmillion on 2008-09-02
You can combine these two commands:
```
#This is the command that removes all the programs the user selected
aptitude -y remove $TOTEMREMOVE$EKIGAREMOVE$RHYTHMBOXREMOVE
aptitude -y purge $TOTEM$EKIGAREMOVE$RHYTHMBOXREMOVE
```
like this:
```

aptitude -y remove --purge $TOTEMREMOVE$EKIGAREMOVE$RHYTHMBOXREMOVE

```
Other than that, there really isn't an easy way to make your ifs into a case statement. I wouldn't worry about it.

Edit: Nevermind. I see what you're doing there.

---

### Post by mssever on 2008-09-02
Instead of keeping separate variables for each package, why not use an array and eliminate $ACROBAT, $AUDACITY, $BANSHEE, etc.? [http://tldp.org/LDP/abs/html/arrays.html](http://tldp.org/LDP/abs/html/arrays.html)

```
declare -a packages # declares an array called packages

# To get a space-separated list of the packages:
aptitude -y install ${packages[@]}

# To count the number of elements in $packages:
echo ${#packages[@]}

# To set the element at index 0:
$packages[0]=some-package

# Putting this all together, to append an item to $packages:
# (Someone tell me, isn't there a simpler way to do this? I know bash
# arrays are horrible, but I sure hope I've overlooked something.)
packages[${#packages[@]}]=some-package
```Of course, bash isn't the ideal language for a task like this. If you used Python or Ruby, this job would be simpler (although Ruby isn't installed by default, so it probably wouldn't be such a good choice in this instance).

---

### Post by ghostdog74 on 2008-09-02
> **mssever said:**
> Of course, bash isn't the ideal language for a task like this. 
If its just pure bash, it may be kludgy BUT doable. However, if its bash coupled with awk (or even just purely awk), it will be possible as in any other languages, since Awk provides the functionality bash lacks.

---

### Post by mssever on 2008-09-02
> **ghostdog74 said:**
> If its just pure bash, it may be kludgy BUT doable. However, if its bash coupled with awk (or even just purely awk), it will be possible as in any other languages, since Awk provides the functionality bash lacks.
While awk is commonly used in conjunction with bash, it is if course a distinct language. So this raises a question: Is awk worth learning these days? I'll admit that my knowledge of awk is minimal. But why not just learn a general-purpose language such as Ruby or Python, and use that language whenever a bash script would be non-trivial (discounting the few situations where shell scripts are required)? It seems to me that awk was a useful tool in its day, but it was superceded by Perl, which is now being superceded by Python and Ruby.

---

### Post by ghostdog74 on 2008-09-02
> **mssever said:**
> While awk is commonly used in conjunction with bash, it is if course a distinct language. So this raises a question: Is awk worth learning these days? 

well, let me ask you back this question :), why is it not worth learning it these days? what is it that you hate about it? If you are interested, you can take a look at the last link in my sig.

> 
 But why not just learn a general-purpose language such as Ruby or Python, and use that language whenever a bash script would be non-trivial (discounting the few situations where shell scripts are required)? 

If you are stuck in a situation where you can't use Ruby or Python and is only allowed to use shell and tools, what would you do? I hate to go into this yet again.

> 
It seems to me that awk was a useful tool in its day, but it was superceded by Perl, which is now being superceded by Python and Ruby.
i disagree. But i am not going to go further.

---

### Post by anotherdisciple on 2008-09-02
Okay... I took a look at the array thing... first off... I think I've reached the peak of my understanding in BASH... I thought array seemed just as messy and harder to interpret. 

with the case situation... I want to know how I can make this work. The reason I used if statements is because zenity spits out a lot of information. I need a way to say "If zenity's output contains the word "Audacity" set the variable AUDACITY="audacity ".

so help me do this with case....

```

case "$CHOICES" in
     'Audacity')
         AUDACITY= "audacity "
         ;;
     'Avant Window Navigator')
         Banshee= "avant-window-navigator "
         ;;
     'Banshee')
         Banshee= "banshee-1 "
         ;;
esac
```

Does this work like the word "contains" or do I need to add wildcards '*Audacity*'? Or have I reached the point where I'm losing my understanding of BASH scripting.

---

### Post by mssever on 2008-09-02
> **ghostdog74 said:**
> well, let me ask you back this question :), why is it not worth learning it these days? what is it that you hate about it? If you are interested, you can take a look at the last link in my sig.Did you just add that link, or did I just overlook it? It's an interesting read.

I didn't intend to give the impression that I hate awk; I don't know it well enough to pass judgment. I asked that question because I don't see it used very often (except in your posts). And because I'd picked up the idea somewhere that awk was on its way out, I wanted to ask about that.


> If you are stuck in a situation where you can't use Ruby or Python and is only allowed to use shell and tools, what would you do?That would, of course, be a time to use awk. But how common are such situations? In my experience, they're rare. That's not to discount the fact that some people may well be in that kind of situation fairly often.

> **anotherdisciple said:**
> Okay... I took a look at the array thing... first off... I think I've reached the peak of my understanding in BASH... I thought array seemed just as messy and harder to interpret.At the very least, you need to handle the case where your program variables, such as $AUDACITY, are not selected and set by your script. If you don't explicitly set them, their value will be inherited from the environment, which in some cases could produce undesireable results. So you should do something like this at the top of your script: ```
AUDACITY=
Banshee=
# etc.
```Using arrays isn't terribly difficult. Here's your code modified to use them: ```
declare -a packages
case "$CHOICES" in
    'Audacity')
        packages[${#packages[@]}]=audacity
        ;;
    'Avant Window Navigator')
        packages[${#packages[@]}]=avant-window-navigator
        ;;
    'Banshee')
        packages[${#packages[@]}]=banshee-1
        ;;
esac

# later...
aptitude -y install ${packages[@]}
```Appending to arrays *is* messy in bash. But when you get an array, you get a data structure that is much more natural to use. And maintaining a whole bunch of variables strung together is sure to cause some bugs sometime.

I really think that you'd be much better off ditching bash and using another language such as Python or Ruby for this task. There just is no clean way to do this in bash.

---

