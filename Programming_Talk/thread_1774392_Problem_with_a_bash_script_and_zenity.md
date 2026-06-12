---
title: "Problem with a bash script and zenity"
date: 2011-06-03
forum: Programming Talk
---

### Post by jman6495 on 2011-06-03
Hey , 
For a while now , the Difficulty for new users to install PPAs has annoyed me quite a bit . People end up downloading Debs that don't stay updated , or generally making mistakes in the installation , It complicates things for new users , So i'm working on a system to make PPA installations Smoother ,It's a bash + Zenity Script that will allow ppa's to be installed from a .usi file (or ubuntu Software installer) , a format which i invented for that purpose.

Here's the installer script :
```

#load the file and variables
FILE=$(zenity --file-selection --title "Select A Ubuntu Software Installer")
PPANAME=$(cat $FILE | head -2 | tail -1)
PACKLIST=$(cat $FILE | head -4 | tail -1)
PROGNAME=$(cat $FILE | head -6 | tail -1)
DESCRIPTION=$(cat $FILE | head -8 | tail -1)
OFFICIALORNOT=$(cat $FILE | head -10 | tail -1)
#Welcome the user ,Explain the situation"
zenity --info --title "USI Software Installer - $PROGNAME" --text="You wish to install $PROGNAME.

$PROGNAME will be automatically updated via PPA.

The following packages will be installed : $PACKLIST From the PPA $PPANAME . 

Description : $DESCRIPTION .

This is a $OFFICIALORNOT Source for this program"
#Ask them if they wish to continue
zenity --question --text="Are you sure you wish to install "
if [ $? == 0 ]
then
{
sleep 2
zenity --info --title 'Preparing install' --text="Commencing installation after you press OK, you will be required to enter your password to continue"
sleep 1
PASSWORD=$(zenity --password)
sleep 1
echo $PASSWORD | sudo -S apt-add-repository $PPANAME
sleep 1
zenity --info --title 'Installation progress' --text="Repository Installed , Commencing Installation when you press OK , this could take a few minutes depending on the size of the program , This may dissapear for a while , You can continue working until a completion message is displayed ."
sleep 1
echo $PASSWORD | sudo -S apt-get update
echo $PASSWORD | sudo -S apt-get -y install $PACKLIST
zenity --info --title 'Install Completed' --text="The Install has been completed. Thankyou for Installing $PROGNAME , Have a nice day :) ."
sleep 2
}
else
zenity --info --title "you have chosen not to install" --TEXT="ohnoz!"
exit
fi
exit

```

and here's an example of a program :

```

#ppa
ppa:docky-core/ppa
#packages
docky
#programname
Docky
#Description
The Best dock no money can buy !
#officialornot
official

```

My problem is that it runs fine , no problems in Terminal ,however if I try just running it , It doesn't work (i think it might be APT): It gets to The Question and then just cuts out. Also I wish to use progress bars for the installation progress , and want to replace package selection by browse to just double clicking on the .upi and launching it with the Upi installer .

Any help would be much appreciated .


              -jman6495

---

### Post by geirha on 2011-06-03
You've forgot the most important part, the first line of the script, the shebang, which tells your system what interpreter to use to parse your script.

There's also a lot of bad practice in there. To name a few:

1. ```
PPANAME=$(cat $FILE | head -2 | tail -1)
```
Useless use of cat, missing quotes, and in general a terrible way to parse a file, use the shell to parse it instead. (*help '\read'*)
2. All uppercase variable names. Use lowercase variables to avoid accidentally overriding environment variables and special shell variables.
3. Don't read in a password to send to sudo, use gksudo and let gksudo ask for the password.
4. ```
if [ $? == 0 ]
``` this is probably where your script fails; without a shebang, I think linux might decide to run it with sh. == is bash specific, and even in bash, you shouldn't use it. Also, don't test $? if you only want to know if it suceeded or not. Just test the command directly:
```
if zenity ...; then
```

Please read [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) so you learn the basic syntax of the shell. Also see [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls) for avoiding such pitfalls in the future.

---

### Post by jman6495 on 2011-06-04
ok cheers , i'l take a look :)

---

