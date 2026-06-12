---
title: "Shell script to execute commands based off of log."
date: 2011-12-10
forum: Programming Talk
---

### Post by alden_pease on 2011-12-10
Hello.  I am having one hell of a time with Shorewall at the moment.  This is not necessarily a problem with Shorewall (but it definitely should be a feature).  I have repeated attempts from various IP address to "find" a way into my system.  They are being dropped by basic drop commands in the "rules" file, but this is cluttering up my syslog, and even rendering it unaccessible at some times due to the amount of data being logged into it.

So, what I want to create is a shell script that searches my syslog (will set it up via crontab to run), and then when it finds a specific value, run a command with that value.  I would expect some type of "for/while" loop or something along those lines, but please remember that I have never created shell scripts with loops before.

Here's an example of what I want to happen.  Search the syslog file at /var/log/syslog, line-by-line, for the value "Shorewall:net2fw".  Then, on that same line, find the instance "SRC=" (I would assume there is an equivalent to the strpos() command as in all C-Style languages?) and take the value following it to the instance of "DST=" (this would be the clients IP Address).  With that variable, drop it into the following command (with %v as the IP): "shorewall drop %v".

Thank you for your time everyone, this is very important.

---

### Post by Lars Noodén on 2011-12-10
A little more data is needed.  Please post an example in full of one of the lines containing "Shorewall:net2fw"  also post one or two lines that you don't want.

---

### Post by alden_pease on 2011-12-10
Here is the example you wanted.  Given this data from the syslog:



```
Dec 10 09:48:45 www kernel: [34088.972628] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:11:09:13:39:67:00:24:b2:b7:29:5a:08:00 SRC=71.191.241.208 DST=172.16.0.50 LEN=58 TOS=0x00 PREC=0x00 TTL=112 ID=958 PROTO=UDP SPT=36005 DPT=48489 LEN=38
Dec 10 09:48:28 www imapd: LOGOUT, user=xxxxx@xxxxx.xxx, ip=[::ffff:xxx.xxx.xxx.xxx], headers=0, body=0, rcvd=94734, sent=6652, time=27
Dec 10 09:48:45 www kernel: [34089.602264] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:11:09:13:39:67:00:24:b2:b7:29:5a:08:00 SRC=76.253.167.47 DST=172.16.0.50 LEN=131 TOS=0x00 PREC=0x00 TTL=111 ID=24163 PROTO=UDP SPT=53709 DPT=55077 LEN=111
Dec 10 09:48:46 www kernel: [34089.933442] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:11:09:13:39:67:00:24:b2:b7:29:5a:08:00 SRC=86.174.92.164 DST=172.16.0.50 LEN=95 TOS=0x00 PREC=0x00 TTL=106 ID=12357 PROTO=UDP SPT=58855 DPT=48489 LEN=75
Dec 10 09:48:46 www kernel: [34090.087666] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:11:09:13:39:67:00:24:b2:b7:29:5a:08:00 SRC=24.86.172.123 DST=172.16.0.50 LEN=58 TOS=0x00 PREC=0x00 TTL=115 ID=14223 DF PROTO=UDP SPT=55802 DPT=55077 LEN=38
Dec 10 09:48:03 www postfix/qmgr[2675]: D17DB70E: from=<xxxxx@xxxxx.xxx>, size=94137, nrcpt=1 (queue active)
Dec 10 09:48:46 www kernel: [34090.555409] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:11:09:13:39:67:00:24:b2:b7:29:5a:08:00 SRC=173.168.175.20 DST=172.16.0.50 LEN=95 TOS=0x00 PREC=0x00 TTL=51 ID=50793 PROTO=UDP SPT=54228 DPT=48489 LEN=75
```

I would like it to find the lines that are declared by Shorewall, and take the SRC value within it.  With that value, place it in the command "shorewall drop [value]".  Thank you.

EDIT: Notice the time codes in this log, as this was taken directly from the syslog (besides the masked email).  The times are mixed up, and with a pretty large difference too.

---

### Post by Lars Noodén on 2011-12-10
You should be able to do something like this with [awk](http://manpages.ubuntu.com/manpages/oneiric/en/man1/awk.1posix.html) and [xargs](http://manpages.ubuntu.com/manpages/oneiric/en/man1/xargs.1.html):

```

awk '$7 ~/^Shorewall:net2fw:/ {sub(/^SRC=/,"",$10);print $10}' /var/log/syslog | xargs shorewall drop

```

Or else like this:

```

tail -f /var/log/syslog | awk '$7 ~/^Shorewall:net2fw:/ {sub(/^SRC=/,"",$10);print $10}' | xargs shorewall drop

```

---

### Post by Lars Noodén on 2011-12-10
It can also be done without [xargs](http://manpages.ubuntu.com/manpages/oneiric/en/man1/xargs.1posix.html)

```

awk '$7 ~/^Shorewall:net2fw:/ {sub(/^SRC=/,"",$10);system("shorewall drop " $10)}' /var/log/syslog

```

tail -f mean take the most recent line(s) as they come

$7 ~// means take lines where the 7th column matches this pattern

sub means find and replace, and it's applied to the 10th column

---

### Post by alden_pease on 2011-12-10
Thank you.  I merged the commands to make this: ```
tail -f /var/log/syslog | awk '$7 ~/^Shorewall:net2fw:/ {sub(/^SRC=/,"",$10);system("shorewall drop " $10)}'
```

Now more on the education aspect, where is a good source to learn about "awk?"  Thank you.

---

### Post by Lars Noodén on 2011-12-11
> **alden_pease said:**
> Now more on the education aspect, where is a good source to learn about "awk?"  Thank you.

Fun stuff, isn't it? :)  I used to use perl for hacking on logs but awk is less complex.

If you're into print then the book [sed & awk](http://shop.oreilly.com/product/9781565922259.do) from O'reilly is a very good choice.  Online the choices are more sparse.  Lately, I've been finding the manual page to usually be enough.  awk is pretty simple.  

For sed, I recommend looking at the various lists of sed one-liners for ideas.

---

### Post by Lars Noodén on 2011-12-11
IBM has some good intro material:

[http://www.ibm.com/developerworks/linux/library/l-awk1/](http://www.ibm.com/developerworks/linux/library/l-awk1/)
[http://www.ibm.com/developerworks/linux/library/l-awk2/](http://www.ibm.com/developerworks/linux/library/l-awk2/)
[http://www.ibm.com/developerworks/linux/library/l-awk3/](http://www.ibm.com/developerworks/linux/library/l-awk3/)

And the awk community has a list of learning materials:

[http://awk.info/?Learn](http://awk.info/?Learn)

---

