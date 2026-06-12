---
title: "Ubuntu 13.04 Update Won't Run"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by RichieB07 on 2013-05-30
When i try to install updates, it comes up saying:

 "Requires installation of untrusted packages

This requires installing packages from unauthenticated sources."

I click on "Ok" and it just closes out.


Here's the list of updates:
[http://i61.photobucket.com/albums/h66/BrokenSilences07/Swagbucks/Selection_001_zpsa05d1689.png](http://i61.photobucket.com/albums/h66/BrokenSilences07/Swagbucks/Selection_001_zpsa05d1689.png)

And the message after:
[http://i61.photobucket.com/albums/h66/BrokenSilences07/Swagbucks/Selection_002_zps6b0b3601.png](http://i61.photobucket.com/albums/h66/BrokenSilences07/Swagbucks/Selection_002_zps6b0b3601.png)

---

### Post by ibjsb4 on 2013-05-31
In terminal:

```
sudo apt-get update
```

That should tell you what package.

---

### Post by RichieB07 on 2013-05-31
W: GPG error: [https://download.01.org](https://download.01.org) Ubuntu Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8D8847D52F4AAA66

Edit:
Okay so I ran "sudo apt-get upgrade" and it asked if I wanted to upgrade without the verification.  I said yes, and now it's running just fine.  It was the X.Org update that was causing the trouble.  I recently installed the Intel Linux Graphics Drivers program, so I'm sure that's why it did this.

---

### Post by ibjsb4 on 2013-05-31
Replace the pubkey with yours (8D8847D5 2F4AAA66).

[http://ubuntuforums.org/showthread.php?t=1869890&p=11395810&viewfull=1#post11395810](http://ubuntuforums.org/showthread.php?t=1869890&p=11395810&viewfull=1#post11395810)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+NO_PUBKEY&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+NO_PUBKEY&sa=Search&cof=FORID:9)

---

