---
title: "HowTo: Create a simple startup reminder"
date: 2006-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by phranx on 2006-10-18
How to create a simple reminder that pops-up at system startup.
Requirements: xmessage, cpp, calendar

1. Create the hidden folder '.calendar' in your home directory
```

mkdir $HOME/.calendar

```

2. Create, in this folder, the file  'myCalendar.cal' in which we'll write our appointments.

'myCalendar.cal' syntax:

```

month/day{TAB}Event for this day

//This is a comment-line

/* This is a
multi-line comment*/

```

With {TAB} I mean the tabulation button on the keyboard ('\t' in C language).
We should pay attention to the precise calendar-file syntax. If we use  {spacebar} instead tabulation, the correspondig line will be ignored.

For example, to go to the lawyer on june the 18 we should write:

```

6/18	Lawyer at 11,30. Hide money in the socks!
6/18 This line will be ignored and not shown by the reminder

```

3. Create 'launchCalendar' in /usr/bin/

```
sudo nano /usr/bin/launchCalendar
```

launchCalendar script is quite simple, so read it and then Copy&Paste.
I suppose all personal calendar-files have '.cal' extension. We'll talk later about this kind of files, at point 4. Pay attention to 'MY_EDITOR' definition: I used gedit,but maybe you prefer another one.

```

#!/bin/bash
#launchCalendar
#requirements: xmessage, calendar
#I suppose all calendar-files have '.cal' extension

#------------------------------------------------
#Francesco Campana
#
#All my scripts are under GPL-License
#------------------------------------------------

NUM_OF_DAYS=7                           #number of days shown by the reminder
MY_EDITOR=gedit                         #favorite text editor
TEMP_CAL=$HOME/.calendar/curMonth       #name of temporary calendar


curDay=$(date +%A-%d-%B)
echo -e Today is $curDay\\n > $TEMP_CAL

echo Events for the next $NUM_OF_DAYS days: >> $TEMP_CAL
calendar -A $NUM_OF_DAYS >> $TEMP_CAL

echo  >> $TEMP_CAL

action=$(xmessage -button Close,ShowCurrentMonth,EditCalendars -default Close -print -center -file $TEMP_CAL -title 'Calendar')

if [ $action = "ShowCurrentMonth" ]; then
        cal -m >> $TEMP_CAL
        action=$(xmessage -button Close,Back -default Close -print -center -file $TEMP_CAL -title 'Calendar')
        if [ $action = "Back" ]; then
                launchCalendar  #restart reminder
        fi
elif [ $action = "EditCalendars" ]; then
        cal -m >> $TEMP_CAL
cal -m >> $TEMP_CAL
	#Personal Calendars: 
	#All files with '.cal' extension in the folder '$HOME/.calendar/' will be open by text-editor
        $MY_EDITOR $HOME/.calendar/*.cal 
        launchCalendar
fi


```

make it executable
```
sudo chmod 755 /usr/bin/launchCalendar
```


4. Create, always in yourHome/.calendar, a file named 'calendar'.
This is the file read by calendar command by default. I used it only to include my personal calendars (*.cal in myHome/.calendar directory). And that's why we need the pre-processor :)

```


LANG=C
//Requirements: cpp
#include </home/yourLoginName/.calendar/myCalendar.cal>
#include </home/yourLoginName/.calendar/myFriendsBirthdays.cal>


```


5. Add 'launchCalendar' at system boot:
Xubuntu: go to 'applications/settings/autostarted applications' menu and add '/usr/bin/launchCalendar' command. 
Ubuntu: go to 'System/Preferences/Sessions/' menu and, on the tab 'Statup Programs', add '/usr/bin/launchCalendar'.
Kubuntu: I can't remember :(


**Use:**
Everytime we boot our system, a window is shown at the centre of the screen. By pressing 'EditCalendars' button all files with '.cal' extension in our '.calendar' dir (i.e. our personal calendars ](*,) ) will be open by our text editor.

For a more accurate description of calendar-files, to add for example, weekly events (such as jazz piano lessons) or reminder for the second sunday of a certain month (like Mom's Day :-({|=), read the calendar manual.
```
man calendar
```

I hope that my english hasn't been too bad and that you will find this procedure usefull :D

---

