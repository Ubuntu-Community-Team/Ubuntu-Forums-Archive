---
title: "Strange crontab-script interaction (bash)"
date: 2013-04-06
forum: Programming Talk
---

### Post by Garrigus Carraig on 2013-04-06
I'm running Ubuntu 12.04 and bash. I've written a pair of shell scripts that allow me to set an alarm which, after ringing, unsets itself. The first, [FONT=courier new]alarmset[/FONT], allows me to enter a time and modifies the alarm line in the crontab. That line launches the second script, [FONT=courier new]alarmring[/FONT], which launches a radio player in a browser window and then comments out the alarm line in the crontab.

[FONT=courier new]alarmring[/FONT] is behaving strangely. If I run it myself directly, it performs both actions: it launches the browser window and edits the crontab. But if I run [FONT=courier new]alarmset[/FONT], when the crontab launches [FONT=courier new]alarmring[/FONT] at the appointed time, [FONT=courier new]alarmring[/FONT] edits the crontab, but does not launch the browser window. 

Finally, when crontab runs [FONT=courier new]alarmring[/FONT], it ignores the [FONT=courier new]set -x[/FONT] command, whereas when I run it directly, [FONT=courier new]set -x[/FONT] is executed. So it's as though the crontab is skipping the first ten lines.

Any ideas on what's going on? I'll paste the two scripts and the crontab below.

** alarmset:**
```
#!/bin/bash
    
    # alarmset
    
    set -x
    
    usage()
    { echo "alarmset [ hour minute | -h ]" }
    
    editcrontab() 
    { 
        echo $'/alarmring/s/^\(.*\)\(\* \* \*\)/'$2$' '$1$' \\2/' > ~/Documents/crontab_script.txt 
        crontab -l | sed --file=/home/username/Documents/crontab_script.txt > ~/Documents/new_crontab.txt crontab ~/Documents/new_crontab.txt 
    }

    ### MAIN 
    case $# in 
        2 ) editcrontab $1 $2 ;; 
        * ) usage 
            exit ;; 
    esac
    
    set +x 
```

**alarmring:**
```
#!/bin/bash
    
    # alarmring
    
    set -x
    
    env DISPLAY=:0
    
    # Ring the alarm : launch BBC World Service in Firefox 
    firefox --new-window http://www.bbc.co.uk/radio/player/bbc_world_service
    
    # Unset the alarm : comment out the alarm line in the crontab 
    crontab -l | sed '/alarmring/s/^/#/1' > ~/Documents/new_crontab.txt 
    crontab ~/Documents/new_crontab.txt
    
    set +x 
```

**crontab:**
```
SHELL=/bin/bash 
    PATH=~/bin:/usr/bin:/bin 
    # 
    # m h dom mon dow command 
    53 07 * * * /home/username/bin/alarmring

```

---

### Post by schragge on 2013-04-06
> **Garrigus Carraig said:**
> But if I run [FONT=courier new]alarmset[/FONT], when the crontab launches [FONT=courier new]alarmring[/FONT] at the appointed time, [FONT=courier new]alarmring[/FONT] edits the crontab, but does not launch the browser window.
This ```
env DISPLAY=:0
``` just displays environment on the screen (or sends it by mail when run from crontab), but doesn't set $DISPLAY for firefox. Instead, do this
```
 
    # Ring the alarm : launch BBC World Service in Firefox 
 [COLOR=#ff0000]DISPLAY=:0[/COLOR] firefox --new-window http://www.bbc.co.uk/radio/player/bbc_world_service

```
It probably doesn't ignore the *set -x* either, cron just sends the output of all commands by mail. Run *mailx* in terminal to see your mailbox, or just ```
more /var/mail/$USER
```

BTW, wouldn't using [at](http://manpages.ubuntu.com/manpages/precise/en/man1/at.1.html) be simpler?

---

### Post by Garrigus Carraig on 2013-04-06
Well, that was fast and easy. Thank you, schragge. I'm a little unclear on the syntax: Does [FONT=courier new]DISPLAY=:0[/FONT] need to be on the same line as the [FONT=courier new]firefox[/FONT] command?

---

### Post by rnerwein on 2013-04-06
hi
my crontab looks (every 2 minutes): */2 * * * * /home/richi/tmp/ff
my script ff:
# not "env" --> export
DISPLAY=:0.0
export DISPLAY
/usr/bin/firefox --new-window [http://www.bbc.co.uk/radio/player/bbc_world_service](http://www.bbc.co.uk/radio/player/bbc_world_service)

this works for me ! 
and another hint is: for crontab jobs - always use the full pathname !!! ;-)
good luck
ciao
ups - schragge was faster :-)

---

### Post by schragge on 2013-04-06
> **Garrigus Carraig said:**
> Does [FONT=courier new]DISPLAY=:0[/FONT] need to be on the same line as the [FONT=courier new]firefox[/FONT] command?There are two options: either on the same line like what I did (then it applies only to the command it prefaces), or on a separate line, then you need to *export DISPLAY* like what **rnerwein** did. In the last case, it applies to all commands in the script that follow it.

---

### Post by Garrigus Carraig on 2013-04-06
Thanks, rnerwein, and thanks for the pathname tip. :)

schragge: I don't know about [FONT=courier new]at[/FONT]; I'll look into it. I'm a noob & glad to have come this far! :D

---

### Post by Garrigus Carraig on 2013-04-06
Thanks again, schragge. One more thing: Is [FONT=courier new]at[/FONT] Ubuntu specific? :confused:

---

### Post by schragge on 2013-04-06
No, it's part of the [POSIX standard]("http://pubs.opengroup.org/onlinepubs/9699919799/utilities/at.html"). On Debian-based distributions it can be installed with ```
sudo apt-get install at
```

---

### Post by Garrigus Carraig on 2013-04-06
Haha well I've been playing around with [FONT=courier new]at[/FONT], and discover indeed that it does exactly what I needed. Ah well, I got some good shell script writing practice. And I've learned that at my level, anything I want to implement has probably already been implemented. :p

---

