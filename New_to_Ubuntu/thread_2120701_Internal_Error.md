---
title: "Internal Error"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by daniell59 on 2013-02-27
Everytime I use the sound recorder, I get an internal error when saving the file. It does not prevent me from using it however. Is this a bug? How can I report it?

Ubuntu 12.04 64

Thanks

---

### Post by TheFu on 2013-02-27
What do your log files show?
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

It is more likely that your system is the issue, but you may have found an issue too.

---

### Post by daniell59 on 2013-02-27
> **TheFu said:**
> What do your log files show?
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

It is more likely that your system is the issue, but you may have found an issue too.

I will be happy to check my log files if you tell me how to.

Thanks for the input.

---

### Post by audiomick on 2013-02-27
Did you actually look at that link? It is about how to search your log files for error messages...

---

### Post by daniell59 on 2013-02-27
> **audiomick said:**
> Did you actually look at that link? It is about how to search your log files for error messages...

I did look at the link. Sorry to say that it is not clear to me.

---

### Post by daniell59 on 2013-02-27
I just figured out how to view the log. Now what do I look for?

eb 27 07:36:52 daniel-P5Q-PRO rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="908" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Feb 27 07:37:06 daniel-P5Q-PRO anacron[1072]: Job `cron.daily' terminated
Feb 27 07:37:06 daniel-P5Q-PRO anacron[1072]: Normal exit (1 job run)
Feb 27 08:02:44 daniel-P5Q-PRO dbus[859]: [system] Activating service name='org.debian.apt' (using servicehelper)
Feb 27 08:02:45 daniel-P5Q-PRO AptDaemon: INFO: Initializing daemon
Feb 27 08:02:45 daniel-P5Q-PRO dbus[859]: [system] Successfully activated service 'org.debian.apt'
Feb 27 08:02:45 daniel-P5Q-PRO AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Feb 27 08:02:45 daniel-P5Q-PRO AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'flashplugin-installer'), dbus.String(u'libpurple-bin'), dbus.String(u'libpurple0'), dbus.String(u'software-center'), dbus.String(u'thunderbird'), dbus.String(u'thunderbird-globalmenu'), dbus.String(u'thunderbird-gnome-support'), dbus.String(u'thunderbird-locale-en'), dbus.String(u'thunderbird-locale-en-us'), dbus.String(u'transmission-common'), dbus.String(u'transmission-gtk'), dbus.String(u'unity-greeter')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Feb 27 08:02:45 daniel-P5Q-PRO AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/9ecf1e3826f34c22887f977bed9eecd0
Feb 27 08:02:45 daniel-P5Q-PRO AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/9ecf1e3826f34c22887f977bed9eecd0
Feb 27 08:02:45 daniel-P5Q-PRO AptDaemon.Worker: INFO: Committing packages: dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'flashplugin-installer'), dbus.String(u'libpurple-bin'), dbus.String(u'libpurple0'), dbus.String(u'software-center'), dbus.String(u'thunderbird'), dbus.String(u'thunderbird-globalmenu'), dbus.String(u'thunderbird-gnome-support'), dbus.String(u'thunderbird-locale-en'), dbus.String(u'thunderbird-locale-en-us'), dbus.String(u'transmission-common'), dbus.String(u'transmission-gtk'), dbus.String(u'unity-greeter')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Feb 27 08:02:47 daniel-P5Q-PRO AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/9ecf1e3826f34c22887f977bed9eecd0
Feb 27 08:03:07 daniel-P5Q-PRO dbus[859]: [system] Reloaded configuration
Feb 27 08:03:08 daniel-P5Q-PRO dbus[859]: [system] Reloaded configuration
Feb 27 08:06:05 daniel-P5Q-PRO dbus[859]: [system] Reloaded configuration
Feb 27 08:06:26 daniel-P5Q-PRO AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/9ecf1e3826f34c22887f977bed9eecd0
Feb 27 08:07:25 daniel-P5Q-PRO AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Feb 27 08:07:25 daniel-P5Q-PRO AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/dd712f28e7f54635a22bf4c6faa7963a
Feb 27 08:07:25 daniel-P5Q-PRO AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/dd712f28e7f54635a22bf4c6faa7963a
Feb 27 08:07:26 daniel-P5Q-PRO AptDaemon.PackageKit: INFO: Get updates()
Feb 27 08:07:27 daniel-P5Q-PRO AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/dd712f28e7f54635a22bf4c6faa7963a
Feb 27 08:12:45 daniel-P5Q-PRO AptDaemon: INFO: Quitting due to inactivity
Feb 27 08:12:45 daniel-P5Q-PRO AptDaemon: INFO: Quitting was requested
Feb 27 08:17:01 daniel-P5Q-PRO CRON[5308]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 27 08:52:41 daniel-P5Q-PRO kernel: [ 5269.888590] show_signal_msg: 36 callbacks suppressed
Feb 27 08:52:41 daniel-P5Q-PRO kernel: [ 5269.888593] gnome-sound-rec[5465]: segfault at 28 ip 000000000040cdf8 sp 00007fff5b907580 error 6 in gnome-sound-recorder[400000+10000]
Feb 27 09:17:01 daniel-P5Q-PRO CRON[6485]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 27 10:17:01 daniel-P5Q-PRO CRON[6566]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 27 11:17:01 daniel-P5Q-PRO CRON[6613]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 27 12:17:01 daniel-P5Q-PRO CRON[6681]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 27 12:43:24 daniel-P5Q-PRO dbus[859]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Feb 27 12:43:24 daniel-P5Q-PRO AptDaemon: INFO: Initializing daemon
Feb 27 12:43:24 daniel-P5Q-PRO AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Feb 27 12:43:24 daniel-P5Q-PRO dbus[859]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Feb 27 12:43:24 daniel-P5Q-PRO AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Feb 27 12:43:24 daniel-P5Q-PRO AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/7acdb30eb8f5445297d92990968b95d6
Feb 27 12:43:24 daniel-P5Q-PRO AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/7acdb30eb8f5445297d92990968b95d6
Feb 27 12:43:25 daniel-P5Q-PRO AptDaemon.PackageKit: INFO: Get updates()
Feb 27 12:43:25 daniel-P5Q-PRO AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/7acdb30eb8f5445297d92990968b95d6

---

### Post by TheFu on 2013-02-27
> **daniell59 said:**
> I did look at the link. Sorry to say that it is not clear to me.

This is not point-n-click. 

* Open a terminal or shell.
* Use the command from that link. Copy/paste.
* Review at the output.
If it is not clear what the issue is, post the relevant output here.  
Posting non-relevant output doesn't help.


Update:
I see you found how to view a log file. There was a line about sound recorder inside it. Take parts of that line and use google.  Doing that I found this: [https://bugzilla.redhat.com/show_bug.cgi?id=100774](https://bugzilla.redhat.com/show_bug.cgi?id=100774) which may or may not have anything to do with your situation.  Carefully read the entire page to see what is relevant or not.

---

### Post by daniell59 on 2013-02-27
I googled it but could not find any problem similar to mine. As I previously stated, it works properly, just gives me the error message.
Any additional advice will be appreciated.

---

### Post by audiomick on 2013-02-27
> **daniell59 said:**
> I just figured out how to view the log. Now what do I look for?
...

Feb 27 08:52:41 daniel-P5Q-PRO kernel: [ 5269.888590] show_signal_msg: 36 callbacks suppressed
[COLOR="Red"]Feb 27 08:52:41 daniel-P5Q-PRO kernel: [ 5269.888593] gnome-sound-rec[5465]: segfault at 28 ip 000000000040cdf8 sp 00007fff5b907580 error 6 in gnome-sound-recorder[400000+10000][/COLOR]
Feb 27 09:17:01 daniel-P5Q-PRO CRON[6485]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 27 10:17:01 daniel-P5Q-PRO CRON[6566]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 27 11:17:01 daniel-P5Q-PRO CRON[6613]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 27 12:17:01 daniel-P5Q-PRO CRON[6681]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)...

My guess would be the line I've marked red, but I have no idea what it means.

---

### Post by daniell59 on 2013-02-27
I think that I was not saving it properly. Previously, I would close the program, then save it when asked. This time I first stopped it, then saved it properly. I don't know whether I should mark it as solved.

---

### Post by audiomick on 2013-02-27
> **daniell59 said:**
>  I don't know whether I should mark it as solved.

If the error message has stopped appearing, and you feel you have found an answer, yes you should mark the thread as solved.

---

