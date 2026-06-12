---
title: "crontab not redirecting complete output to file"
date: 2014-03-24
forum: New to Ubuntu
---

### Post by koteswararao2 on 2014-03-24
i am new to Linux Ubuntu I had a shell script which has to redirect 18000 lines output to file. output is truncating at 2006th line. is there any buffer settings for crontab
my shell script is below rcap.sh
```

 #!/bin/bash
/usr/local/bin/sshpass -p "xxxxxxxxx" ssh -2oStrictHostKeyChecking=no xxxxxxxx[EMAIL="xxxxxxxx@10.0.0.1"]@10.0.0.1[/EMAIL] "sh ip route bgp"
| awk '{print $2 }' > /home/ubuntuusr/scripts/mplsupid.txt

```
and my crontab entry is 
```

* * * * * /home/ubuntuusr/scripts/rcap.sh

```

when I run manually I am getting full 18000+ lines output to mplsupid.txt

when I run with crontab only 2006 lines only

---

### Post by whitesmith on 2014-03-24
This suggestion is a bit "out there," but you might bring up the file in an editor and examine line 2007 to see if it is malformed in some way. Buffer overrun may also be an issue.

---

### Post by koteswararao2 on 2014-03-24
manually I am getting full output with 18000 lines.

---

### Post by koteswararao2 on 2014-03-24
[**[COLOR=#000000]whitesmith[/COLOR]**]("http://ubuntuforums.org/member.php?u=664837") I am getting full output when I run same script manually

---

### Post by koteswararao2 on 2014-03-24
I am getting full output when I run same script manually

---

### Post by Impavidus on 2014-03-24
How long does the script need for running? Cron starts the script every minute, I imagine things go wrong when the new instance truncates the file and starts writing it from the beginning before the previous instance has finished.

---

### Post by koteswararao2 on 2014-03-24
when I run manually script is running for 4-8 sec only and I test for every 30 minutes 30 * * * *  still I am getting same truncating at 2006th line

---

### Post by Dave_L on 2014-03-24
To eliminate the possibility that the file is getting overwritten, you could timestamp the filename:
```
/home/ubuntuusr/scripts/mplsupid_`date +%Y%m%d_%H%M%S`.txt
```

To view any diagnostic messages, add to the end of the command:
```
 2>&1
```

---

### Post by koteswararao2 on 2014-03-24
I had added log file & I changed as /home/ubuntuusr/scripts/mplsupid_`date +%Y%m%d_%H%M%S`.txt
&

* * * * * /home/ubuntuusr/scripts/rcap.sh >> /home/ubuntuusr/scripts/script.log 2>&1

no error displaying in script.log

---

### Post by Habitual on 2014-03-24
Never, ever use passwords in shell scripts. EVER!

---

### Post by koteswararao2 on 2014-03-24
there is no syntax errors in my shell script. manually my script is running correctly and with correct output. when i scheduled with crontab running without errors but getting partial output.

---

### Post by Impavidus on 2014-03-24
When started by cron a script may have different (fewer) environment variables then when started from a terminal. The script may terminate prematurely because of a missing environment variable.

---

### Post by vasa1 on 2014-03-24
> **Impavidus said:**
> When started by cron a script may have different (fewer) environment variables then when started from a terminal. The script may terminate prematurely because of a missing environment variable.

I'm getting that feeling as well. If something works in a terminal, it doesn't mean it *will* work in cron (or crontab).

---

### Post by koteswararao2 on 2014-03-24
how to check & set environment variable of cron

---

### Post by Impavidus on 2014-03-25
The command **env** will list all currently defined environment variables. Run it once from a terminal and once from a cronjob and see the differences. Try to find out which of the environment variables is needed by the script and set it by adding something like```
export VARIABLE=value
```at the start of your script.

Sometimes however the environment variable you need is not static, but may be different each time you login or reboot. When you need a variable that looks like a random string this usually is the case. In this case you first need to extract the information you need from somewhere. As an example, I have a script (fancy wallpaper switcher) that needs the DBUS_SESSION_BUS_ADDRESS variable. It's defined in a terminal, but not in my cronjob. This environment variable can also be found in a file, so I had to define it in my script with```
export $(grep ^DBUS_SESSION_BUS_ADDRESS $HOME/.dbus/session-bus/$session)
```

---

