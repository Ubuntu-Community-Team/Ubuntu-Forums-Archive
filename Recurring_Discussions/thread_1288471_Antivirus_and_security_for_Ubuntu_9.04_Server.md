---
title: "Antivirus and security for Ubuntu 9.04 Server"
date: 2009-10-11
forum: Recurring Discussions
---

### Post by abioticrhyme on 2009-10-11
I am new (a newbie) to using Ubuntu 9.04 server so please forgive me if this sounds totally paranoid. Right now I am very concerned about infecting others that might visit my site. Even though I use Ubuntu on my laptop and desktop at home when I am at work or at school I am forced to use Windows machines to upload files including pictures and music I share with my family. I am not sure if it is possible to infect someone streaming to them or if they are viewing pictures on my site, I believe it is, but I do not want to risk infecting others. I currently have Clam Av installed but I am not sure how well it protects against viruses and malicious code that can infect Windows machines. Am I right in my thinking or totally wrong? What other precautions should I take to secure my server?

Thanks,

AbioticRhyme

---------------- Now playing: [Headstrong - The Truth (David West Remix)]("http://www.foxytunes.com/artist/headstrong/track/the+truth") via [FoxyTunes]("http://www.foxytunes.com/signatunes/")

---

### Post by Rich_Roast on 2009-10-11
Clam AV should protect against all known viruses, including those that compromise Windows systems. It is considered polite to scan for viruses when networking with Windows boxes, so this is a good thing.

Other good security policies are to shut down any services that aren't being used, particularly any beginning with r (like rsync, if you're not a backup server), and configure a firewall to protect your machine from unknown things trying to connect with it; on Mint ufw is installed by default, for example (but needs to be activated). Apply common sense when browsing and opening email attachments.

To verify what the outside world can see the computer can be audited using nmap, preferably on a separate machine on the network, to scan the computer and see if there are any interesting ports open; ideally there won't be.

---

### Post by cariboo on 2009-10-11
If you are that worried about infecting other people, why not upload the pictures and music to a directory that only you have access to, then check them for malware first before posting the files where others can access them.

---

### Post by fela on 2009-10-11
I don't understand this 'good etiquette to use up power scanning for windows viruses so that windows users can be lazy' policy. If you're gonna use windows, get some decent security and work out yourself how you're gonna avoid viruses, I say. It isn't the responsibility of Linux users to make sure windows users don't get viruses.

---

### Post by CharlesA on 2009-10-11
> **fela said:**
> I don't understand this 'good etiquette to use up power scanning for windows viruses so that windows users can be lazy' policy. If you're gonna use windows, get some decent security and work out yourself how you're gonna avoid viruses, I say. It isn't the responsibility of Linux users to make sure windows users don't get viruses.

So, if a person is storing a file that is infected with a virus on **your** server, who's responsibility is it to deal with said virus?

Ounce of prevention is worth a pound of cure, or so they say.

Personally I've got clamav running on my server, I've got it set to scan the entire file system every night. I don't care if linux isn't virus prone, but when it's being used in a hybrid linux/windows environment, you are better safe then sorry. I would rather have my "wasted" power scanning user files then risk having a bunch of machines being infected (even if I do have decent AV on them).

> **cariboo907 said:**
> If you are that worried about infecting other people, why not upload the pictures and music to a directory that only you have access to, then check them for malware first before posting the files where others can access them.

This would be the best course of action tbh. If you are that worried, upload them where you have access and scan them before sending them out.

---

### Post by donato roque on 2009-10-12
Those Windows users can be your mother or father or your closest friend.
The original poster in fact are worried about those people close to her who still use windows.

---

### Post by abioticrhyme on 2009-10-12
> **cariboo907 said:**
> If you are that worried about infecting other people, why not upload the pictures and music to a directory that only you have access to, then check them for malware first before posting the files where others can access them.

Actually I had not thought of doing it that way. Thanks for the idea. 


AbioticRhyme
 ---------------- Now playing: [Armin Van Buuren - Edge Of Space (Whiteroom Remix)]("http://www.foxytunes.com/artist/armin+van+buuren/track/edge+of+space") via [FoxyTunes]("http://www.foxytunes.com/signatunes/")

---

### Post by rnodal on 2009-10-13
Sorry for sabotaging,
Can ClamAV be used as an on demand virus scanner? 

Like if I wanted to scan /data/somedir? I thought it was only intended for
email attachments scans.

Any input would be appreciated.

-r

---

### Post by cariboo on 2009-10-13
You can start a scan of a directory manually. I tried clamav at one time, but found it wasn't worth the effort. I use Thunderbird for my email client, the only two viruses I'v ever seen were attachments, so they were pretty easy to get rid of.

---

### Post by rnodal on 2009-10-13
Well, 

I run a server and I would like to scan uploaded files for viruses. I will inspect ClamAV closely.

Thank you!

-r

---

### Post by CharlesA on 2009-10-13
I've got it set to scan the entire drive once a day. Works well for me.

---

### Post by rnodal on 2009-10-13
> **CharlesA said:**
> I've got it set to scan the entire drive once a day. Works well for me.

Do you know of a guide that explains the process of using ClamAV as an on demand scanner? Or is it just a manner of just apt-get install clamav and then running it from the command line like any other system tool?

Any input appreciated.

-r

---

### Post by CharlesA on 2009-10-13
> **rnodal said:**
> Do you know of a guide that explains the process of using ClamAV as an on demand scanner? Or is it just a manner of just apt-get install clamav and then running it from the command line like any other system tool?

Any input appreciated.

-r

The help file is pretty good.

I just did an apt-get install clamav. It setups up an update daemon that updates the virus definitions every hour.

Basically to scan something, just cd to that folder and run:

```
clamscan (-options) (path to target)
```

I use: ```
clamscan -ri /
```

So that it'll recursively scan the root directory and only display and infected files.

Hope that helps. :-)

---

### Post by rnodal on 2009-10-13
> **CharlesA said:**
> The help file is pretty good.

I just did an apt-get install clamav. It setups up an update daemon that updates the virus definitions every hour.

Basically to scan something, just cd to that folder and run:

```
clamscan (-options) (path to target)
```

I use: ```
clamscan -ri /
```

So that it'll recursively scan the root directory and only display and infected files.

Hope that helps. :-)

NICE! What you just wrote is all I needed. :)
Thank you!!!

-r

---

### Post by Viva on 2009-10-14
It is not a matter of morals or etiquette, your site will be blacklisted by major security companies if it spreads viruses.

---

### Post by SunnyRabbiera on 2009-10-14
> **Viva said:**
> It is not a matter of morals or etiquette, your site will be blacklisted by major security companies if it spreads viruses.

Indeed, on a server antivirus is far more needed.
Not to protect the server in the case of linux but to protect others.

---

### Post by abioticrhyme on 2009-10-14
I came across this in Ubuntu Hacks to help automate antivirus scans. 
I added it to my crontab this evening, hope this can help others also. 

00 3 * * * root mkdir /tmp/virus ; clamscan -ri --log=/var/log/clamscan.log --move=/tmp/virus /

---

### Post by CharlesA on 2009-10-15
> **abioticrhyme said:**
> I came across this in Ubuntu Hacks to help automate antivirus scans. 
I added it to my crontab this evening, hope this can help others also. 

00 3 * * * root mkdir /tmp/virus ; clamscan -ri --log=/var/log/clamscan.log --move=/tmp/virus /

Nice command, thanks!

I've got mine set to shoot me an email with the results daily, so I can deal with any threats at that time. Does the log mention where the original file was located?

---

### Post by abioticrhyme on 2009-10-15
> **CharlesA said:**
> Nice command, thanks!
 
I've got mine set to shoot me an email with the results daily, so I can deal with any threats at that time. Does the log mention where the original file was located?
 
I am not sure yet I just set this up last night and it ran its first scan. Can I ask how you set yours up to send you an email?

---

### Post by CharlesA on 2009-10-15
> **abioticrhyme said:**
> I am not sure yet I just set this up last night and it ran its first scan. Can I ask how you set yours up to send you an email?

I set it up in cron.

Here's what my crontab looks like:
```
# Scan / for viruses every day at midnight
0 0 * * * ~/avscan >/dev/null 2>&1
```the file ~/avscan is executable and looks like this:
```
clamscan -ri --exclude-dir=^/sys\|^/proc\|^/dev / | mail -s "ClamAV Scan Results for `date +%D`" email@domain.com
```

It'll send an email with the subject of: "ClamAV Scan Results for 10/15/2009" to whatever email address is set.

Hope this helps!

---

