---
title: "Crontab appears to not be working"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by Dubslow on 2012-02-29
Hey everybody. 

I tried once to get my crontab working, because it seemed useful and cool; it didn't work.

At the time, when I tried to edit my crontab, nano would appear to be in some random folder in /tmp/[ahlphanumeric-crap]/filename.

I filled in the file at the time with a cp/backup command, and a command with output >> ~/text, e.g.
```
11 6 * * * collatz $(( $RANDOM % 20000 )) >> /home/bill/text
```
(Collatz is a bash script of my own making.) This was like April/May 2011, and I just checked, and there is no such file in my directory, despite the fact that the job is supposed to run daily. I also never saw the backup folder specified by the cp command I had in the file. The command I used was 'crontab -e'. I also tried 'sudo crontab -u root -e', but what I put in that file didn't work either.

The most remarkable thing is that despite being in /tmp/[alphanumeric-carp]/, when I just ran those commands today (9 months later) the crontab lines are still there, and still not doing anything.

So my questions are:
1) Why did crontab direct me to a file in /tmp?
2) Why (How?) did the file not change over 9 months, if it's in /tmp?
3) Why didn't the jobs run?
4) Should I instead directly edit /var/spool/cron/crontab, as in, would that actually work?

---

### Post by Dubslow on 2012-02-29
Should have started with Google...


[http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work](http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work)

---

### Post by papibe on 2012-02-29
Hi Dubslow.

crontab has a very limited environment. So here are a few tips:

[LIST]
[*]First, I would include the full path to your script.
[*]I'm almost sure that $RANDOM isn't available there. If you really want to use it, call it in a full bash environment.
[/LIST]
For instance, using crontab -e, you could test this:
```
# m h  dom mon dow   command
*/1 * * * * /path/to/script.sh

```
That executes every minute, so it's perfect for testing. Then sript.sh would be:
```
#!/bin/bash
echo $(( $RANDOM % 20000 )) >> /home/bill/text.txt

```
$RANDOM will be available because it is inside a script with a bash [crunchbang]("http://en.wikipedia.org/wiki/CrunchBang_Linux"). Don't forget to add execute permission to the script:
```
chmod a+x script.sh
```
I hope this helps, and tell us how it goes.
Regards.

---

### Post by Dubslow on 2012-02-29
Actually, what I meant but didn't say was that the link above helped solve my problems. The full path is among the discoveries I made there. I did run a few test cases and those appeared to work fine. Thanks though ;)

---

