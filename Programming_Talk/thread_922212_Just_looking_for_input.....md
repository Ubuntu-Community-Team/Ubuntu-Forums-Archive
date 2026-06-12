---
title: "Just looking for input...."
date: 2008-09-17
forum: Programming Talk
---

### Post by jmap82 on 2008-09-17
I don't consider myself a programmer, but I do find it fascinating. I'm tinkering around with bash scripting just to see what I can do.

I wrote a simple script to focus my learning experience.  I got it to work pretty much the way I want it, and now is the stage of my learning process where I ask experienced people to tell me how to do it better.

**Synopsis**

[HandBrake]("http://handbrake.fr/") is a powerful H.264 video encoder that processes DVD files for archiving.  HandBrakeCLI is officially supported by Handbrake on Linux systems, and it is easy enough to learn.  However, when archiving personal video collections there are two processes involved: Ripping and Encoding.  The Ripping process requires the user to be at the console changing out DVDs and saving the files to an appropriate directory.  The Encoding can be batch processed while you sleep.  There is nothing that can be done about having to manually change DVDs but I thought I could save myself and others some time by writing a script that will create a batch file automatically, considering that the same settings are typically used for each video.

**The Script**

```

#!/bin/sh
#
#My humble attempt to write a script that will generate 
#a batch file for HandBrakeCLI.
#
#
clear  #Clear the screen for the following message.
cat << EOF
**********************************************************
*         Copy the HandBrakeCLI binary into the          *
*      /home/USER/ direcory if you want to run the       *
*   the batchfile upon completion.  Feel free to alter   *
*           this script to suit your needs.              *
*  Message me at forums.ubuntu.com U/N jmap82.  Thanks.  *
*                                                        *
*              Press Enter to continue.                  *
*                                                        *
**********************************************************
EOF
read zzzz  #Pause for user feedback.

cd /media/Love/RippedDVDs  #A default start directory.
rm HBBatch  #Removes prevous batch file to so a new one will be created and ensures this file is not included in ls or dir output.
echo "You are now in `pwd`"  #Feedback for user.
echo "Files in this directory are:"; dir  #Feedback for user.
echo "Is this where you want to be? ('y' or 'n')"  #Opportunity for user to change directory without re-writing the script.
read ans  #Listener for confirmation.
while [ $ans != y ]  #Begin While loop to change directories.
do
echo "Where are your source DVD files? (address from root)"
read address  #Listener for new source directory.
cd $address  #Go to new source directory.
echo "You are now in `pwd`"  #Feedback for user.
echo "Files in this directory are:"; dir  #Feedback for user.
echo "Is this correct? ('y' or 'n')"  #Request for confirmation.
read ans  #Listener for Confirmation.
done  #End While loop.

ls > /tmp/FileList

num=`cat /tmp/FileList|wc -l` #Counts the number of lines in the file (which is equal to the number of files in the folder) to provide an upper limit for the While loops.

i=1  #Sets counter to 1 for While loop.
while [ $i -le $num ]  #While loop to  plug file names into a string for the batch file.
do
name=`awk "FNR == $i" /tmp/FileList`  #"FNR == $i" MUST be in DOUBLE QUOTES otherwise the variable will not be interpreted.
echo "$HOME/HandBrakeCLI -i `pwd`/$name -o $HOME/Videos/$name.mp4;">> `pwd`/HBBatch  #Plugs all previously assigned variables into a command string for HandBrakeCLI.  Other options can be added of course.
i=`expr $i + 1`  #Increases value of $i by 1
done

rm /tmp/FileList  #Clean up Temporary files.

chmod +x HBBatch  #Prepare batch file for execution.

echo "Process Complete.  Batch file as been created in `pwd`"  #Feedback for user.
echo ""
echo "To begin encoding with HandBrakeCLI enter 'y'"  #Request to process batch file.
read go  #Listener for confirmation.

if [ $go = y ]  #If loop to check the confirmation variable.
then
./HBBatch
else
exit 0
fi

```

I'm sure its pretty messy, but I'm still learning.  I hope you guys can help me make it better :).

Thanks in advance.

jmap82.

---

### Post by jmap82 on 2008-09-17
Sorry, because I was using dummy files to test the script... I overlooked something very basic and stupid.  The script creates new names for the directories for filtering purposes and saves them to an external file, but does not actually rename the directories... so when the batch file is run it won't be able to call them by the newly created names.

I guess the wall I'm hitting is a way to assign each file/directory name in a directory to a variable one at a time so it can later be plugged into a string...  Is there anyway to do that?

The method I used above will work if the user numbers the files accordingly as they are created.  (01.filename, 02.filename... 11.filename, 12.filename, ...)  But I was trying to automate this process to make the script more independent.  

Another thing I noticed was that, when I was trying to debug for situations when there are more than 10 files, I made one of the While loops run for a minimum of 9 times, which of course will create output with incomplete references, not effecting the quality of your output, but just leaving a string of errors as the end of your batch process.

I guess this is part of the learning process...

Any suggestions would be welcomed.

---

### Post by ghostdog74 on 2008-09-17
> **jmap82 said:**
> 

```

#!/bin/sh
#
#My humble attempt to write a script that will generate 
#a batch file for HandBrakeCLI.
#
#
clear
echo "**********************************************************"
echo "* Copy the HandBrakeCLI binary into the                  *"
echo "*  /home/USER/ direcory if you want to run the           *"
echo "* the batchfile upon completion.  Feel free to alter     *"
echo "* this script to suit your needs.                        *"
echo "*                                                        *"
echo "* Press Enter to continue.                               *"
echo "*                                                        *"
echo "**********************************************************"
read zzzz

```


you can use HERE document to reduce all those extra echoes
```

cat << EOF
**********************************************************
* Copy the HandBrakeCLI binary into the                  *
*  /home/USER/ direcory if you want to run the           *
* the batchfile upon completion.  Feel free to alter     *
* this script to suit your needs.                        *
*                                                        *
* Press Enter to continue.                               *
*                                                        *
**********************************************************
EOF

```


> 
```

ls >/tmp/FileList
num=`cat /tmp/FileList|wc -l`
nl -n rz -s . -w 2 /tmp/FileList>/tmp/FL2

```


```

ls -1 | awk '{print NR , $0}'

```

[/QUOTE]

---

### Post by jmap82 on 2008-09-17
Thanks.  I used your suggest for the message at the beginning of the script.  I'm still working on a way to incorporate your use of awk, however I will have to re-write my filters in my loops to get it to work correctly.  That will take me some time since I'm still pretty new to all this.

Thanks again!

---

### Post by ghostdog74 on 2008-09-17
> **jmap82 said:**
>  I'm still working on a way to incorporate your use of awk, however I will have to re-write my filters in my loops to get it to work correctly. 
you don't have to if your method works for you.

---

### Post by jmap82 on 2008-09-19
I think I have this script working perfectly now!  I learned that awk can be used to call specific lines from files using the FNR variable.

This will call line 3 from file "filename".
```
awk 'FNR == 3' filename
```

Most documentation used the apostrophe(') distinguish the definition of the FNR variable from the rest of the command.  For my purposes I needed to assign FNR to another variable ($i) and the apostrophes wouldn't allow the shell to read it.  I then discovered that by using Double Quotes(") the variable was preserved, resulting in the following code.

```
awk "FNR == $i" filename
```

This discovery was huge for me and unlocked the biggest set back of my script.  I hope it helps others too.

Peace,

jmap82

---

### Post by Tomosaur on 2008-09-19
> **jmap82 said:**
> I think I have this script working perfectly now!  I learned that awk can be used to call specific lines from files using the FNR variable.

This will call line 3 from file "filename".
```
awk 'FNR == 3' filename
```Most documentation used the apostrophe(') distinguish the definition of the FNR variable from the rest of the command.  For my purposes I needed to assign FNR to another variable ($i) and the apostrophes wouldn't allow the shell to read it.  I then discovered that by using Double Quotes(") the variable was preserved, resulting in the following code.

```
awk "FNR == $i" filename
```This discovery was huge for me and unlocked the biggest set back of my script.  I hope it helps others too.

Peace,

jmap82

I remember when I first learnt the distinction between ' and " in Bash scripting - the vast majority of my headaches disappeared instantly. That's what you get for jumping the gun I suppose :P When I was learning how to script bash - I was using web tutorials and stuff, but since I'm such an impatient idiot, I must have skipped over the pages telling me about the ' / " difference!

---

### Post by jmap82 on 2008-09-19
> **Tomosaur said:**
> I remember when I first learnt the distinction between ' and " in Bash scripting - the vast majority of my headaches disappeared instantly. That's what you get for jumping the gun I suppose :P When I was learning how to script bash - I was using web tutorials and stuff, but since I'm such an impatient idiot, I must have skipped over the pages telling me about the ' / " difference!

Haha, glad to know I'm not the only one :)

---

### Post by ghostdog74 on 2008-09-19
> **jmap82 said:**
>   I then discovered that by using Double Quotes(") the variable was preserved, resulting in the following code.

```
awk "FNR == $i" filename
```

you don't have to grapple too much about shell and awk quoting. Pass your shell variable to awk using -v 
```

awk -v shellvar=$myshellvar 'NR==shellvar{ blah }' file

```

---

### Post by jmap82 on 2008-09-20
> **ghostdog74 said:**
> you don't have to grapple too much about shell and awk quoting. Pass your shell variable to awk using -v 
```

awk -v shellvar=$myshellvar 'NR==shellvar{ blah }' file

```

Nice Thanks :)

---

### Post by jmap82 on 2008-10-13
So I'm pretty sure this thread is dead, but on the off chance that anyone cares, I touched up my script a little bit.

-added loop to customize options
-added choices for what to do once the script is finished

Check it out at:

[http://script.jmap82.com](http://script.jmap82.com)



Thanks again to those who helped.

---

