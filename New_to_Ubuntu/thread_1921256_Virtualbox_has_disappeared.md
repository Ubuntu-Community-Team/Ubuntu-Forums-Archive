---
title: "Virtualbox has disappeared"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by gyozu on 2012-02-06
I installed and got VB (downloaded Lucid Lynx 64 bit version from VB site) running with Mint 12 yesterday. Later that day, I tried to get Kindle for PC with Wine and BitPM to work. Neither would work and I tried a variety of suggestions. 

Today I went to activate VB and it has disappeared from the Applications>System Tools placement. Now there is Dolphin and KpackageKit, which must have come in due to some of the mucking around I did.  


Any ideas on how to restore it or check to see if the virtual partition is still there?

Or, am I better off just reinstalling things?

---

### Post by ubudog on 2012-02-06
Could you try opening a terminal and typing the following?
```
virtualbox
```

What happens?  (press enter after typing virtualbox)

---

### Post by gyozu on 2012-02-06
> mdg1@mdg1-desktop:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose-qt
mdg1@mdg1-desktop:~$ 

Seems like it gone entirely?

---

### Post by gyozu on 2012-02-06
I don't know if this is of any use, bit I scanned home folder with "Disk Usage Analyzer"
.Virtualbox and Mint 12 still show up.
??????????????

---

### Post by ubudog on 2012-02-06
I think it's still there.  Try: 
```
virtualbox-ose
```

and see if it opens. 

:)

---

### Post by gyozu on 2012-02-06
I tried it two ways. Here is the response.

---

### Post by ubudog on 2012-02-06
The second time, you typed 'virtualbox -ose'.  It should be: 
```
virtualbox-ose
```
(together)

:)

---

### Post by gyozu on 2012-02-06
Yep, tried it together. No response.

---

### Post by LinuxFan999 on 2012-02-06
It looks like you will need to reinstall Virtualbox. Make sure to remove any remaining traces of the previous installation first.

---

### Post by bluexrider on 2012-02-06
For whatever reason Mint 12 let it go I would reinstall it and give it another whirl.

---

