---
title: "Get strings out of XML file."
date: 2011-10-27
forum: Programming Talk
---

### Post by ryanrio95 on 2011-10-27
This file is created by gnome shell. I would like to have a sh script that can get the id's that have the highest score.
Like this:
It checks, doesn't matter how, which id has the highest score and than defines like this:
$APP1=firefox.desktop
$APP2=nautilus.desktop
$APP3=gedit.desktop
$APP4=thunderbird.desktop

with an maximum of five applications.

File Example:
<?xml version="1.0"?>
<application-state>
  <context id="">
    <application id="firefox.desktop" open-window-count="1" score="4636" last-seen="1319735831"/>
    <application id="gedit.desktop" open-window-count="0" score="2191" last-seen="1319734615"/>
    <application id="nautilus.desktop" open-window-count="0" score="3971" last-seen="1319734920"/>
    <application id="thunderbird.desktop" open-window-count="0" score="1432" last-seen="1319195188"/>
    <application id="exampleapp.desktop" open-window-count="0" score="243" last-seen="1319195188"/>
    <application id="another.desktop" open-window-count="0" score="241" last-seen="1319195188"/>
    <application id="otherapp.desktop" open-window-count="0" score="45" last-seen="1319195188"/>
  </context>
</application-state>

Please help me out.

Thanks in Advance, Ryan

---

### Post by cgroza on 2011-10-27
This perl script extracts your data:
```
use strict;
use XML::Simple;
my $file = $ARGV[0];
my $xml_tree = XML::Simple -> new() -> XMLin($file) -> {"context"}{"application"};;

foreach (keys %$xml_tree){
    my $score = $xml_tree -> {$_} -> {"score"};
    print "$_ $score\n";
}

```

---

### Post by gsmanners on 2011-10-27
I was bored so I took a shot (took a bit longer than I thought). This is in Python 2.x:

```
import libxml2
import sys

filelist = []

if sys.argv.__len__() > 1:
    sys.argv.pop(0)
    filelist = sys.argv

for name in filelist:
    f = open(name)
    input = libxml2.inputBuffer(f)
    reader = input.newTextReader("tst")
    apps = {}

    while reader.Read():
        if reader.Name() == 'application':
            apps[ reader.GetAttribute('id') ] = int( reader.GetAttribute('score') )
    f.close()

    for num in range(5):

        id = "nothing"
        score = 0
        for node in apps:
            if apps[node] > score:
                id = node
                score = apps[node]

        if score > 0:
            print "$APP%d=%s" % (num + 1, id)
            del apps[id]
```

---

### Post by ryanrio95 on 2011-10-30
> **gsmanners said:**
> I was bored so I took a shot (took a bit longer than I thought). This is in Python 2.x:

```
import libxml2
import sys

filelist = []

if sys.argv.__len__() > 1:
    sys.argv.pop(0)
    filelist = sys.argv

for name in filelist:
    f = open(name)
    input = libxml2.inputBuffer(f)
    reader = input.newTextReader("tst")
    apps = {}

    while reader.Read():
        if reader.Name() == 'application':
            apps[ reader.GetAttribute('id') ] = int( reader.GetAttribute('score') )
    f.close()

    for num in range(5):

        id = "nothing"
        score = 0
        for node in apps:
            if apps[node] > score:
                id = node
                score = apps[node]

        if score > 0:
            print "$APP%d=%s" % (num + 1, id)
            del apps[id]
```

Hi. Can i put python in a sh script??

Greets, ryan.

---

### Post by ofnuts on 2011-10-30
> **ryanrio95 said:**
> Hi. Can i put python in a sh script??

Greets, ryan.In a shell script, to extract the name of the top 5 apps, sorted by descending score:

```

grep "<application id" $data | sed -e 's/^<application id="\([^"]\+\)" open-window-count=".*" score="\([^"]\+\)".*$/\2 \1/' | sort -rn | head -5  | cut -d " " -f 2

```
(where $data is your input file)

---

### Post by cgroza on 2011-10-30
> **ryanrio95 said:**
> Hi. Can i put python in a sh script??

Greets, ryan.
You can call Python scripts in a bash script. In fact, this is what it does almost all the time: calls other scripts and programs.

---

### Post by Arndt on 2011-10-31
> **ryanrio95 said:**
> This file is created by gnome shell. I would like to have a sh script that can get the id's that have the highest score.
Like this:
It checks, doesn't matter how, which id has the highest score and than defines like this:
$APP1=firefox.desktop
$APP2=nautilus.desktop
$APP3=gedit.desktop
$APP4=thunderbird.desktop

with an maximum of five applications.

File Example:
<?xml version="1.0"?>
<application-state>
  <context id="">
    <application id="firefox.desktop" open-window-count="1" score="4636" last-seen="1319735831"/>
    <application id="gedit.desktop" open-window-count="0" score="2191" last-seen="1319734615"/>
    <application id="nautilus.desktop" open-window-count="0" score="3971" last-seen="1319734920"/>
    <application id="thunderbird.desktop" open-window-count="0" score="1432" last-seen="1319195188"/>
    <application id="exampleapp.desktop" open-window-count="0" score="243" last-seen="1319195188"/>
    <application id="another.desktop" open-window-count="0" score="241" last-seen="1319195188"/>
    <application id="otherapp.desktop" open-window-count="0" score="45" last-seen="1319195188"/>
  </context>
</application-state>

Please help me out.

Thanks in Advance, Ryan

A little more convoluted than I wanted it, but the main point is the 'xpath' command:

```
$ xpath -q -e '//application/attribute::*[name()="id" or name()="score"]' </tmp/xmll | sed -n '{N; s/\n//; p}' | sort -r -t' ' -n -k 3.8
 id="firefox.desktop" score="4636"
 id="nautilus.desktop" score="3971"
 id="gedit.desktop" score="2191"
 id="thunderbird.desktop" score="1432"
 id="exampleapp.desktop" score="243"
 id="another.desktop" score="241"
 id="otherapp.desktop" score="45"
```

---

### Post by ryanrio95 on 2011-11-30
Sorry guys,
but i don't get any of these scripts to work right now.

I don't know what i have to change to make them work.
I know i have to define the xml file to load.
But the rest..

Greets, Ryan.

---

### Post by Arndt on 2011-12-01
> **ryanrio95 said:**
> Sorry guys,
but i don't get any of these scripts to work right now.

I don't know what i have to change to make them work.
I know i have to define the xml file to load.
But the rest..

Greets, Ryan.

So what are the problems you encounter?

---

### Post by Bodsda on 2011-12-01
Python solution with a very dodgy string split and dict sort

```

lines = open("C:\\xml.txt", "r").readlines()
scores = {}

for i in lines:
    if 'score=' not in i:
        lines.remove(i)
    else:
        scores[i.split("=")[1].split(".")[0].strip('"')] = int(i.split("score=")[1].split()[0].strip('"'))
        
for key, value in sorted(scores.iteritems(), key = lambda (k,v): (v,k)):
    print "%s:  \t%s" % (key, value)

```

Bodsda

---

### Post by ryanrio95 on 2011-12-02
Okay, my actual goal was to make an script that auto runs on login (i know how to do this).
But i wanted to make an script that canges the gconf settings launcher of docky to load the ten most used applications.

So, i want to convert the ten most used applications out of the xml file to the gconf setting, only the top 10 and in order of highest score.

Greets.

---

### Post by Bodsda on 2011-12-02
> **ryanrio95 said:**
> Okay, my actual goal was to make an script that auto runs on login (i know how to do this).
But i wanted to make an script that canges the gconf settings launcher of docky to load the ten most used applications.

So, i want to convert the ten most used applications out of the xml file to the gconf setting, only the top 10 and in order of highest score.

Greets.

Should be fairly simple, most of the solutions already print the program name. The difficulty you may run into is if the app name is not the same as the command to launch the program. 

Have you got any code at all to attempt this yet or are you asking for someone to write this for you?

Bodsda

---

### Post by ryanrio95 on 2011-12-03
I'am actually asking to write this for me.
After that i will read the code and search what everything means.
So i can learn from that.

Greets

---

### Post by ryanrio95 on 2011-12-16
no one can help me with this anymore??

---

### Post by Arndt on 2011-12-16
> **ryanrio95 said:**
> no one can help me with this anymore??

How far did you get with the suggestions you were already given? Which ones did you try?

---

### Post by ryanrio95 on 2011-12-17
i have tried all of them. but none is working fine

greet

---

### Post by ju2wheels on 2011-12-18
Heres another solution, not sure if this output matches what you wanted though:

```

#!/bin/bash

usage()
{
    echo;
    echo "$0 <applications.xml>"
    echo;
}

if [ $# -ne 1 ]; then
    usage;
    exit 1;
elif [ ! -f "$1" ]; then
    echo "ERROR: Application xml file is not a file or does not exst...";
    exit 1;
fi

XMLFILE="$1";
MAXAPPS=5;

APPS=`grep '<application id' ${XMLFILE} 2>/dev/null | awk '{print $4 " " $2;}'`;

if [ ! -z "${APPS}" ]; then
    SORTEDAPPS="";
    
    while read appScore appName; do
	appScore=${appScore%\"};
	appScore=${appScore#*\"};

	appName=${appName%\"};
	appName=${appName#*\"};
	
	#This string spans two lines purposely, dont change it 
	SORTEDAPPS="${SORTEDAPPS}
${appScore} ${appName}";
    done <<< "${APPS}"

    SORTEDAPPS=`echo "${SORTEDAPPS}" | sort -n -r | head -n ${MAXAPPS}`;

    appCount=1;

    while read appScore appName; do
	echo "\$APP${appCount}=${appName}";
	appCount=$[ ${appCount} + 1 ];
    done <<< "${SORTEDAPPS}"
fi

```

Sample run:
```

user@ubuntu:~/Desktop$ cat apps.xml 
<?xml version="1.0"?>
<application-state>
<context id="">
<application id="firefox.desktop" open-window-count="1" score="4636" last-seen="1319735831"/>
<application id="gedit.desktop" open-window-count="0" score="2191" last-seen="1319734615"/>
<application id="nautilus.desktop" open-window-count="0" score="3971" last-seen="1319734920"/>
<application id="thunderbird.desktop" open-window-count="0" score="1432" last-seen="1319195188"/>
<application id="exampleapp.desktop" open-window-count="0" score="243" last-seen="1319195188"/>
<application id="another.desktop" open-window-count="0" score="241" last-seen="1319195188"/>
<application id="otherapp.desktop" open-window-count="0" score="45" last-seen="1319195188"/>
</context>
</application-state>
user@ubuntu:~/Desktop$ ./topapps.sh apps.xml 
$APP1=firefox.desktop
$APP2=nautilus.desktop
$APP3=gedit.desktop
$APP4=thunderbird.desktop
$APP5=exampleapp.desktop

```

Hope that helps.

---

### Post by ryanrio95 on 2011-12-20
this is how i wanted it to be.
really thanks, but i have a little problem, sorry.

when i run topapps.sh, i get this error:
topapps.sh: 36: Syntax error: redirection unexpected

so it has something to do with line 36 but i don't know what.

greets

---

### Post by ju2wheels on 2011-12-21
Can you attach the file you are using, Im not getting that error. Did you double check that you copied it correctly and that lines 34-35 span two lines as shown in the sample?

Also are you editing this file on Windows at all and then moving it onto your Ubuntu box, or doing all the editing in Ubuntu?

---

### Post by ryanrio95 on 2011-12-21
yes, i didn't change anything in the file and line 34 and 35 are spanning two lines.
maybe a need an dependency to make it work?

greeets

---

### Post by ryanrio95 on 2011-12-21
i already got it.
i wasn't using:
./topapps.sh
but:
sh topapps.sh

so now it's working :)

thanks, i really appreciate your work and do you need credits for it?

greets

Edit: how could i define an gconf setting like this? it only shows file:///usr/share/applications/

gconftool-2 --type list --set  /apps/docky-2/Docky/Interface/DockPreferences/Dock1/Launchers --list-type string "[file:///usr/share/applications/ $APP1 ,file:///usr/share/applications/ $APP2 ,file:///usr/share/applications/ $APP3 ,file:///usr/share/applications/ $APP4 ,file:///usr/share/applications/ $APP5 ]"

---

### Post by ryanrio95 on 2011-12-21
no one knows how to do this?

---

### Post by Vaphell on 2011-12-21
do i see spaces between file:///usr/share/applications/ and $APPx?

---

### Post by ryanrio95 on 2011-12-21
yes, but when i don't use spaces it also didn't work.
even:

echo "$APP1"

doesn't work

so i thought it's because of $APP1 isn't declared.
this is in the script. but i don't know how to declare the $APPx in this script.

greets,

---

### Post by Vaphell on 2011-12-21
if you take the script from #17 and replace the part at the end
```
    appCount=1;

    while read appScore appName; do
	echo "\$APP${appCount}=${appName}";
	appCount=$[ ${appCount} + 1 ];
    done <<< "${SORTEDAPPS}"
```with
```
  str_list=;

  while read appScore appName
  do
    str_list="${str_list}, file:///usr/share/applications/${appName}"
  done <<< "${SORTEDAPPS}"
  str_list=${str_list#,}
  echo gconftool-2 --type list --set /apps/docky-2/Docky/Interface/DockPreferences/Dock1/Launchers --list-type string "[$str_list]"
``` you should be good to go. I have **echo gconftool-2 ...** only because i wanted to see if the command is properly set up

---

### Post by ryanrio95 on 2011-12-22
oh yeah,

i love it. really thanks.

cheers, ryan.

---

