---
title: "Brute force attempts into my mailserver?"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by duceduc on 2012-02-25
Hi. I just noticed these live logs when I was tailing my mail.log. There were massive of this log entries with the same ip address.
> Feb 26 11:49:25 revomix postfix/smtpd[3074]: lost connection after AUTH from unknown[ip.address.]
Feb 26 11:49:25 revomix postfix/smtpd[3074]: disconnect from unknown[ip.address]
Feb 26 11:49:26 revomix postfix/smtpd[3074]: connect from unknown[ip.address]
Feb 26 11:49:26 revomix postfix/smtpd[3074]: lost connection after AUTH from unknown[ip.address]
Feb 26 11:49:26 revomix postfix/smtpd[3074]: disconnect from unknown[ip.address]
Feb 26 11:49:27 revomix postfix/smtpd[3074]: connect from unknown[ip.address]
Feb 26 11:49:28 revomix postfix/smtpd[3074]: lost connection after AUTH from unknown[ip.address]
Feb 26 11:49:28 revomix postfix/smtpd[3074]: disconnect from unknown[ip.address]
Feb 26 11:49:28 revomix postfix/smtpd[3074]: connect from unknown[ip.address]
Feb 26 11:49:25 revomix postfix/smtpd[3074]: lost connection after AUTH from unknown[ip.address.]
Feb 26 11:49:25 revomix postfix/smtpd[3074]: disconnect from unknown[ip.address]
Feb 26 11:49:26 revomix postfix/smtpd[3074]: connect from unknown[ip.address]
Feb 26 11:49:26 revomix postfix/smtpd[3074]: lost connection after AUTH from unknown[ip.address]
Feb 26 11:49:26 revomix postfix/smtpd[3074]: disconnect from unknown[ip.address]
Feb 26 11:49:27 revomix postfix/smtpd[3074]: connect from unknown[ip.address]
Feb 26 11:49:28 revomix postfix/smtpd[3074]: lost connection after AUTH from unknown[ip.address]
Feb 26 11:49:28 revomix postfix/smtpd[3074]: disconnect from unknown[ip.address]
Feb 26 11:49:28 revomix postfix/smtpd[3074]: connect from unknown[ip.address]

---

### Post by HeroOfCanton on 2012-02-25
Looks like it. You could block the IP, but I wouldn't expect that to help for very long. Are they getting authenticated or is it failing? Are they hitting a particular account or does it look more like a script testing different logins?

Sorry, I'm used to more detailed logs.

If they are not getting authenticated it's really not atypical. You can setup measures like a limited number of attempts and such. That's what I did after an account on one of my servers was compromised. 10 failed attempts and wait 90 minutes! Worked like a charm (along with stricter password requirements).

---

### Post by d4m1r on 2012-02-25
You should have posted the IP and I could have told you where it was coming from.

Anyway, I also noticed my Apache server was being bruteforced, there are bots on the internet than scan all possible IPs and Ports and there is nothing we can do...Most infected PCs seem to coming from China or Southeast Asia in my case.

Google "fail2ban", install it, and configure it to work with your specific mail server applications (it supports many many different applications).

---

### Post by duceduc on 2012-02-25
This is pretty much all there is to the log. Just repetition of the same ip. 

I didn't want to post the ip just in case it wasn't hack. I can't say for sure if they are using an exact email address. I don't think so or it show up on log. It is probably coming from China. As most of my email accounts were attacked from China. 

I use flurdy's guide for my mail server. How do I setup security measures? What files do I need to edit?

I saw a thread about fail2ban. I will also look into that as well.

---

### Post by Old_Grey_Wolf on 2012-02-25
If you expose a service like mail, ssh, rdp, ftp, etc., this happens. There are all sorts of people/BOTS looking for open services. As long as they aren't successful at getting into your server then don't get to paranoid about it. At first it bothered me; however, I have seen so many failed attempts over the years that I find it funny these days.

I am not complacent assuming I am secure. I still check the logs occasionally.

---

### Post by HeroOfCanton on 2012-02-25
You can start here [http://flurdy.com/docs/postfix/#extend](http://flurdy.com/docs/postfix/#extend)

Like Gray Wolf said though, if they aren't getting in it's really nothing to lose sleep over. I'm not familiar with that mail system, but the attempts per timeframe thing worked great for me even after a compromise (and therefore greatly increased attempts).

---

### Post by enjoijesus94 on 2012-02-25
Make Your Password Isnt Weak.
Very Very Bad When Bruteforcing Comes Along.

Same Goes For Router,Accounts,MailServers.

Looks Like Somebody Tried To Get Into Your MailServer.

I Dont Know Why They Would BruteForce.

Getting Into Mail Accounts Is Easy.

Anyway Just Make Sure The Password Isnt Weak.
Just To Be Sure He Or She BruteForces Again.

---

### Post by duceduc on 2012-02-25
I am looking at the auth.log as well. I don't see any activities within those timeframe of attacks. They weren't successful if there were no entries?

---

### Post by collisionystm on 2012-02-25
if you are worried you could just install Fail2Ban

---

### Post by HeroOfCanton on 2012-02-25
> **duceduc said:**
> I am looking at the auth.log as well. I don't see any activities within those timeframe of attacks. They weren't successful if there were no entries?

Correct. If nothing was authed you have most likely not been compromised in any way. Failed attempts are common. Probably just a bot scanning your server looking for an easy target to send spam from.

---

### Post by Old_Grey_Wolf on 2012-02-25
> **duceduc said:**
> I am looking at the auth.log as well. I don't see any activities within those timeframe of attacks. They weren't successful if there were no entries?

I don't think you have been compromised.

Here is a sticky from the Security sub-forum that you may want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812). Although it is old, it has some good links on how to detect intrusions.

---

### Post by CharlesA on 2012-02-25
> **Old_Gray_Wolf said:**
> I don't think you have been compromised.

Here is a sticky from the Security sub-forum that you may want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812). It has some good links for detecting intrusions.
The link in my sig has some basics too. :)

---

### Post by Old_Grey_Wolf on 2012-02-25
> **CharlesA said:**
> The link in my sig has some basics too. :)

Nice guide! =D>
[COLOR="White"].
.
.[/COLOR]

---

### Post by duceduc on 2012-02-26
Thanks guys for the info.

---

