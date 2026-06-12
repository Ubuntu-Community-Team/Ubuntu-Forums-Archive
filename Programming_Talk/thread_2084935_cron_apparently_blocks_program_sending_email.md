---
title: "cron apparently blocks program sending email"
date: 2012-11-16
forum: Programming Talk
---

### Post by agillator on 2012-11-16
I have written a short perl program to check specific files, create and email a report using Net::SMTP_auth. When run in a terminal it runs perfectly. However, when run as a cron job syslog shows it running, shows no errors, but there is no email. I can only assume there is something about cron that is blocking the output. I have been careful to ensure the only thing the program does is send an email, there is no other output and no messages printed. MAILTO in cron is set to "" but since I am not asking cron to mail anything that should make no difference. I have no qualms about using the bigger hammer solution, however in this case I can't figure out where to apply the hammer. What about cron am I missing?

---

### Post by Bachstelze on 2012-11-16
Check your Postfix logs.

---

### Post by agillator on 2012-11-16
I'm not running postfix or any email server. The program (i.e. the Net::SMTP_auth module) contacts the ISP SMTP server directly. There is no other program or server that it should be going through other than what is required to make and maintain a TCP/IP  connection. The module handles the SMTP protocol requirements.

---

### Post by agillator on 2012-11-17
Problem solved. [www.ubuntuforums.org/showthread.php?t=1930738](www.ubuntuforums.org/showthread.php?t=1930738) led me to the solution. In short, cron passes a very limited and 'clean' environment to programs it is executing. My program depends on an environment variable that is in my 'normal' environment but not the one cron passes. I added this variable in my crontab as VARIABLE=VALUE in the global section and everything is now fine. If you are facing a similar problem, how you find the variable(s) is up to you. The brute force method, of course, is to add all your normal environment variables and then eliminate them one by one (or vice versa).

---

### Post by mevun on 2012-11-17
> **agillator said:**
> Problem solved. [www.ubuntuforums.org/showthread.php?t=1930738]("http://www.ubuntuforums.org/showthread.php?t=1930738") led me to the solution. In short, cron passes a very limited and 'clean' environment to programs it is executing. My program depends on an environment variable that is in my 'normal' environment but not the one cron passes. I added this variable in my crontab as VARIABLE=VALUE in the global section and everything is now fine. If you are facing a similar problem, how you find the variable(s) is up to you. The brute force method, of course, is to add all your normal environment variables and then eliminate them one by one (or vice versa).

Glad to hear you solved your problem.

The following isn't really directed to you, but I thought I would comment on the debugging technique for the possible benefit of others.

With the brute force method, you shouldn't have to do it one-by-one if and only if there is only one missing env. variable.  The other way is to do it by binary search for the missing env. variable (the key).  So you leave out half the normal env. variables.  If it works, the key is in the half you left in, otherwise it is in the other half.  Then you take half of the respective half (which you know based on last result) and try again until you've narrowed it down to one.  It helps to have a good editor that can comment multiple lines at once in a block.  Of course, one does not need to do exact halves if you have a guess of the right answer.  So you can have the equivalent of searching an unbalanced tree with a probability of worse time.

In reality, it is hard to use for shell scripts  where oftentimes the env. variables are defined in terms of other env. variables, e.g. $USR_DIR=${HOME}/usr, as well as no guarantees that there is exactly one missing env. variable.

Anyway, this debugging technique of using binary search to find a bug, is one that more programmers should be familiar with.  I did not learn software engineering in college, but did take a few CS classes and we weren't taught much with respect to debugging.  I learned this technique from a colleague after a few years of work experience.

---

