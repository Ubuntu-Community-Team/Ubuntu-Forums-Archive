---
title: "Scanner not detected"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by eduardo saxel on 2012-10-24
Hi there,

I've got my DCP-165C printer and scanner connected. It's on too.
I can print but can't scan. When I open the simple-scan, it says "no scanners detected". What to do?

Thanks on advance

---

### Post by danielbauwens on 2012-10-24
I'm not completely sure, but it might be you have to add it by printers incase it sees it like a printer:

```
System Settings > Printers > Add
```

Hope this helps.
Daniel

---

### Post by eduardo saxel on 2012-10-24
> **danielbauwens said:**
> I'm not completely sure, but it might be you have to add it by printers incase it sees it like a printer:

```
System Settings > Printers > Add
```

Hope this helps.
Daniel

It's already added. The printer is working normally, but the scanner (same printer) is not.

---

### Post by danielbauwens on 2012-10-24
Is it able to connect directly to the computer? 
If yes, I would suggest trying that.

---

### Post by plucky on 2012-10-24
> **eduardo saxel said:**
> It's already added. The printer is working normally, but the scanner (same printer) is not.

Go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html) and download the scanner driver for your printer and install.

Follow the instuctions how to install.

Good Luck

---

### Post by eduardo saxel on 2012-10-24
there's a list of drivers :

brscan3 32bit	rpm	0.2.11-4	60 KB	2011.Feb.04
brscan3 64bit	rpm	0.2.11-5	71 KB	2012.Jun.05
scan-key-tool 32bit	rpm	0.2.4-0	48 KB	2012.Oct.09
scan-key-tool 64bit	rpm	0.2.4-0	54 KB	2012.Oct.09
brscan3 32bit	deb	0.2.11-4	57 KB	2011.Feb.04
brscan3 64bit	deb	0.2.11-5	68 KB	2012.Jun.05
scan-key-tool 32bit	deb	0.2.4-0	45 KB	2012.Oct.09
scan-key-tool 64bit	deb	0.2.4-0	51 KB	2012.Oct.09

so, no clue on which one I need

---

### Post by plucky on 2012-10-24
> **eduardo saxel said:**
> there's a list of drivers :

brscan3 32bit	rpm	0.2.11-4	60 KB	2011.Feb.04
brscan3 64bit	rpm	0.2.11-5	71 KB	2012.Jun.05
scan-key-tool 32bit	rpm	0.2.4-0	48 KB	2012.Oct.09
scan-key-tool 64bit	rpm	0.2.4-0	54 KB	2012.Oct.09
brscan3 32bit	deb	0.2.11-4	57 KB	2011.Feb.04
brscan3 64bit	deb	0.2.11-5	68 KB	2012.Jun.05
scan-key-tool 32bit	deb	0.2.4-0	45 KB	2012.Oct.09
scan-key-tool 64bit	deb	0.2.4-0	51 KB	2012.Oct.09

so, no clue on which one I need

Either the 64bit brscan3.deb file if you are running a 64bit system or the 32bit brscan3.deb file if you are running a 32bit system.

Look at ```
uname -a
``` to see what system you are running.


Good Luck

---

### Post by eduardo saxel on 2012-10-24
> **plucky said:**
> Either the 64bit brscan3.deb file if you are running a 64bit system or the 32bit brscan3.deb file if you are running a 32bit system.

Look at ```
uname -a
``` to see what system you are running.


Good Luck


When trying to install it, terminal said dpkg requires superuser privilege. What to do ?

---

### Post by eduardo saxel on 2012-10-24
> **eduardo saxel said:**
> When trying to install it, terminal said dpkg requires superuser privilege. What to do ?

Ok, installed using alien. But now I really don't know what to do regarding the next step of the installing :

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html#dpkg1](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html#dpkg1)

---

### Post by eduardo saxel on 2012-10-24
> **eduardo saxel said:**
> Ok, installed using alien. But now I really don't know what to do regarding the next step of the installing :

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html#dpkg1](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html#dpkg1)

Ok, I made it using sudo, but how to use simple-scan as a normal user ?

---

### Post by plucky on 2012-10-24
Try installing sane-utils.

```
sudo apt-get install sane-utils
```

Then reboot and see if simple-scan will work.


Why did you use alien.If you double click a .deb file,it will open the Software Centre and install the application.

What does ```
uname -a
``` in a terminal produce?

---

