---
title: "Cron Bash Sudo OpenVPN issue"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by Declan_K on 2014-01-26
Hi All
I am trying to automate my connection to my vpn proxy and am having an issue with cron.

Here is the code of my bash script, "/usr/local/bin/cloak.sh";
```
#!/bin/bash


LOG_FILE=/home/declan/log/cloak.log


LogEntry()
    {
        while read data
        do
            echo "$(date "+%Y %m %d %T") ; $data" >>$LOG_FILE 2>&1;
        done
    }


echo "---------------------" | LogEntry


if [ $1 -eq 1 ]
then
    echo "Turning Cloak On" | LogEntry 
    /etc/init.d/openvpn start proxpn.miami | LogEntry
else
    echo "Turning Cloak Off" | LogEntry
    /etc/init.d/openvpn stop | LogEntry
fi


echo "---------------------" | LogEntry
echo " " | LogEntry

```

When I run this scipt from a command line the VPN is turned on.
```
declan@mx:~/log$ wget http://ipecho.net/plain -O - -q ; echo
74.196.220.81 <<-- This is my real IP address
declan@mx:~/log$ sudo /usr/local/bin/cloak.sh 1 <<-- Turn the VPN on
declan@mx:~/log$ wget http://ipecho.net/plain -O - -q ; echo
173.0.8.33 <<-- This is my VPN IP address
declan@mx:~/log$ sudo /usr/local/bin/cloak.sh 0 <<-- Turn the VPN off
declan@mx:~/log$ wget http://ipecho.net/plain -O - -q ; echo
74.196.220.81 <<-- Back to my real IP address
declan@mx:~/log$

```

My issue is that when I run in in crontab, the VPN is not being turned on. Looking at the log file, the init.d script is being called by cron but if I check the IP address is still my local address.

I am using "sudo crontab -e" to edit the crontab, so it should be running as sudo, right?

Here are the entries in crontab
```
# Cloak on at midnight, off at 7:15AM
00 00 * * * /usr/local/bin/cloak.sh 1
15 07 * * * /usr/local/bin/cloak.sh 0
```

---

### Post by ian-weisser on 2014-01-26
When I try a crontab of "00 00 * * * /some/script", I get an error:
"/tmp/crontab.vBSoc8/crontab":26: bad command
errors in crontab file, can't install.

Those hours and minutes don't look right. Don't fill in the hours and minutes to two digits - the system usually doesn't expect that.
Are you getting an error when trying to install that crontab?

Try a crontab of "0 0 * * * /your/script" (which has expected values for hour and minute, and I can install)

---

### Post by Declan_K on 2014-01-27
I made the change to the cron job, but it does not have any affect. Per my log file, the bash script is being called at the correct time, with the correct paramter, but the IP address is still not changing.

Is there anything that would prevent a cronjob from running as sudo?

---

### Post by Declan_K on 2014-01-31
shameless bump.....

---

### Post by SeijiSensei on 2014-01-31
What happens if you just put the OpenVPN commands in crontab?
```

# Cloak on at midnight, off at 7:15AM
00 00 * * * /etc/init.d/openvpn start proxpn.miami  >> /var/log/openvpn
15 07 * * * /etc/init.d/openvpn stop >> /var/log/openvpn

```
I'd also try specifying the full path to proxpn.miami.

---

### Post by Declan_K on 2014-02-04
> **SeijiSensei said:**
> What happens if you just put the OpenVPN commands in crontab?
```

# Cloak on at midnight, off at 7:15AM
00 00 * * * /etc/init.d/openvpn start proxpn.miami  >> /var/log/openvpn
15 07 * * * /etc/init.d/openvpn stop >> /var/log/openvpn

```
I'd also try specifying the full path to proxpn.miami.

That also didn't work, but it did give me some error data in the log, which was a great help.
I added ```
[COLOR=#000000][FONT=Consolas]PATH[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]=/[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]usr[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/[/FONT][/COLOR][COLOR=#00008B][FONT=Consolas]local[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]sbin[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]:/[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]usr[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/[/FONT][/COLOR][COLOR=#00008B][FONT=Consolas]local[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]bin[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]:/[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]usr[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]sbin[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]:/[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]usr[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]bin[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]:/[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]sbin[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]:/[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]bin[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]:/[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]usr[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]games[/FONT][/COLOR]
``` to my crontab and now everything is working as intended.

Thanks for the help.
Declan

---

