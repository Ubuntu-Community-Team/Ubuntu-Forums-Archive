---
title: "yet another shutdown issue."
date: 2012-02-27
forum: New to Ubuntu
---

### Post by Jake5 on 2012-02-27
I just shutdown via the cli, I wanted to try the +m feature so I set it for five minutes.
It started shutting down, purple ubuntu screen and all, then it hung up on the line

Shutting down power management.

---

### Post by uRock on 2012-02-28
Can you share the command you used for shutdown?

---

### Post by Jake5 on 2012-02-28
Yeah, I'm sorry that would have been helpful,

```
sudo shutdown +5
```

it hung up on a black screen with six lines stating they  were shutting down different options such as bluetooth, the one it got stuck on was

```
switching off power management
```

---

### Post by matt_symes on 2012-02-28
Hi

Is there anything in the log files ?

I would check /var/log/syslog.

Kind regards

---

### Post by Jake5 on 2012-02-28
Sorry about the wait, 
checked the log files and didn't come up with anything,

I was trying to view them using

```
sudo /var/log/syslog
```

etc...

I would think the system would let me view the logs under sudo, perhaps I am missing a command, I tried the ol' Google search and thats what it told me to do, [http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/.]("http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/")

Or perhaps there are no log files, idk.
Being totally honest, I could use a bit of a briefing on log files to gain a better understanding.
I'll Google that next

---

### Post by audiomick on 2012-02-28
The command "shutdown" needs an option, I believe.

Try for instance
```
sudo shutdown -P +5
```to power off in 5 minutes

or
```
sudo shutdown -r now
```for an immediate re-start.

Have you looked at the man page? Man pages are often cryptic, but the one for shutdown is fairly readable, I find.

```
man shutdown
```

---

### Post by Jake5 on 2012-02-28
That was the problem audiomic, 
I told the system to bring itself down without asking it to power down afterwards. 
This sparks my interest as I am new to this, I've been stuck on the GUI for years.
Incidentally I learned my way around a few simple commands in MS-Dos when I was like eight,
However, upon getting into more advanced stuff and crashing my parents computer, twice,
I was banned from Dos.
Learning my way around the Terminal and I am Loving It!
Anyways, the revelation of what I did raises another question: 
Are there undesirable after effects of shutting the system down the way that I did,
```
sudo shutdown
```
other than having to power down manually? Hardware issues, whatever?

this came from
```
man shutdown
...
-P     Requests that the system  be  powered  off  after  it  has  been
              brought down
...
```

Thank you all once again, You guys are my Hero's!
Just converted both of my computers to 11.10 from the evil empire.
I would have been in way over my head if it weren't for all the help I've received here.

---

### Post by audiomick on 2012-02-28
> **Jake5 said:**
> 
Anyways, the revelation of what I did raises another question: 
Are there undesirable after effects of shutting the system down the way that I did,
```
sudo shutdown
```other than having to power down manually? Hardware issues, whatever?

I don't think so. The shutdown command goes back a long way, perhaps to back before a computer was able to turn itself off completely. I imagine that in the old days, it was normal to run the system down and then turn off the power. I'm guessing, but I expect the -P and -r options all came along a bit later.

Anyway, once shutdown has run, I believe the operating system is not running anymore. Turning off the power at the switch is only a problem if the operating system is still running. If you interrupt it in the middle of something, you can really mess it up. If the system is down, I don't think anything can go wrong.

---

### Post by Jake5 on 2012-02-28
Good to know
Thanks again.

---

