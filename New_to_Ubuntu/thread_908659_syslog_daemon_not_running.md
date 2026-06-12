---
title: "syslog daemon not running?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by robert shearer on 2008-09-02
Having run rkhunter it reports that the  syslog daemon is not running.
Rebooting has not fixed this.
How do I re-enable it?

---

### Post by robert shearer on 2008-09-04
bump

---

### Post by hyper_ch on 2008-09-04
```

sudo /etc/init.d/syslogkd start

```

```

sudo update-rc.d /etc/init.d/syslogkd defaults

```

---

### Post by robert shearer on 2008-09-04
Hmmm, running sudo /etc/init.d/syslogkd start results in sudo: /etc/init.d/syslogkd: command not found


what now?

and after re-installing syslogkd then running sudo update-rc.d /etc/init.d/syslogkd defaults   this is what I get   sudo update-rc.d /etc/init.d/syslogkd defaults
update-rc.d: /etc/init.d//etc/init.d/syslogkd: file does not exist

---

### Post by hyper_ch on 2008-09-04
yes, what now?
What would you do now?

---

### Post by robert shearer on 2008-09-04
> **hyper_ch said:**
> yes, what now?
What would you do now?

Well, having tried what I can with my (very) limited knowledge for the last three days and having posted here I guess I will re-install the whole o/s and if that doesn't fix it then I will throw in the towel and go find another o/s that works or maybe try to install the real-time kernel for plain vanilla Ubuntu?
I had hoped that eAR-OS would be an out-of-the-box audio easy distro but so far I have had many troubles including the firewall not starting on boot, atieventsd writing to disc every 5 seconds for no reason,the sysklogd failing every boot and repeated zombie sim-dock events.

---

### Post by hyper_ch on 2008-09-04
how about a simple typo in the code I gave? Did that cross your mind? I mean you know what I run and where from, did you ever look what's in there?

And the firewall start always... it's part of the kernel... beside you normally you don't need to worry about a firewall. This is not windows.

---

### Post by robert shearer on 2008-09-04
> **hyper_ch said:**
> how about a simple typo in the code I gave? Did that cross your mind? I mean you know what I run and where from, did you ever look what's in there?

And the firewall start always... it's part of the kernel... beside you normally you don't need to worry about a firewall. This is not windows.

I thank you for your attempt to help.

As a beginner it is a big ask for me to GUESS that you may have made a typo especially as the rkhunter log said "syslog daemon" you said "syslogkd" and it turns out to be sysklogd.

I got there in the end and will try the code with the new term.

The firewall comes with the eAR_OS distro and is CONFIGURED to start on boot.The fact that it doesn't I thought may be a symptom relating to the other problem of the logging daemon.

---

### Post by hyper_ch on 2008-09-04
but reading error messages helps ;)

---

### Post by robert shearer on 2008-09-04
So, running,   sudo /etc/init.d/sysklogd start   does start. Progress!

However running  sudo update-rc.d /etc/init.d/syslogkd defaults  returns this      sudo update-rc.d /etc/init.d/sysklogd defaults
update-rc.d: /etc/init.d//etc/init.d/sysklogd: file does not exist

and doing    gksudo gedit /etc/init.d/sysklogd   opens a file.

Thus the error message is in error. 

One step forward two back.

---

### Post by robert shearer on 2008-09-07
> **hyper_ch said:**
> ```

sudo /etc/init.d/syslogkd start

```

```

sudo update-rc.d /etc/init.d/syslogkd defaults

```

just to help anyone who saw this post the correct code is...

sudo /etc/init.d/sysklogd start

to start the logging daemon.  and....

sudo update-rc.d sysklogd defaults

to set the defaults.


The post whilst, presumably, well meant was both wrong AND typo-ed.

5 days of googling and experimenting found the right commands but could just have easily led back through the Windows!

Sometimes the help is worth what you pay for it.

---

