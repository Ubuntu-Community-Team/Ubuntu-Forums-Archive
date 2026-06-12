---
title: "Little project - where to start??"
date: 2005-07-23
forum: Programming Talk
---

### Post by senshisteph on 2005-07-23
My internet connection is unstable and needs disconnecting and reconnecting when it freezes, but my partner is scared of the command line and wakes me up to do it for him if it freezes... I'm getting kind of tired, so I'd like to make him a little gui that has a 'disconnect' button which runs the command 'eciadsl-stop', takes password and then when it's stopped display a note to unplug the modem for 20 seconds, and a 'connect' button which runs 'eciadsl-start', again takes password if needed and displays a connection successful/failed message.

Sounds like it ought to be fairly simple (in fact I bet it's been done but I want to have a go myself just as a learning experience), but the trouble is I don't have a clue where to start - the only programming I've done is some fairly low-level stuff in VB6. 
Can anyone give me some advice on what language would be best and where I should look for information - e.g. good websites and such?
Thanks!  :grin:

---

### Post by DJ_Max on 2005-07-23
This is farely simple. Any high-leve language like Python, Ruby or even Perl would be easy. If I get the time, I may whip one up, unless someone beats me to the punch.

---

### Post by senshisteph on 2005-07-23
[QUOTE=DJ_Max]This is farely simple. Any high-leve language like Python, Ruby or even Perl would be easy. If I get the time, I may whip one up, unless someone beats me to the punch.[/QUOTE]

Thanks - any info on the best places to find out more about these languages? I thought it would make a nice beginner project for me  ;-)

Edit: D'uh - just found lots of good links in the 'how did you learn to program' thread - silly me  ;-)

---

### Post by tomchuk on 2005-07-24
I think anything but a shell script is overkill for this. Take a look at zenity for creating gtk dialogs from a script

```

#!/bin/bash

ZEN="/usr/bin/zenity --title Reconnector"

# 20 second countdown in fives
function countdown() {
    for i in $(seq 0 5 100)
    do
        echo ${i}
        sleep 1
    done
}

${ZEN} --question --text="Reset Internet Connection?"

# if clicked 'OK' reset connection, else exit
if [[ "${?}" -eq "0" ]]
then
    /usr/bin/gksudo eciadsl-stop
else
    exit 1
fi

${ZEN} --info --text "Please unplug modem, click OK when you have done this"

countdown | ${ZEN} --progress --auto-close --text "Waiting 20 seconds"

${ZEN} --info --text "Please plug in the modem"

gksudo eciadsl-start

# did we reconnect alright?
if [[ "$?" -eq "0" ]]
then
    ${ZEN} --info --text="Reconnected"
    exit 0
else
    ${ZEN} --error --text="Oops, there was a problem, run this program again"
    exit 1
fi

```

---

### Post by DJ_Max on 2005-07-24
[QUOTE=senshisteph]Thanks - any info on the best places to find out more about these languages? I thought it would make a nice beginner project for me  ;-)

Edit: D'uh - just found lots of good links in the 'how did you learn to program' thread - silly me  ;-)[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=50916](http://ubuntuforums.org/showthread.php?t=50916)

---

### Post by senshisteph on 2005-07-24
Thanks guys, now I have lots of resources and a 'model answer' for if I get stuck - much appreciated :D

---

