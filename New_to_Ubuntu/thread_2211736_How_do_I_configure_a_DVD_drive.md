---
title: "How do I configure a DVD drive?"
date: 2014-03-17
forum: New to Ubuntu
---

### Post by fiona3 on 2014-03-17
New to Ubuntu 12.04 LTS and want to back stuff up to disc.

My desktop is a Dell and comes with a DVD RW drive and a read-only drive. 

I inserted blank DVDs in each drive. I installed XFBurn and Brasero and they both say there is no disc in the drive. 
At least they recognise that there is a drive. It's called PBDS DVD+-RW DH-16W 1S 
I still can't burn a disc though.

How else can I test the drive, or look at the configuration? 
Where would I find a list of attached hardware I could look through? 
Can anyone suggest a Terminal command to display better info?
Are there any key words I could search for?
E.G. I can see my printer in System Settings, but I don't know where to look for other peripheral devices in Ubuntu.

What can I do now, do you think? Should I look for drivers via the Ubuntu Software Centre? 
Sorry to post so stupidly, but I don't know where to start with this one, or what info to post. 

Fiona

---

### Post by SuperFreak on 2014-03-17
I have had good results with [K3B]("http://www.k3b.org/"). I don't know if that would solve your problems though. Have you tried using a different brand of media?

---

### Post by fiona3 on 2014-03-17
Many thanks. I installed K3B - quick & straightforward, glad I downloaded it. Appreciate the software tip.

Still "no medium", so enough of this seance! The drive or discs I have might be duds. I'll try a different disc tomorrow when the shops open.

Thanks again for help.

---

### Post by SuperFreak on 2014-03-17
Good Luck. An alternative might be to back up to USB stick or External Hard Drive. USB sticks are pretty cheap - I bought an 8GB Kingston Stick for about $6 the other day and larger sticks of 32 or 64 GB are even cheaper(Per GB). Plus you can rewrite these which you can't do with a DVD unless you use DVD RW

---

### Post by pqwoerituytrueiwoq on 2014-03-17
just to be sure the thing can burn
```
sudo hwinfo --cdrom
```
you will probally need to install that
```
sudo apt-get install hwinfo
```

---

### Post by monkeybrain20122 on 2014-03-18
```
sudo apt-get install libcdio-utils
```
Then run
```
cd-drive
```

hwinfo is no longer in the repo, it depends on hal and the later is deprecated.

---

