---
title: "How can I stop crontab from messing up this super simple BASH script?"
date: 2010-08-25
forum: Programming Talk
---

### Post by prupert on 2010-08-25
I have a strange issue, relating to running a BASH script via cron (invoked via crontab -e).

Here is the script:

```
#!/bin/bash

SIG1="$(iwconfig wlan0 | awk '/Quality=/ { print $2} ' | cut -c 9-10)"
SIG2="$(iwconfig wlan0 | awk '/Quality=/ { print $2} ' | cut -c 12-13)"

echo "$SIG1:$SIG2" >> test.txt
exit
```
When run from the commandline, I get the expected output of XX:XX (e.g. 45:70) echoed to the end of the text file. However, when I run the script via cron (using crontab -e) and the following entry:

```
* * * * * bash /home/rupert/test.sh
```

I just get the colon (:) echoed to the text file, the values SIG1 and SIG2 aren't printed and I have no idea why. Why would running via cron mess up the script?

FWIW, here is the output of iwconfig wlan0 with no additional processing:

```
wlan0     IEEE 802.11abgn  ESSID:"plumternet"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:18:84:2A:68:AD
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
I am doing all this because I want to display the WiFi Link Quality value "46/70" on an LCD screen and the program I use does this by reading a text file. However, when run via cron, the values get lost...???

I am using cut -c 9-10 and cut -c 12-13 because I was thinking the "/" might be causing an issue in the script, I'd be happy to just use cut -c 9-13, but I thought it might fix the issue, but it didn't.

Help!!

---

### Post by spjackson on 2010-08-25
When run from cron, PATH is usually different from the PATH of a login shell. I would guess that iwconfig is not in the path when run from cron. I suggest you use the full path in your script, i.e. /sbin/iwconfig .

---

### Post by prupert on 2010-08-25
Ahh, awesome, that fixed it. Is there a way to set the PATH for cron (when invoked via crontab -e) so it is the same as the user's PATH.

Here is the results of your efforts (its an LCD screen showing various info for a headless server, including WiFi strength):

[[IMG]http://img835.imageshack.us/img835/4175/20100825122413.jpg[/IMG]](http://img835.imageshack.us/i/20100825122413.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by mobilediesel on 2010-08-25
> **prupert said:**
> Is there a way to set the PATH for cron (when invoked via crontab -e) so it is the same as the user's PATH.

When you edit the crontab via **crontab -e** you can just enter the path like this:
```
PATH=/usr/bin:/bin:/usr/local/bin
```
add whatever other paths you might want, separated by colons "**:**"

I have mine at the top of the crontab but I don't think its position matters.

---

