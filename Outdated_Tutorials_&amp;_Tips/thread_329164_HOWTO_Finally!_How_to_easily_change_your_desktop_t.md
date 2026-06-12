---
title: "HOWTO: Finally! How to easily change your desktop to a random file at specified times"
date: 2007-01-01
forum: Outdated Tutorials &amp; Tips
---

### Post by davidY on 2007-01-01
Ok, on these forums I found very silly ways to change your desktop picture randomly at intervals. Some involved installing programs, daemons, or using python(!) to achieve this simple task. Here is the solution, using plain old methods. 

First, a shell script is used. This will do most of the work - basically the windows equivalent is a batch file, except this is advanced. This is the code, pretty intuitive:

```
#!/bin/bash

# Set your folder with the pics
picsfolder="/media/documents/Desktops/"

# Go to your folder with the pics
cd $picsfolder

# Create an array of the files
files=(./*/*.jpg)

# Get the size of the array
N=${#files[@]}

# Select a random number between this range
((N=RANDOM%N))

# Get the name of this file
# a bit overly complicated. basically it takes the Nth string from files ${files[$N]}, and then removes the first two letters which is the "./" at the beginning 
randomfile=`echo ${files[$N]} | cut --characters="1 2" --complement`

# start of gconftool command and set the desktop
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$picsfolder$randomfile"
```

Note that the last command is what does the work - it calls a program to set this "registry key" thing to point to your new file. Now to actually make this code do stuff, we have to save it to a file. In a terminal do this:

```
execute: gksu gedit
paste the above code
save to: /bin/changewallpaper.sh
exit the gedit
execute: gksu chmod +x /bin/changewallpaper.sh 
```

now we have a script to change the wallpaper. we have also made the file executable (+x). you can run it in your terminal by typing changewallpaper.sh
Now to make it run every so often, you use cron - a schecheduling program that most linux distributions has. In a terminal do this:

```
execute: crontab -e
add an extra line: */15 * * * * changewallpaper.sh
add an extra line: @reboot changewallpaper.sh
press: control+x
press: y
press: enter
```

what that means is that every 15 minutes and every time the computer starts, it will run changewallpaper.sh
modify that 15 if you want.
check [http://mkaz.com/ref/unix_cron.html](http://mkaz.com/ref/unix_cron.html) for more cron info

**Notes**
Here are some other suggestions, and some seem better
[http://www.ubuntuforums.org/showpost.php?p=2069526&postcount=14](http://www.ubuntuforums.org/showpost.php?p=2069526&postcount=14)
[http://www.ubuntuforums.org/showpost.php?p=2039814&postcount=13](http://www.ubuntuforums.org/showpost.php?p=2039814&postcount=13)

[COLOR="Red"]**Troubleshooting**[/COLOR]
Copied from [http://www.ubuntuforums.org/showpost.php?p=2223718&postcount=16](http://www.ubuntuforums.org/showpost.php?p=2223718&postcount=16)
If your wallpapers do not change, just add them to the gnome wallpaper manager. After it seems like the wallpapers change

Quoted from pt123: 
I get the error:
scripts/changeWallpaper.sh: 10: arith: syntax error: "RANDOM%921+1"
pt123's solution:
I found why it wont work when called in a terminal from another forum. if you're running ubuntu you may find /bin/sh is symlinked to dash and not bash. sometimes you find weird errors occurring because of that.
So the solution was:
```
rm /bin/sh
then
ln -s /bin/bash /bin/sh
```

---

### Post by K.Mandla on 2007-01-05
Nicely done. I'll give this one a try with feh too, and see if it does the same thing without gconftool.

---

### Post by loko on 2007-01-05
Thank your for this nice how-to

---

### Post by davidY on 2007-01-05
Yeah, the problems with earlier shell scripts is that they would often impose restrictionso n file names - like no spaces, or no subdirectories. 

I think gconftool is probably the easiest - it is installed auto with ubuntu right? so everybody can use it. Although feh seems pretty cool

---

### Post by KingArthur10 on 2007-01-05
I use desktop drapes.  Works well.  Just a few bugs from times to time.  Look into it.  It's got a GUI.

---

### Post by davidY on 2007-01-06
That is true GUI > CLI when it is for people who want it. But i didn't know about this, so I had to write 5 lines of shell code *sad*.....

On the plus side if I learnt tcl/tk, i could probably whip up a (dodgy) GUI for this to install a crontab, and to install the script...

---

### Post by george_apan on 2007-01-06
Thank you very much! This is really nice! :)

One question though: how do I make the array read files from 2 or more seperate directories? Would a "files=(./dir1/*.jpg ./dir2/*.jpg)" work?

---

### Post by Hobbes on 2007-01-16
anyone know why i would be getting "10: Syntax error: "(" unexpected"?

it is the line 'files=(./*/*.jpg)' that is being complained about, but i cant find any difference between that and the code given?

---

### Post by marianom on 2007-01-17
davidY,
 in 
```
execute: gksu gedit
paste the above code
save to: /bin/changewallpaper.sh
exit the gedit
execute: gksu chmod +x /bin/change.sh

```

shouldn't it be

```
execute: gksu gedit
paste the above code
save to: /bin/changewallpaper.sh
exit the gedit
execute: gksu chmod +x /bin/changewallpaper.sh

```

?

---

### Post by Rui Pais on 2007-01-17
or more easily:

```
gksudo gedit /bin/changewallpaper.sh
save and exit
sudo chmod +x /bin/changewallpaper.sh

```

---

### Post by marianom on 2007-01-17
Hobbes, not sure here but I guess you need to change #!/bin/sh for #!/bin/bash in the first script.

Anyone can tell us if it's right?

Rui Pais: nice signature. It's always nice to see that somebody else appreciates the same writers that I do.

---

### Post by Rui Pais on 2007-01-17
> **marianom said:**
> Hobbes, not sure here but I guess you need to change #!/bin/sh for #!/bin/bash in the first script.

Anyone can tell us if it's right?

Rui Pais: nice signature. It's always nice to see that somebody else appreciates the same writers that I do.

it should works both ways since the code it's simple and didn't require nothing specific to one shell. I had a some problems with certain scripts on edgy due to shell change but this one don't seems to have anything problematic to edgy/dash (didn't try it)



About Becket. Well a few moth ago i was in middle of reading Watt, when an opportunity appeared to saw 'waiting for Godot'. 
My first time i saw it :(. And i was amazed by the quality of text, the solutions he gets for the self raised problems, the circular absorbing essence of the *wait* replacing the means of the action, the motives and even the lives of the personages!... 
And then suddenly they said that 2 phrases... i was devastated with concept. More then depressing it's terrifying. Not the point of lose rights or some one take them away, but one volunteer "get rid of them".... (And worst, what was written with a burlesque, sad/comic, almost clowning intention it 's so common around us on our days, in our society... )

---

### Post by tweedledee on 2007-01-20
> **Hobbes said:**
> anyone know why i would be getting "10: Syntax error: "(" unexpected"?

it is the line 'files=(./*/*.jpg)' that is being complained about, but i cant find any difference between that and the code given?

I got the same error, as well as it choked on a directoy with a space in the name.  Upon further investigation, I have come up with an even simpler script, which at least works on my system:
```

#!/bin/bash

# Set your folder with the pics
picsfolder="/media/documents/Desktops/"

# Go to your folder with the pics
cd "$picsfolder"

# Get the name of a random file
randomfile=`ls *.jpg *.png |sed -n $((RANDOM%$(ls *.jpg *.png |wc -l)+1))p`

# start of gconftool command and set the desktop
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$picsfolder$randomfile"
```

You can follow davidY's instructions for executing, etc.

I also don't know if this is a quirk of my system or not, but I find I have to add all the files to the list of available backgrounds (via the Desktop Background tool) before any of the files will actually display when set.

EDIT: you should also be able to extend this to multiple directories (provided they are sub-directories of the main directory) as follows:
```

#!/bin/bash

# Set your folder with the pics
picsfolder="/media/documents/Desktops/"

# Go to your folder with the pics
cd "$picsfolder"

# Get the name of a random directory
randomdir=`ls -d */ |sed -n $((RANDOM%$(ls -d */ |wc -l)+1))p`

# Go to the selected directory
cd "$randomdir"

# Get the name of a random file
randomfile=`ls *.jpg *.png |sed -n $((RANDOM%$(ls *.jpg *.png |wc -l)+1))p`

# start of gconftool command and set the desktop
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$picsfolder$randomdir$randomfile"
```

To deal with multiple independent directories is more complicated; I'd suggest putting them all into a file and using cat to display the line (instead of the "ls" commands) and process it similarly.

EDIT 2: See post #22 for an improved version of the multiple directories approach.

---

### Post by eternalsword on 2007-01-27
feel free to modify this to use random.  it allows for multiple directories through a file and allows for spaces in directories and file names.
this also makes it possible to have different wallpaper directories per user since the .directorylist file is in the users home directory

```
#!/bin/bash
IFS=$'\n'
ALIST=( `cat ~/.wallpaper/.directorylist` )
COUNTER=${#ALIST[@]}
find "${ALIST[$COUNTER-1]}" -maxdepth 1 -mindepth 1 -type f | grep ".jpg\|.png" > .wallpaperlist
let COUNTER-=1
until [  $COUNTER -lt 1 ]; do
find "${ALIST[$COUNTER-1]}" -maxdepth 1 -mindepth 1 -type f | grep ".jpg\|.png" >> .wallpaperlist
let COUNTER-=1
done
ALIST=( `cat .wallpaperlist` )
RANGE=${#ALIST[@]}
let LASTNUM="`cat .lastwallpaper` + 1"
let "number = $LASTNUM % $RANGE"
echo $number > .lastwallpaper
echo "${ALIST[number]}" > .currentwallpaper
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "${ALIST[$number]}"

```

---

### Post by groova on 2007-02-27
I tried to set this up and put the script in my home-folder. (Also written without sudo or sdgk) The pictures are also in a subfolder of home.

Now when I execute the script, my background turnes white. Any idea why that is? (I just want to understand... :( )

---

### Post by tweedledee on 2007-02-27
> **groova said:**
> I tried to set this up and put the script in my home-folder. (Also written without sudo or sdgk) The pictures are also in a subfolder of home.

Now when I execute the script, my background turnes white. Any idea why that is? (I just want to understand... :( )

I've tried all the variants posted here, and without exception I had to add the background pictures to my list of desktop wallpapers before the images would appear (right-click on your desktop -> change wallpaper -> add wallpaper -> select all the files you want to rotate through (you can do them all at once if they are in the same folder).  This basically just seems to make Nautilus "aware" of the files.

---

### Post by talcite on 2007-03-03
I'm having the same problem as other people in this thread. No matter what I do, I get no changes in my wallpaper. I have added all my wallpapers to the wallpaper manager. 

This is my code: 

#!/bin/bash

# Set your folder with the pics
picsfolder="/home/matthew/wallpapers"

# Go to your folder with the pics
cd "$picsfolder"

# Get the name of a random file
randomfile=`ls *.jpg *.png |sed -n $((RANDOM%$(ls *.jpg *.png |wc -l)+1))p`

# start of gconftool command and set the desktop
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$picsfolder$randomfile"


Thanks for your help guys.
Btw, if i don't run it under gksu, the screen goes white
If i run it under gksu, there's no change in wallpaper.

---

### Post by pt123 on 2007-03-03
> **tweedledee said:**
> 
randomfile=`ls *.jpg *.png |sed -n $((RANDOM%$(ls *.jpg *.png |wc -l)+1))p`

what is the character in front of ls and after p is it ` the character which share the key with ~ ?

Because when I use this and try to run the script I get this error :

```

scripts/changeWallpaper.sh: 10: arith: syntax error: "RANDOM%921+1"

```


When I change it to an apostrophe i.e. ' 
When I look in the gconftool for picture_filename it says
/media/d/Collection/Wallpapers/zNew/ls *.jpg *.png |sed -n $((RANDOM%$(ls *.jpg *.png |wc -l)+1))p

I am assuming its just quoting it. 

Can someone please tell me what the problem is?

---

### Post by talcite on 2007-03-03
Never mind guys, it worked =S The Cron script works... it changes automatically, but when I run the changewallpaper script manually, it doesn't change anything 0.o

---

### Post by pt123 on 2007-03-03
I changed it to ` now the script works in cron 

but it doesn't work when it manually i.e. sh scripts/changeWallpaper.sh

I get the error:
scripts/changeWallpaper.sh: 10: arith: syntax error: "RANDOM%921+1"

What is causing this error?

---

### Post by pt123 on 2007-03-03
I found why it wont work when called in a terminal from another forum.
> if you're running ubuntu you may find /bin/sh is symlinked to dash and not bash. sometimes you find weird errors occurring because of that.

So the solution was:
> 
rm /bin/sh
then
ln -s /bin/bash /bin/sh


---

### Post by pt123 on 2007-03-03
I changed tweedledee script so that when it looks into a subfolder and if it has no photos then to look for subfolders within the subfolder.

 I also added a seconds multiplication to the random number hoping to improve the randomisation.

Here is the script if anyone wants it
```

#!/bin/bash

# Set your folder with the pics
picsfolder="/media/d/Collection/Wallpapers/"

# Go to your folder with the pics
cd "$picsfolder"

# the seconds is used to get a better randomisation as it is  multiplied to the random number
seconds=`eval date +%s`
echo "$seconds"

# Get the name of a random directory
randomdir=`ls -d */ |sed -n $((RANDOM*seconds%$(ls -d */ |wc -l)+1))p`
echo "$randomdir"

# Go to the selected directory
cd "$randomdir"
numberOfPics=`(ls *.jpg *.png |wc -l)`
echo $numberOfPics
wpPath=""
if [ $numberOfPics -lt 1 ]	# is $X less than $Y ? 
then
	echo "number of pics is less than 1"	
	# Get a random sub Directory because there are no pics in folder	
	randomSubDir=`ls -d */ |sed -n $((RANDOM*seconds%$(ls -d */ |wc -l)+1))p`
	cd "$randomSubDir"
	numberOfSubPics=`(ls *.jpg *.png |wc -l)`
	echo $numberOfSubPics
	randomSubFile=`ls *.jpg *.png |sed -n $((RANDOM*seconds%$numberOfSubPics+1))p`
	echo $randomSubFile
	wpPath="$picsfolder$randomdir$randomSubDir$randomSubFile"
else
	# there are pics in folder dont bother looking for sub directories	
	randomfile=`ls *.jpg *.png |sed -n $((RANDOM*seconds%$numberOfPics+1))p`
	wpPath="$picsfolder$randomdir$randomfile"
fi
echo $wpPath



# start of gconftool command and set the desktop
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$wpPath"


```

---

### Post by tweedledee on 2007-03-03
> **pt123 said:**
> I changed tweedledee script so that when it looks into a subfolder and if it has no photos then to look for subfolders within the subfolder.

 I also added a seconds multiplication to the random number hoping to improve the randomisation.

Here is the script if anyone wants it
Progress!  I don't actually use the multiple directories (at least to date), but I'm glad you found it useful enough to improve upon it.  I've updated my post to point to your changes.

---

### Post by pt123 on 2007-06-10
A new script to change the wallpaper. What it does is grabs all the images from your wallpaper folder including sub directories. Then it creates a list and saves it to your hard disk. Then it randomly chooses a WP from the list. Whenever you run it checks to see if the number images in your list matches the number of images in your WP folder, if not it saves the updated list to disk.

```

#!/bin/bash

# Set your folder with the pics
picsfolder="/media/main/Wallpapers/"

#Set the Path to the Wallpaper list will be created
wplistpath="/home/username/wplist.txt"


#go to the picture directory
cd "$picsfolder"

#load the list of pics to a variable
wpDirList=`(find . -regex ".*\(jpg\|jpeg\|gif\|png\|svg\)$"  -type f)`
#find the number of pics in the WP dir based on the extension
numberOfPicsDir=`echo "$wpDirList" | wc -l`



# Count number of pics in the Wallpaper list by counting number of lines.
numberOfPicsList=0  #initial lise


#check if the wallpaperlist Exists
if [[ -e "$wplistpath" ]]
    then
       numberOfPicsList=$(wc -l < "$wplistpath")
     else
 	echo "WP list does not exist"
fi
       

# inform the user
echo $numberOfPicsDir" --- "$numberOfPicsList

# if they don't match rewrite the wallpaper list
# this if can be removed and the list can be saved every time

if [ $numberOfPicsDir -ne $numberOfPicsList ]
then
	#save the list to disk 	
	echo -n "$wpDirList" > "$wplistpath"

fi

# Find a random line number in the wallpaper list
r=$((RANDOM % numberOfPicsDir + 1))       # Random number from 1..n.

# print what the line number is 
picPath=`sed -n "$r{p;q;}" "$wplistpath"`   # Print the r'th line.
wpPath="${picsfolder}${picPath#./}"     # #./ crops that substring but it doesn't matter if it left there
echo "$wpPath" 

#set the wallpaper in Gnome Config Editor
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$wpPath"


```


Preferably you should break the script into two scripts one that creates the wallpaper list and this should be scheduled to run once a week and the other script that will pick an image from the wallpaper list which can be run every 5,10,15,60 mins etc.

That said I am running this on a list of 3000+ images without problems.

Here is a link to a good Bash FAQ/Tutorial.
[http://wooledge.org/mywiki/BashFAQ?action=show&redirect=BashFaq](http://wooledge.org/mywiki/BashFAQ?action=show&redirect=BashFaq)

---

### Post by cyberbuff on 2008-01-01
gksu chmod +x /bin/changewallpaper.sh


gave me: 

```
(gksu:11991): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
/home/dutta/.themes/snow-leopard-mac/gtk-2.0/gtkrc:41: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/dutta/.themes/snow-leopard-mac/gtk-2.0/gtkrc:42: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/dutta/.themes/snow-leopard-mac/gtk-2.0/gtkrc:43: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
```
 it's not working. :(

---

### Post by pt123 on 2008-01-02
That just gives execute permissions for the script
the errors just on theme
if you try 
sudo chmod +x /bin/changewallpaper.sh

it wont show any errors

---

### Post by ~LoKe on 2008-01-02
Interesting script.  Not something I'd use because I'm very picky about my wallpapers, but it's definitely useful!  Nice work.

---

### Post by yabbadabbadont on 2008-01-02
The only problem I see with the script, is that the bash RANDOM built-in is limited to 32K.  That just doesn't cut it for a *serious* wallpaper collector like myself...  :lol:

(about 60,000 or so)

---

### Post by pt123 on 2008-01-02
Thanks Loke,

yabbadabbadont then you can create 2+ lists, depending on how you have kept your wallpapers. 

Or you can create 2 random numbers 
eg. random1x 3 + (RANDOM2 % 3)
will handle 32,000 X 3 wallpapers.

---

### Post by aitvo on 2008-01-02
I wrote a script 4 years ago to change wallpaper randomly on a timer. This works with Gnome, WindowMaker, Fluxbox, and with a little edit any other desktop environment that can change wallpaper from a commandline.

[http://www.stangdude.com/download.pl?filename=bgbuddy-1.23.tar.gz](http://www.stangdude.com/download.pl?filename=bgbuddy-1.23.tar.gz)

Also, it's page on gnomefiles: [http://www.gnomefiles.com/app.php/Background_Buddy](http://www.gnomefiles.com/app.php/Background_Buddy) and it's homepage: [http://www.stangdude.com/news/articles/12519005125776/](http://www.stangdude.com/news/articles/12519005125776/)

---

### Post by yabbadabbadont on 2008-01-02
> **pt123 said:**
> Thanks Loke,

yabbadabbadont then you can create 2+ lists, depending on how you have kept your wallpapers. 

Or you can create 2 random numbers 
eg. random1x 3 + (RANDOM2 % 3)
will handle 32,000 X 3 wallpapers.
I just wrote a tiny C program to generate them.  It works well with my randomizing and rotating scripts.  Besides, I think that your method won't work.  I'm not positive, but I think that all numeric variables are limited to 32K in bash.  Don't quote me on that though.

In case anyone wants it, here is my getrandom.c code:
```

#include <time.h>
#include <stdlib.h>
#include <stdio.h>

/*
** With no parameter, just print the
** results of calling random() to stdout.
**
** With a parameter, limit the maximum
** value printed to that parameter.
*/

int main(int argc, char *argv[])
{
        int i = 0;
        long int j = 0;

        /*
        ** Seed the PRNG with the current time.
        */

        srandom((unsigned int) time((time_t *) NULL));

        /*
        ** PRNG's generally return better results
        ** after they have been hit a few thousand
        ** times.  My needs aren't that strict, so
        ** I'll just hit it a thousand times. ;)
        */

        for (i = 0; i < 1000; i++)
                j = random();

        /*
        ** Are we limiting the value?
        */

        if (argc == 2)
        {
                printf("%ld", (j % atol(argv[1])) + 1);
        }
        else
        {
                printf("%ld", j);
        }

        return 0;
}

```

---

### Post by Saint Angeles on 2008-01-02
> **yabbadabbadont said:**
> ...That just doesn't cut it for a *serious* wallpaper collector like myself...  :lol:

(about 60,000 or so)

holy... ****

---

### Post by yabbadabbadont on 2008-01-02
> **Saint Angeles said:**
> holy... ****

<Jeopardy>What do you find in baby Jesus' diapers?</Jeopardy>

:lol:

You have to pull some tricks to optimize things so that the scripts will actually run in a reasonable amount of time.  ;)

---

### Post by Birk on 2008-01-21
I did not check your scripts, but use **_*[I]wallpaper tray*[/I]_**. This is a nice little program, that does everything I need (change randomly ...) and is easily downloadable  with the synaptic package manager. :)

---

### Post by Bodsda on 2008-02-04
Wicked tuto m8,. nice and simple like,. cheers

---

### Post by cor2y on 2008-03-13
I have to ask for those using gnome how sudden are the wallpaper changes.
I remember i tried something similiar a few years ago in gnome but i didn't like how the transition from one wallpaper to the next was so sudden.
I was looking for something that did smooth transitions from one wallpaper to the next like what happens in Mac desktops, has it progressed as far as that?

---

### Post by pt123 on 2008-03-13
it is a sudden change

---

### Post by guywithcable on 2008-09-20
A fellow user and I wrote a GUI program to do this. It works with Gnome's built in feature and it has a fading effect. It is released as a deb, so it can be installed with a couple clicks. It is GPL.

Check out this post:
[http://ubuntuforums.org/showpost.php?p=5751005&postcount=30](http://ubuntuforums.org/showpost.php?p=5751005&postcount=30)

From this thread:
[http://ubuntuforums.org/showthread.php?t=798634](http://ubuntuforums.org/showthread.php?t=798634)

---

### Post by Prestwick on 2008-09-29
Thanks for the great howto!

---

### Post by lost_guy598 on 2009-02-13
great tutorial, but i seem to have a problem with the timer - doesnt change pics, i can change manually, but doesnt change automatically. any suggestions???

---

### Post by pt123 on 2009-02-13
which version are you using as there have been a few modifications in this thread

---

### Post by lost_guy598 on 2009-02-13
ubuntu version 8.10, first version of coding(post 1) - nt sure on what u mean by which version

---

### Post by pt123 on 2009-02-14
ok there are other few modifications of the scripts in later posts, including one by me.

---

### Post by lost_guy598 on 2009-02-18
my problem seems to be with the timer as it changes on reboot an i can change it manually

---

### Post by Niicodemus on 2009-02-18
I just switched back to Gnome from XFCE, and found myself sorely missing the random wallpapers function on a timer that displays a unique wallpaper on each monitor. So I wrote a perl script to do it for me. I have posted it at [http://lotech.org/code/random_wallpaper.pl.html](http://lotech.org/code/random_wallpaper.pl.html) if you're interested.

---

### Post by phenest on 2009-02-28
Here's a script that can search recursively through sub-folders ...
```
#!/bin/bash

folder="pictures"

cd $HOME/$folder
files=(`find * | grep -i "\.jpg$\|\.gif$\|\.png$\|\.bmp$"`)

# Get the size of the array
n=${#files[@]}
# Prevent a blank screen if there are no pictures
if [ $n -eq 0 ]; then exit 1; fi

# Set a random wallpaper with gconftool-2
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$HOME/$folder/${files[RANDOM%n]}"

exit 0
```
... but perhaps someone can tell me why it has problems with spaces in filenames?

---

### Post by phenest on 2009-03-03
Ok. I solved the problem with spaces in the filename.
```
#!/bin/bash

files=(`find $HOME/pictures | grep -i "\.jpg$\|\.gif$\|\.png$\|\.bmp$" | tr ' ' '¿'`)

# Set a random wallpaper with gconftool-2
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "`echo ${files[RANDOM%${#files[@]}]} | tr '¿' ' '`"

exit 0
```
2 lines of code! I added "tr ' ' '¿'" to change spaces to another character (¿), which is very unlikely to be found in a filename. It then gets changed back to a space when setting the background.

---

### Post by deathowl on 2009-04-22
Dude,there is something wrong with my pc cant get through with the administrator!i think i am being hacked cos when i pay my monthly bill other name appear on list and it was not my computer's name.when I log in to my pc there are two user's and i cannot log in to my account cos it needs a password.they say reformat is the best solution so I try but it's still there!now I am using other account without password and the name of the account is KAMANDAG...anyone,please help me!:confused:i try the how to but it wont work,it say that is not recognized as an internal or external command,operable program or batch file...I am suffering this situation for already two Fu***&&& months...please help! tnxz...you guys rock:guitar:

---

### Post by SuperZ on 2009-04-22
wow... pretty impresive! man... i wanna get unbuntu just for this kind of stuff!:)

---

### Post by xeddog on 2009-04-24
Niicodemus - 

This perl script looks to be exactly what I am looking for.  I have dual monitors and would like a different wallpaper on each monitor.  I downloaded your script and gave it a try but have some syntax errors.

I edited two of the Options section as follows:

```
my @screens = (
  ['1280', '1024'], # Left monitor
  ['1280', '1024'], # Right monitor
);
```

```
my @wallpaper_dirs = (
  '/home/twoblues/Pictures',
);
```

When I run the script I get this:

```
twoblues@Stealth:~/Documents$ ./random_wallpaper.pl
syntax error at ./random_wallpaper.pl line 142, near "&gt;"
syntax error at ./random_wallpaper.pl line 142, near "&lt"
syntax error at ./random_wallpaper.pl line 142, near "&lt"
syntax error at ./random_wallpaper.pl line 142, near "$tile_height) "
syntax error at ./random_wallpaper.pl line 146, near "}"
syntax error at ./random_wallpaper.pl line 156, near "];"
syntax error at ./random_wallpaper.pl line 161, near "&gt;"
syntax error at ./random_wallpaper.pl line 161, near ""${columns}x${rows}")"
BEGIN not safe after errors--compilation aborted at ./random_wallpaper.pl line 172.
```

Since I know about as much about perl as I do about quantum mechanics, I could sure use your help.

TIA,

xeddog


Edit:  almost forgot.  I don't know if this matters or not, but yesterday I upgraded my Intrepid installation to Jaunty using the upgrade process.  I did not try this on Intrepid.  I am using Intel 32-bit with an ATI Radeon 9600 graphics card which means that I am having to use the opensource drivers since the ^%$#@ at AMD are dropping support for it.

---

### Post by xeddog on 2009-04-25
Niicodemus - 

I tried your perl script on another Jaunty install (this one upgraded from Intrepid), and it works great.  One question though.  Can it 1) be modified to access images from multiple directories, and/or 2) be modified to include sub-directories?

And I still have the errors in my previous post for the original installation.  I would still like to get that resolved too. 

TIA,

xeddog

---

### Post by hyperAura on 2009-07-28
thnx a lot nice 1

i used the perl script works fine

---

### Post by gnudoc on 2009-09-13
Here's my fairly simple take on this. Since intrepid, gconftool has used DBUS, breaking the older scripts. This script works with both newer and older versions of Ubuntu.
It works with as many directories as you like, and handles recursion happily.
Although it's a fairly large file (nearly 3kb), that's mostly because of the heavy commenting.

Your thoughts?

---

### Post by tpjk on 2009-09-27
> **gnudoc said:**
> Here's my fairly simple take on this. Since intrepid, gconftool has used DBUS, breaking the older scripts. This script works with both newer and older versions of Ubuntu.
It works with as many directories as you like, and handles recursion happily.
Although it's a fairly large file (nearly 3kb), that's mostly because of the heavy commenting.

Your thoughts?


this script works really well for me - so thanks:]

the only weird thing i encountered was that i got the following error message when running the script from the shell:
```
touch: cannot touch `.../scripts/wallpaper/Xdbus_details': No such file or directory
chmod: cannot access `.../scripts/wallpaper/Xdbus_details': No such file or directory
```

i know it says in your comments that i need to change the path to the Xdbus_details file, but since i'm fairly new to scripting i couldn't make sense of what you meant by ```
source the file at $DETAILS in your cronjob
"*/10 * * * * . /path/to/Xdbus_details; /path/to/setwallpaper.sh" is the sort of thing you want
```

plus, i can't seem to find the Xdbus_details file anywhere in my file system.

other than that, thanks again for sharing the script!

---

### Post by shawnhcorey on 2009-10-02
I just installed 9.04 in anticipation of the Big Day and now *crontab* won't change my background.

[LIST]
[*]It worked fine in 8.04
[*]It works fine in a terminal
[*]It correctly changes [FONT="Courier New"]~/.gconf/desktop/gnome/background/%gconf.xml[/FONT]
[/LIST]

It just doesn't change the image.

Anybody got any ideas?

**Update 2009.10.3:** After some investigation, I discovered that the daemon to change the background, [FONT="Courier New"]gconfd-2[/FONT], does not realizes that the gconf files have changed.  The result, no change in the image.  Now to figure out what to do about it. :)

---

### Post by major.stubble on 2009-10-27
> **shawnhcorey said:**
> **Update 2009.10.3:** After some investigation, I discovered that the daemon to change the background, [FONT=Courier New]gconfd-2[/FONT], does not realizes that the gconf files have changed.  The result, no change in the image.  Now to figure out what to do about it. :)

This is covered in  [Bug #285937]("http://https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/285937").

There are suggestions provided in the bug, but I prefer this:

```
export DBUS_SESSION_BUS_ADDRESS=${DBUS_SESSION_BUS_ADDRESS:=$(grep "^DBUS_SESSION_BUS_ADDRESS=" ${HOME}/.dbus/session-bus/$(cat /var/lib/dbus/machine-id)-${DISPLAY##:[0-9].} )}
```This will export the needed environment variable "DBUS_SESSION_BUS_ADDRESS" if it is not set or is null.  I would not put this in your crontab.  Instead, it should be in the code calling gconftool-2.  It must be set prior to the line executing gconftool-2.

---

### Post by Derek S on 2009-11-22
Here's the script I use for changing wallpaper in gnome.  It uses the shuf command, not arrays.  I'm not sure if it is in all versions of Ubuntu, but it works in 9.10 Karmic

```
#!/bin/bash

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/home/username/Pictures/background"

# Command to Select a random jpg file from directory
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)

# Command to set Background Image
gconftool -t string -s /desktop/gnome/background/picture_filename $PIC
```I pieced it together from other posts solving different problems, and it works, but if it can be improved let me know.

---

### Post by ashokiiit on 2010-06-27
Hello, first of all good work but when i execute the command

sudo sh /bin/changewallpaper.sh 

it is showing the following error. 

/bin/changewallpaper.sh: 10: Syntax error: "(" unexpected

Can u help me in this....

---

### Post by pt123 on 2010-06-27
have you tried my script?
[http://ubuntuforums.org/showpost.php?p=2816683&postcount=24](http://ubuntuforums.org/showpost.php?p=2816683&postcount=24)

---

### Post by ashokiiit on 2010-06-28
hey tried the script...but now wall paper is not changing randomly i added following lines 
crontab -e
*/1 * * * * changewallpaper.sh
@reboot changewallpaper.sh

any suggestions ??

---

### Post by pt123 on 2010-06-28
does the script run when you run it from a terminal. i.e. 
```
sh changewallpaper.sh
```

---

### Post by sefirot on 2010-12-31
Hello, how change pictures automatic each 4 0 5 minutes? It can?
Sefirot

> **pt123 said:**
> A new script to change the wallpaper. What it does is grabs all the images from your wallpaper folder including sub directories. Then it creates a list and saves it to your hard disk. Then it randomly chooses a WP from the list. Whenever you run it checks to see if the number images in your list matches the number of images in your WP folder, if not it saves the updated list to disk.

```

#!/bin/bash

# Set your folder with the pics
picsfolder="/media/main/Wallpapers/"

#Set the Path to the Wallpaper list will be created
wplistpath="/home/username/wplist.txt"


#go to the picture directory
cd "$picsfolder"

#load the list of pics to a variable
wpDirList=`(find . -regex ".*\(jpg\|jpeg\|gif\|png\|svg\)$"  -type f)`
#find the number of pics in the WP dir based on the extension
numberOfPicsDir=`echo "$wpDirList" | wc -l`



# Count number of pics in the Wallpaper list by counting number of lines.
numberOfPicsList=0  #initial lise


#check if the wallpaperlist Exists
if [[ -e "$wplistpath" ]]
    then
       numberOfPicsList=$(wc -l < "$wplistpath")
     else
     echo "WP list does not exist"
fi
       

# inform the user
echo $numberOfPicsDir" --- "$numberOfPicsList

# if they don't match rewrite the wallpaper list
# this if can be removed and the list can be saved every time

if [ $numberOfPicsDir -ne $numberOfPicsList ]
then
    #save the list to disk     
    echo -n "$wpDirList" > "$wplistpath"

fi

# Find a random line number in the wallpaper list
r=$((RANDOM % numberOfPicsDir + 1))       # Random number from 1..n.

# print what the line number is 
picPath=`sed -n "$r{p;q;}" "$wplistpath"`   # Print the r'th line.
wpPath="${picsfolder}${picPath#./}"     # #./ crops that substring but it doesn't matter if it left there
echo "$wpPath" 

#set the wallpaper in Gnome Config Editor
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$wpPath"


```
Preferably you should break the script into two scripts one that creates the wallpaper list and this should be scheduled to run once a week and the other script that will pick an image from the wallpaper list which can be run every 5,10,15,60 mins etc.

That said I am running this on a list of 3000+ images without problems.

Here is a link to a good Bash FAQ/Tutorial.
[http://wooledge.org/mywiki/BashFAQ?action=show&redirect=BashFaq](http://wooledge.org/mywiki/BashFAQ?action=show&redirect=BashFaq)

---

### Post by pt123 on 2010-12-31
you can use cron to run the above script at intervals

I don't want to go into this . This thread deals Cron comprehensively
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

---

