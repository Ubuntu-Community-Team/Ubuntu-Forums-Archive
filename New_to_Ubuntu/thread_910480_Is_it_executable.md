---
title: "Is it executable?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Andrew U.K. on 2008-09-04
Hi,
I'm trying to make this script executable. I follow the instructions (i think) and  then check it but it is still just a text file icon. In properties it says it is a plain text document.
Have I made it executable?

Cheers
Andrew
    *

      #
      # MythWakeSet
      #
      # set mythtv wake-up time with UTC-adjusted time
      #

      # temp file for working with time
      temp_stamp=/home/mythtv/timestamp

      # store the wake time passed from mythbackend
      echo $1\ $2 > $temp_stamp

      # Read the date in *locale* time format and tag the time-zone info to the wake time
      localeadd=$(/bin/date -f $temp_stamp +%F\ %T\ %z)
      echo $localeadd > $temp_stamp

      # adjust this to UTC and store the final wake time
      utcadj=$(/bin/date -u -f $temp_stamp +%F\ %T)

      # set the alarm
      echo $utcadj > /proc/acpi/alarm

Now, make the script executable and put a copy of it in /usr/bin:

    *

      $ chmod +x MythWakeSet
      $ sudo cp MythWakeSet /usr/bin

---

### Post by Hendrixski on 2008-09-04
I don't know how effective the text-icon is for letting you know whether it's executable or not.... you may have to hit F5 to update it?

When you run ls -l, it should tell you if it's executable or not.

and yes, sudo chmod +x should be enough to make it executable.  Just... I don't know if that permission copies properly, you may want to sudo cp .... and THEN sudo chmod :-p

---

### Post by Thingymebob on 2008-09-04
do 
```

ls -l /usr/bin/MythWakeSet

```
your output should be something like:
```

-rw**[COLOR="Red"]x[/COLOR]**r-**[COLOR="Red"]x[/COLOR]**r-**[COLOR="Red"]x[/COLOR]** ........

```
as long as the executable bits are set (**[COLOR="Red"]x[/COLOR]**)
then its executable

---

### Post by halitech on 2008-09-04
> **Andrew U.K. said:**
> Hi,
I'm trying to make this script executable. I follow the instructions (i think) and  then check it but it is still just a text file icon. In properties it says it is a plain text document.
Have I made it executable?

Cheers
Andrew

**SNIP**

      $ chmod +x MythWakeSet
      $ sudo cp MythWakeSet /usr/bin

all a script is is a plain text file with a set of instructions telling the system what to do and when so it will show as a text file for an icon

---

### Post by Andrew U.K. on 2008-09-04
Thanks all for the replies. It worked, and every day i'm learning a bit more.

Andrew

---

### Post by garyed on 2008-09-04
One other unimportant thing is if you start the file with:
```
#!/bin/bash
```
then it will show up as a shell script in the terminal using the file command. Otherwise it will list it as a plain text file.
In the Nautilus it shows up as a script either way.
It executes regardless of the heading.

---

