---
title: "Problems with Update Manager"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by BlackDaemonion on 2008-05-29
Whenever I attempt to use update manager or even download let say.. a codec to use mp3 and other video ones, etc I get a nice error:

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_CA.bz2)  
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_CA.bz2)  
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_CA.bz2)  
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_CA.bz2)  
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_CA.bz2)  
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_CA.bz2)  
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_CA.bz2)  
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_CA.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.

I have no bloody idea how to fix this and couldn't find anything to help.
Any help would be much appreciated

Cheers

---

### Post by rubrboots on 2008-05-29
I am having a similar problem, every time I try to update or install software through synaptic I get this:

```
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out 
```

HELP!!!

---

### Post by ercferret18 on 2008-05-29
just checking lol... are you connected to the internet?

---

### Post by rubrboots on 2008-05-29
Yep, I am posting this on the very same computer.

---

### Post by BlackDaemonion on 2008-05-29
As am I, lol

---

### Post by ercferret18 on 2008-05-29
it seems like your update manager can't connect to the internet... try going to system, administration, network proxy and setting your proxy settings there. see if that works

---

### Post by BlackDaemonion on 2008-05-29
I went into Network and eth1 and eth0 were both set to 'roaming', so I changed them to DHCP and it wont pick up an address...

---

### Post by ercferret18 on 2008-05-29
hmm... all i know is that synaptic package manager can't connect to the internet but firefox can... try disabling any firewalls you have

---

### Post by rubrboots on 2008-05-29
GOT IT!. Looks like the Canadian servers are down, Go to System --> Administration --> Software Sources and change "Server for Canada" to "Main Server" this has happened before but I didn't know what was happening, I think I willjust stick the main server from now on.

---

### Post by ercferret18 on 2008-05-29
LOL why were they even set to canadian?

---

### Post by BlackDaemonion on 2008-05-29
Cheers mate! thanks a lot!

---

### Post by rubrboots on 2008-05-29
LOL, cuz we live in Canada EH!

---

### Post by BlackDaemonion on 2008-05-29
Some of us LIVE in Canada dude =P

---

### Post by BlackDaemonion on 2008-05-29
*insert stereotypical Canadianism*

---

### Post by ercferret18 on 2008-05-29
lol america is better =P

---

### Post by BlackDaemonion on 2008-05-29
Now, now, lets not start one of those debates...

---

### Post by ercferret18 on 2008-05-29
good idea lol

---

### Post by temaki on 2008-05-29
thank you guys that worked! being a newbie myself, i was going to reinstall! thank you thank you thank you

---

### Post by ercferret18 on 2008-05-31
you're welcome! don't think i did anything to help though...

---

