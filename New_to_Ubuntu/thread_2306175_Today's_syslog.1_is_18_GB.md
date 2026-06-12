---
title: "Today's syslog.1 is 18 GB"
date: 2015-12-12
forum: New to Ubuntu
---

### Post by dave194 on 2015-12-12
A notice that my drive was almost out of space prompted me to notice that syslog.1 for today is 18 GB in size (and yesterday's zipped archive is 33 MB).  No one else uses the computer, and all I did was surf the web a few times briefly (16 MB total in/out for today according to vnstat) and disconnect when not surfing.  I have all automatic updates shut off (due to bandwidth constraints).  I'm a relative noobie, running Ubuntu 14.04 LTS for a few months now at home.  I installed nothing during that time except FileZilla and Bluefish Editor.  The syslog.1 file does not seem to be growing much now, so tail -n20 /var/log/syslog.1 didn't reveal anything helpful.  The syslog file (without .1) is 249 KB.  No other logs are unusually large.  Is there a way to shut off logging to syslog.1?  Or to set logging to a less verbose level for day-to-day operation?  Thanks, Dave

---

### Post by ian-weisser on 2015-12-13
/var/log/syslog.1 is *yesterday's* syslog. Nothing should be appending to it.
/var/log/syslog is today's syslog. Lots should be appending to it.

 A bit of poking around further in that huge syslog to determine the problem seems appropriate. 18GB is quite abnormal, and you want to know the problem!

After you have completed your investigation, you can safely replace syslog.1 with an empty file of similar name, if your storage space is an issue.

---

### Post by dave194 on 2015-12-13
Thank you, Ian.   To see what was logged most, I ran this command: 

```
less /var/log/syslog.1 | tr -s ' ' | cut -d' ' -f5 | sort | uniq -c | sort -rn
```

and found that nearly all of the logging was done by the kernel 

```
133025728  kernel:     157 NetworkManager[781]:     
154 ModemManager[698]:     
117 colord:     
102 ModemManager[708]:     
101 NetworkManager[778]:      
41 dbus[685]:      
33 ModemManager[683]:      
32 rtkit-daemon[1400]:      
22 rtkit-daemon[1393]:      
22 dbus[620]:      
20 NetworkManager[783]:      
16 udev-configure-printer:      
13 pppd[3188]:      
13 pppd[2375]:      
13 acpid:      
12 dnsmasq[2400]:
```  

Any suggestions as to what to do now, if this continues to occur? Thanks, Dave

---

### Post by nerdtron on 2015-12-13
What did you do before it happened? Did you install any software related to networking/VPN etc.
Also, we'll to see longer logs, maybe we can see if it could be related to a hardware problem.

---

### Post by dave194 on 2015-12-13
I didn't install anything or do anything unusual.  I surfed the web a bit around 6:30 a.m., then shut off the laptop, and surfed a few minutes again around 9:30 p.m.  But I do seem to recall seeing a system error message popup on screen a couple of times.  I dismissed them and kept doing what I was doing online, because I lacked the time to look into it.  Whatever was wrong seems to have righted itself after a reboot -- no more excessive logging.  Thank you, again.

---

### Post by Doug S on 2015-12-14
The "kernel" entries are pretty generic. Myself, I would try to break them down into more detailed bins, and find the dominant entry (or entries) and post examples back here for review and potential comment. For example, my syslog file is currently dominated by specific entries from my iptables rule set where they are blocking an ongoing e-mail issue:```
Dec 14 08:30:04 doug-64 kernel: [838124.574235] EMAIL BAD:IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:6c:be:e9:a7:f1:07:08:00 SRC=120.55.86.151 DST=my domain IP LEN=52 TOS=0x02 PREC=0x00 TTL=115 ID=20250 DF PROTO=TCP SPT=62247 DPT=25 WINDOW=8192 RES=0x00 CWR ECE SYN URGP=0
```

---

### Post by Habitual on 2015-12-14
[Chinese IP]("http://www.tcpiputils.com/browse/ip-address/120.55.86.151")
trying to send mail through or to your server...?
```
**[COLOR=#ff0000]SRC=120.55.86.151[/COLOR]** DST=my domain IP LEN=52 TOS=0x02 PREC=0x00 TTL=115 ID=20250 DF PROTO=TCP SPT=62247** [COLOR=#ff0000]DPT=25[/COLOR]**
```

You running a mail server on "my domain IP"?

---

### Post by Doug S on 2015-12-14
> **Habitual said:**
> [Chinese IP]("http://www.tcpiputils.com/browse/ip-address/120.55.86.151")trying to send mail through or to your server...?
@Habitual: My post was just an example, perhaps a poor one, for the OP, where I isolated the dominant "kernel:" entry in my file.
Yes, that IP was attempting to use my server a relay, and was being denied. Finally [my iptables rule set]("http://ubuntuforums.org/showthread.php?t=2304442&p=13397718#post13397718") kicked in and that IP address is now banned, but still logging attempts.
> **Habitual said:**
> You running a mail server on "my domain IP"?Yes.

As a side note: I have noticed a dramatic increase in email related bad stuff in the last 2 months, including an incredible increase in persistence, going on for days and days after they get on my "bad guy" list, and are then banned. To reduce log file clutter, I have moved a few of the culprits to my permanent "bad guy" list, which doesn't log.

OP: sorry for the tangent on your thread.

---

### Post by Doug S on 2015-12-14
> **jono6 said:**
> What 18GB ? o_0Hi and welcome to Ubuntu forums.

By "18GB" the OP meant that the file size of his /var/log/syslog file for one day was 18 Giga Bytes, which is a staggering size for a daily syslog file. However the OP also mentioned that there were 133025728  kernel lines, which is only 14 characters per line, but an average of 1540 lines per second (which seems incredible).

Hope this helps.

EDIT: Everybody. The basic math I did above raises an interesting point: Each "kernel:" line has 43 characters of overhead, before the payload message even starts (depending on your computer name, mine is 3 chars):
```

Dec 14 12:12:51 s15 kernel: [    0.000000] BIOS-e820: [mem 0x00000000cec06000-0x00000000ceffffff] usable
12345678901234567890123456789012345678901234567890
         1         2         3         4   4
Dec 14 12:12:51 s15 kernel: [    0.000000] BIOS-e820: [mem 0x00000000cf800000-0x00000000df9fffff] reserved


```So how could there be 133025728  of them?

---

### Post by TheFu on 2015-12-14
Rather than guessing, let's just ask the OP to post 50 lines with the errors/warnings?
I've seen this sort of thing with failing disk controllers or bad cables or a disk that was about to fail.

---

### Post by Doug S on 2015-12-14
> **TheFu said:**
> Rather than guessing, let's just ask the OP to post 50 lines with the errors/warnings?
I've seen this sort of thing with failing disk controllers or bad cables or a disk that was about to fail.+1. Yes of course, and that is what I suggested in post #6, but since "kernel: is so generic, I was suggesting to be sure to find and post the dominant messages.

---

### Post by dave194 on 2015-12-15
Thanks very much, Doug, Habitual and TheFu.  Your suggestions and comments are greatly appreciated.

Whatever happened must have been a one-time fluke, rather than a persistent problem.  The system reboot took care of it, and it has not happened again.

You raise some interesting questions.  But please forgive me if I lack the curiosity to investigate further at this time.  After all, I am simply an Ubuntu user due to economic necessity (and happy to deny Bill Gates the profits he would gain by emptying my wallet).  I apologize, but I'm quite happy to remain in ignorance of its inner workings, as long as the system does what I ask it to do when I log on.

If the nastiness rears its ugly head again in the future, I will be sure to re-visit this topic with more log data -- and hope that you will put up with such a layman as myself.

Thanks, again, very much for your help and your expertise!

---

