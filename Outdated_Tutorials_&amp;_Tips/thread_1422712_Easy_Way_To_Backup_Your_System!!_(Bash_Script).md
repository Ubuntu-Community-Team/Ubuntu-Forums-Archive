---
title: "Easy Way To Backup Your System!! (Bash Script)"
date: 2010-03-05
forum: Outdated Tutorials &amp; Tips
---

### Post by lonewaster on 2010-03-05
[I][B]WARNING: NO CODE IS FLAWLESS, AND THIS IS NO DIFFERENT.
THINGS MIGHT GO WRONG WHEN USING THIS METHOD, SO I SUGGEST TAKING A HARD-COPY (ON CD/DVD) OF ANYTHING THAT YOU REALLY CAN'T AFFORD TO LOSE.
THIS IS MEANT ONLY AS A STARTING POINT, AND YOU SHOULD LEARN A BETTER WAY AS YOU GET MORE INTO USING UBUNTU.
[/B][/I]***THIS SCRIPT COMES WITH NO WARRANTY OR GUARANTEE OF ANYTHING. THOUGH I WILL HELP ANYONE WHO ASKS FOR IT NICELY IN ANY WAY I CAN.***

Hello Everyone.
  I understand how frustrating it can be to come from an OS like Windows, to something as excellent as Ubuntu.
  Your so used to Windows that it all seems very new and frightening.
  Well, Don't give up!!!
  It gets easier, and along with that it gets BETTER than Windows ever got.
  You'll never want to go back...kinda like...nahh i better not :p
  
  Anyway...
  In this article, I'm going to show you how you can backup your entire system.
  Not only that, but I'm going to show you how you can create a BASH script to do it for you, and how to add said script to the system PATH so that all you need to do is-
  
[LIST=1]
[*]Open A Terminal
[*]Type in " backup " (without the quotes)
[*]Hit Enter
[*]Giggle as Ubuntu does all the crazy stuff for you
[/LIST]
   So...How can it be THAT easy you might ask?
  Well, First off lets give a little to bash scripts.
  Bash scripts are basically just bits of code that are run in bash (command-line).
  When a bash script is run, it runs the commands as if the user were typing them in his or her -self. Line-by-line.
  Bash scripts can be anything from backing up the system, to wiping it out ;)
  But there are plenty of tutorials on the word wide web that will give plenty info regarding them.
  I'm here to show you a practical use for bash scripting, while showing you how to backup your system.
  I will also add in a restore script later on, in this thread. SO KEEP YOUR EYES OPEN on this one, cause I'll be adding updates and stuff to make her better (yes, my script is a she)
  Okay, so....:popcorn:
  
  What you need to do first is make the script.
  I have taken the liberty of writing the script(which I use for myself when I need to backup my system for whatever reason) and here she is-
  
  ```

  #!/bin/bash
  # Print Pre-text Containing Script Version Info & Creator Info (please leave current credits intact and add a separate line if you modify the script & pass it on)
  clear
  echo "Backup Script"
  echo ""
  echo "V.1.3"
  echo ""
  echo "Created by Lonewaster@gmail.com"
  echo "VIVA LA LINUX!!!"
  echo ""
  read -p "Please Press ENTER To Continue..." waitForEnter
  # Alert The User & Wait 3 Clicks
  echo "BACKUP Initiating..."
  echo ""
  sleep 3
  # Ask The User For Their Current Username (For Backup File Placement & Permissions)
  read -p "What username are you currently logged into? (must be IDENTICAL to username you are currently using!!): " backupUser
  # Backup Entire System To the Specified User's homedir/backup.tgz (../../ included so script can be put in subdirectory)
  sudo tar cvpzf ../../home/$backupUser/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media /
  # Upon Completion Of Backup, Alert The User
  echo ""
  echo "BACKUP Complete!"
  echo ""
  # Then Set backup.tgz File Privilidges So That The Specified USER Can Read, Write & Execute
  echo "Setting Backup File Privilidges..."
  echo ""
  # Set The File's Group As the Specified $backupUser
  chgrp $backupUser ../../backup.tgz
  # Set Read, Write & Execute Privilidges For The Owner (root)
  chmod u+rwx ../../backup.tgz
  # Set Read, Write & Execute Privilidges For The Specified Group ($backupUser)
  chmod g+rwx ../../backup.tgz
  # Alert The User, Wait 3 Clicks & Terminate The Script
  echo "TERMINATING..."
  echo ""
  sleep 3
  # End Of Backup.sh Script
  
```Now, I don't really need to explain much because the comments in the script (anything on a line after a # ) tells you what is happening as it is happening.
  But for anyone who wants a little bit more info, here are the BASH commands explained.
  
  #!/bin/bash   -   tells the computer that the following code is bash script. so that the computer knows how to deal with it.
  
  clear   -   clears the terminal window of all text so that it looks nice and clean and organised.
  
  echo   -   this function tells the computer to print something on the screen. in the terminal window. 
  ```
echo "Hello World!" 
```The above code would show "Hello World!" on the screen.
  
  read   -   this funtion prints some text and then takes some input and stores it in a variable.
  the first time our script uses it is just to wait for the user to press enter. There is probably a better way to do this, but I used this way for simplicity.
  
  ```
read -p "What is your name? " strName
```The above code will ask the user for their name, and then store it in the variable strName. Then, if you wanted the program (or script) to print the person's name, you would put this after the above code-
  ```
echo "Hello $strName"
``````
read -p "What username are you currently logged into? (must be IDENTICAL to username you are currently using!!): " backupUser
```We use this bit to get the username that the user is currently logged into and stores it in a variable (backupUser) so that we can place the backup.tgz file in the correct directory and set the user's file permissions. Once again, there is probably a better way to do this (and I would like to invite anyone to give it forth) but I just went with this for simplicity.
  
  ```
sudo tar cvpzf ../../home/$backupUser/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media /
```This is the good part. This tells the computer to basically copy the entire file system into a file in the given username's home folder called backup.tgz and compress it.
  The extra parts at the end of the command (--exclude=/media ... etc ...) tells the program we are using NOT to copy certain folders. This is because we don't need to backup these folders.
  For example, we don't need to backup /media because that is CDs,DVDs, etc.. That are in the computer.
  
  ```
chgrp $backupUser ../../backup.tgz
```This little snippet changes backup.tgz's group to the username that was inputted earlier, allowing us to run the following command to give that user Read, Write & Execute privilidges.
  
  ```
chmod g+rwx ../../backup.tgz
```This bit sets the file permissions to allow the file's group to Read, Write & Execute.
  The group has already been changed with our *chgrp *command (shown above this bit of code).
  I'm not sure that this bit is necessary but I chose to add it in anyway.
  If anyone of more experience in this field has any say for this part, then please- go ahead.
  At the very least, this gives newer users an introduction to useful bash commands...though they are all useful at some point.
  
  ```
chmod u+rwx ../../backup.tgz
```This bit sets the file permissions to allow root to Read, Write & Execute. This isn't really necessary...but neither is drinking whisky- but I still love to do it!!
  
 Finally, We need to edit environment variables so that we can just type "backup" in a terminal (no quotes) to run our script.
  Firstly, type the following in a terminal-
  ```
gedit /etc/environment
```  This will open the text editor with your PATH environment variable.
  Now, my path looked like the following(and yours should be something similar)-
  ```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```  This contains a list of places that contain binary programs and scripts.
  For example, when you type in *gedit file.txt* ubuntu checks in these folders for the program called gedit and then (if it finds it) uses that program to process file.txt.
  
  Now, you need to add in the directory your script is in for this to work.
  What I have done on my laptop is make a folder in */home/billy/* called *bin *(*/home/billy *is my home directory, yours will be */home/yourUsername/ *).
 So click n *PLACES *in your toolbar, then click on *HOME FOLDER. *This is where you need to make your personal *BIN* folder. You can call this folder whatever you want, but I would call it *bin* for convention.
 Add the following to the end of your *PATH* variable that you have open in your text editor. Add it after all the other folders, but before the closing "-
 ```
:/home/**username**/**bin**
``` Where **username **is the username you use to log in to your ubuntu account when you turn on your computer & **bin **is the folder you just created in your home directory.
 The file that you have open in your text editor should now look something like this-
 ```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/**username**/**bin**"
``` Once again replacing **username** with your login username & **bin** with the name of the folder you have just created in your home directory.
 
 Now, finally, all you need to do is edit your *.bashrc* file.
 Type the following in a **NEW** terminal window-
 ```
gedit .bashrc
``` This will open a new text editor window with the contents of your *.bashrc* file.
 
 All you need to do is add the following to the bottom of the open file-
 ```

 # set PATH so it includes user's private bin if it exists
 if [ -d ~/bin ] ; then
     PATH=~/bin:"${PATH}"
 fi
 
```-EDIT-
To make sure the script can be run, open a terminal and *cd *to the directory that the *backup* script is in. Run the following command to make it executable.
```
sudo chmod +x backup
```You will need to set +x for all scripts you make, as this is to set it as an EXECUTABLE FILE.
-EDIT-

Now SAVE & CLOSE the text editor and any other windows you might still have open from the previous exercise.
 
This means that whenever you wish to backup your system, all you have to do is open a terminal window and type the following before hitting **ENTER**- 
```
backup
```***VOILA!!***
Test it out!
Hopefully, once the script has finished running, there will be a file (of significant size) called ***backup.tgz*** in your home folder (which, in my case, is */home/billy/* ).

And that's it!
Now just run backup whenever you wish to back up your system.
You can also now add a button to your system toolbar that is linked to this script, just by making it run *"backup"* !!!
 
  For more information on these commands, check out the forum and the rest of the ubuntu community for tutorials, examples and other helpful stuff.
  
  I hope that this has been of some use to someone...
  Please feel free to comment and criticise :D
  As I said before, I will write a ***restore*** script and put it in this thread, along with a similar explanation of it line-by-line.
  
  For those who wish to know, I plan to add the ability to let the user choose which folders (if any) to exclude.
  
  Anyway, Thanks for reading and I hope it helps you with your endeavours.
  
  !!! VIVA LA LINUX !!!
  
  lonewaster

---

### Post by lonewaster on 2010-03-05
I know it's only been a few hours, but I got bored so I added the ability for the user to choose the exclusions(folders that he/she DOESN'T want added to the backup.tgz).

I will explain and then provide you with a copy of the entire script, so you can either learn how to do it yourself, or just copy & paste into a file...but that's the lazy way! :P

[B]WARNING: IF YOU DO NOT UNDERSTAND WHICH FOLDERS SHOULD.SHOULDN'T BE INCLUDED IN A BACKUP, THEN JUST STICK WITH V.1.3 (THE SCRIPT IN MY FIRST POST ABOVE THIS ONE) AS IT DOES IT ALL FOR YOU!
-BACKING UP FOLDERS THAT AREN'T REALLY NEEDED CAN RESULT IN UNFORSEEN PROBLEMS & AN EXCESSIVELY BIG BACKUP.TGZ FILE!!-
[/B]
Okay, so...
Remember the following line from our old V.1.3 ?

sudo tar cvpzf ../../home/$backupUser/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media /

Well, all we need to do is replace that with the following-
```

# Backup Entire System To the Specified User's homedir/backup.tgz (../../ included so script can be put in subdirectory)
echo "Enter any directories you want to exclude from the backup.tgz"
echo "Syntax: --exclude=/folder"
read -p "Please enter them now, each separated with a space: " strExclusions
# Ask the user for a list of folders in the root directory to exclude from the backup.tgz
# And then backup the system, excluding all the folders the user chose (which are saved in $strExclusions)
sudo tar cvpzf ../../home/$backupUser/backup.tgz $strExclusions /

```Now, although I have explained this in the comments (anything on a line after a # ), I will go into more depth.........

Okay, well firstly I have already explained the *echo *function, and it just prints stuff on the screen ;)
I also explained the use of *read* in the last post. All it does is prints something on the screen(just like *echo*) and then places whatever the user types in in the specified variable(in this case *$strExclusions*).
What I have done is use *echo* to explain to the user ***HOW*** to specify what folders to exclude.
This is saved in the *$strExclusions* variable, which is then passed to the computer in the backup process-
```
sudo tar cvpzf ../../home/$backupUser/backup.tgz $strExclusions /
```Well...that's it!
If you are having trouble with any of the commands used here, then check my first post and if you are still finding it hard then either google it, check the rest of the forums or reply to this thread and I will try and help!

Finally, Here is the entire script for those of you who came here for a copy & paste job.

```

#!/bin/bash
# Print Pre-text Containing Script Version Info & Creator Info (please leave current credits intact and add a separate line if you modify the script & pass it on)
clear
echo "Backup Script"
echo ""
echo "V.2"
echo ""
echo "Created by Lonewaster@gmail.com"
echo "VIVA LA LINUX!!!"
echo ""
read -p "Please Press ENTER To Continue..." waitForEnter
# Alert The User & Wait 3 Clicks
echo "BACKUP Initiating..."
echo ""
sleep 3
# Ask The User For Their Current Username (For Backup File Placement & Permissions)
read -p "What username are you currently logged into? (must be IDENTICAL to username you are currently using!!): " backupUser
# Backup Entire System To the Specified User's homedir/backup.tgz (../../ included so script can be put in subdirectory)
echo "Enter any directories you want to exclude from the backup.tgz"
echo "Syntax: --exclude=/folder"
read -p "Please enter them now, each separated with a space: " strExclusions
# Ask the user for a list of folders in the root directory to exclude from the backup.tgz
# And then backup the system, excluding all the folders the user chose (which are saved in $strExclusions)
sudo tar cvpzf ../../home/$backupUser/backup.tgz $strExclusions /
# Upon Completion Of Backup, Alert The User
echo ""
echo "BACKUP Complete!"
echo ""
# Then Set backup.tgz File Privilidges So That The Specified USER Can Read, Write & Execute
echo "Setting Backup File Privilidges..."
echo ""
# Set The File's Group As the Specified $backupUser
chgrp $backupUser ../../backup.tgz
# Set Read, Write & Execute Privilidges For The Owner (root)
chmod u+rwx ../../backup.tgz
# Set Read, Write & Execute Privilidges For The Specified Group ($backupUser)
chmod g+rwx ../../backup.tgz
# Alert The User, Wait 3 Clicks & Terminate The Script
echo "TERMINATING..."
echo ""
sleep 3
# End Of Backup.sh Script

```***REMINDER: ***If you are just copying & pasting you will still have to run the *chmod +x backup.tgz* command to make it executable.
That's all...

I will no doubt make more additions and improvements, but for now I need to get some sleep. Got a date tomorrow! (and we all know a date for a geek is somewhat of a rare occurrence :p )

Until then.........

***!!! VIVA LA LINUX !!!***

lonewaster

-EDIT- 
Remember that if this helped you AT ALL, then PLEASE reply and let me know!
Also give me any ideas or criticism you have, too.
I welcome it all.
Cheers!
-EDIT-

---

### Post by hoopoo on 2010-03-05
I have been looking for a wile now on how to back up ubuntu.
with no luck, after formating the wrong drive
I was thinking  ubuntu needs a backup. 

How do I restore the backups.


I have been looking a backup 
in case I do some thing well stupid.8-[


And thanks for taking the time to 
help us all and share your code.:D

---

### Post by isee on 2010-03-05
:KS

This is excellent for someone like me!  Thanks lonewaster!

---

### Post by oldmankit on 2010-03-06
> **hoopoo said:**
> How do I restore the backups.
It depends how much you want to restore.  If you accidentally delete a file or directory, it's very easy to restore.  If you follow lonewaster's detailed instructions, you'll have a file called backup.tgz.  That is a compressed file, like windows .zip files.  Open backup.tgz using 'fileroller', find the directory or file that you want to restore, and extract them to wherever you want to put them.

If you have a more serious error and screw up your whole system, lose all your files, your harddrive, whatever, it's a bit harder, but not too hard!  Find an Ubuntu installation CD, make a fresh installation.  You then just need to extract the entire contents of that backup.tgz file to your new installation.


On a related note (and I don't want to detract from the great instructions given here), there is a way to emulate Apple's 'time machine'.  It will take snapshot backups of your harddrive whenever you choose.  It does not require backuping up every single file every time, but it only looks for the files that have been changed since your last backup.  Full details here:  [http://blog.interlinked.org/tutorials/rsync_time_machine.html](http://blog.interlinked.org/tutorials/rsync_time_machine.html)

---

### Post by isee on 2010-03-06
Please I need this answered.  Will this back-up my Filesystem as well as my LOCAL DISK(which has my C:\ and D:\  drives)?

I can back up to an external hard drive and restore on a new disk if I have a hard drive failure?  It will copy my partitions?

Thanks!

---

### Post by Enigmapond on 2010-03-06
Thank you for this brilliant script!:D

---

### Post by hoopoo on 2010-03-06
Thanks oldmankit for the replay and the help. 
lonewaster your script seams to be jest 
what I was looking for.

If some thing like this was built into ubuntu 
it might help so many others to fix there 
systems and save frustrations not only
for the end user but the ones helping 
in the forums.
I know she (lonewaster script)
would have saved alot if my hair from being 
riped out by the root trying to get a "VM"
up and running again a couple of days ago.

PS. keep the help coming lonewaster;)

---

### Post by mikewhatever on 2010-03-06
This work is [s]not original[/s] inspired by another howto, and the OP should give credit where it's due.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

------------------------------------------------------------------------------------------------------------

> **isee said:**
> Please I need this answered.  Will this back-up my Filesystem as well as my LOCAL DISK(which has my C:\ and D:\  drives)?

I can back up to an external hard drive and restore on a new disk if I have a hard drive failure?  It will copy my partitions?

Thanks!

No. The mount directories are excluded so that the backup will not go into Windows. Furthermore, restoring to another hdd takes more then just copying the files. I recommend you look at Clonezilla.

---

### Post by HermanAB on 2010-03-06
Hmmm, it is mostly fresh ex-Windows users that are looking for backup scripts.  Dervish and Rbackup are pretty good.

However, old hands realize that it is a waste of time backing up everything since after disaster striked, you would probably want to install the latest version of Ubuntu, not a 3 year old multiple updated semi messed up system from a months old backup...

Soooo, how do old hands do it? Read the rsync man page (there are examples at the end) and then craft a one liner in a desktop launcher to backup your data only - forget about the rest of the system, it doesn't matter.

---

### Post by 1915flyer on 2010-03-06
Thanks for the backup script.

In looking through the resulting backup file (backup.tgz) on my computer from the original script, I noted that about 800M of the 3.1G backup.tgz file is backup.tgz. This is in spite of the instructions in the script to exclude it.

I also happened to be watching while the script was running (only occasionally, I have to admit) and saw a long pause when backup.tgz was shown as being added to the file. My thoughts were that it had to run through it anyway but would not add it, but that was apparently incorrect.

The script crashes when run from the bin directory.

---

### Post by JKyleOKC on 2010-03-06
> **1915flyer said:**
> In looking through the resulting backup file (backup.tgz) on my computer from the original script, I noted that about 800M of the 3.1G backup.tgz file is backup.tgz. This is in spite of the instructions in the script to exclude it.While I've not tried running the script yet, I did note that the --exclude option for backup.tgz had "/" in front of it. This makes it an absolute path name, so it excludes a file named backup.tgz located in the root directory "/" but the actual backup file isn't there. It's in the home directory and thus isn't excluded.

I think there are several options for fixing this. Simplest is to remove the "/" from that --exclude option so that any file named "backup.tgz" is excluded. Next is to add "$HOME" in front of the "/" to change the location to the user's home directory. Another would be to change the location to put the actual file into the "/" directory but this would require running the script with sudo since only root has write permission there.

I did something similar when tweaking my configuration files, to save just the /etc directory so that I could easily roll back in case I messed things up (which I did several times). Here's my version:

```
#!/bin/bash
#
# backs up configuration files...

NOW=`date +%Y%m%d%H%M`
sudo tar cvpzf /home/jim/bak-$NOW.tgz /etc >/home/jim/list.txt
exit 0
```
Using the "NOW" temporary variable prevents overwriting older copies, and redirecting the output to "list.txt" creates a list of all that's backed up. Including "sudo" in the script makes it ask for the password when run.

Backing up is a good idea, even though you may never want to restore a year-old system exactly. If you've installed extra packages such as VirtualBox, or tweaked firewall settings, you definitely need to save at least /etc in addition to your home directory if you expect to get back all of your customizations...

---

### Post by lonewaster on 2010-03-06
Okay, 
First off- thanks very much for all the comments and constructive criticisms. My self-esteem just jumped up a fair little bit =)
And, as pointed out, the commands used in the script I learned from the following post-
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
by the ubuntu forums user ***Heliode*** and, as pointed out, credit is due- im sorry for forgetting that part ***Heliode***.
I can assure you all that the script is entirely my own creation, but I learned how to backup/restore my system using ***Heliode***'s tutorial.
So, credit to him/her and credit to you (**mikewhatever**)  for pointing it out to me, athough I do feel that saying "this work is **not** original" is a bit strong as the script IS original, but the commands were learned from somewhere else. I wrote the script & tutorial myself.
There's always something missing, eh?
Okay, 
I'm in the process of writing *v.1* of the *restore* script(which I will put in here asap), whilst ALSO addressing the issue raised about excess size of the ***backup.tgz*** file- I will do something about it.
As far as the better, more efficient ways of backing up- yes, I would suggest you learn to use them, but if you are new and, as I stated initially, 'frightened' by this new, amazing being called ***ubuntu***, then I would recommend you start by using this until you find your feet.
***NOTE: ***This is also intended as an introduction to automating processes and adding things to the ***PATH*** environment variable.
As for the catch-22 of using this method, reinstalling & upgrading ubuntu, then restoring- one can use *V.2 *of my/your own version of the script to selectively **exclude** folders/files to **ONLY** backup your personal files, emails, etc... 
**PLEASE LET ME KNOW IF I'M WRONG IN THINKING THIS, BY THE WAY!!**
 
Finally, I'm thinking of adding in a selection ability to pick whether you just want to do a standard backup, personal files backup, system files backup, etc...
Do you all think this would be good?
*Input is greatly appreciated!!*
 
Once again, **all** input is appreciated. Ideas or creative criticism, I will take it ALL on board.
Hope to continue helping you, check back later for my restore script(I will have it online within 24 hours- got dinner out tonight)
 
**!!! VIVA LA LINUX !!!**
 
lonewaster ;)

---

### Post by mikewhatever on 2010-03-06
> **lonewaster said:**
> ...
So, credit to him/her and credit to you (**mikewhatever**)  for pointing it out to me, athough I do feel that saying "this work is **not** original" is a bit strong as the script IS original, but the commands were learned from somewhere else. I wrote the script & tutorial myself.
...

Fare enough, I'll edit my previous post to 'inspired by'.;)

---

### Post by Penguin Guy on 2010-03-06
This backup script is badly made, will not always backup files as expected and creates major security risks. Keep in mind, backup scripts are serious ****, making the slightest mistake could loose someone their files, which could land you in serious legal trouble. You should learn more about programming before you publish things like this.

Sorry, I don't mean to be rude, but this could cause serious damage.

---

### Post by lonewaster on 2010-03-06
> **Penguin Guy said:**
> This backup script is badly made, will not always backup files as expected and creates major security risks. Keep in mind, backup scripts are serious ****, making the slightest mistake could loose someone their files, which could land you in serious legal trouble. You should learn more about programming before you publish things like this.

Sorry, I don't mean to be rude, but this could cause serious damage.

Please explain so I can fix the issues!
I mean...I set the backup script so that it would set the file's group and change the file permissions...so is it just a risk by having a copy of certain 'files', you mean?
The way I see it, anyone worrying about their security would probably have better knowledge than the need to use this script anyway...I mean, I've said that it's aimed at first-timers as a kind-of tutorial and birth into the linux world or works..
But please, let me know and I will fix / appropriately warn people :)

**mikewhatever**: thanksmuch ;)

okay, well...here it is. As promised.
the* restore* script !!
Once again, credit to **Heliode** for his/her tutorial that taught me how to do this. And credit to me for writing the 'tutorial' and script :)

[I]**REMEMBER: ALWAYS RUN YOUR NEW **backup **AND **restore [B]SCRIPT AS ROOT!
NOTE: TO GET ROOT, I ALWAYS USE THE COMMAND-
[/B][/I]```
sudo -i
```***ALTHOUGH THERE ARE MOST LIKELY BETTER WAYS, WHICH I INVITE OTHERS TO POST HERE FOR THE REST OF US :P***

Here's the V.1.2 of the *restore* script (yes, I said V1.**2** ! I decided to fix up the original a little bit before uploading it =)

```

#!/bin/bash
# Print Pre-text Containing Script Version Info & Creator Info (please leave current credits intact and add a separate line if you modify the script & pass it on)
clear
echo "Restore Script"
echo ""
echo "V.1.2"
echo ""
echo "Created by Lonewaster@gmail.com"
echo "VIVA LA LINUX!!!"
echo ""
read -p "Please Press ENTER To Continue..." waitForEnter
# Alert The User & Wait 3 Clicks
echo "RESTORE Initiating..."
echo ""
sleep 3
# Ask the user for their ubuntu username so that the script can fetch the batch file from their home directory (needed as script is run as root)
read -p "What username are you currently logged into? (must be IDENTICAL to username you are currently using!!): " restoreUser
# Restore the system using the backup.tgz file located in the users home directory, which is selected using the $restoreUser variable we just set from the user input
tar xvpfz /home/$restoreUser/backup.tgz -C /
# Upon Completion, Alert The User
echo ""
echo "RESTORE Complete!"
echo ""
echo "Please REBOOT Your Computer To Complete The Restore."
echo ""
echo "After A Few Days, I Recommend You Run Another Backup, To Keep It Fresh!"
echo ""
# Alert The User, Wait 3 Clicks & Terminate The Script
echo "TERMINATING..."
echo ""
sleep 3
# End Of restore Script

```All the commands used in this script are pretty much the same as in our *backup* script from before, except the **tar** command, which has been edited to UNLOAD files from, instead of PACKING them into, the backup.tgz file (so to speak).

Also, I upgraded the *backup* script a little to allow for some user choice in what happens.
Here she is, in all her glory (and insecurities and what not :D )-
```

#!/bin/bash
# Print Pre-text Containing Script Version Info & Creator Info (please leave current credits intact and add a separate line if you modify the script & pass it on)
clear
echo "Backup Script"
echo ""
echo "V.2.3"
echo ""
echo "Created by Lonewaster@gmail.com"
echo "VIVA LA LINUX!!!"
echo ""
read -p "Please Press ENTER To Continue..." waitForEnter
# Alert The User & Wait 3 Clicks
echo "BACKUP Initiating..."
echo ""
sleep 3
# Ask The User For Their Current Username (For Backup File Placement & Permissions)
read -p "What username are you currently logged into? (must be IDENTICAL to username you are currently using!!): " backupUser
echo "This version allows you to select WHAT kind of backup you wish to do."
echo "Just type the number corresponding to the type you want, and hit enter."
echo "[1] Standard backup (full system, standard exclusions. this will restore you computer to exactly as it is now)"
echo "[2] Standard backup with optional exclusions (full system, you choose what to exclude from the backup)"
echo "[3] Personal backup (ONLY backup personal files & folders, excludes system files. this will ONLY restore your personal files & folders)"
echo ""
read -p "So, What backup type would you like? (1 / 2 / 3): " backupType
if [ $backupType = 1 ] 
    then
    # if the user chose to just do a standard full system backup
    # Tell him/her what the standard exclusions are...
    echo "Standard directory exclusions are-"
    echo "--exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media"
    echo "If you want to add/remove any directories from this list, then use backup type [2]"
    strExclusions="--exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media"
    # Then store the standard folder exclusions in our strExclusions variable
    strBackupFolder="/"
    # And Set The folder we want to backup as the base directory (root)
elif [ $backupType = 2 ] 
    then
    # if the user chose to pick their own exclusions...
    # Ask the user for a list of folders to exclude from the backup.tgz
    echo "Enter any directories you want to exclude from the backup.tgz"
    echo "Syntax: --exclude=/folder"
    read -p "Please enter them now, each separated with a space: " strExclusions
    # And store them in strExclusions
    strBackupFolder="/"
    # And Set The folder we want to backup as the base directory (root)
elif [ $backupType = 3 ] 
    then
    # if the user chose to just backup their personal files...
    # Tell him/her what folders will be excluded...
    echo "This backup type will ONLY backup the selected username's /home/ folder. This contains your Documents, Desktop, Video, Music, Pictures, Etc.. Folders"
    echo "If you would rather choose your own folders to exclude from the backup, then use backup type [2]"
    echo "If you would rather just backup the entire system, then use backup type [1]"
    strExclusions=""
    # Set no folder exclusions because we are only telling it to backup ONE folder (/home)
    strBackupFolder="/home/$backupUser"
else
    # if a valid backup type wasn't entered then alert the user
    echo "Incorrect backup type selection (1 / 2 / 3)..."
    echo "Please try again!.."
    echo ""
    echo "TERMINATING..."
    echo ""
    sleep 3
    exit
    # and terminate the backup script
fi
# And if everything went okay, then backup the system, excluding all the folders the user chose (which are saved in $strExclusions)
# We use the $strBackupFolder so that we can change the directory that is to be backed up, without having to use this command more than once(for the new type [3] backup!!)
tar cvpzf ../../home/$backupUser/backup.tgz $strExclusions $strBackupFolder
# Backup Entire System To the Specified User's homedir/backup.tgz (../../ included so script can be put in subdirectory)
# Upon Completion Of Backup, Alert The User
echo ""
echo "BACKUP Complete!"
echo ""
# Then Set backup.tgz File Privilidges So That The Specified USER Can Read, Write & Execute
echo "Setting Backup File Privilidges..."
echo ""
# Set The File's Group As the Specified $backupUser
chgrp $backupUser ../../backup.tgz
# Set Read, Write & Execute Privilidges For The Owner (root)
chmod u+rwx ../../backup.tgz
# Set Read, Write & Execute Privilidges For The Specified Group ($backupUser)
chmod g+rwx ../../backup.tgz
# Alert The User, Wait 3 Clicks & Terminate The Script
echo "TERMINATING..."
echo ""
sleep 3
# End Of backup Script

```If you want to know whats happening on a line-to-line basis, then just look at my comments (anything on a line after a # symbol).
There isn't **much** of a difference....just the user choice part.
This used a simple if/elseif/else statement, which are built like the following.
```

if [ this happens ]
then
do this code here
elif [ this happens ]
then
so this instead of the bit above
else
do this when none of the above criteria are met
fi

```What happens is first the code checks the first **if []** statement to see IF its true, then IF it IS then it does the code after that bit.
**elif** means **else if.  **so **otherwise IF[]** such-and-such is true, then do that little bit of code.
And we use an **else** statement for what happens if none of the other **if/elif** statement criteria are met.
**REMEMBER: GOOGLE IS YOUR FRIEND FOR ANY NEEDS, SO IF YOU STILL WANT TO LEARN MORE THEN GOOGLE IT AND CHECK THE REST OF THE FORUM!!!**

and, thx to **penguin guy** for pointing out potential security issues! so here's a warning for those who don't know better-
[B]WARNING: USING THIS BACKUP SCRIPT MAY CAUSE SECURITY ISSUES IN ITS CURRENT STATE, AND SO YOU ARE RECOMMENDED TO USE A SAFER SYSTEM IF YOU HAVE SOMETHING YOU WANT TO KEEP COMPLETELY SECURE, BUT FOR THOSE F YOU JUST STARTING OUT, UNLESS YOU HAVE LIKE NATIONAL SECRETS ON YOUR CMPUTER, THEN YOU SHOULD BE PRETTY SAFE! :P
I PROMISE TO WORK ON SECURING THIS SYSTEM!!
IF YOU WISH TO USE THIS SCRIPT & BE AS SECURE AS POSSIBLE THEN USE BACKUP TYPE [2] AND SPECIFY WHICH FOLDERS TO EXCLUDE FROM THE BACKUP, AND PREVENT ANY SECURITY ISSUES!![/B]
[B]
LEGAL NOTICE: I ACCEPT NO RESPONSIBILITY _WHATSOEVER_ FOR ANY SECURITY RISKS RAISED BY THIS AND ANY OF MY SCRIPTS. YOU USE THEM AT YOUR OWN RISK. 
THAT SAID, I GUARANTEE ANYNE USING MY SCRIPT THAT I WILL HELP WHEREVER POSSIBLE TO MAKE IT BETTER AND SAFER AND TO REPAIR ANY DAMAGE THAT MAY RESULT FROM THE USE OF (ALTHOUGH IF USED CORRECTLY THEN THERE SHOULDN'T REALLY BE MUCH OF A PROBLEM).[/B]

I'm not a big shell coder. I can when I need to, but I don't claim to be professional. 
I'm just a programmer in my spare time. If you have a better way to do things then i suggest you use it, as there is ALWAYS a better way to do something when it comes to programs.
There is ALWAYS a security risk, and with every fix there opens another backdoor.
This said I understand what it is like for people to change from windows to linux. (my mum and dad and sister were converted by me =D   ) and this and possibly other stuff I make/post will be aimed at that sort of group.
So long as you don't use this to backup anything you need to keep REALLY secure, or if you just create the backup and copy it to a CD/CDV then remove the file from your computer then I can see no real harm. 
BUT as I said- There is always a way into a system. And there is always someone who will be able to find their way in if they really want to.

Anyway...Its **1:18AM **here in bonny Scotland, so I shall return tomorrow probably.
But for now, I sleeps ;)

**!!! VIVA LA LINUX !!!**

lonewaster

---

### Post by lonewaster on 2010-03-07
To any new users wondering about how hard it is to get into making your **OWN** scripts in ubuntu, let me tell you this-
this is the **first** bash script I have ever put more than one line into.
I didn't know how to backup my system manually until I read **Heliode**'s tutorial thread.
**That's** how easy it is!
Just google for " ubuntu bash script tutorial " ( without the quotes ) and look for a beginners tutorial.
My advice would be to get a book (such as a For Dummies book or whatever) and use that as a **REFERENCE** for when you are actually programming.
I use a reference for **all** my programming languages. **[HTML/CSS/JAVASCRIPT/PHP/PERL/C++/BYOND]** and it makes a hell of a difference to my stress levels :P
Just persevere, and you can do _**ANYTHING**_ **!!!**

**!!! VIVA LA LINUX !!!**

*lonewaster*

---

### Post by Penguin Guy on 2010-03-07
> **lonewaster said:**
> Please explain so I can fix the issues!
I mean...I set the backup script so that it would set the file's group and change the file permissions...so is it just a risk by having a copy of certain 'files', you mean?
The way I see it, anyone worrying about their security would probably have better knowledge than the need to use this script anyway...I mean, I've said that it's aimed at first-timers as a kind-of tutorial and birth into the linux world or works..
But please, let me know and I will fix / appropriately warn people :)
Trust me, I have written my own backup script and there is a **lot** of stuff that can go wrong. Programs never work exactly as you expect. You really don't know what you're doing, at least put a warning on the front page:
> 
[COLOR="Red"]Warning: I cannot guarantee that this script will function as expected.
This script comes with no warranty, not even the implied warranty of fitness for a particular purpose. [/COLOR]


---

### Post by uRock on 2010-03-07
Shouldn't have to put a warning. Anyone with the smallest inkling of common sense would know that backups stand a chance of not working right, just look at the ones for MS.

---

### Post by lonewaster on 2010-03-07
yeah...I will put a warning on the main page.
The thing is man, as i said, i'm **not**, nor am I claiming to be, a professional programmer.
Anyone who wants something better can do so, and anyone wanting to keep their stuff more secure will no doubt have the ability to encrypt their files in a backup. Or at least the ability to learn how to do so.
This is just aimed at people who don't know any better or who, like my dad for instance, don't want to spend time learning a new OS from start-to-finish and just want it to "work".
I never claimed this to be flawless, but hell no script is completely without fault.

anyway, it's not as if anyone is going so sue **me**.
I have **nothing**. and i mean **NOTHING.**
So if you are thinking of suing me- think again. you will only cause yourself some significant financial loss.

I'd like you to give me a few examples of these problems you're talking about, and how you discovered them. Just for personal interest.

thx.

**!!! VIVA LA LINUX !!!**

*lonewaster*

---

### Post by Penguin Guy on 2010-03-07
> **lonewaster said:**
> yeah...I will put a warning on the main page.
The thing is man, as i said, i'm **not**, nor am I claiming to be, a professional programmer.
Anyone who wants something better can do so, and anyone wanting to keep their stuff more secure will no doubt have the ability to encrypt their files in a backup. Or at least the ability to learn how to do so.
This is just aimed at people who don't know any better or who, like my dad for instance, don't want to spend time learning a new OS from start-to-finish and just want it to "work".
I never claimed this to be flawless, but hell no script is completely without fault.

anyway, it's not as if anyone is going so sue **me**.
I have **nothing**. and i mean **NOTHING.**
So if you are thinking of suing me- think again. you will only cause yourself some significant financial loss.

I'd like you to give me a few examples of these problems you're talking about, and how you discovered them. Just for personal interest.

thx.

**!!! VIVA LA LINUX !!!**

*lonewaster*

Thanks, just didn't want some newbie thinking 'Hey, great, I have a backup program, now my computer is foolproof.'. Like I said, no offence meant.

Some of the main issues:
[LIST]
[*]Doesn't check if it has root permissions
[*]Doesn't check if they entered a valid username
[*]Changes the permissions on the backup
[LIST]
[*]What do you gain by changing permissions?
[*]The backup archive is open to anyone - minor security risk
[*]When you restore from the backup, the whole system is open to anyone - major security risk
[/LIST]
[*]The [FONT="Courier New"]sleep[/FONT] statements serve no purpose
[*]Probably want to look into excluding the [FONT="Courier New"]gvfs[/FONT] file
[*]Might want to look into [FONT="Courier New"][rsync]("apt:rsync")[/FONT] - it considerably speeds up backups
[/LIST]

Also, you are putting the backup in [FONT="Courier New"]~/backup.tgz[/FONT] and then excluding [FONT="Courier New"]/backup.tgz[/FONT] from the backup (not the same file). You really should make the backup at [FONT="Courier New"]/backup.tgz[/FONT]:
```
sudo tar cvpzf /backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media /
```
Then you won't have to worry about asking for a username either.

---

### Post by lonewaster on 2010-03-07
Thanks man, no offense taken.
No problem, I'm working on addressing they kind of issues now.
Thanks for the tipoff about the file location stuff- I had forgot to fix that bit.
And the sleep functions were really just an excuse to use them =P
Yeah I have been looking at other methods of backing up and also how to improve this script.
I changed the file permissions because the backup.tgz wasn't showing in my file browser unless I was set as root, and that fixed it. That's inevitably why I put the file in the home folder after that. It's going back to root now though.

As I said, I welcome ALL kinds of input, so long as it is meant for the purpose of improvement. Constructive, you know? I dislike people who diss on those who are trying to learn. After all, isn't that partly what open-source software is about? (allowing people to learn from it)

I will be adding a newer version of the script in a few days, with improved function and security.

**QUESTION: I'm thinking of adding a switch to allow the user to select an encrypted backup file. Good Idea? I figure that would secure it up a bit, and alongside my securer update it would maybe help move the script forward?**

[B]!!! VIVA LA LINUX !!!

[/B]*lonewaster*

---

### Post by lonewaster on 2010-03-12
Hey,
Just to let anyone who cares know that I'm going to implement rsync into the backup script and possibly an encryption method.
I will include an install script for those who just want to use it, not learn how it works or how to do it manually.
Shouldn't be long.
Cheers.
 
**!!! VIVA LA LINUX !!!**
 
*lonewaster*

---

### Post by AndyDeGroo on 2010-03-23
In reality backup should be task for root exclusively. Just for one reason - not all files in file system are readable by user and there may be important files left out.

It's ok for learning, but the best suggestion for newcomers from Redmond hemisphere would be to get GUI application like "Simple Backup Suite". Its package name is  sbackup and description goes like this:
> Simple Backup Suite is a set of backend backup daemon and GNOME
GUI frontends that provide a simple yet powerful backup
solution for common desktop users.

Backups can be written to local directory or remote servers using
GNOME VFS technology. A fine control is possible regarding what
folders and files to backup. Files can be excluded even with a set
of regular expressions. Regular backups can be scheduled.
do I have to say more?

Although the package is in universe section and not supported by Canonical it works great for common desktop backup tasks.
That may be _THE easiest_ way for those who come from windows environment.

Also no offense intended. Keep learning and share what you've learned. That's the real open-source spirit after all.

---

### Post by lonewaster on 2010-03-29
i agree- anyne who wants an easy way to backup should use the method in the post above this.
i will pst my updated bash script when i have worked on it,
thing is, i have been working on perl scripting lately, and haven't really had the need to write any bash.
i will update it, but as i said- i think anyone like my dad (who is coming from a windows or mac environment and wants their new OS to just 'work') should go with the application linked to by the poster above me ( AndyDeGroo )

thanks for all constructive criticisms and thankyous, it was nice to have people comment on some of my programming for once.
and AndyDeGroo - that **is** the spirit of open-source, and it is the spirit flowing through my veins.
to learn, to make, to improve, to better. it is my drug. and i am completely addicted.

so, if you want to see a new version of the backup bash script with a newer tutorial, then check back here over the next few weeks.
i just have to finish my perl IRC client that im making and then i will update the bash script stuff, maybe write a new one for something...

thanks again all

billy

---

### Post by lonewaster on 2010-04-08
i have rewritten this script using **rsync** and instead of continuing to post in this practically dead thread, i will put it in my package that i am making.
no name for it yet (not a DEFINITE name, anyway) but the package will consist of 
this backup + restore script
my installed package backup script
and more.
so keep an eye out on the beginner section.
and on [www.swedger.com](www.swedger.com) (my site) - i will be hosting it on there when it is ready for release.

---

### Post by lonewaster on 2010-04-26
i have created the first installment of my new toolkit. i am going to make a new thread for it, so just search the forums for ' Swedger-Toolkit ' (no quotes) and go there.

[http://swedger.com/swedgertoolkit-1.5.tgz](http://swedger.com/swedgertoolkit-1.5.tgz)   << direct download if you wanna look =)
make sure and read the new thread for info regarding the toolkit though!!

-darksider-

---

### Post by Penguin Guy on 2010-04-26
You should think before putting it under the GPL. I release all my work in the public domain because I want anyone to be free to use my work as they please.

---

### Post by lonewaster on 2010-04-26
yeah, a friend suggested the BSD license.
i might write my own, so i can perfect it for this particular package & purpose.
thanks for the input, what did u think of the program(s)/script(s) themself?
any ideas/suggestions are welcome.
i would also like to invite anyone who has scripts or programs they'd like to add into the toolkit to do so through me, that way it will be in the original and official version of SwedgerTK.
feel free to patch/upgrade/etc and lemme know, just remember and comment it and document what you're doing for users and for me so if i am adding it to a release i can understand it for implementation and possibly a little editing.

all content of swedger-toolkit version 1.5 (and earlier or later versions) are the sole property of their respective creator(s)/author(s) and their affiliates, swedgerdotcom(swedger.com) and it's affiliates and staff, and of darksider himself (original author of swedgerdotcom(swedger.com) **and **the Swedger Toolkit).
SwedgerToolkit and all relevant materials are subject to the relevant licensing information.
they are free to download, modify, distribute, patch, and host on websites - but ALL credits/comments must be left INTACT.
anyone who writes new content code/programs should submit it to me personally for validation and implementation.

---

### Post by Penguin Guy on 2010-04-26
Nice work making all those from scratch, really great programs, sadly the internals are lacking. Also, I think you've way overdone the amount of text on the hex-table page, no one is likely to use it if you're forcing them to keep that text in place.

---

### Post by lonewaster on 2010-04-27
> **Penguin Guy said:**
> Nice work making all those from scratch, really great programs, sadly the internals are lacking. Also, I think you've way overdone the amount of text on the hex-table page, no one is likely to use it if you're forcing them to keep that text in place.
PenguinGuy - thanks man, i appreciate the input. What do you think i could do to improve the internals??


i **totally** understand.
i am going to begin working on the new version tonight.
I will clean up the hex generator first, then i am going to improve the packup script and backup script.
I have posted a new thread to gather a list of files to block from the backup.
Stuff that messes up a system if replaced...like the sudo file.
i backed up a system using my app and replaced my /home/ folder with it and it kept giving me an "ICEauthority" error.
and i couldn't use 
```
sudo
```
because the file was obviously different, and the permissions were all messed up.
the idea is that if i can get a list of files that **shouldn't** under **any** circumstances be backed up/replaced/edited/etc... so i can program in a check in ever loop to prevent them being copied- and also so that if the user selects the standard **'auto'** backup it won't backup these files/kinds of files/etc...
I also would like to get a list of packages that are standard to ubuntu installs or that shouldn't be backed up/edited/replaced/etc.. for the same reasons as the files mentioned above.

i am reading up to try and figure out a nice way to package the toolkit... maybe a .DEB installer or just an automated-install script.. i dunno.
if anyone has any thoughts/ideas/contributions to this then post and let me know!!

**EVERYONE IS INVITED TO HELP OUT WITH MY TOOLKIT. IT IS OPEN-SOURCED FOR A REASON, SO IF YOU HAVE AN IDEA OR A SCRIPT/PROGRAM YOU THINK WOULD BENEFIT THE USERS AND THE PACKAGE ITSELF- PM ME NOW!!**

:guitar:

---

### Post by Penguin Guy on 2010-04-27
If you're going to package it, don't package it as a toolkit - package each program separately. As for the internals being ugly - I guess you just get used to writing pretty internals after reading a lot of code (use the source Luke). As for why the backup is failing - it's probably because you've changed the file permissions:
> **Penguin Guy said:**
> Some of the main issues:
[LIST]
[*]Doesn't check if it has root permissions
[*]Doesn't check if they entered a valid username
**[*]Changes the permissions on the backup**
[LIST]
[*]What do you gain by changing permissions?
[*]The backup archive is open to anyone - minor security risk
[*]When you restore from the backup, the whole system is open to anyone - major security risk
[/LIST]
[*]The [FONT="Courier New"]sleep[/FONT] statements serve no purpose
[*]Probably want to look into excluding the [FONT="Courier New"]gvfs[/FONT] file
[*]Might want to look into [FONT="Courier New"][rsync]("apt:rsync")[/FONT] - it considerably speeds up backups
[/LIST]

I have attached a patch - this patch will remove the [FONT="Courier New"]chmod[/FONT] and [FONT="Courier New"]chgrp[/FONT] statements. It will also remove the [FONT="Courier New"]-r[/FONT] option, and one of the [FONT="Courier New"]-v[/FONT] options from the rsync options (since they are repeats). The patch ends in [FONT="Courier New"].txt[/FONT] because Ubuntu Forums will not accept [FONT="Courier New"].diff[/FONT]s.

To make a patch: [FONT="Courier New"]diff -u old-file new-file >patch.diff[/FONT]
To apply a patch: [FONT="Courier New"]patch old-file patch.diff[/FONT] (this will overwrite [FONT="Courier New"]old-file[/FONT])

---

### Post by lonewaster on 2010-04-27
[B]*edit*

* PENGUINGUY *[/B]
*i believe it should be* the following to patch a file using a .diff-extension file :::
```

patch <original_file> <patch_file.diff>

```
i mean, i **could** be wrong, but i couldn't get **diff** to work, just showed me output in the terminal.
i used **patch** and now i have the fresh version.
*** PENGUINGUY ***

**I HAVE UPGRADED THE BACKUP SCRIPT'S VERSION TO v1.6 ---> THANKS TO PENGUINGUY FOR THE PATCH!!**

****edit**** 

woah, thanks man =)
you will be assigned the appropriate credit for this in the Documentation and in comments.
thanks for the hard work, friend!
i am currently looking at ways to improve my systems internals.
and also have some small changes to the hex generator that i will release tomorrow most likely.
i appreciate your input, and moreso, your contribution to the toolkit.
when i start working on the toolkit's section on the site, i will be sure and give you a page and a mention as a contributor !! =]

this is hwy i love ubuntu - freedom to mix and match, make and patch, meet and greet xD
and because of people like you, who are willing to criticize in a helpful manner and help to do what they think will make it better.
<3 ubuntu <3

---

### Post by lonewaster on 2010-04-27
i have released swedgertoolkit-v1.6 - just to do anyone who it concerns until v2 is released(which will be just as soon as i complete the restore script, along with the other stuff in COMING_SOON [comes with toolkit]
it can be downloaded from here-
[http://www.swedger.com/swedgertoolkit-1.6.tgz](http://www.swedger.com/swedgertoolkit-1.6.tgz)

the main parts of this update are-
[B]+++   PenguinGuy's BACKUP script permissions PATCH
+++   Logging system started. implemented for BACKUP and PACKUP scripts (infant stages just now, will improve with time.)
+++   See VERSION file(inside swedgertoolkit-1.6.tgz) for more 'what's new to this version'
[/B]
please let me know what you think, or if you have any suggestions or anything....
big thanks for Penguinguy as well (xD) for patching the **backup** script's permissions issues.

***-darksider-***

---

### Post by Penguin Guy on 2010-04-28
> **lonewaster said:**
> *i believe it should be* the following to patch a file using a .diff-extension file :::
```

patch <original_file> <patch_file.diff>

```
i mean, i **could** be wrong, but i couldn't get **diff** to work, just showed me output in the terminal.
i used **patch** and now i have the fresh version.
Ooops, copy & paste fail, sorry. Anyway, I'm glad the patch worked.

---

### Post by lonewaster on 2010-04-28
Yeah, me too.
I appreciate the input and - as always - if you can think of anything you'd like to see in STK or if you have any scripts/apps that you would like to add to it, then message me and let me know =)

i am currently working on a **working, *finished*** version of the RESTORE script.
Not much more to do for it to be completed, really.
I also have alot of ideas, contained in the COMING_SOON file [included in the toolkit] although, i have added a fair amount of new material since releasing v1.6.

[B]I would love to have some more people on-board as a sort of 'swedger-tk team' if anyone is interested?
[/B]though i will be making STK its own thread maybe tonight/or by tomorrow evening.
***v2*** is not very far away, so stay calm folks.

thanks again PenguinGuy. Much appreciated!! If you have any further material/ideas - don't hesitate to let me know!!

PEACE all

-darksider-

---

