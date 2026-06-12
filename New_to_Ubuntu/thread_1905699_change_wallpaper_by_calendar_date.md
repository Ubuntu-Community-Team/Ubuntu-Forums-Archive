---
title: "change wallpaper by calendar date"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by Roger Norton on 2012-01-07
Hi,

I'm wanting to change my wallpaper daily, so that for each date a particular wallpaper is shown (I have scans of a old Farside desk calendar, with a cartoon for each day, and I want to show the right date for each day).

Any ideas how I might go about this (ubuntu 11.10)?

Thanks,

Roger.

---

### Post by grahammechanical on 2012-01-07
Ubuntu uses a script that keeps each background image on the screen for a set number of seconds and then the image changes to the next image in the list. The script has a start date which is midnight 4th August 2009.

I do not know how the script gets its time or how it counts. If it starts counting from the booting of the computer then it will be of no good for you. If the count began at midnight 4th August 2009 and some how uses the time and date of the BIOS then all you need to do is edit the script to point to your images and change the duration of the image to reflect the number of seconds in 24 hours. But this is all un-tested.

You will find the script at /usr/share/backgrounds/contest. It is called background-1.xml. Note that the background images are in /usr/share/backgrounds and not in the contest folder.

In 10.10 and 11.04 there were two slide shows on offer. The method was to create a second folder in /usr/share/backgrounds and put the additional background images in there along with a modified background-1.xml script. The name is not changed but the paths to the new images would be different.

I have copies of the scripts and background images for 10.10 and 11.04 and I can confirm that the scripts from 10.10 to 11.10 all start from 4th August 2009.

I suggest that you do not change the start date. You might try making a copy of the script and changing the duration timings and then using the modified script in place of the original script. In this way you might find out if the background image changes every 24 hours before modifying the script to point to your images. Save wasted effort.

Regards.

---

### Post by Roger Norton on 2012-01-12
Thanks,

the .xml file can be modified (using gksudo gedit in the terminal) so that the the background changed between wallpaper of my choice daily (see attached file - durations have been changed to 24 hours, but only some wallpapers have been changed).  

However the wallpaper doesn't change at midnight GMT (it did not change at all if the computer is running, and it changed before midnight if the computer was switched off, and then on again before midnight).

Also the images I am using have a different aspect ratio (1500x1300) from my screen (1600x900), and are shown truncated at the top and bottom, which cuts off the caption (if any).

Any thoughts on how to solve these problems?

---

### Post by Chronon on 2012-01-13
For the cropping, you could use ImageMagick's convert or mogrify to scale the images to appropriate dimensions for your screen.  No idea about the other issues.

---

### Post by Roger Norton on 2012-01-15
Thanks,

think I've sorted it:

date and time problem solution: change time and date in the .xml file to 1 AM Jan 1st of the current year (don't know how BST will affect this).  Background changes at midnight, but only if the computer is restarted.  Haven't added a full year's backgrounds yet though.

cropping problem: use a graphics programme to add a border - total image size with border 3200 x 2700, image size as before - the computer shrinks the image to fit the screen, and has better resolution than with a total image size of 1600 x 1350 and a half-size image.

.txt version of .xml file attached, in case anyone wants to use it.

---

### Post by Derek Karpinski on 2012-01-15
If you have it, could you please post, or PM me the far side with the head-hunters paddling down the Amazon one way, and the potato head looking tourists paddling the other way?  That one always made my day!

Thanks:D

---

### Post by Roger Norton on 2012-01-16
Don't remember that one.  The attached is as close as I get.

---

### Post by Derek Karpinski on 2012-01-16
HAHAHA! Close.....the one I'm talking about is 'Palmer' and his wife waving at the headhunters..........but this one still made my day.  Thanks! :D

---

### Post by trikster_x on 2012-01-16
There is a way to do it using a shell script and a program called cron. It may require you to rename your image files in a manner that will allow the script to pull the name up easily, but it will work much better than using the .xml file. I will work on the script for you when I have some time a bit later.

EDIT: Okay, so I worked up the script. The most reliable way to name your images will be by "month" and "day of month". I can also do it by day of the year, but that will take some script magic and mathemagics to compensate for leap years. If you don't mind renaming your files to Monthday.exttype(i.e. Jan16.jpg), then you can use the script as follows:

```

#! /bin/bash

bgImage=`date +%b%d`.jpg

gsettings set org.gnome.desktop.background picture-uri file:///path/to/your/$bgImage
```

Just copy paste this to a text file(naming convention says to use the .sh extension for shell scripts), set to executable in the properties menu, and run it. It will update your background to whatever file corresponds to that month and day.

To make it run automagically, you simply open a terminal and type:

```
crontab -e
```
It will ask you which editor you want to use, I personally use nano [option 2] then move your cursor down to the first empty line after the instructions and put in the following

```
0 0 * * * /path/to/script/here
@reboot /path/to/script/here
```

The first line will run your script at 0 minutes, 0 hours(12:00 am, midnight), every day. The second line will run the script every time the computer is restarted, that way if your computer is off at midnight, you still get the right image when you next boot up.

I can also make a script that would base the image on a 3 digit day of year file name, but that would take considerably more effort to compensate for a leap year. In that case you simply name files 001, 002, 003, ..., 366.

I hope this all makes sense. If not, just leave a reply and I will try to clear up any questions you might have.

---

### Post by Roger Norton on 2012-01-17
Hi trikster_x,

your suggestion doesn't appear to work (which is not to say that it doesn't).  

I set the background to an unchanging plain colour, so the xml file should not be active.

I created the shell script (changer.sh, attached below), and saved it in the same folder as the images, and made it executable.  I altered the image files to format MonthDate.jpg.  

I edited crontab as suggested, though I am unable to find the resulting file using the file search utility - the 2 crontab files (there is also an anacrontab file and a crontab folder, which is inaccessible) I have found do not contain the lines added, and when I entered crontab -e in a terminal a second time, no lines were shown.  It is possible I didn't save correctly the first time - I think I used the Ctrl-X command, and put Y when asked if I wished to save. I have attached a screenshot of a later terminal window, after I had entered crontab -e.

Please note that I am running ubuntu 11.10.

Any suggestions?

---

### Post by trikster_x on 2012-01-17
Your script isn't running because of one fatal error lots of people make. The space in the directory name /farside calendar. Terminal commands and shell scripts really hate spaces in directory and file names. I suggest you use something like farside_calendar, farside-calendar, or farsidecalendar. It's not that you can't use spaces, but your life will be far easier if you learn to use a character to represent a space or eliminate them completely(at least if you ever plan to familiarize yourself with shell commands). Otherwise you have to use quotes(i.e. /Pictures/"farside calendar"/Jan17.jpg) any time you try to use it in a terminal. Also, the first letter in the month in your image file name should be capitalized(just to make sure there are no problems). You can use the command "date +%b%d" in a terminal to see the formatting that the script uses, which is the first three letters of the month followed by the number of the day. 

```
gsettings set org.gnome.desktop.background picture-uri file:///home/roger/Pictures/cartoons/"farside calendar"/$bgImage
```

This should fix the problem as your directory is named right now. Try running it when you have modified the content and let me know if it is working for you(just set the background to one of the defaults). 

As for the crontab, I think that may just be that the save got messed up. Give it another try, it should look like the link at the bottom. Then just press ctrl+x, press Y, press enter.

Let me know if it works for you.

[http://imageshack.us/photo/my-images/688/screenshotat20120117111.png/]("http://imageshack.us/photo/my-images/688/screenshotat20120117111.png/")

---

### Post by Roger Norton on 2012-01-18
Hi trikster_x,

no joy I'm afraid.  Updated changer programme, crontab screenshot and background chooser screenshot attached.  Have tried the crontab with the farside calendar part of the changer programme address without inverted commas.

---

### Post by Derek Karpinski on 2012-01-18
Does the script run and work without crontab? Does your cron log show any errors.
 
I once made a cron job that queried gnome-screensaver, and I had to export the DISPLAY.
 
I think the thing to keep in mind is that cron runs without any knowledge of paths, env variables, etc.
 
See below for crontab, and script.
 
crontab:
```
#Keep external drive from spinning down by touching a file every 5 min
*/5 * * * * /usr/sbin/no_sleep.sh > /dev/null 2>&1
```
 
script:
```
#!/bin/bash
# Script to keep external drive from spinning down
export DISPLAY=:0.0
scnsav=$(gnome-screensaver-command -q | grep -wc inactive)
diskmounted=$(mount | grep -wc public)
if [ $scnsav -gt 0 ]
then
   if [ $diskmounted -gt 0 ]
   then
      touch /home/public/.nosleep
   fi
fi
```

---

### Post by trikster_x on 2012-01-18
> **Derek Karpinski said:**
> 
I once made a cron job that queried gnome-screensaver, and I had to export the DISPLAY.

This is exactly what I was going to reply with a bit earlier, but I was pressed for time and couldn't post right away. I was running the script on my test machine which has cron set up with a bit of code so I don't have to do the export in-script. I didn't notice it because I added that bit of code to my test machine a few years ago and my screenshot came from me making a cron job on my laptop(which did not have that code because I very rarely run any cronjobs on it). That's why it worked fine while I was testing, but not when you used it.

So, the fix is simple enough, and there are a couple ways to do it.

Easiest way to address cron scripts that need to have a display specified, if you are running a single monitor:

```
XAUTHORITY=~/.Xauthority
DISPLAY=:0.0
```

copy pasta that as the first line of code in your crontabs(should be by itself, before any of the jobs) and it will automatically do the export for you without having to include it in your script or adding it to every cronjob.

The next way is for a multiple screen setup:

```
export DISPLAY=:0 && /path/to/script
```

This bit goes on the cronjob itself after the time descriptor. Use this if you have a script that you use on multiple machines but don't want the program running on the same window on different machines(i.e. one has a single monitor and another you have a choice of monitors, and want it to rn on the second one). Simply change :0 to whichever screen you wish to have the script run on. 0 is your default screen, 1 would be the second, 2 the third, and so on.

For the last method, you would simply include the "export DISPLAY=:0" bit of code in the script itself. That is useful if you have a script that you will always want to run on the same screen regardless of the number of them.

---

### Post by Derek Karpinski on 2012-01-18
I could never get the cron job to export the display. That's why I put it in the script.

---

### Post by Roger Norton on 2012-01-19
To deal with the most recent posts in the order of posting:

Re Derek Karpinski's: I have restarted the computer with a crontab which was blank (screenshot attached), while the .sh file was present, if that's what you mean by running without crontab - although there are other crontab files present (presumably came with the OS - see screenshot of filesearch for crontab).  Where do I find the cron log?

Re trickster_x's: Nope, still nothing.  Screenshot of current crontab and filesearch for crontab, and changer.sh attached.  Please note that I have changed the name of the folder containing the images from farside calendar to farside to avoid problem mentioned earlier.

---

### Post by trikster_x on 2012-01-19
Try running the script through terminal and post the output you get. Just open a terminal window and input the path to your script:
```
/home/roger/Pictures/cartoons/farside/changer.sh
```

If your desktop background changes to the correct image when you run the script from a terminal, then the problem lies in your crontab. If it doesn't, you should get information about the error in the terminal, which can be posted here so we can help troubleshoot what is going on. If no errors get printed in the terminal, then it is most likely a problem with your file path. I suggest you change your background to the default background or some other image; in the event it is your file path, the background will change to a solid color. 

If you find the script DOES work when you run it through a terminal, try using some of the other methods of specifying a display to run on:
```
0 0 * * * export DISPLAY=:0.0 && /home/roger/Pictures/cartoons/farside/changer.sh

or

0 0 * * * env DISPLAY=:0.0 && /home/roger/Pictures/cartoons/farside/changer.sh
```

Or try adding the export command to the script itself. As Derek mentioned, there may be problems with cron running the export command:

```
#! /bin/bash

bgImage=`date +%b%d`.jpg

export DISPLAY=:0.0

gsettings set org.gnome.desktop.background picture-uri file:///home/roger/Pictures/cartoons/farside/$bgImage
```

At the very least, I know the script should work as I have run it several times, manually and through cron.

---

### Post by Roger Norton on 2012-01-20
The script works when run from a terminal (and incidentally alters the background shown in the System Settings window - see attached).

Have not yet got it to work on startup.  New crontab screenshot and changer.sh attached.

---

### Post by Derek Karpinski on 2012-01-20
Good, your scrpit works........cron is the problem. Try changing cron to get it to run every 5 min just so we can create an output file with the errors.
 
```
*/5 * * * * /home/roger/Pictures/cartoons/farside/changer.sh > /home/roger/Desktop/cron.log 2>&1
```
 
Wait for 5 minutes, and a file should appear on your desktop named 'cron.log'. Post the contents of the file here.

---

### Post by trikster_x on 2012-01-20
Along with what Derek asked, could you run 
```
ps -ef | grep cron
```
in a terminal and tell us if you get any output? If there is output, cron is loading fine. If there is NO output, cron isn't loading on startup.

---

### Post by Roger Norton on 2012-01-21
Screenshots of output of ps -ef | grep cron and updated crontab file attached. cron log was blank.

The background altered to the desired cartoon.

---

### Post by trikster_x on 2012-01-21
[COLOR="Blue"]**_I have tested ALL the crontab entries on my own system and they run fine, so  please do not change the command sections of them for any reason. If you do, it may cause the job to not run._**[/COLOR]

Okay, cron is loading on startup. See if you can get cron to run anything at all. Use the following job, just to see if cron is doing anything:
```
* * * * * /bin/mkdir /home/roger/crontest && /bin/echo "cron works fine" && /bin/ls /home/roger/doesnotexist > /home/roger/crontest/test.log 2>&1
```

Set the minute and hours to a minute or two ahead of your local time, so you don't have to rush to delete the entry. This does three things. It runs the command **mkdir** and creates a directory in your home folder called crontest. Then it creates a log file in the folder that will have the standard output "cron works fine". And finally, it tries to list the files of a directory which presumably does not exist. This causes the log file to get some standard error as well. This will let us know that cron is working as intended. Once you are certain of the outcome, go ahead and delete the file and folder.

If we get the green light on cron from that bit, we need to check that it is able to run simple GUI commands. For that we will attempt to run Banshee:
```
* * * * * /usr/bin/env DISPLAY=:0.0 /usr/bin/banshee
```

Again, set minute and hour a couple minutes ahead of local time.Should that start up banshee, we will know that cron is in fact capable of starting a GUI program using the **env** command.

If the commands DON'T run, then we need to try some drastic measures, purging and reinstalling cron. In a terminal, use the following commands:
```
sudo apt-get remove --purge cron
```
```
sudo apt-get install cron
```

If you get a message about unmet dependencies that says to try
```
sudo apt-get install -f
```
go ahead and run that as well. All that will remove and reinstall cron so you can start all of it from scratch.

Once you have either determined cron is running fine or you have purged and reinstalled, try running the script again. Use the following as your script and your crontab, and set the background to one of the default images:

```
#! /bin/bash

bgImage=`date +%b%d`.jpg

gsettings set org.gnome.desktop.background picture-uri file:///home/roger/Pictures/cartoons/farside/$bgImage
```

```
* * * * * /usr/bin/env DISPLAY=:0.0 /home/roger/Pictures/cartoons/farside/changer.sh
```

Rmember to set for local time. If it still does not work, I will have one more suggestion for you, then the problem is beyond my ability and I won't be of much more help without physical access to the machine. I really hope this gets it going for you, though.

---

### Post by Derek Karpinski on 2012-01-21
Wait trikster...........he said it did change.  Right?

---

### Post by trikster_x on 2012-01-21
So he did, I must have misread. That's what I get for trying to offer advice a few minutes after I wake up :P

I'll still leave the previous post up for reference, since it is a good cron troubleshooting method. But if cron is working correctly now, there is no reason to use all the info in that post.

---

### Post by Derek Karpinski on 2012-01-21
I wonder if you have to pipe the output of cron to /dev/null, or a log file for it to work with a GUI application?

Since that's all I really had him change.

---

### Post by Roger Norton on 2012-01-22
The background showed yesterday's cartoon on start-up today, with the crontab as it was on my previous posting.  Think I'm going to avoid drastic measures, and stick with the .xml.  Thanks for your help.

---

### Post by trikster_x on 2012-01-22
> **Derek Karpinski said:**
> I wonder if you have to pipe the output of cron to /dev/null, or a log file for it to work with a GUI application?

Since that's all I really had him change.

Not the case. I have run this and several other GUI scripts recently with cron and never needed to do anything with /dev/null or a log file. I'm not sure exactly what is happening, but I'm fairly sure it is a problem with cron itself.

---

### Post by grahammechanical on 2012-01-22
@Roger Norton

Hi. I see that you have been having fun! I decided to use the information that I gave to you to create some additional slide shows using background images from previous versions of Ubuntu. I have just finished and I found out something that you might need to know.

When we use sudo gedit or gksudo gedit to give the editor administrator privileges to edit and save those xml files, well, when we save them gedit creates a backup of the file. It calls it be the same name and sticks a tilde character ( ~ ) on the end of the file extension. So, that folder will contain a background-1.xml and a background-1.xml~ file.

Gnome-control-center which runs the Appearance utility (soon to be changed to User Interface in 12.04) reads both files and this produces a duplication of images in the Appearance side panel. It can cause the Appearance utility to do strange things.

The backup up copy will need to be deleted by sudo nautilus. You will not have a problem when doing this in 11.10 but I am testing 12.04 and sudo nautilus does not have a top menu in 12.04. You cannot set it to see hidden files as you can with the normal nautilus.

This should not be a problem except that the tilde character ( ~ ) turns these xml files into a hidden file. So, sudo nautilus in 12.04 alpha cannot see the hidden files. Until I noticed this I could not work out why things were not working correctly and why the Appearance utility would sometimes crash.

There is another script that has an effect on the backgrounds used in the appearance utility. It is /usr/share/gnome-background-properties/ubuntu-wallpapers.xml. This is the script that tells the Appearance utility what to put in the side panel. This also needs editing to see the additional slide show.

I hope this helps.

Regards.

---

### Post by Roger Norton on 2012-01-23
Hi grahammechanical,

screenshot of the Appearances panel attached.  It seems to show the images listed in /usr/share/gnome-background-properties/ubuntu-wallpapers.xml, and the current date's cartoon, without duplication.  The correct date's cartoon is shown on start-up, but does not change at midnight (rarely relevant), so it works as well as needed.  I will delete background-1.xml~ once I have finished writing background-1.xml and before I update to 12.04.  

Thanks for your help.

---

