---
title: "Get Tomboy Notes into Conky"
date: 2008-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by pt123 on 2008-05-23
I know all of most of you use Conky to remind yourself, about your cpu specs ;)
Anyway here is simple tutorial on getting your Tomboy notes into Conky. 

Tomboy is great for jotting down notes, but I don't like to have it open when I am not using. While Conky is perfect for displaying information in a subtle manner.

This Tutorial attempts to take advantage of this, using the awesome D-Bus interface. 
This neat tutorial on Arstechnica was of great help.
[http://arstechnica.com/journals/linux.ars/2007/09/26/using-the-tomboy-d-bus-interface](http://arstechnica.com/journals/linux.ars/2007/09/26/using-the-tomboy-d-bus-interface)

**Step One Tomboy**
I have a note in Tomboy called "Tasks" where I will note down tasks and important reminders.  You can use any note in Tomboy for this tutorial.  
I was able to write a simple python script (my first python script ) to extract this Tomboy note to a text file. In the script you need to set 2 variables, the name of theTomboy note and the file path to the export text file.
```

#!/usr/bin/env python
import sys, dbus, gobject, dbus.glib

#Varibale you need to assign values to
noteName = "Tasks"  #enter the name of your tomboy note
exportFileName = '/home/myhomefolder/journal/tasks.txt' # the export file

#Read the tomboy note
bus = dbus.SessionBus()
obj = bus.get_object("org.gnome.Tomboy", "/org/gnome/Tomboy/RemoteControl")
tomboy = dbus.Interface(obj, "org.gnome.Tomboy.RemoteControl")

note = tomboy.GetNoteContents(tomboy.FindNote(noteName))

#export the note
file = open(exportFileName, 'w')
file.write(note)  # write the file
file.close() # close it

```

You need to cut and past the above code into a file called exportTomboyNote.py in a folder.

Then you can run the script in a terminal by
```
python /pathtoFolder/ exportTomboyNote.py
```

If you want you can get the script to run every X minutes by editing your cron. I don't want to go into this . This thread deals Cron comprehensively
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

**Step Two Conky**
To get the note in your Conky, edit your config file.
```
gedit .conkyrc 
```

Then find the word "TEXT" in it, below it you can add the following line
```
${head /pathToexportFile/tasks.txt 30 20}
```

Note. 30 is the number of lines from the top of text file. You also need to increase your text buffer if you planning to read many lines by editing the following lines. 
```

# Maximum size of buffer for user text, i.e. below TEXT line.default is 16384 bytes
max_user_text 32768

```


That's it.

This was tested on the Tomboy & Conky that came with Hardy 8.04

---

### Post by pt123 on 2008-06-02
Wow, didn't realise this got approved. 

Sadly no one found it useful :(

---

### Post by Mandrake12 on 2008-06-04
This is great, thanks! Now I'm trying to get todays appointments from evolution calendar / google ical into conky.

---

### Post by melina on 2008-06-04
Max international is a center of providing excellent & quality Technical Support and BPO Services to IT Organizations all over the globe. Providing technical solution is our area of expertise so we have good combination of domain knowledge & experience. For level 1 technical support our customers can leverage benefit of our existing infrastructure & our technical & Information Technology expertise. Our technical helpdesk provides completely customized after-hours support, selected-hours or 24x7 support. 

Technical Support outsourcing can be implemented in Banking, Finance, Telecommunication, Technology, Transport, Manufacturing, Entertainment etc sectors. We have technical background which gives your guarantee of best quality technical support in the BPO Industry. 

Technical support services cover : 
> Desktop Support 
> Operating Support 
> Application Support 
> Antivirus Helpdesk 
> Back Office Support 
> Database creation & Management 
> IT Helpdesk 
[www.imaxintl.com](www.imaxintl.com)

---

### Post by pt123 on 2008-06-04
> **Mandrake12 said:**
> This is great, thanks! Now I'm trying to get todays appointments from evolution calendar / google ical into conky.
Thanks

I will post a Tutorial in getting you calendar items from Google Calendar into Conky using gcalcli (it's in the repos) soon.

[http://code.google.com/p/gcalcli/](http://code.google.com/p/gcalcli/)

I have submitted the thread I will msg you when it gets approved.

---

### Post by sweetthdevil on 2008-06-05
Well, thanks for the tomboy script, but please let me know for the Google Calendar I am more than interested!

---

### Post by sweetthdevil on 2008-06-06
Well, while we are talking about Tomboy in Conky, It will be nice for the scripts to fetch the layout and also the font (bold/underline/etc etc)

Thanks,

---

### Post by edmondt on 2008-06-06
Wow this is really cool :) Do you have time to post any screenshots and files? :D

---

### Post by sweetthdevil on 2008-06-06
Well, to update the note automatically I placed the following option in my conky:

${execi 900 ~/.scripts/exportTomboyNote.py}
(900 secondes => 15minutes!)

However, every times it does update, tomboy is lunch, and when already lunch the log file become empty.  
Is there a way, for the script to be fetching the information without lunching tomboy, and to fetch the information, when tomboy is open?

---

### Post by pt123 on 2008-06-06
> **sweetthdevil said:**
> Well, while we are talking about Tomboy in Conky, It will be nice for the scripts to fetch the layout and also the font (bold/underline/etc etc)
Thanks,
I wanted to be able to do strike through but Conky doesn't seem to be able to handle different changes italics, bold or strike through in fonts. 

Conky can do colour and a complete change in font, so I was planning to do a script will show the finished tasks in a different color

so in the above code rather calling GetNoteContents you need to call **GetNoteContentsXml**

You get an output like this:
```

<note-content version="0.1">Tasks
Clean Fridge
Clear Dust from Computer
<strikethrough>Clean Bathroom
Hair cut</strikethrough>
<strikethrough>
</strikethrough>
<bold><size:large>Reoccuring</size:large></bold>

```. 

So you will need to then write a script that will replace <strikethrough>  to ${color lightgrey}.

---

### Post by pt123 on 2008-06-06
> **edmondt said:**
> Wow this is really cool :) Do you have time to post any screenshots and files? :D

Not sure what you mean by files the small changes you need to make to your conky are listed in my first post. 

Attached is a screenshot which has conky listing my tasks.

---

### Post by pt123 on 2008-06-06
> **sweetthdevil said:**
> Well, to update the note automatically I placed the following option in my conky:

${execi 900 ~/.scripts/exportTomboyNote.py}
(900 secondes => 15minutes!)

However, every times it does update, tomboy is lunch, and when already lunch the log file become empty.  
Is there a way, for the script to be fetching the information without lunching tomboy, and to fetch the information, when tomboy is open?
One way to get around this is have Tomboy running in the panel as an applet, which I wind is useful. It neatly hides away as shown in the above screenshot. 

Or you can encase the above script in a bash script which will test if Tomboy is running.
```

#!/bin/sh

if ps ax | grep -v grep | grep "tomboy" > /dev/null
then
    #tomboy is running run the script 
 python exportTomboyNote.py
else
    #not running just cat the exported tasks text file
    cat exported_tasks.txt
    exit
fi

```

---

### Post by uzi09 on 2008-06-08
i just decided to have a nice little text file which conky just displays:
```
${color slate grey}To Do:
${color}${head /home/uzair/.tasks 30 20}
```

and if i ever need to add a task, it's as simiple as:
```
echo "1) Save the world" >> .tasks
```
to remove, just edit the file and delete the line :)

i guess i never got into using tomboy cuz it required too much. i think note taking should be super quick :)

---

### Post by pt123 on 2008-06-08
But then it is cumbersome to delete, I use Tomboy for other stuff so managing tasks through it is effective for me. 

I have also wrote a small python script that take completed tasks and place it in another text file so Conky can distinguish the complete & incomplete tasks.

Here is the other tutorial about getting your Google Calendar into Conky

[http://ubuntuforums.org/showthread.php?t=818053](http://ubuntuforums.org/showthread.php?t=818053)

---

### Post by sweetthdevil on 2008-06-08
> **pt123 said:**
> One way to get around this is have Tomboy running in the panel as an applet, which I wind is useful. It neatly hides away as shown in the above screenshot. 

Or you can encase the above script in a bash script which will test if Tomboy is running.
```

#!/bin/sh

if ps ax | grep -v grep | grep "tomboy" > /dev/null
then
    #tomboy is running run the script 
 python exportTomboyNote.py
else
    #not running just cat the exported tasks text file
    cat exported_tasks.txt
    exit
fi

```


Thanks, but could you please be a little bit specific on how to integrate the code?

---

### Post by pt123 on 2008-06-08
> **sweetthdevil said:**
> Thanks, but could you please be a little bit specific on how to integrate the code?

rather than running this 
```
${execi 900 ~/.scripts/exportTomboyNote.py}
```
 in conky like you wanted to (in your earlier post 
run this
```
${execi 900 ~/.scripts/checkIfTomboyOpenThenExportTomboyNote.sh}
```

That checkIfTomboyOpenThenExportTomboyNote.sh is the above script I wrote, which checks if Tomboy is open before calling the export python script.

---

### Post by sweetthdevil on 2008-06-08
Alright, sorry to be such an idiot, but I do not know understand the code, so I am asking,

I create the file, in my folder ~./scripts gave it the right to execute, close tomboy to check if working; and obviously something is wrong

"cat: exported_tasks.txt: Aucun fichier ou dossier de ce type"

What should I do?

---

### Post by pt123 on 2008-06-08
> **sweetthdevil said:**
> 
"cat: exported_tasks.txt: Aucun fichier ou dossier de ce type"

What should I do?

Is looking for the file called  exported_tasks.txt in the directory where this script is.

You need to change that line to
```
cat /path/to/exported_tasks.txt
```
it is where the initial script saves your tomboy tasks to,

Here is the script more tailored to what you are after
```

#!/bin/sh

if ps ax | grep -v grep | grep "tomboy" > /dev/null
then
    #tomboy is running run the script 
 python exportTomboyNote.py
else
    #not running just cat the exported tasks text file
   # do nothing
fi
cat /path/to/exported_tasks.txt

```

---

### Post by sweetthdevil on 2008-06-08
Many thanks, works great now, but just to make sure I understand.

Now when Conky is going to start, the "checkIfTomboyOpenThenExportTomboyNote.sh"is going to run, if tomeboy is running then the other script is going to fetch the information, but if tomboy is not running, are the information going to be fetch?

---

### Post by pt123 on 2008-06-08
> **sweetthdevil said:**
> but if tomboy is not running, are the information going to be fetch?

yep it will fetch the notes from the last successful fetch by "cat-ing" (reading it) that saved file.

---

### Post by sweetthdevil on 2008-06-08
Little trouble though, when I do like that, both tomboy note and GoogleCalendar got double information. 

See attach picture.
[[img]http://images0.hiboox.com/vignettes/2408/9179dc520ee6b8709796dec4a6c9c6a8.png[/img]](http://www.hiboox.fr/go/images/informatique/capture,9179dc520ee6b8709796dec4a6c9c6a8.png.html)

---

### Post by pt123 on 2008-06-09
Post your conky file, and run the sh file in a terminal and post the output here. This should tell which is causing the double up.

---

### Post by sweetthdevil on 2008-06-09
Well, the double information only occurs when tomboy is not running, I checked tasks.txt and gcal.txt and they're ok.  

Starting Conky Output: 

```
'/home/sweetth/.scripts/conky_start.sh' 
sweetth@ubuntu:~$ Conky: one or more $endif's are missing
Conky: forked to background, pid is 9239
Conky: desktop window (10000b8) is subwindow of root window (13b)
Conky: window type - override
Conky: drawing to created window (3200001)

Conky: drawing to double buffer
Conky: desktop window (10000b8) is subwindow of root window (13b)
Conky: drawing to desktop window
Conky: drawing to double buffer
Conky: desktop window (10000b8) is subwindow of root window (13b)
Conky: window type - override
Conky: drawing to created window (3800001)
Conky: drawing to double buffer
```

conkyrc2 (tomboy)

```
use_xft yes
xftfont verdana:size=8
xftalpha 0.8
background no
update_interval 2.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type override
double_buffer yes
cpu_avg_samples 2
net_avg_samples 2
use_spacer right
alignment top_right
gap_x 1110


 TEXT

${execi 900 ~/.scripts/checkIfTomboyOpenThenExportTomboyNote.sh}
${font tintin:size=12}${color #d0d3e4}${head /home/sweetth/.scripts/tasks.txt 30 20}${font}${color}
```

conkyrc3 (Gcalcli)

```
use_xft yes
xftfont verdana:size=8
xftalpha 0.8
background no
update_interval 2.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type override
double_buffer yes

cpu_avg_samples 2
net_avg_samples 2
use_spacer right
alignment top_right
gap_x 550


 TEXT
${execi 900 ~/.scripts/gcal.sh}
${font tintin:size=12}${color #d0d3e4}${head /home/sweetth/.scripts/gcal.txt 10 20}${color}${font}
```

Thanks for your help

---

### Post by pt123 on 2008-06-09
> **sweetthdevil said:**
> 
conkyrc2 (tomboy)

```

${execi 900 ~/.scripts/checkIfTomboyOpenThenExportTomboyNote.sh}
${font tintin:size=12}${color #d0d3e4}${head /home/sweetth/.scripts/tasks.txt 30 20}${font}${color}
```


There is the problem, you are reading it twice. When you run execi it outputs the info to conky and then head is reading that same output which was saved to the text file.

So you might want to change it to 

```

${font tintin:size=12}${color #d0d3e4}${execi 900 ~/.scripts/checkIfTomboyOpenThenExportTomboyNote.sh}

```

and likewise for Gcal

---

### Post by sweetthdevil on 2008-06-09
Many thanks for the quick reply, day and night :lolflag:

Change both like you said, but both conky do not show any result now?

---

### Post by pt123 on 2008-06-09
> **sweetthdevil said:**
> Many thanks for the quick reply, day and night :lolflag:

Change both like you said, but both conky do not show any result now?

I tried to run that script and if was giving an error because the "Else" statement was empty.

So replace that sh with this:
```

#!/bin/sh

if ps ax | grep -v grep | grep "tomboy" > /dev/null
then
    #tomboy is running run the script 
 python exportTomboyNote.py
fi
cat /path/to/exported_tasks.txt

```

---

### Post by sweetthdevil on 2008-06-09
Great!! Work fantasticly!!!

Many thanks

---

### Post by sweetthdevil on 2008-06-09
a quick question, my notes are not display completly, you've seen my conkyrc and I had as you suggest in the first topic, "max_user_text 32768" but it didn't change anything, any idea?

---

### Post by pt123 on 2008-06-09
rather than
```
cat /path/to/exported_tasks.txt

```
try 

```
head /path/to/exported_tasks.txt -n 30

```

where 30 is the number of lines.

If that doesn't work then you might not be able to execi.

---

### Post by sweetthdevil on 2008-06-10
Well, I found a solution:

I remove the head function from the checkIfTomboyOpenThenExportTomboyNote.sh and had it in the conkyrc 


Many thanks for your help!!

---

### Post by apokkalyps on 2008-07-15
If you can do this, in your opinion, how hard would it be to write software that would directly read and write your tomboy notes through an (php?) interface on the web?  Making a wiki, so that your tomboy notes can be accessed and modified anywhere...

This would be extremely useful for alot of people and I can't find where anyone has done it yet.

---

### Post by pt123 on 2008-07-16
It shouldn't be hard because php has a function that can execute shell functions like the ones used in the my scripts. 

If you are look for a wiki you can try zim wiki.

---

### Post by apokkalyps on 2008-07-16
thanks actually I just left mediawiki and started using tomboy, in fact I am desperatly trying to get the content out of my old mediawiki that i stupidly didnt export.  Zim seems like tomboy with a few extra features like tree organization of notes and formulaes.  Tomboy works fine for me.  But neither of them from what I can tell have the ability to host your notebooks through a webserver, which is what I am looking for.  Basicly I want read/write access to my tomboy notes from anywhere on the internet.  But I dont want anything as bulky and complicated as mediawiki.  I want the simplicity of tomboy brought into an online wiki interface.

It surprises me that no one has written a script to host your tomboy files directly as an online wiki.  Even the makers of tomboy, it seems like such an obvious way to improve the software.  They currently have webdav and ways to synchronize files.  But IMO synchronizing is a pain and doesnt really work well in two directions.  Plus theres just no need to keep two copies of the files if tomboy is on the same machine as your webserver.  

Maybe I am just a small demographic, being someone with my own domain and webserver.

Anyway I didnt mean to threadjack, I just thought you might know something about it.

---

### Post by kmaster228 on 2009-07-09
hello this tutorial seems interesting but when i made the python script and ran it i would get and error saying 
```
python exporttom.py
Traceback (most recent call last):
  File "exporttom.py", line 17, in <module>
    file.write(note)  # write the file
UnicodeEncodeError: 'ascii' codec can't encode character u'\u2022' in position 6: ordinal not in range(128)
```
 and this is my python script 
```
#!/usr/bin/env python
import sys, dbus, gobject, dbus.glib

#Varibale you need to assign values to
noteName = "Tasks"  #enter the name of your tomboy note
exportFileName = '/home/kmaster/Documents/tasks.txt' # the export file

#Read the tomboy note
bus = dbus.SessionBus()
obj = bus.get_object("org.gnome.Tomboy", "/org/gnome/Tomboy/RemoteControl")
tomboy = dbus.Interface(obj, "org.gnome.Tomboy.RemoteControl")

note = tomboy.GetNoteContents(tomboy.FindNote(noteName))

#export the note
file = open(exportFileName, 'w')
file.write(note)  # write the file
file.close() # close it

```

---

### Post by pt123 on 2009-07-09
what sort encoding (UTF, ASCII) is your text file using?

more info
[http://www.pyzine.com/Issue008/Section_Articles/article_Encodings.html](http://www.pyzine.com/Issue008/Section_Articles/article_Encodings.html)

---

### Post by vancheese on 2011-05-31
The unicode error is from using a bulletpoint in Tomboy
The easiest solution is to not use them!

---

