---
title: "ubuntu 13.04 trying to update clamav"
date: 2013-09-30
forum: New to Ubuntu
---

### Post by rafaelbachman on 2013-09-30
trying to update clamav virus database. Downloaded new tar.gz package from clamav website but dont know how to use it.  Any help?

---

### Post by DuckHook on 2013-09-30
Are you running an e-mail server, web server or similar? If this is just a desktop Ubuntu installation, you do not need antivirus. It just hogs system resources, adds pointless complexity, distracts time and attention away from real security measures and actually adds more services/daemons at risk for attack. As I have posted elsewhere, AV on Linux is like wearing a parachute in a submarine.

[This]("http://ubuntuforums.org/showthread.php?t=510812") sticky on the security subforum is an excellent security primer.

However, if you insist on using *clam*, the manual is [here]("http://www.clamav.net/lang/en/doc/").

---

### Post by rafaelbachman on 2013-09-30
I know linux does not necessarily need an antivurs but I like to run it to scan windows partitions for viruses and remove them as i have other and friends computers i would like to use linux for removing and scanning for threats

---

### Post by DuckHook on 2013-09-30
I don't use *clam*, so hopefully, a knowledgeable user could jump in here to help. However, many different threads have mentioned that *clam* may not be the best or most reliable for scanning. I don't know much more than such generalities because I largely lost touch with AV when I converted from Windows. Sorry that I can't be of much further help.

---

### Post by SeijiSensei on 2013-09-30
The installation should have included the "freshclam" utility which handles updating the database for you.  If you don't have a copy of /usr/bin/freshclam, install the **clamav-freshclam** package.

I recommend putting a symbolic link to the freshclam binary in the /etc/cron.daily directory so the updater will run automatically each night:

```

cd /etc/cron.daily
sudo ln -s /usr/bin/freshclam

```

If you're really paranoid, you can put the link in /etc/cron.hourly instead.

---

### Post by rafaelbachman on 2013-09-30
thank you would avg be better than clam then?

---

### Post by DuckHook on 2013-10-01
As mentioned, I'm no longer familiar enough with AV (it's like being let out of jail :D). Hopefully *SeijiSensei* can advise. He's a server guru among other things.

---

### Post by Petro Dawg on 2013-10-01
From what I read in the past (which may not still be true) AVG performs better than CLAM, as in AVG catches more and has less false alarms.  I use AVG as default antivirus on my XP partitions (not that I ever log into them).

I'd probably just burn the AVG rescue CD (or USB) to use to scan other peoples windows partitions.  [http://www.avg.com/us-en/avg-rescue-cd-download](http://www.avg.com/us-en/avg-rescue-cd-download)

---

### Post by SeijiSensei on 2013-10-01
I use ClamAV with MailScanner to scan email for attached malware and, in conjunction with SquidClamAV, to scan all downloaded objects on a gateway server I built for a client.  My only problem with ClamAV is that it has a tendency to report false positives.  I think this probably results from the policy of allowing anyone to upload signatures to the database.  False positives eventually get weeded out, but it can take a while.  (I've wondered whether some of these submissions are trolls from Microsoft-haters, as we've gotten a few hits for updates from Microsoft's own servers.)  AVG, being a commercial product, is more tightly controlled.  When people using Windows ask me for advice about which antivirus product to use, I generally recommend AVG.  So if all you are interested in doing is scanning Windows machines for Windows malware, it's probably a better choice.

---

### Post by rafaelbachman on 2013-10-01
Thanks for the responses. Just trying to figure out why i cant get the database to update from downloading the tar.gz package from clamav website and the instructions not helping, haha.  Also any other tar ive tried to extract/convert to deb package using alien is not working says its corrupt or incomplete.  Trying to install playstaion media server, avg, and clamav virus database .98(whatever the recent one is).  Dont know what im doing wrong. can anyone help of point me to the correct thread please/thank you.

---

