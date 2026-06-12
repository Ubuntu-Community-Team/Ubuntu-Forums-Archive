---
title: "HowTo eject your CD drive from the keyboard"
date: 2008-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by autocrosser on 2008-01-06
HowTo eject your CD drive from the keyboard:

Ok--you've got unused keys on your keyboard now you are using Linux....Let's make use of some of them.

First...take a look at your /etc/fstab file. Down at the bottom of the file it will define your CD drive(s). Newer versions of Ubuntu (Edgy & newer) use /dev/sdx or /dev/scdx for your mounted removable drives----Dapper & older use /dev/hdx for them. Next---open a terminal & depending on your drive # type in:

eject /dev/scd(number of the drive)  or eject /dev/hd(number of the drive)   >return

If you just had a CD drive open up--congrats!!  If not, you have a drive that either has firmware too old or can't be used by eject.

Next: Let's try something--Type:  eject -t (/dev of the drive that opened)--your drive should have just closed--up arrow & try the command again--If your drive just opened with the -t command--you are one of the lucky ones!! (also try with the -T option, sometimes that will work).   Repeat the commands for any other CD/DVD drives you have, using the correct #'s for each one.


OK, we now know that the eject command will work your drive(s) from the terminal, now let's transfer that info to a keyboard shortcut. (look at the Terminal pic & the first pair of Config Editor pics at the bottom)

First thing--If you look at Menu>Preferences>Keyboard Shortcuts---You will find under "Sound" that F12 is used as "Eject" for Music Players---Fine, let's map your CD eject to F12.

Open Menu>System Tools>Configuration Editor.  Toggle the "apps" arrow & scroll down to Metacity. Toggle the Metacity arrow & look at the global_keybindings & keybinding_commands. We'll use keybinding_commands first.

Right-click on command_1- & select "edit key"----in the "Value" box type: eject /dev/(your main CD drive)--ok & then click on command_10--type: eject -t /dev/(your main CD drive)

This assumes you can't use eject -t to "toggle" your drive in & out--if you can "toggle" your drive--command_1 would be eject -t /dev/(your main CD drive)

Next we'll goto global_keybindings---Look for run_command_1 & right-click-edit key-in the "Value" box type F12 & then OK it.  Now you should be able to open your CD with the F12 key. Next goto run_command_10 & right-click-edit key-in the "Value" box type the key you want--I'll choose F11. Test again & the drive should close.

OK, you can open & shut you drive(s) from the keyboard--now for a slightly harder method........

We'll show you how to use only one key to open & shut your drive  (thanks for the script Rhubarb!!! His post:  [http://ubuntuforums.org/showthread.php?t=656674](http://ubuntuforums.org/showthread.php?t=656674) )

First we need to know if you only have one drive or more than one....

If you only have one:

Open Text Editor & paste the following:

#./bin/bash

tray_status=`cat .tray_status.sh`
if [ "$tray_status" == "Closed" ]
then
    eject
    echo "Open" > .tray_status.sh
elif [ "$tray_status" == "Open" ]
then
    eject -t
    echo "Closed" > .tray_status.sh
else
    eject
    echo "Open" > .tray_status.sh
fi

Save the file to your /home as tray_status.sh  (note that it matches the info in the script!!!)

Next open a terminal & chmod 755 /home/(your home)/tray_status.sh

chmod 755--The user has read, write and execute permissions; the group and others can only read and execute. 
That is the safest way to set permissions on the file.

Next, open up Configuration Editor. I have found that you can't bind this command to F12 (not sure, will need to do more checking).

So we are going to bind the command to F11.  I chose command_10, you can use command_1 & modify the rest of the keybinding to match your choice.

In any case, the command should be /home/(your home)/tray_status.sh
 Next we'll move to the global_keybindings. Under run_command_10, I used the the F11 key.

For more than one CD Drive:

You will need to modify the script if you have more than one CD drive--my script for my Main CD drive looks like:

#!/bin/bash

tray_status=`cat .tray_status1.sh`
if [ "$tray_status" == "Closed" ]
then
    eject /dev/scd1
    echo "Open" > .tray_status1.sh
elif [ "$tray_status" == "Open" ]
then
    eject -t /dev/scd1
    echo "Closed" > .tray_status1.sh
else
    eject /dev/scd1
    echo "Open" > .tray_status1.sh
fi

Note that you need to define the script & add the /dev you are controlling--in this case it is tray_status1.sh & /dev/scd1
Change the script to meet your needs--also make sure to chmod 755 the finished script.

Take a look at the second pair of pictures for what my Configuration Editor looks like.


Great!! you can now open & close your drive from the keyboard...If you have more drives just use your own keys for them.

Have fun with the easier way to use your drive!!!

For more info goto frodon's custom keyboard shortcut & you can customize your keys as much as you want!!!!

[http://ubuntuforums.org/showthread.php?t=79560]("http://ubuntuforums.org/showthread.php?t=42404")

---

### Post by nowshining on 2008-01-07
Woah, thanks man :) this is really really helpful and fun, congrats on finding this neat trick. 10/10 stars from me.

---

### Post by Rhubarb on 2008-01-07
If you want to be able to toggle your tray position with one command or key, then use my simple bash script here:
[http://ubuntuforums.org/showthread.php?t=656674](http://ubuntuforums.org/showthread.php?t=656674)
```
tray_status=`cat .tray_status.txt`
if [ "$tray_status" == "Closed" ]
then
	eject
	echo "Open" > .tray_status.txt
elif [ "$tray_status" == "Open" ]
then
	eject -t
	echo "Closed" > .tray_status.txt
else
	eject
	echo "Open" > .tray_status.txt
fi
```
You could save this script and bind it to F12.

---

### Post by autocrosser on 2008-01-07
Very nice script!! Mind if I add it to the HowTo with notes how to install/use it?

---

### Post by Rhubarb on 2008-01-07
Sure, no problem :)

---

### Post by autocrosser on 2008-01-07
Ok--I created one---looks like:

tray_status=`cat .tray_status1.txt`
if [ "$tray_status" == "Closed" ]
then
    eject /dev/scd0
    echo "Open" > .tray_status1.txt
elif [ "$tray_status" == "Open" ]
then
    eject -t /dev/scd0
    echo "Closed" > .tray_status1.txt
else
    eject /dev/scd0
    echo "Open" > .tray_status1.txt
fi

Opens my second drive--I'll make another & write up a addon to the Howto--I'll PM you with the final....

---

### Post by nowshining on 2008-01-08
a good deal is to have a dedicated script direcoty in ur home folder to keep all ones scripts in one place and  thanks for the scripts Rhubarb, it's abeit slower than before, but still useful.

---

### Post by nils234 on 2008-01-09
Hey, 

I'm using ubuntu 7.10 ( gutsy ). When I open the terminal and I type " eject " it opens my drive, no need for any other arguments. When I open the terminal and I type " eject -t "  it closes the drive. I thought I was just lucky and opened Applications > Other > Input Actions.

I made a new rule, called it " Eject DVD Drive " made a new " Trigger " , used F11, then made a new action " eject ". I click apply then ok, but when I press F11 nothing happens.

What am I doing wrong.

---

### Post by autocrosser on 2008-01-09
You need to try the eject -t twice---if eject -t will close the drive & then open it again you are in luck--you also might try eject -T (again twice).

I would really recommend Config Editor--you are adding rules directly to Metacity. I'm not sure what the requirements are for Input Actions. 

If you want a one key solution that we are sure works---use the script.

---

### Post by autocrosser on 2008-01-13
I have found the reason you can't bind the script version to F12. You need to first unbind F12 from Eject--look at Menu>System>Preferences>Keyboard Shortcuts & goto Sound>Eject. Highlight F12 & remove it. Eject will be replaced by the script we are using.

Then install the script as per above & you can use F12 :)

---

### Post by Rhubarb on 2008-01-14
Excellent!  :D

---

### Post by Les_Caesars on 2008-02-18
I know this is kind of a luxury, but how do you make the same Eject emblem that shows when you use Keyboard Shortcut's eject function, show when you use this method?

---

### Post by autocrosser on 2008-02-19
I'll say that I've not looked into that--I am sure that Eject calls the .png during operation......I might have some time to look into that this weekend--sounds like fun.

---

### Post by kaibob on 2008-09-02
> **autocrosser said:**
> OK, you can open & shut you drive(s) from the keyboard--now for a slightly harder method........

We'll show you how to use only one key to open & shut your drive  (thanks for the script Rhubarb!!! His post:  [http://ubuntuforums.org/showthread.php?t=656674](http://ubuntuforums.org/showthread.php?t=656674) )...


The eject command was updated today (09-02-08 ) so that the -T option now works properly. As a result, you can use one key to toggle a CD drive opened and closed with the following simple command:

```
eject -T
```

As explained by autocrosser above, you may need to identify the drive after eject if you have more than one.

---

