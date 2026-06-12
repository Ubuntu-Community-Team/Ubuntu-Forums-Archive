---
title: "Simple shell script for power management"
date: 2010-04-24
forum: Programming Talk
---

### Post by renkinjutsu on 2010-04-24
Recently, i've been more environmentally conscious and also, i'm trying to lower my energy bill. Thus, i've been experimenting with some tools made available in any decent linux distro, but my limited knowledge is holding me back from completion!

I'm on a desktop, so i don't run the gnome-power-manager daemon, nor do i have it installed because i have a minimalistic installation.

I've already written a shell script that runs as a daemon that tells the machine to ( suspend to ram | suspend to disk | reboot | shutdown ) depending on the arguments i send it. The frontend to that daemon, i named it pkstate. I have those pkstate commands bound to certain keystrokes.

While this works well, I wanted to implement another powersaving feature that would make things more convenient for me.
> I want to write a script that checks for any hardware input activity as well as cpu usage/load and all that

```

revised code below.

```

This is only my first day testing it.. Nothing has gone wrong YET, but i noticed some limitations in the script:
[COLOR="Silver"]1) it takes 15 minutes to poll mouse activity
       # what if i had no mouse activity, but instead i had kbd activity during this time?

2) it takes 15 minutes to poll keyboard activity
       # what if i had no keyboard activity, but instead mouse activity during this period?

3) If the previous two conditions are met, then i would experience an out-of-the-blue suspend, and i'd probably become frustrated. ( i also intend to share this script with other users )[/COLOR]
[COLOR="Silver"]----  I don't think i'll have the problems above anymore, but they still exist when looking at the code =\[/COLOR]
4) One other thing that would be nice is for the script to notice that there is some sort of load cpu/io that is going on.. anyone have any idea how to do that? the misc_lc variable works well, but what if say rtorrent was opened and it wasn't using the network at all. I wouldn't want my computer to be turned on if rtorrent's not doing anything.


I thought it was a fun project, but now i'm at my wit's end, i want to stop problems before they BECOME problems =]

anyway, i'm laying my script out there to absorb any improvements anyone might have.. Also it'd be nice if someone who has better scripting habits were to maybe implement his/her own script that is more efficient and gets the job done better than what my "rag-tag hackish, half-assed" scripting-self can come up with.

revised script (thanks tookyoutime):
```

#!/bin/zsh
echo "* pkidle activating"

# list of priority programs
alias misc_lc='ps aux | grep -w -c \
-e mplayer \
-e rtorrent \
-e deluge \
-e sshd\: \
-e scp \
-e ffmpeg \
-e mencoder \
-e lzma \
-e gunzip \
-e bzip \
-e tar \
-e svn \
-e git \
-e make \
-e gcc \
-e rpm \
-e yum \
-e mv \
-e cp \
-e rm \
-e rsync \
'
mins=15 # sets the number of minutes to wait before initiating powersaving actions (default 15)
secn=$(expr 60 \* $mins)

function envsuspend {
        # suspends the computer and takes precautions to ensure computer doesn't
        # immediately suspend itself upon awakening
        sustime=$(date)
        /home/moymoy/bin/pkstate --suspend && sleep 18
        DISPLAY=:0 su moymoy -c "notify-send --expire-time=50000 'Time Suspended' '$sustime'"
        first_etal=$(date +%s)
}


# set wc input from HID's
alias entropy='echo $( cat /dev/input/by-id/*mouse& pidmouse=$! ; cat /dev/input/by-id/*kbd& pidkbd=$! ;  sleep 2; kill $pidmouse $pidkbd 2> /dev/null ) | wc -c'

while true; do

        # define conditions and set variables
        [ $(entropy) -gt 1 ] && first_etal=$(date +%s)

        # Finds the delta in seconds for time between mouse/keyboard (HID) input
        now_etal=$(date +%s)
        delta_etal=$( expr $now_etal - $first_etal )


        if [ $delta_etal -gt $( expr 60 \* $( expr $mins + 2 ) ) ]; then
                first_etal=$(date +%s)
        elif [ $delta_etal -gt $secn ] && [ $(misc_lc) = 1 ]; then
                envsuspend
        fi  

        misc_lc > /home/moymoy/ramdisk/misc_lc
        echo $delta_etal > /home/moymoy/ramdisk/delta_etal

done

```

---

### Post by tookyourtime on 2010-04-24
Set a counter every time there is keyboard or mouse movement to the current time. 

Then if (system time - counter) > 15 minutes, go into sleep.

---

### Post by renkinjutsu on 2010-04-25
What an elegant solution you have!
i'll be posting up my revised script to the op in a moment

---

### Post by tookyourtime on 2010-04-25
That was quick.

Does it not cause a bit of a drain now though if you are checking the mouse and keyboard constantly?

---

### Post by renkinjutsu on 2010-04-25
I don't think so (not sure)

the revised script cycles once every 4+ seconds, so it's less than those /dev/sr1 polling daemons that ship with linux distros (edit: nevermind, those daemons poll every 16 seconds). Also, looking under htop, my script is dead last on the list even scrolling past all the kernel processes.
(new questions now popping up in my head [ gonna do a google search ] "what is console-kit-daemon and why is it running with 50+ threads?"

Oops! i forgot to account for the programs listed in misc.. will edit now

---

### Post by renkinjutsu on 2010-04-25
I just revamped my "revised" script.. i'm surprised it was able to operate for so long with all the silly bugs i had left in there! :p

---

