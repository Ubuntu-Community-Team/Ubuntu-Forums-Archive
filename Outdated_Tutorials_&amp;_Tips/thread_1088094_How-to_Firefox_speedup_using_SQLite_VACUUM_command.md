---
title: "How-to: Firefox speedup using SQLite VACUUM command"
date: 2009-03-05
forum: Outdated Tutorials &amp; Tips
---

### Post by TheLions on 2009-03-05
my friend of mine found out that Firefox can run faster if it's database is purged of empty entries. Firefox database is using SQLite to manage its database

you'll need:
1)SQLite >=3.0
you can check your version by typing in CLI ```
sqlite3
(exit typing .exit)
```
if you don't have it you can obtain it here: [http://www.sqlite.org/](http://www.sqlite.org/) or with ```
sudo apt-get install sqlite3
```

2)you'll need this script:
```
#!/bin/bash

username=$(whoami)
proc="$(ps aux | grep $username | grep -v $0 | grep firefox | grep -v grep)"
if [ "$proc" != "" ]
then
        echo "shutdown firefox first!"
        exit 1
fi

curdir=$(pwd)

for dir in $(cat ~/.mozilla/firefox/profiles.ini | grep Path= | sed -e 's/Path=//')
do
        cd ~/.mozilla/firefox/$dir 2>/dev/null
        if [ $? == 0 ]
        then
                echo "i'm in $(pwd)"
                echo -e "    running...\n"

                for F in $(find . -type f -name '*.sqlite' -print)
                do
                        sqlite3 $F "VACUUM;"
                done

                echo -e "done in  $(pwd) ...\n"
        else
                echo -e "\n    !!!! Nisam uspio uci u direktorij $dir, preskacem ga !!!!\n"
        fi
done
echo "Job finished";

cd $curdir
```

use gedit (or any other text editor) to paste text in it,then save it in your home folder. Open your home folder, right-click on it, select properties. Then select Permissions tab and check the "Allow executing file as program" click Close.

Then close Firefox and run your script from terminal using ./name_of_script

when script done it's work start Firefox and you should feel the difference!;)

---

### Post by batharoy on 2009-03-08
This worked really good for me, thanks.

---

### Post by vasiauvi on 2009-03-08
Yes, I really see a difference!Thanks!

---

### Post by aktiwers on 2009-03-08
Seams to have done a bit here too..

What really made my browsering faster was adding:
> export MOZ_DISABLE_PANGO=1

to the end of .bashrc.

```
gedit .bashrc
```

And the line at the end

---

### Post by stormtrooprdave on 2009-03-08
In what area should I be seeing speed increase?  Page loading? Startup? I don't see any difference but I don't know what I should be looking for.

---

### Post by tehforum on 2009-03-08
Will this work with Firefox 2?

---

### Post by androidkerra on 2009-03-08
whoa!!! very nice how-to bro..tried it and it worked, when i open firefox i already felt the power :D

awesome!!!

---

### Post by binbash on 2009-03-09
Working perfect

---

### Post by TheLions on 2009-03-09
> **stormtrooprdave said:**
> In what area should I be seeing speed increase?  Page loading? Startup? I don't see any difference but I don't know what I should be looking for.

it affects on Startup, Smart Location Bar, History, bookmarks...

> **tehforum said:**
> Will this work with Firefox 2?

Firefox 2 also uses SQLite databases so it should work

---

### Post by itisbasi on 2009-03-09
Should I run the script before starting every new session of Firefox?

---

### Post by zika on 2009-03-09
thanks, it worked, nice addition to my alias that daily updates Minefield ... ;)
hvala.

---

### Post by TheLions on 2009-03-09
> **itisbasi said:**
> Should I run the script before starting every new session of Firefox?

i think it's not necessary, once in month should be fine! ;)

> **zika said:**
> hvala.
nema na &#269;emu! (You welcome!)

---

### Post by jjte on 2009-03-09
Hey what's that error message say near the end of the script? I think it's in Croatian, but I'm not sure.

---

### Post by TheLions on 2009-03-10
> **jjte said:**
> Hey what's that error message say near the end of the script? I think it's in Croatian, but I'm not sure.

yes it is Croatian, I forgot to translate it.

"Nisam uspio uci u direktorij $dir, preskacem ga" means
"Error while entering directory $dir"

---

### Post by vegetarianshrimp on 2009-03-30
good howto..thanks

---

### Post by ewaguespack on 2009-03-30
shorter version.



find ~/.mozilla/firefox/ -type f -name "*.sqlite" -exec sqlite3 {} VACUUM \;

---

### Post by U-Bom-2 on 2009-04-25
maybe sounds noobish and yes i am, but i dont understand this first step! lol can someone explain it more detailed? where do i need to write this or what i need to do

[QUOTE=TheLions;6845423]
1)SQLite >=3.0
you can check your version by typing in CLI ```
sqlite3
(exit typing .exit)
```

Thanks

---

### Post by TheLions on 2009-04-26
> **U-Bom-2 said:**
> maybe sounds noobish and yes i am, but i dont understand this first step! lol can someone explain it more detailed? where do i need to write this or what i need to do

[QUOTE=TheLions;6845423]
1)SQLite >=3.0
you can check your version by typing in CLI ```
sqlite3
(exit typing .exit)
```

Thanks[/QUOTE]

you need to open your Terminal (Programs-->Acessories->Terminal or Alt+F2 then type terminal)
and write it there.

then you need to run script. If you get stuck just ask!

---

### Post by U-Bom-2 on 2009-04-26
ohh lol, i dont got what was CLI :) Thanks

---

### Post by Andy06 on 2009-05-31
Umm it sort of bothers me why this works :)?

What does it get rid of? If the gunk we got rid of was so unnecessary, why was it there in the first place?

Are we sacrificing some functionality or covenience by running this script?

Thanks a lot

---

### Post by TheLions on 2009-06-01
> **Andy06 said:**
> Umm it sort of bothers me why this works :)?

What does it get rid of? If the gunk we got rid of was so unnecessary, why was it there in the first place?

Are we sacrificing some functionality or covenience by running this script?

Thanks a lot

> When an object (table, index, or trigger) is dropped from the database, it leaves behind empty space. This empty space will be reused the next time new information is added to the database. But in the meantime, the database file might be larger than strictly necessary. Also, frequent inserts, updates, and deletes can cause the information in the database to become fragmented - scrattered out all across the database file rather than clustered together in one place.

The VACUUM command cleans the main database by copying its contents to a temporary database file and reloading the original database file from the copy. This eliminates free pages, aligns table data to be contiguous, and otherwise cleans up the database file structure.

The VACUUM command may change the ROWIDs of entries in tables that do not have an explicit INTEGER PRIMARY KEY.

VACUUM only works on the main database. It is not possible to VACUUM an attached database file.

The VACUUM command will fail if there is an active transaction. The VACUUM command is a no-op for in-memory databases.

As of SQLite version 3.1, an alternative to using the VACUUM command is auto-vacuum mode, enabled using the auto_vacuum pragma. When auto_vacuum is enabled for a database, large deletes cause the size of the database file to shrink. However, auto_vacuum also causes excess fragmentation of the database file. And auto_vacuum does not compact partially filled pages of the database as VACUUM does.

The page_size and/or auto_vacuum mode of a database can be changed by invoking the page_size pragma and/or auto_vacuum pragma and then immediately VACUUMing the database.

[http://www.sqlite.org/lang_vacuum.html](http://www.sqlite.org/lang_vacuum.html)

---

### Post by Gen2ly on 2009-06-01
After having used firefox quite a bit I noticed this did make a difference.  Thanks for the tip.

---

### Post by gregh7470 on 2009-06-24
> **itisbasi said:**
> Should I run the script before starting every new session of Firefox?
nah....that's not necessary...and it does work, especially on start up and revisiting pages I've already been to - thx

---

### Post by Elep.Repu on 2009-06-25
I ran the script after I closed ff, 
terminal said it was in the settings directory, and said it was working,
but after about 5 minutes I got tired of it and closed the terminal, and did not notice any difference.

---

### Post by TheLions on 2009-06-25
> **Elep.Repu said:**
> I ran the script after I closed ff, 
terminal said it was in the settings directory, and said it was working,
but after about 5 minutes I got tired of it and closed the terminal, and did not notice any difference.

did script finished before closing terminal? 

If not, it seems that your profile is huge so it needs a lot of time to complete. Try leaving it for 20 minutes or more.

---

### Post by harecanada on 2009-06-25
Thanks to The Lions!! This worked really good without a hitch.

harecanada

---

### Post by zika on 2009-06-25
Just to say that I'm using the following alias to do the job:
```
alias cff='find ~/.mozilla/firefox-3.5/ -type f -name "*.sqlite" -exec sqlite3 {} VACUUM \; && find ~/.mozilla/firefox-3.6/ -type f -name "*.sqlite" -exec sqlite3 {} VACUUM \; && find ~/.mozilla/firefox/ -type f -name "*.sqlite" -exec sqlite3 {} VACUUM \;'
```Same thing in different packaging ... :) Yes, I have all 3 versions active ... :) Just put it in ~/.bash_aliases and add```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```to ~/.bashrc to enable use of separate file to store aliases.

---

### Post by Andrew.Z on 2009-07-01
You don't need command line ninja skills:  [BleachBit vacuums Firefox](http://bleachbit-project.appspot.com/features/)  (and performs other cleaning tasks) from a GUI with just a click.  It's in the Ubuntu 9.04 repositories, but the repo has an old version, so the link above has a newer Ubuntu package.

---

### Post by danbuk on 2009-07-04
:p thx a lot broo.....
i see that diffrence than before.....

---

### Post by danbuk on 2009-07-04
bro...i wanna ask about something...
what will happen if i hidding that programs..it still run or not ?
thanks a lot..

---

### Post by TheLions on 2009-07-04
> **danbuk said:**
> bro...i wanna ask about something...
what will happen if i hidding that programs..it still run or not ?
thanks a lot..


I can not understand you very well.
If you are asking me would script work while firefox running, answer is no.

---

### Post by Fred Better on 2009-07-13
Thanks for the hints. Here's my version
```
#!/bin/bash
username=$(whoami)

function check_app {
    proc="$(ps aux | grep $username | grep -v $0 | grep $1 | grep -v grep)"
    if [ "$proc" != "" ]
    then
        echo "!!! Shutdown $1 first!"
        exit 1
    fi
}

function vacuum_mozillas {
    echo "Vacuuming $1..."
    find $2 -type f -name '*.sqlite' -exec sqlite3 -line {} VACUUM \;
}

check_app firefox
check_app thunderbird
vacuum_mozillas firefox ~/.mozilla/firefox/
vacuum_mozillas thunderbird ~/.thunderbird

echo 'Done!'
```

---

### Post by cwhisperer on 2009-07-22
> **Fred Better said:**
> Thanks for the hints. Here's my version
```
#!/bin/bash
username=$(whoami)

function check_app {
    proc="$(ps aux | grep $username | grep -v $0 | grep $1 | grep -v grep)"
    if [ "$proc" != "" ]
    then
        echo "!!! Shutdown $1 first!"
        exit 1
    fi
}

function vacuum_mozillas {
    echo "Vacuuming $1..."
    find $2 -type f -name '*.sqlite' -exec sqlite3 -line {} VACUUM \;
}

check_app firefox
check_app thunderbird
vacuum_mozillas firefox ~/.mozilla/firefox/
vacuum_mozillas thunderbird ~/.thunderbird

echo 'Done!'
```

had to replace vacuum_mozillas thunderbird ~/.thunderbird with
vacuum_mozillas thunderbird ~/.mozilla-thunderbird

and works like a charm ;) great job

---

### Post by The Real Dave on 2009-09-06
Didn't really see much of an improvement to be honest, opened .2 seconds faster. Gereral operation was a bit quicker, but not much. My install is only about a week old though, so that could be why.

---

### Post by Barriehie on 2009-10-23
> **itisbasi said:**
> Should I run the script before starting every new session of Firefox?

I added mine to the crontab file to be run before my twice a week backups.

Barrie

---

### Post by paddy.melon on 2010-03-28
Worked quite well... why isn't this (at, say 1hr intervals), run inside firefox? Trash Collection... lol

---

### Post by cmcanulty on 2010-04-18
Great! Can you type exactly what I need to type into the scheduled tasks boxes to make it run once a month?

---

### Post by torturedutopian on 2010-05-11
Thanks for the tip ! Definitely makes a difference with Firefox. Not sure (yet) about Thunderbird 3 though ? Here I dunno why, Thunderbird eats a significant amount of CPU & disk usage at each startup. Probably due to indexing, but why each time ?

Cheers !

---

### Post by Sami Lehtinen on 2010-08-16
I were studing SQLite3 internals and remembered that FF uses it. After thinking a while I found out that Firefox most propably doesn't do vacuuming automaticly, which is true. But installing additional software to do it? That's no the way to do it.

These solutions in this thread are clearly way way over engineered. Why to install and compile additional software? Or write scripts or stuff like that? I think it's making things way more complex than they need to be. Even if it's very lovely geekish. 

It's possible to vacuum bases without installing any additional software or compiling anything. Like if you're using workstation without adming rights.

Just use FF's console to evalute following code:
```

Components.classes["@mozilla.org/browser/nav-history-service;1"].getService(Components.interfaces.nsPIPlacesDatabase).DBConnection.executeSimpleSQL("VACUUM");

```My work firefox data lost 90% of it's size and at home I got "only" 75% reduction.

---

