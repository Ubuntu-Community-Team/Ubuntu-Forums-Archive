---
title: "HDD keeps disconnecting randomly"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by ShawnHeim on 2013-03-31
Hi, 

After I changed from windows to xubuntu my hdd has kept disconnecting randomly. Is this a sign of the drive going to break? Or is this due to a power saving feature with hdd drivers / ubuntu? 

hdd: Seagate Barracuda 3TB 7.2k 64MB
xubuntu: 12.10

Thanks for any help.

---

### Post by lincoln32 on 2013-03-31
I suspect your drive is heading south test it with disk utility but it will not always show a weak drive. it could be cables but I doubt it:p

---

### Post by robsablah on 2013-03-31
> **lincoln32 said:**
> I suspect your drive is heading south test it with disk utility but it will not always show a weak drive. it could be cables but I doubt it:p

In addition to this (thinking simply) if its an external check the connections are not loose....?

Are you able to provide more info to assist?
eg. 
1. is it internal or external?
2. check the syslog after it disconnects and post results - # tail -n 20 /var/log/syslog
3. age of the HDD
4. any other info that could assist us in diagnosing this one for you.

I hope this helps.

---

### Post by ShawnHeim on 2013-03-31
1. Internal drive
2. 
```

Mar 31 10:12:17 user-System-Product-Name rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1097" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Mar 31 10:15:49 user-System-Product-Name anacron[1245]: Job `cron.daily' terminated (mailing output)
Mar 31 10:15:49 user-System-Product-Name postfix/sendmail[3173]: fatal: open /etc/postfix/main.cf: No such file or directory
Mar 31 10:15:49 user-System-Product-Name anacron[1245]: Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail) exited with ststus 75
Mar 31 10:15:49 user-System-Product-Name anacron[1245]: Normal exit (1 job run)
Mar 31 10:17:02 user-System-Product-Name CRON[3175]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 31 10:25:36 user-System-Product-Name kernel: [ 2124.761065] show_signal_msg: 42 callbacks suppressed
Mar 31 10:25:36 user-System-Product-Name kernel: [ 2124.761071] mount.ntfs-3g[985]: segfault at 7f5cb3833390 ip 00007f5cb34c69bc sp 00007fffe9c7bb10 error 4 in libfuse.so.2.9.0[7f5cb34bf000+28000]
Mar 31 10:39:01 user-System-Product-Name CRON[3635]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Mar 31 10:55:37 user-System-Product-Name pulseaudio[1692]: [alsa-sink] alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Mar 31 10:55:37 user-System-Product-Name pulseaudio[1692]: [alsa-sink] alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_ctxfi'. Please report this issue to the ALSA developers.
Mar 31 10:55:37 user-System-Product-Name pulseaudio[1692]: [alsa-sink] alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.

```
3. Age 4 months
4. Usually happens when I'm away from my keyboard, possibly only when the computer is idle..

---

### Post by lincoln32 on 2013-03-31
I do not use sleep or hibernate but that would disconnect a hard disk drive. I think there are some known issues might want to just turn them off to test it for a while

---

### Post by ShawnHeim on 2013-03-31
I have now done a check of the drive, but the tool reported OK status on all tested things, not that it is proof that errors do not exist...
I have also tried to disable all power saving features what I found in settings and disabled screen saver etc. and so far the drive has not disconnected, but who knows, it might do it again in a second.

---

### Post by robsablah on 2013-03-31
> **ShawnHeim said:**
> 1. Internal drive
2. 
```

Mar 31 10:12:17 user-System-Product-Name rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1097" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Mar 31 10:15:49 user-System-Product-Name anacron[1245]: Job `cron.daily' terminated (mailing output)
Mar 31 10:15:49 user-System-Product-Name postfix/sendmail[3173]: fatal: open /etc/postfix/main.cf: No such file or directory
Mar 31 10:15:49 user-System-Product-Name anacron[1245]: Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail) exited with ststus 75
Mar 31 10:15:49 user-System-Product-Name anacron[1245]: Normal exit (1 job run)
Mar 31 10:17:02 user-System-Product-Name CRON[3175]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 31 10:25:36 user-System-Product-Name kernel: [ 2124.761065] show_signal_msg: 42 callbacks suppressed
Mar 31 10:25:36 user-System-Product-Name kernel: [ 2124.761071] mount.ntfs-3g[985]: segfault at 7f5cb3833390 ip 00007f5cb34c69bc sp 00007fffe9c7bb10 error 4 in libfuse.so.2.9.0[7f5cb34bf000+28000]
Mar 31 10:39:01 user-System-Product-Name CRON[3635]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Mar 31 10:55:37 user-System-Product-Name pulseaudio[1692]: [alsa-sink] alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Mar 31 10:55:37 user-System-Product-Name pulseaudio[1692]: [alsa-sink] alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_ctxfi'. Please report this issue to the ALSA developers.
Mar 31 10:55:37 user-System-Product-Name pulseaudio[1692]: [alsa-sink] alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.

```
3. Age 4 months
4. Usually happens when I'm away from my keyboard, possibly only when the computer is idle..



OK, 

Look from this line here:
Mar 31 10:25:36 user-System-Product-Name kernel: [ 2124.761071] mount.ntfs-3g[985]: segfault at 7f5cb3833390 ip 00007f5cb34c69bc sp 00007fffe9c7bb10 error 4 in libfuse.so.2.9.0[7f5cb34bf000+28000]

Its an NTFS drive that MAY (guessing here) have not disconnected from windows correctly - I think (without checking) you connect it to a windows machine, run a disk check and reboot twice and reconnect. Painful - i know :(

A quick google from a couple of readable bits above (love that trick) - error 4 in libfuse.so.2.9.0
Gives me this bug: [https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/1072270](https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/1072270)

Have a flick though there and see if either one of those help.

---

### Post by ShawnHeim on 2013-03-31
> **robsablah said:**
> OK, 

Look from this line here:
Mar 31 10:25:36 user-System-Product-Name kernel: [ 2124.761071] mount.ntfs-3g[985]: segfault at 7f5cb3833390 ip 00007f5cb34c69bc sp 00007fffe9c7bb10 error 4 in libfuse.so.2.9.0[7f5cb34bf000+28000]

Its an NTFS drive that MAY (guessing here) have not disconnected from windows correctly - I think (without checking) you connect it to a windows machine, run a disk check and reboot twice and reconnect. Painful - i know :(

And what can I do if I do not have windows in my system anymore?

---

### Post by robsablah on 2013-03-31
Bit of a pickle then.... Sorry dude, I can only give you suggestions at this point.
Got a friend / person who trusts you enough with their windows system?

---

### Post by robsablah on 2013-03-31
Something I just thought of, seeing as it is NTFS
Backup the data (if needed), Format to EXT3
This should over write any existing problems (unless its definitely a hardware fault) and avoid using the NTFS-3g driver

---

### Post by ShawnHeim on 2013-03-31
To backup data and reformat is like the last thing I would like to try since this happens to be my largest hdd. Maybe I can bug one of my friends with windows PCs to help me out with running a disk check and rebooting the drive. But what about upgrading libfuse from 2.9.0 to 2.9.2, would that help me?

Thanks for all the suggestions so far, I really appreciate it.

---

### Post by robsablah on 2013-03-31
Seems like that is the way to go from the bug.
I would suggest putting your input into the bug report (the line of code - when it happens, type of system etc. anything to help) and then report back if the update works or not.

As for the thanks, no worries at all. I'm sure if you lookup my threads here you'll see me asking some pretty green questions and was helped out by generous people in this community. Pay it forward ShawnHeim.

---

### Post by ShawnHeim on 2013-04-01
Seems like updating libfuse fixed the problem, at least for 24+ hours it hasn't disconnected now so I'm going to mark this thread as solved.

---

